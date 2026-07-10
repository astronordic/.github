# Contributing · Contribuindo

<sub>🇬🇧 English · 🇧🇷 <a href="#-português">Português</a></sub>

These guidelines apply to **every `@astronordic` repository** unless a repo overrides them.

## 🇬🇧 English

### Workflow

1. **Fork / branch** — create a branch off the default: `feat/…`, `fix/…`, `docs/…`, `chore/…`.
2. **Commit** with [Conventional Commits](https://www.conventionalcommits.org):
   `type(scope): imperative subject`. Types: `feat` `fix` `docs` `refactor` `perf` `test` `chore` `ci` `style` `build`.
3. **Keep it focused** — one logical change per pull request.
4. **Green CI** — type-check, lint and tests must pass before review.
5. **Open a PR** — fill in the template, describe the *why*, link any issue.

### Local setup

Each repo's `README` documents how to install and run it. Match the pinned runtime
(`.nvmrc` for Node, the deployment target for macOS). Run the formatter before committing.

### Code style

- Match the surrounding code — naming, structure, comment density.
- Formatting is automated (Prettier / `swift-format`); don't hand-fight it.
- Prefer small, well-named units with clear responsibilities.

## 🇧🇷 Português

### Fluxo

1. **Fork / branch** — crie um branch a partir do padrão: `feat/…`, `fix/…`, `docs/…`, `chore/…`.
2. **Commit** com [Conventional Commits](https://www.conventionalcommits.org):
   `tipo(escopo): assunto no imperativo`. Tipos: `feat` `fix` `docs` `refactor` `perf` `test` `chore` `ci` `style` `build`.
3. **Mantenha focado** — uma mudança lógica por pull request.
4. **CI verde** — type-check, lint e testes precisam passar antes da revisão.
5. **Abra um PR** — preencha o template, descreva o *porquê*, linke a issue.

### Ambiente local

O `README` de cada repo documenta como instalar e rodar. Use o runtime fixado (`.nvmrc` para Node, o
deployment target para macOS). Rode o formatador antes de commitar.

### Estilo de código

- Combine com o código ao redor — nomes, estrutura, densidade de comentários.
- Formatação é automatizada (Prettier / `swift-format`); não brigue com ela na mão.
- Prefira unidades pequenas, bem nomeadas e com responsabilidades claras.
