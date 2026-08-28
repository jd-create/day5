---
name: Highlights of Day
description: Fetches the GitHub Agentic Workflows FAQ and adds one unused Q&A to today's Daily Updates entry in index.html.
on:
  schedule:
    - cron: "0 */6 * * *"
  workflow_dispatch:
engine: copilot
permissions:
  contents: read
  copilot-requests: write
tools:
  edit:
  web-fetch:
network:
  allowed:
    - gh-aw
safe-outputs:
  create-pull-request:
    allowed-files:
      - "index.html"
    max: 1
---

# Highlights of Day

## Task

1. Use the workflow run's **UTC date** (Month Dth wording, e.g. "28th of
   August") as today's date.

2. Fetch the GitHub Agentic Workflows FAQ:
   https://github.github.com/gh-aw/reference/faq/

3. Read `index.html` and identify every FAQ question already represented in
   any `.daily-update-dialog` (by question text, not just by date).

4. Select **one** FAQ question from the fetched page that is not already
   represented in `index.html`. If every fetched FAQ is already represented,
   make no change.

5. Determine today's Daily Updates entry:
   - If a navigation control and dialog for today's UTC date already exist:
     - If that dialog already contains an FAQ question/answer, make no
       change.
     - Otherwise (it is a placeholder dialog without an FAQ), reuse that
       same dialog and add the selected FAQ's question and a concise,
       accurate answer to it.
   - If no navigation control or dialog exists yet for today's UTC date, add
     a new navigation control and a new matching dialog containing the
     selected FAQ's question and answer.

6. Match the existing HTML structure, `id` conventions, date wording, and
   styling used by the current Daily Updates entries exactly. Do not modify
   `styles.css`.

7. Never duplicate a date, navigation control, dialog, or FAQ. Preserve
   every existing daily update entry and dialog exactly as-is.

Only modify `index.html`. If no change is needed, make no changes at all.
