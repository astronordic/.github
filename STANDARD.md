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

1. **Header** — the Nordic banner (`docs/banner.svg`, see [section 10](#10-visual-identity)) with a
   centered `<sub>` metadata line and at most **one badge: the live CI status**. No `# H1` heading —
   GitHub already displays the repository name above the README.
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

## 10. Visual identity

One banner grammar, one palette per project. The grammar is fixed; the personality is the color.

### The banner — `docs/banner.svg` (1280 × 420)

- **Rounded panel** — `rect` with `rx=24`, inset ~2px, dark per-project base fill, 1px hairline
  stroke `rgba(255,255,255,0.08)`.
- **Texture, restrained** — heavily blurred radial "aurora" blobs (`feGaussianBlur` with
  `stdDeviation ≥ 40`) and/or a fine grid pattern at ≤ 6% opacity. Texture never competes with
  text contrast.
- **Left-aligned text stack** — with a brand mark: mark centered near (210, 210), text starts at
  x ≈ 330. Without one: text starts at x ≈ 82.
  - **Wordmark** — baseline y ≈ 205, 76–92px (smaller for long names), weight 800,
    letter-spacing ~-0.02em, fill = vertical gradient `#FFFFFF → #B9C0CE`.
  - **Eyebrow** — baseline y ≈ 258, monospace, 20–22px, UPPERCASE, letter-spacing 4–6px, in the
    project accent color.
  - **Tagline** — baseline y ≈ 300, 26–28px, weight 500, muted grey, one line of plain English
    ≤ 85 characters; may carry one accent-colored `tspan`.
- **System font stacks only.** GitHub serves README SVGs through its camo proxy inside an `<img>`,
  where webfonts never load.
  - display: `-apple-system, BlinkMacSystemFont, 'SF Pro Display', 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif`
  - mono: `ui-monospace, 'SF Mono', 'JetBrains Mono', 'Cascadia Code', 'Segoe UI Mono', Consolas, monospace`
- **Fully self-contained** — everything inline; raster assets only as base64 `data:` URIs.
- **English only** — including the `aria-label` and `<title>` on the SVG root. **No emoji.**

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

- **Full-bleed** — no rounded panel, no hairline border; platforms crop the edges.
- **Centered composition** — mark above or beside the wordmark, eyebrow beneath. All critical
  content inside a centered **1120 × 560 safe area**. No pills, no side motifs — previews render
  small.
- **Rasterize with headless Chrome**:
  `chrome --headless=new --disable-gpu --hide-scrollbars --window-size=1280,640 --screenshot=<abs>.png file://<abs>.svg`
- **Upload is manual** — repository *Settings → Social preview*. GitHub has no API for it.

### Project palettes

| Project | Background | Accent |
|---------|-----------|--------|
| cleanfy | `#0A0B12 → #0D1020` | teal `#16E0C0` · violet `#7B5CFF` |
| financeapp | `#060B14` | blue `#4C82F7` |
| trustly | `#0F1A1A` | lime `#58C411` (gradient `#9EEA6C → #58C411 → #14B6A6`) |
| profile / .github | `#0A0A0C` | monochrome |

A new repository picks one background and one accent and inherits everything else.

---

<sub>make it work → make it right → make it beautiful.</sub>
