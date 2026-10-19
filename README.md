# Persona — Redesign

Repositório de trabalho do redesign visual do **Persona**: plataforma de **narrativa profissional** (SaaS B2C). A pessoa registra experiências no Diário, confirma evidências, acompanha o Narrative Score e ativa essas evidências no Persona Live e nos Artefatos.

Este repositório contém **somente material validado**. Ele é a fonte que o Claude Design (e qualquer agente) deve ler antes de desenhar uma tela.

## Pasta local do projeto

```text
C:\Users\yansi\OneDrive\ref_redisgn_persona
```

A pasta local espelha `docs/` e guarda material que **não** é versionado aqui: exportações do Claude Design, o PDF do design system e as imagens de referência do case iStudio (obra de terceiros).

## Conteúdo e ordem de leitura

| # | Arquivo | Papel | Precedência |
|---|---|---|---|
| 1 | [`docs/persona-fluxos-e-features.md`](docs/persona-fluxos-e-features.md) | **Produto:** ciclo, navegação, 20 features validadas, 7 fluxos de ponta a ponta, fichas por tela, componentes, regras de honestidade e massa de dados | Vence em qualquer dúvida de produto, fluxo, texto ou dado |
| 2 | [`docs/design-dna-persona.md`](docs/design-dna-persona.md) | **Visual:** tokens, tipografia, cor, contrastes WCAG, componentes e efeitos | Vence em dúvida visual |
| 3 | [`docs/plano-correcao-claude-design.md`](docs/plano-correcao-claude-design.md) | **Execução:** prompts em ordem para corrigir o projeto no Claude Design (v2.0) | Ordem e critérios de aceite |

## Decisões vigentes

- **Produto:** segue os documentos aprovados do app (`persona_mvp_v2/docs`, atualizados em 16/09/2026). Navegação: Início · Diário · Evidências · **Persona Live** · Artefatos, mais Configurações no rodapé.
- **Cores:** paleta Persona mantida — Indigo `#7C3AED` (primária) + Slate (neutros).
- **Tipografia:** Plus Jakarta Sans (títulos) + Inter (leitura).
- **Referência estrutural:** [Student Career Dashboard — iStudio (Behance)](https://www.behance.net/gallery/257051775/Student-Career-Dashboard-UIUX-Design-Case-Study-2026). As imagens de terceiros não são versionadas aqui.
- **Sem chat** em nenhuma tela; a IA age por ações nomeadas e a pessoa confirma.
- **Fora do escopo:** planos e preços, paywall, carta de apresentação, cadastro/senha (entrada só com Microsoft), upload de arquivo, áudio.
- **Mascote Xisto:** suspenso no redesign até existirem arquivos-fonte (D3, sujeita a veto).
- **Ferramentas de geração:** Claude Design (projeto `ff1a7bce-a6f2-4fa9-af99-a6196b748678`) e Google Stitch.

## Histórico

| Data | Mudança |
|---|---|
| 18/10/2026 | Design DNA v1.0 e README |
| 19/10/2026 | Plano de correção v1.0 (Opção A) |
| 19/10/2026 | Conferência contra o produto aprovado: novo `persona-fluxos-e-features.md`, plano v2.0, Design DNA v1.1 e pasta local movida para `OneDrive\ref_redisgn_persona` |
