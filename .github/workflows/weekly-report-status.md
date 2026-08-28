---
name: Weekly Report Status
description: Publishes a weekly activity report covering commits, issues, and pull requests from the previous seven days.
on:
  schedule:
    - cron: "0 9 * * 1"
  workflow_dispatch:
engine: copilot
permissions:
  contents: read
  issues: read
  pull-requests: read
  copilot-requests: write
tools:
  github:
    mode: gh-proxy
    toolsets: [default]
safe-outputs:
  create-issue:
    title-prefix: "[weekly-report] "
    max: 1
---

# Weekly Report Status

## Task

Generate a concise activity report for this repository covering the **last 7
full days ending at workflow start (UTC)**.

Use `gh` commands to gather, for that window:

- **Commits** pushed to the default branch
- **Issues** opened, closed, or commented on
- **Pull requests** opened, merged, closed, or reviewed

## Report Style

Publish the report as a new issue using the configured safe output. Structure
the body as:

### Summary

- Commits: `<count>`
- Issues: `<opened>` opened, `<closed>` closed
- Pull requests: `<opened>` opened, `<merged>` merged, `<closed>` closed

### Commits

List the commits from the window (short SHA, message, author), or state
clearly that no commits were pushed in the last 7 days.

### Issues

List the issues opened or closed in the window (number, title, state), or
state clearly that no issue activity occurred in the last 7 days.

### Pull Requests

List the pull requests opened, merged, or closed in the window (number,
title, state), or state clearly that no pull request activity occurred in the
last 7 days.

If there was no activity at all in any category, state that plainly in the
Summary section instead of leaving it ambiguous.

## Safe Outputs

- Always publish the report as a single new issue using `create-issue`, even
  when there was no activity — the issue must clearly state that no activity
  occurred.
