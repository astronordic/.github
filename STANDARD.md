# The Nordic Standard 🇬🇧

> The engineering conventions every `@astronordic` repository follows.
> Portuguese version: [`PADRAO.md`](./PADRAO.md).

The goal: any repo, opened cold, should feel **familiar, documented, and trustworthy** within ten
seconds. Consistency is the feature.

---

## 1. Repository anatomy

Every repository has, at minimum:

```
├── README.md            # English — the front door
├── README.pt-BR.md      # Portuguese — same content
├── LICENSE              # explicit license, always
├── CHANGELOG.md         # Keep a Changelog format
├── .editorconfig        # shared editor settings
├── .gitignore
└── .github/
    ├── ISSUE_TEMPLATE/  # (inherited from astronordic/.github if absent)
    └── PULL_REQUEST_TEMPLATE.md
```

`CONTRIBUTING.md`, `CODE_OF_CONDUCT.md` and `SECURITY.md` are **inherited automatically** from the
[`astronordic/.github`](https://github.com/astronordic/.github) repository unless a repo needs its own.

## 2. README anatomy

Bilingual, in this order. A language switcher sits at the very top: `🇬🇧 English · 🇧🇷 Português`.

1. **Header** — logo/banner, project name, one-line tagline, badges.
2. **About** — what it is and the problem it solves, in 2–4 sentences.
3. **Features** — a scannable list or table.
4. **Screenshots / Demo** — images or a short clip. Show, don't tell.
5. **Tech stack** — languages, frameworks, infra.
6. **Architecture** — how the pieces fit; a diagram when it helps.
7. **Getting started** — clone → install → run, copy-pasteable.
8. **Testing** — how to run the tests and what they cover.
9. **Roadmap** — what's next (optional).
10. **License** — one line linking to `LICENSE`.

**Badges** (shields.io, `for-the-badge` when decorative, flat when informational): license · CI status
· primary language/stack · version.

## 3. Commits — Conventional Commits

```
<type>(<scope>): <subject in the imperative>
```

**Types:** `feat` · `fix` · `docs` · `refactor` · `perf` · `test` · `chore` · `ci` · `style` · `build`.
Scope is optional but encouraged (`feat(api)`, `fix(auth)`). Subject: imperative, lower-case, no
trailing period. Portuguese subjects are fine — be consistent within a repo.

## 4. Branches & pull requests

- Default branch: **`main`** (existing repos keep their current default to avoid deploy breakage).
- Work on `feat/…`, `fix/…`, `docs/…`, `chore/…`.
- Never push directly to the default branch of a **production** repo — open a PR.
- One logical change per PR. Fill in the PR template. Green CI before merge.

## 5. Versioning — SemVer

`MAJOR.MINOR.PATCH`. Keep the version consistent across **every** place it appears (package manifest,
Info.plist, in-app label, README badge, git tag `vX.Y.Z`). Record changes in `CHANGELOG.md`.

## 6. Licensing

Every repo has an explicit `LICENSE` — silence is not a license. Default posture is
**proprietary — All Rights Reserved**. Public/portfolio repos add a *source-available* note: the code
may be read and evaluated, but not reused, without permission. See
[`templates/LICENSE-proprietary.txt`](./templates/LICENSE-proprietary.txt).

## 7. Continuous Integration

Every repo runs CI on pull requests. At minimum: **type-check + lint + build/test**. The README carries
a live CI status badge. Ready-made workflows live in [`templates/`](./templates).

## 8. Tooling baseline

- **`.editorconfig`** in every repo ([template](./templates/.editorconfig)).
- **Formatter**: Prettier (JS/TS) / `swift-format` (Swift). Config committed; formatting is not a debate.
- **Dependabot** for dependency updates on package-managed repos ([template](./templates/dependabot.yml)).
- **Runtime pinning**: `.nvmrc` (Node), deployment target (macOS) — documented and matching CI.

---

<sub>make it work → make it right → make it beautiful.</sub>
