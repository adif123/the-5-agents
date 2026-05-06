# Yael Agent — Working Directory

This folder is the working directory for the **Yael** content-writer agent.

**Agent definition** (read by Claude Code): `.claude/agents/yael.md`

## Files & Folders

- `style-guide.md` — **user-maintained**. The project's voice/tone guide. Yael reads it at the start of every session. Optional but strongly recommended.
- `reference/` — examples of past content that demonstrates the project's voice. Yael reads all `.md` files here at the start of every session. Optional.

## How Yael Fits Into the Pipeline

```
Content/<article>.md
       │
       ▼  (CEO routes "rewrite this" → yael)
     Yael
       │
       ▼
Output/<article>.md  (rewritten draft, with {{IMAGE_NEEDED}} placeholders)
       │
       ▼  (CEO Phase 4.5: invoke yuval for each placeholder, substitute)
Output/<article>.md  (final, with images embedded)
       │
       ▼  (CEO moves source)
Content/Ready/<article>.md
```

Yael is **LLM-only**: she has Read, Write, Edit, Glob, Grep — no Bash, no Web, no API. She cannot invoke Yuval directly; she leaves placeholders and the CEO handles the rest.
