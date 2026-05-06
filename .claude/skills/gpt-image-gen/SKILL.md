---
name: gpt-image-gen
description: Use this skill whenever an agent needs to generate an image from a text prompt. Calls the OpenAI Images API (gpt-image-2) and saves the result as a PNG file. Requires OPENAI_API_KEY in .env.
---

# gpt-image-gen — OpenAI Image Generation Wrapper

Generates a PNG image from a prompt using OpenAI's `gpt-image-2` model.

## Prerequisites

- `OPENAI_API_KEY` set in the project `.env` file
- `curl` available (standard on macOS/Linux/Git Bash)
- `jq` OR `python3` for base64 decoding

## Inputs

| Variable | Description |
|----------|-------------|
| `PROMPT` | The image generation prompt (string) |
| `OUTPUT_PATH` | Destination path for the PNG, e.g. `yuval/outputs/2026-05-06-my-image.png` |

## Step 1 — Load API Key

```bash
# From project root
set -a && source .env && set +a
```

If `OPENAI_API_KEY` is empty after sourcing, halt:
```
Error: OPENAI_API_KEY is not set. Add it to .env and retry.
```

## Step 2a — Generate Image (curl + jq, primary)

```bash
curl -s -X POST "https://api.openai.com/v1/images/generations" \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H "Content-Type: application/json" \
  -d "{
    \"model\": \"gpt-image-2\",
    \"prompt\": \"$PROMPT\",
    \"size\": \"1024x1024\",
    \"quality\": \"medium\",
    \"output_format\": \"png\"
  }" | jq -r '.data[0].b64_json' | base64 --decode > "$OUTPUT_PATH"
```

## Step 2b — Generate Image (Python fallback, when jq unavailable)

```python
import json, base64, subprocess, os, sys

prompt = os.environ["PROMPT"]
output_path = os.environ["OUTPUT_PATH"]
api_key = os.environ["OPENAI_API_KEY"]

payload = json.dumps({
    "model": "gpt-image-2",
    "prompt": prompt,
    "size": "1024x1024",
    "quality": "medium",
    "output_format": "png"
})

result = subprocess.run(
    ["curl", "-s", "-X", "POST",
     "https://api.openai.com/v1/images/generations",
     "-H", f"Authorization: Bearer {api_key}",
     "-H", "Content-Type: application/json",
     "-d", payload],
    capture_output=True, text=True
)

try:
    data = json.loads(result.stdout)
    b64 = data["data"][0]["b64_json"]
    with open(output_path, "wb") as f:
        f.write(base64.b64decode(b64))
    print(f"Saved: {output_path}")
except (KeyError, json.JSONDecodeError) as e:
    print(f"API error: {result.stdout}", file=sys.stderr)
    sys.exit(1)
```

Run as: `python3 generate_image.py` (after writing the script to a temp file with the env vars set).

## Step 3 — Verify Output

```bash
if [ -f "$OUTPUT_PATH" ] && [ -s "$OUTPUT_PATH" ]; then
  echo "Success: $OUTPUT_PATH ($(wc -c < "$OUTPUT_PATH") bytes)"
else
  echo "Error: output file missing or empty at $OUTPUT_PATH"
  exit 1
fi
```

## Error Handling

| Condition | Action |
|-----------|--------|
| `OPENAI_API_KEY` missing or empty | Halt, prompt user to add key to `.env` |
| API returns non-200 / error JSON | Surface raw error message to user |
| Output file missing after write | Report failure; show raw API response for debug |
| `jq` not found | Fall back to Python method automatically |
