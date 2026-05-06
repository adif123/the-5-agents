# CEO Agent Setup

## Overview

הקמת CEO Agent — סוכן ה-orchestration הראשי של מערכת `the-5-agents`. ה-CEO הוא נקודת הכניסה היחידה לכל משימה מהמשתמש. הוא מנתח את המשימה, בוחר סוכן-משנה מהרג'יסטרי, מעביר אליו את העבודה, ומסכם את הפלט. ה-CEO לא מבצע עבודת תוכן בעצמו.

**קבצים מרכזיים:**
- `agent.md` (שורש הפרויקט) — config שנקרא בכל ריצה: identity, registry, routing rules, output format, language
- `.claude/agents/ceo.md` — הגדרת ה-agent ב-Claude Code עם frontmatter + system prompt בן 5 שלבים

## Open Questions

- מה השמות והתפקידים הסופיים של 4 הסוכנים? (כרגע: researcher, writer, coder, analyst — placeholders)
- האם ה-CEO יתעד את היסטוריית הניתוב תוך הסשן עבור המשתמש?
- מה ה-fallback כשכוונת המשתמש חוצה כמה סוכנים?

## Session Log

### 2026-05-06 — הקמת CEO Agent v1.0 [shipped]
- **What was done:** נוצרו `agent.md` (registry עם 4 stubs: researcher, writer, coder, analyst) ו-`.claude/agents/ceo.md` (system prompt בן 5 phases: boot, intake, routing, delegation, consolidation + error handling). עודכן `_index.md` של vault.
- **Decisions:** registry ב-`agent.md` נפרד מקובץ ה-agent — שינוי registry לא דורש שינוי קוד. 4 stubs עם `status: placeholder` כדי ש-CEO יודע שיש 4 slots מוגדרים אבל לא מיושמים. CEO משתמש ב-Read tool כדי לקרוא `agent.md` בכל ריצה.
- **Notes / Caveats:** כל 4 הסוכנים הם placeholders — ה-CEO יודיע למשתמש אם ינתב אליהם. לא נוצרו קבצי agent נפרדים לסוכנים עצמם (out of scope v1.0).
- **Related:** [[project-structure]], [[skills-catalog]], [[project-documentation-setup]]
