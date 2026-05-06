# Image Generation Skill — Reference

Yuval uses the **gpt-image-gen** skill for all image generation.

**Skill definition**: `.claude/skills/gpt-image-gen/SKILL.md`

The skill wraps the OpenAI Images API (`gpt-image-2` model) and handles:
- Loading `OPENAI_API_KEY` from `.env`
- Sending the prompt via curl
- Decoding the base64 PNG response (with Python fallback when jq is unavailable)
- Saving the result to disk and verifying the output

**Requires**: `OPENAI_API_KEY=` set in `.env` (see `.env.example`).
