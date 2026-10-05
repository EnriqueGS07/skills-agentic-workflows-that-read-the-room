---
name: update-github-info
description: Draft practical updates for Mona's GitHub Info website from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before researching or editing. It contains Mona's editorial guidance.

Use `web-fetch` to read these sources:

- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Identify recent items that will help developers learn GitHub faster. Keep each summary short and practical, verify details against the source, and include the relevant source link whenever an update comes from the GitHub Blog, GitHub Changelog, or Awesome Copilot workflows. Do not invent announcements or repeat items that are already covered without a useful new angle.

Use the `edit` tool to update `site/content/github-info.md` with the selected information while preserving its existing structure and voice. If neither source has a useful new item, leave the file unchanged and do not open an empty pull request.

Open a pull request for Mona to review, with a concise title mentioning Mona or GitHub Info and a body summarizing the changes and linking to their sources. Do not write directly to `main`; use `safe-outputs` with `create-pull-request` so all changes are proposed for review.