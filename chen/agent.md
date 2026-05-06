# Chen — Web Researcher (pointer doc)

Chen is the web-research sub-agent of `the-5-agents`. She finds current articles on the web, filters for reliable sources, and saves the chosen one as a prepared input file in `Content/` for Yael to later rewrite.

- **Canonical agent definition:** [.claude/agents/chen.md](../.claude/agents/chen.md)
- **Search memory log:** [chen/Memory/searches.md](Memory/searches.md)
- **Output directory:** project-root [`Content/`](../Content/) — Yael's inbox

Chen reports to the CEO after every run. She never invokes Yael directly; the CEO decides whether the next step is rewriting.

Tools: `WebSearch`, `WebFetch`, `Read`, `Write`, `Edit`, `Glob`, `Grep`. No Bash, no external API skills.
