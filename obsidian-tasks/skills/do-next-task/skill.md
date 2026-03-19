---
name: obsidian-tasks:do-next-task
description: Read the user's Obsidian daily note, find the highest priority incomplete task, attempt to complete it autonomously, then mark it done and report back.
---

# Do Next Task

## Overview

This skill reads the user's Obsidian vault daily note, identifies the highest priority incomplete task using the [Obsidian Tasks plugin](https://github.com/obsidian-tasks-group/obsidian-tasks) conventions, attempts to complete it if capable, and marks it done.

The daily note aggregates tasks from across all daily notes via Tasks plugin query blocks — so you must search across the vault for incomplete tasks, not just today's note.

## Steps

### 1. Read today's daily note

Today's date is available via the `currentDate` context. The vault is at `~/personal/obsidian-vault/`. Daily notes follow the path pattern:

```
daily-notes/YYYY/Dth_Mon_YYYY.md
```

For example: `daily-notes/2026/19th_Mar_2026.md`

Read today's daily note to understand the task sections present (`Working On`, `Reading`, `Side of Desk`, etc.).

### 2. Find all incomplete tasks across the vault

Use Grep to search for `- [ ]` across all files under `daily-notes/YYYY/` to find every open task aggregated by the Tasks plugin. Filter to only tasks that appear under relevant headings (`Working On`, `Reading`, `Side of Desk`).

### 3. Determine priority

The Obsidian Tasks plugin uses emoji priority markers:

- 🔺 Highest
- ⏫ High
- 🔼 Medium
- (no marker) Normal
- 🔽 Low

Pick the highest priority incomplete task. If multiple tasks share the same priority, prefer the one from the most recent daily note.

### 4. Assess capability

Before attempting the task, consider:

- Does the task require action in external systems you have access to (GitHub, etc.)?
- Does it require information you don't have?
- Is it something that requires human judgment or physical action?

If you cannot complete the task autonomously, clearly explain what is needed from the user and stop.

### 5. Attempt the task

Complete the task using available tools. Be explicit about what you are doing and any decisions you make along the way.

If partway through you discover you need more information, stop and ask rather than guessing.

### 6. Mark as done and report

Once the task is complete (or if you cannot complete it), update the task in the daily note file where it lives by changing `- [ ]` to `- [x]`.

Report back with:

- What the task was
- What you did
- Any decisions or trade-offs made
- Anything the user needs to follow up on manually
