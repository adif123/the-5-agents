# Yuval Agent — Working Directory

This folder is the working directory for the **Yuval** creative visual agent.

**Agent definition** (read by Claude Code): `.claude/agents/yuval.md`

## Folders

- `reference/` — Place style/inspiration images here. Yuval scans these before each generation to extract color palettes, composition patterns, and visual style. Empty = no style enrichment.
- `outputs/` — Generated images are saved here, named `YYYY-MM-DD-<slug>.png`. Each image has a sibling `.txt` file with the exact prompt used (for iteration).

## Usage

Ask the CEO agent (or Yuval directly) to generate an image:
- עברית: "צור תמונה של ..." / "תמונה של ..."
- English: "Generate an image of ..." / "Create a picture of ..."
