# Persona — Redesign

Repositório de trabalho do redesign visual do **Persona**: **plataforma com agente de IA** para narrativa profissional (SaaS B2C), **não um CRM**. A pessoa conversa com o Agente Persona, registra experiências no Diário, confirma evidências, acompanha o Narrative Score e ativa essas evidências no Persona Live e nos Artefatos.

Este repositório contém **somente material validado**. Ele é a fonte que o Claude Design (e qualquer agente) deve ler antes de desenhar uma tela.

## Pasta local do projeto

```text
C:\Users\yansi\OneDrive\ref_redisgn_persona
```

A pasta local espelha `docs/` e guarda material que **não** é versionado aqui: exportações do Claude Design, o PDF do design system e as imagens de referência do case iStudio (obra de terceiros).

## Conteúdo e ordem de leitura

| # | Arquivo | Papel | Precedência |
|---|---|---|---|
| 1 | [`docs/persona-fluxos-e-features.md`](docs/persona-fluxos-e-features.md) | **Produto:** ciclo, navegação, 20 features validadas + o Agente Persona (F-21, direção, não implementado), 8 fluxos de ponta a ponta, fichas por tela, componentes, regras de honestidade e massa de dados | Vence em qualquer dúvida de produto, fluxo, texto ou dado |
| 2 | [`docs/design-dna-persona.md`](docs/design-dna-persona.md) | **Visual:** tokens, tipografia, cor, contrastes WCAG, componentes e efeitos | Vence em dúvida visual |
| 3 | [`docs/plano-correcao-claude-design.md`](docs/plano-correcao-claude-design.md) | **Execução:** prompts em ordem para corrigir o projeto no Claude Design (v2.2) | Ordem e critérios de aceite |
| 4 | [`docs/guia-execucao-design-system.md`](docs/guia-execucao-design-system.md) | **Guia de execução** das Etapas 2 e 3, com evidências e checkpoints de parada | Como o Claude Design conduz as tarefas |

## Decisões vigentes

- **Produto:** segue os documentos aprovados do app (`persona_mvp_v2/docs`, atualizados em 16/09/2026). Navegação: Início · Diário · Evidências · **Persona Live** · Artefatos, mais Configurações no rodapé.
- **Cores:** paleta Persona mantida — Indigo `#7C3AED` (primária) + Slate (neutros).
- **Tipografia:** Plus Jakarta Sans (títulos) + Inter (leitura).
- **Referência estrutural:** [Student Career Dashboard — iStudio (Behance)](https://www.behance.net/gallery/257051775/Student-Career-Dashboard-UIUX-Design-Case-Study-2026). As imagens de terceiros não são versionadas aqui.
- **Agente no centro, sem CRM** (decisão de Yan, 19/10/2026): o Agente Persona é o eixo (campo "Buscar ou perguntar" no Início e painel acoplado em todas as telas). Listas são **cards**, detalhes são **painéis flutuantes com seções** e não há abas. Dentro do Persona Live e dos Artefatos a IA age por ações nomeadas, sem chat. O agente (LD-026) **não está implementado** no app e os contratos das Fases 7 e 8 não preveem chat aberto: este redesign é um protótipo de direção.
- **Fora do escopo:** planos e preços, paywall, carta de apresentação, cadastro/senha (entrada só com Microsoft), upload de arquivo, áudio.
- **Mascote Xisto:** **fora do redesign** (D3 confirmada por Yan em 19/10/2026). Só ícones Lucide.
- **Ferramentas de geração:** Claude Design (projeto `ff1a7bce-a6f2-4fa9-af99-a6196b748678`) e Google Stitch.

## Histórico

| Data | Mudança |
|---|---|
| 18/10/2026 | Design DNA v1.0 e README |
| 19/10/2026 | Plano de correção v1.0 (Opção A) |
| 19/10/2026 | Conferência contra o produto aprovado: novo `persona-fluxos-e-features.md`, plano v2.0, Design DNA v1.1 e pasta local movida para `OneDrive\ref_redisgn_persona` |
| 19/10/2026 | Painel experimental do Agente Persona com chat (decisão de Yan, opção A): fluxos v1.1, plano v2.1 |
| 19/10/2026 | **Direção "plataforma com agente de IA, não CRM"** (decisão de Yan): fluxos v1.2, Design DNA v1.2, plano v2.2 (T1.2b, T3.5, Etapa 4 em cards/painéis flutuantes/seções) e novo `guia-execucao-design-system.md`. A v2.1 (agente experimental) fica superada |
