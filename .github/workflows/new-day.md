---
name: New Day
description: Adds a daily update entry to index.html confirming the workflow ran for the current UTC date.
on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:
engine: copilot
permissions:
  contents: read
  copilot-requests: write
tools:
  edit:
safe-outputs:
  create-pull-request:
    allowed-files:
      - "index.html"
    max: 1
---

# New Day

## Task

Use the workflow run's **UTC date** (the date the run started, in
`Month Dth` wording, e.g. "28th of August") as today's date.

In `index.html`:

1. Add today's date to the existing **Daily Updates** navigation
   (`.daily-updates-list`), following the existing HTML structure, ID
   conventions (e.g. `id="august-1-dialog"`), date wording, and button markup
   used by the existing entries.
2. Add a matching accessible `<dialog>` element with the same structure as the
   existing daily update dialogs (header, close button, question heading,
   answer paragraph) that confirms the daily update workflow ran successfully
   for today's date.
3. Do **not** modify `styles.css`.
4. Do **not** duplicate a date, navigation control, or dialog. If a
   navigation entry or dialog for today's UTC date already exists, make no
   change.
5. Preserve every existing daily update entry and dialog exactly as-is.

Only modify `index.html`. If no change is needed, make no changes at all.
