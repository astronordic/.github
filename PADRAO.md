# O Padrão Nordic 🇧🇷

> As convenções de engenharia que todo repositório `@astronordic` segue.
> Versão em inglês: [`STANDARD.md`](./STANDARD.md).

O objetivo: qualquer repo, aberto do zero, deve parecer **familiar, documentado e confiável** em dez
segundos. Consistência é a funcionalidade.

---

## 1. Anatomia do repositório

Todo repositório tem, no mínimo:

```
├── README.md            # Inglês — a porta de entrada
├── README.pt-BR.md      # Português — mesmo conteúdo
├── LICENSE              # licença explícita, sempre
├── CHANGELOG.md         # formato Keep a Changelog
├── .editorconfig        # configuração de editor compartilhada
├── .gitignore
└── .github/
    ├── ISSUE_TEMPLATE/  # (herdado de astronordic/.github se ausente)
    └── PULL_REQUEST_TEMPLATE.md
```

`CONTRIBUTING.md`, `CODE_OF_CONDUCT.md` e `SECURITY.md` são **herdados automaticamente** do
repositório [`astronordic/.github`](https://github.com/astronordic/.github), a menos que o repo
precise dos seus próprios.

## 2. Anatomia do README

Bilíngue, nesta ordem. Um seletor de idioma fica bem no topo: `🇬🇧 English · 🇧🇷 Português`.

1. **Header** — logo/banner, nome do projeto, tagline de uma linha, badges.
2. **Sobre** — o que é e o problema que resolve, em 2–4 frases.
3. **Funcionalidades** — lista ou tabela escaneável.
4. **Screenshots / Demo** — imagens ou um clipe curto. Mostre, não conte.
5. **Stack** — linguagens, frameworks, infra.
6. **Arquitetura** — como as peças se encaixam; um diagrama quando ajudar.
7. **Como rodar** — clone → instale → rode, prontos para copiar e colar.
8. **Testes** — como rodar os testes e o que eles cobrem.
9. **Roadmap** — o que vem a seguir (opcional).
10. **Licença** — uma linha linkando o `LICENSE`.

**Badges** (shields.io, `for-the-badge` quando decorativo, flat quando informativo): licença · status
de CI · linguagem/stack principal · versão.

## 3. Commits — Conventional Commits

```
<tipo>(<escopo>): <assunto no imperativo>
```

**Tipos:** `feat` · `fix` · `docs` · `refactor` · `perf` · `test` · `chore` · `ci` · `style` · `build`.
Escopo é opcional mas incentivado (`feat(api)`, `fix(auth)`). Assunto: imperativo, minúsculo, sem
ponto final. Assunto em português tudo bem — seja consistente dentro do repo.

## 4. Branches & pull requests

- Branch padrão: **`main`** (repos existentes mantêm seu default atual para não quebrar deploy).
- Trabalhe em `feat/…`, `fix/…`, `docs/…`, `chore/…`.
- Nunca dê push direto no branch padrão de um repo de **produção** — abra um PR.
- Uma mudança lógica por PR. Preencha o template de PR. CI verde antes do merge.

## 5. Versionamento — SemVer

`MAJOR.MINOR.PATCH`. Mantenha a versão consistente em **todo** lugar que ela aparece (manifesto do
pacote, Info.plist, label no app, badge do README, tag git `vX.Y.Z`). Registre mudanças no `CHANGELOG.md`.

## 6. Licenciamento

Todo repo tem um `LICENSE` explícito — silêncio não é licença. A postura padrão é
**proprietária — Todos os Direitos Reservados**. Repos públicos/de portfólio adicionam uma nota
*source-available*: o código pode ser lido e avaliado, mas não reutilizado, sem permissão. Veja
[`templates/LICENSE-proprietary.txt`](./templates/LICENSE-proprietary.txt).

## 7. Integração Contínua (CI)

Todo repo roda CI nos pull requests. No mínimo: **type-check + lint + build/test**. O README carrega um
badge de status de CI ao vivo. Workflows prontos ficam em [`templates/`](./templates).

## 8. Base de ferramentas

- **`.editorconfig`** em todo repo ([template](./templates/.editorconfig)).
- **Formatador**: Prettier (JS/TS) / `swift-format` (Swift). Config commitada; formatação não se discute.
- **Dependabot** para atualização de dependências em repos com gerenciador de pacotes ([template](./templates/dependabot.yml)).
- **Fixar runtime**: `.nvmrc` (Node), deployment target (macOS) — documentado e igual ao CI.

---

<sub>make it work → make it right → make it beautiful.</sub>
