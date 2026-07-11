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

English, minimalist, text-first — and written for **two audiences**. The top of the README speaks
to anyone in plain language; everything technical lives inside a single `## For developers`
section. A non-technical reader knows they can stop reading when they reach it.

In this order, with these exact section names:

1. **Header** — the Nordic banner (`docs/banner.svg`, see [section 10](#10-visual-identity)) with a
   centered `<sub>` metadata line and at most **one badge: the live CI status**. No `# H1` heading —
   GitHub already displays the repository name above the README.
2. **About** — what it is, who it is for, and why, in 2–4 plain-language sentences.
3. **How it works** *(optional)* — the product's flow, explained for a person, not a programmer.
4. **Features** — benefits, not technologies. A scannable list or table.
5. **Design — "Name"** *(optional)* — the project's design language, when it has a named one.
6. **Screenshots** *(optional)* — when the project is visual. Show, don't tell.
7. **Roadmap** *(optional)* — what's next, in plain language.
8. **For developers** — a single `## H2`; every technical topic is an `### H3` inside it, in this
   order: **Tech stack** · **Architecture** *(optional)* · **Getting started** · **Testing** ·
   **Docs** *(optional)*.
9. **License** — exactly one line: `Proprietary — All Rights Reserved. See [LICENSE](./LICENSE).`
   (public source-available repos append their viewing-only note).
10. **Footer** — every README closes with
    `<div align="center"><sub>make it work → make it right → make it beautiful.</sub></div>`.

**The audience rule:** above `## For developers`, no gratuitous technical terms — "SSR",
"monorepo", "SwiftUI" belong in the developer zone. Deep reference material (API routes, data
models, environment variables, operations) lives in `docs/*.md` and is linked from **Docs** —
the README stays scannable.

**Metadata line** — one centered `<sub>` under the banner:
`<platform/stack> · vX.Y.Z · Proprietary — All Rights Reserved[ · domain]`.

**No table of contents.** No `---` dividers between sections (only the one after the header).

**Badges are informative, never decorative.** The only badge is the live CI status badge from
GitHub Actions (default flat style). License, stack, platform and version are written as text.
No `for-the-badge` walls, no stats cards, no counters.

**No emoji anywhere in the README** — headings, body, or diagrams. Text first.

The `astronordic` profile and `.github` repos are special: their bodies use bespoke sections, but
the header, banner, and footer rules above still apply.

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

## 10. Visual identity

One banner grammar, one accent per project. The grammar is fixed — layout, background, texture,
and typography are **identical in every repo**; the accent color is the only thing that changes.

### The banner — `docs/banner.svg` (1280 × 420)

- **Rounded panel** — `rect` with `rx=24`, inset ~2px, **solid `#0A0A0C`** (the same in every
  repo), 1px hairline stroke `rgba(255,255,255,0.08)`.
- **Texture** — only the fine white grid (64px cells) at **4% opacity**. No aurora blobs, no
  glows, no background gradients, no rasters.
- **Text only** — no brand marks or logos. Left-aligned text stack starting at x ≈ 82:
  - **Wordmark** — baseline y ≈ 205, **84px** (long names shrink to fit, minimum 64px),
    weight 800, letter-spacing ~-0.02em, fill = vertical gradient `#FFFFFF → #B9C0CE`.
  - **Eyebrow** — baseline y ≈ 258, monospace, 21px, UPPERCASE, letter-spacing 5px, in the
    project accent color.
  - **Tagline** — baseline y ≈ 300, 26px, weight 500, muted grey `#9AA0AB`, one line of plain
    English ≤ 85 characters, with **exactly one** accent-colored `tspan`.
- **System font stacks only.** GitHub serves README SVGs through its camo proxy inside an `<img>`,
  where webfonts never load.
  - display: `-apple-system, BlinkMacSystemFont, 'SF Pro Display', 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif`
  - mono: `ui-monospace, 'SF Mono', 'JetBrains Mono', 'Cascadia Code', 'Segoe UI Mono', Consolas, monospace`
- **Fully self-contained** — everything inline. **English only** — including the `aria-label`
  and `<title>` on the SVG root. **No emoji.**

### README header

Every README opens with this block — no `# H1`, GitHub already shows the repository name:

```html
<div align="center">

<img src="docs/banner.svg" alt="<Project> — <tagline>" width="100%" />

<sub>meta · stack · vX.Y.Z · license posture</sub>

<p>
  <a href="https://github.com/astronordic/<repo>/actions/workflows/ci.yml"><img alt="CI" src="https://github.com/astronordic/<repo>/actions/workflows/ci.yml/badge.svg" /></a>
</p>

</div>

---
```

Repos without CI omit the badge `<p>` entirely.

### Social preview — `docs/social-preview.svg` → `.png` (1280 × 640, < 1 MB)

- **Full-bleed** — no rounded panel, no hairline border; platforms crop the edges. Solid
  `#0A0A0C`, white grid at 3% opacity.
- **Centered composition, text only** — wordmark (120px; long names smaller) with the eyebrow
  beneath, both centered. All critical content inside a centered **1120 × 560 safe area**. No
  marks, no pills, no side motifs — previews render small.
- **Rasterize with headless Chrome**:
  `chrome --headless --disable-gpu --hide-scrollbars --force-device-scale-factor=1 --window-size=1280,640 --screenshot=<abs>.png file://<abs>.svg`
- **Upload is manual** — repository *Settings → Social preview*. GitHub has no API for it.

### Profile cards — `docs/card-<project>.svg` (1280 × 220, profile repo only)

The profile README showcases projects with cards that follow the same grammar at card scale:
`rx=16` panel, same solid background, grid, and hairline; project name 48px weight 700 at x ≈ 82
(same wordmark gradient); one-line description 22px `#9AA0AB`; stack line monospace 16px
UPPERCASE letter-spacing 3px in the project accent.

### Project accents

The background is `#0A0A0C` everywhere. Each project owns **one** accent color:

| Project | Accent |
|---------|--------|
| cleanfy | teal `#16E0C0` |
| financeapp | blue `#4C82F7` |
| trustly | lime `#58C411` |
| profile / .github | monochrome — eyebrow `#8A8F98`, accent `tspan` `#E8E8EC` |

A new repository picks one accent and inherits everything else.

---

<sub>make it work → make it right → make it beautiful.</sub>
