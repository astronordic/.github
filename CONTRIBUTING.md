# Contributing

These guidelines apply to **every `@astronordic` repository** unless a repo overrides them.

## Workflow

1. **Fork / branch** — create a branch off the default: `feat/…`, `fix/…`, `docs/…`, `chore/…`.
2. **Commit** with [Conventional Commits](https://www.conventionalcommits.org):
   `type(scope): imperative subject`. Types: `feat` `fix` `docs` `refactor` `perf` `test` `chore` `ci` `style` `build`.
3. **Keep it focused** — one logical change per pull request.
4. **Green CI** — type-check, lint and tests must pass before review.
5. **Open a PR** — fill in the template, describe the *why*, link any issue.

## Local setup

Each repo's `README` documents how to install and run it. Match the pinned runtime
(`.nvmrc` for Node, the deployment target for macOS). Run the formatter before committing.

## Code style

- Match the surrounding code — naming, structure, comment density.
- Formatting is automated (Prettier / `swift-format`); don't hand-fight it.
- Prefer small, well-named units with clear responsibilities.
