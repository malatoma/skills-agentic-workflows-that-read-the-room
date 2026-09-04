---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
engine:
  id: copilot
  model: gpt-5-mini
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
    - github.com
    - github.blog
    - awesome-copilot.github.com
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use these sources:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Read external public guidance with the `web-fetch` tool. Read repository guidance
or reference files with GitHub repository API tools, not terminal, CLI, or
sandboxed commands.

Web fetch https://awesome-copilot.github.com/workflows/ and use relevant Awesome
Copilot workflows as an additional source.

Review the existing `site/content/github-info.md`, then update it with concise,
practical guidance for developers. Mention the source whenever an update comes
from the GitHub Blog or GitHub Changelog. Keep unrelated content unchanged.

Use the `edit` tool to update `site/content/github-info.md`. After making the
change, open a pull request for Mona to review using the `create-pull-request`
`safe output`. Use a pull request title that mentions Mona or GitHub Info.

Check that this workflow configuration is syntactically valid. Do not compile
this workflow.