# The Nordic Standard

> The engineering conventions every `@astronordic` repository follows.

The goal: any repo, opened cold, should feel **familiar, documented, and trustworthy** within ten
seconds. Consistency is the feature.

---

## 1. Language & identity

- **Everything is written in English** — READMEs, docs, code comments, commit subjects, issue and
  PR text, repository descriptions. No translated mirrors.
- **The author is `nordic (@astronordic)`** — in licenses, commits, and docs. Always.

## 2. Repository anatomy

Every repository has, at minimum:

```
├── README.md            # English — the front door
├── LICENSE              # explicit license, always
├── CHANGELOG.md         # Keep a Changelog format
├── .editorconfig        # shared editor settings
└── .gitignore
```

`CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`, issue forms and the PR template are
**inherited automatically** from the [`astronordic/.github`](https://github.com/astronordic/.github)
repository. A repo only defines its own when it genuinely needs to. `dependabot.yml` is the
exception — it is always per-repo.

## 3. README anatomy

English, minimalist, text-first. In this order:

1. **Header** — project name (`# H1`) and a one-line tagline. Optionally one banner or logo image,
   and at most **one badge: the live CI status**.
2. **About** — what it is and the problem it solves, in 2–4 sentences.
3. **Features** — a scannable list or table.
4. **Screenshots / Demo** — when the project is visual. Show, don't tell.
5. **Tech stack** — a plain-text line or short list.
6. **Architecture** — how the pieces fit; a diagram when it helps.
7. **Getting started** — clone → install → run, copy-pasteable.
8. **Testing** — how to run the tests and what they cover.
9. **Roadmap** — what's next (optional).
10. **License** — one plain-text line linking to `LICENSE`.

**Badges are informative, never decorative.** The only badge is the live CI status badge from
GitHub Actions (default flat style). License, stack, platform and version are written as text.
No `for-the-badge` walls, no stats cards, no counters.

**No decorative emoji in headings.** Text first.

## 4. Commits — Conventional Commits

```
<type>(<scope>): <subject in the imperative>
```

**Types:** `feat` · `fix` · `docs` · `refactor` · `perf` · `test` · `chore` · `ci` · `style` · `build`.
Scope is optional but encouraged (`feat(api)`, `fix(auth)`). Subject: English, imperative,
lower-case, no trailing period.

## 5. Branches & pull requests

- Default branch: **`main`**.
- Work on `feat/…`, `fix/…`, `docs/…`, `chore/…`.
- Never push directly to the default branch of a **production** repo — open a PR.
- One logical change per PR. Fill in the PR template. Green CI before merge.

## 6. Versioning — SemVer

`MAJOR.MINOR.PATCH`. Keep the version consistent across **every** place it appears (package manifest,
Info.plist, in-app label, git tag `vX.Y.Z`). Record changes in `CHANGELOG.md`.

## 7. Licensing

Every repo has an explicit `LICENSE` — silence is not a license. Default posture is
**proprietary — All Rights Reserved**, held by `nordic (@astronordic)`. Public/portfolio repos add a
*source-available* note: the code may be read and evaluated, but not reused, without permission. See
[`templates/LICENSE-proprietary.txt`](./templates/LICENSE-proprietary.txt).

## 8. Continuous Integration

Every repo runs CI on pull requests. At minimum: **type-check + lint + build/test**. The README
carries the live CI status badge. Docs-only pushes skip CI via `paths-ignore`. Ready-made workflows
live in [`templates/`](./templates).

## 9. Tooling baseline

- **`.editorconfig`** in every repo ([template](./templates/.editorconfig)).
- **Formatter**: Prettier (JS/TS) / `swift-format` (Swift). Config committed; formatting is not a debate.
- **Dependabot** for dependency updates on package-managed repos ([template](./templates/dependabot.yml)).
- **Runtime pinning**: `.nvmrc` (Node), deployment target (macOS) — documented and matching CI.

---

<sub>make it work → make it right → make it beautiful.</sub>
