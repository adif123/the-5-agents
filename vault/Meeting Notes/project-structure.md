# Project Structure

## Overview

מבנה הפרויקט הבסיסי של `the-5-agents`. הפרויקט הוא מערכת multi-agent ליצירת תוכן: סוכן ראשי (CEO) מנהל צוות סוכנים מתמחים. שורש הפרויקט מכיל את קבצי ההגדרה, תצורת Claude Code תחת `.claude/`, vault תיעוד ב-Obsidian, ומשתני סביבה.

**קבצים מרכזיים:**
- `CLAUDE.md` — הוראות ל-Claude Code על הפרויקט
- `.env` / `.env.example` — משתני סביבה (GITHUB_TOKEN, ANTHROPIC_API_KEY)
- `.gitignore` — מוציא `.env` מה-git
- `.claude/agents/` — הגדרות סוכנים (ריק כרגע)
- `.claude/skills/` — skills מ-superpowers + obsidian
- `.claude/commands/` — פקודות מותאמות (ריק כרגע)
- `.obsidian/` — תצורת Obsidian לקריאת ה-vault

## Open Questions

- אילו סוכנים ספציפיים יוגדרו תחת `.claude/agents/`?
- מה טכנולוגיית הבסיס של הפרויקט (Python? Node.js?)

## Session Log

### 2026-05-06 — הקמת מבנה פרויקט בסיסי [shipped]
- **What was done:** נוצרו `.claude/agents/`, `.claude/skills/`, `.claude/commands/`, `CLAUDE.md`, `.env`, `.env.example`, `.gitignore`. הועלה ל-GitHub בריפו `adif123/the-5-agents`.
- **Decisions:** שימוש ב-`.gitkeep` לשמירת תיקיות ריקות ב-git; `.env` מוחרג מה-git להגנה על מפתחות.
- **Notes / Caveats:** ה-GitHub token הראשוני נחשף בצ'אט — יש להחליפו.
- **Related:** [[superpowers-skills-install]], [[project-documentation-setup]]
