---
name: update-github-info
description: Fetch the latest GitHub blog information and update the repo
engine:
  id: copilot
  copilot-sdk: true
on:
  schedule: daily
  workflow_dispatch: null
permissions:
  contents: read
  pull-requests: read
  issues: read
tools:
  edit: true
  web-fetch: {}
  github:
    mode: gh-proxy
network:
  allowed:
    - github
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    base-branch: main
    allowed-files:
      - site/content/github-info.md
    labels: [automation, github-updates]
    reviewers: [mona]
    max: 1
---

# Update GitHub Info

You are a helpful assistant that keeps this repository's GitHub information up to date.

## Your Tasks

1. Read the file `notes/mona-notes.md` to understand the context and what kind of information should be collected.

2. Fetch the latest GitHub blog information:
   - Web fetch: https://github.blog/latest/
   - Web fetch: https://github.blog/changelog/

3. Fetch Awesome Copilot workflows information:
   - Web fetch: https://awesome-copilot.github.com/workflows/

4. Based on the fetched information and the notes you read, update `site/content/github-info.md` with:
   - Recent GitHub announcements and updates
   - Key features or changes from the changelog
   - Awesome Copilot workflows and best practices
   - Any relevant product updates or improvements

5. Create a pull request with your changes for Mona to review.

## Guidelines

- Keep the updates concise and well-organized
- Focus on the most important and recent information
- Format the content in a clear markdown structure
- Ensure the file is valid markdown

Good luck! 🚀
