# Obsidian Vault Workflow Skill

## Overview

ה-skill שמאכף את פרוטוקול ה-vault על Claude Code. מוגדר ב-`.claude/skills/obsidian-vault-workflow/SKILL.md`. מחייב שימוש בתחילת כל משימה (Phase 1: קריאת context) ובסוף כל משימה (Phase 2: כתיבת Session Log). כולל מבנה קובץ מדויק, תגיות status, wikilinks, ועדכון Overview.

**Skills Obsidian קיימים:**
- `obsidian-vault-workflow` — פרוטוקול read/write
- `obsidian-markdown` — כתיבה נכונה ב-Obsidian markdown
- `obsidian-bases` — שימוש ב-Obsidian Bases

## Open Questions

- none

## Session Log

### 2026-05-06 — תיעוד skill ראשוני [shipped]
- **What was done:** קריאת ה-SKILL.md המלא (228 שורות). הבנת פרוטוקול Phase 1 + Phase 2, מבנה קבצים, status tags, anti-patterns.
- **Decisions:** יש להפעיל את ה-skill אוטומטית בכל סשן — לא רק כשמתבקש.
- **Notes / Caveats:** ה-skill מגדיר anti-patterns מפורשים — בפרט: לא ליצור קבצים ממוארים, תמיד לוודא Read-back לאחר כתיבה, תמיד wikilinks ב-Related.
- **Related:** [[project-documentation-setup]], [[skills-catalog]]
