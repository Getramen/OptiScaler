---
name: add-or-update-quirk
description: Workflow command scaffold for add-or-update-quirk in OptiScaler.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-update-quirk

Use this workflow when working on **add-or-update-quirk** in `OptiScaler`.

## Goal

Adds or modifies a 'quirk' (special-case logic or compatibility fix) for a specific game or scenario.

## Common Files

- `OptiScaler/misc/Quirks.h`
- `OptiScaler/dllmain.cpp`
- `OptiScaler/inputs/FG/DLSSG_Mod.h`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit OptiScaler/misc/Quirks.h to add or modify a quirk
- Optionally update related files (dllmain.cpp, DLSSG_Mod.h, etc.) if the quirk requires integration
- Commit with a message referencing the quirk or game

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.