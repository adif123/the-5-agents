# Superpowers Skills Install

## Overview

התקנה ידנית של ספריית skills מהמאגר הפתוח [obra/superpowers](https://github.com/obra/superpowers). הותקנו 14 skills ל-`.claude/skills/`. המאגר לא כלל `commands/` או `agents/`. Skills אלה מוסיפים יכולות meta לעבודה עם Claude Code: תכנון, debugging, code review, ועוד.

## Open Questions

- none

## Session Log

### 2026-05-06 — התקנת 14 skills מ-superpowers [shipped]
- **What was done:** clone של `obra/superpowers` ל-temp, העתקה של 14 תיקיות skills ל-`.claude/skills/` ללא דריסת קבצים קיימים. commit ו-push ל-`origin/main`.
- **Decisions:** שימוש ב-`cp -r` עם בדיקת קיום לפני כל העתקה — הגנה על קבצים מקוריים.
- **Notes / Caveats:** ה-skill `obsidian-vault-workflow`, `obsidian-bases`, `obsidian-markdown` כבר היו קיימים לפני ה-clone (נוצרו ידנית). commit hash: `189f6b0`.
- **Related:** [[project-structure]], [[obsidian-vault-workflow-skill]]
