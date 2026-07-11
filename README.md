# The Nordic Standard

The shared engineering standard for every [`@astronordic`](https://github.com/astronordic) repository.

This is a **special repository**. On GitHub, a public repository named `.github` provides
**default community health files** — `CONTRIBUTING`, `CODE_OF_CONDUCT`, `SECURITY`, issue and
pull-request templates — to every other repository on the account that doesn't define its own.

In other words: this repo is the **single source of truth**. Define a convention here once, and it
is followed everywhere. Individual repos may override a file when they genuinely need to.

## What lives here

| File | Purpose |
|------|---------|
| [`STANDARD.md`](./STANDARD.md) | The full engineering standard (language, commits, branches, READMEs, versioning, licensing) |
| [`CONTRIBUTING.md`](./CONTRIBUTING.md) | How to contribute across all repos |
| [`CODE_OF_CONDUCT.md`](./CODE_OF_CONDUCT.md) | Community expectations |
| [`SECURITY.md`](./SECURITY.md) | How to report a vulnerability |
| [`.github/ISSUE_TEMPLATE/`](./.github/ISSUE_TEMPLATE) | Bug report and feature request forms |
| [`.github/PULL_REQUEST_TEMPLATE.md`](./.github/PULL_REQUEST_TEMPLATE.md) | The PR checklist |
| [`templates/`](./templates) | Drop-in files: `LICENSE`, `.editorconfig`, CI workflows, Dependabot |

## The projects that follow it

| Project | What it is | Stack |
|---------|-----------|-------|
| [**Cleanfy**](https://github.com/astronordic/cleanfy) | Native macOS disk cleaner and live memory monitor | Swift · SwiftUI |
| **Trustly** (private) | PIX escrow platform for safe middleman deals | TypeScript · Express · Next.js |
| **FinanceApp** (private) | Personal and business finance SaaS for the Brazilian market | TypeScript · Next.js · Supabase |

---

<sub><em>make it work → make it right → make it beautiful.</em></sub>
