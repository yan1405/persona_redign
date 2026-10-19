# Guia de execução — Design System do Persona (Etapas 2 e 3)

> **Versão:** 1.0 · 19/10/2026
> **Público:** o Claude Design (leitor) e Yan (quem cola os prompts).
> **Escopo:** Etapa 2 (componentes) e Etapa 3 (shell e layout) do [`plano-correcao-claude-design.md`](plano-correcao-claude-design.md) v2.2. A Etapa 4 (telas) terá um guia próprio, depois que esta etapa for aprovada.
> **Direção:** o Persona é uma **plataforma com agente de IA, não um CRM**. Produto em [`persona-fluxos-e-features.md`](persona-fluxos-e-features.md) (v1.2) e visual em [`design-dna-persona.md`](design-dna-persona.md) (v1.2).

---

## 1. Como este guia funciona

Este arquivo **não executa sozinho**. O Claude Design só age quando Yan cola um prompt. O guia existe para que cada prompt seja executado com o mesmo padrão e para que nenhuma tarefa seja dada como concluída sem prova.

Fluxo de cada tarefa:

1. Yan cola o prompt da tarefa (o texto está no plano, no bloco da tarefa de mesmo ID).
2. O Claude Design executa **somente** aquela tarefa.
3. O Claude Design entrega a **evidência exigida** (tabela da seção 4).
4. O Claude Design escreve a linha de checkpoint e **para**.
5. Yan confere a evidência e responde **"ok"** (aprovado) ou descreve o ajuste.
6. Só depois do "ok" a tarefa seguinte começa.

## 2. Regras de conduta (valem para todas as tarefas)

1. **Uma tarefa por vez.** Não adiante a seguinte e não altere nada fora do escopo do prompt.
2. **Sem "feito" sem ter visto.** Toda alteração visual precisa de capturas em 1024, 1280 e 1440 px, abertas e olhadas por você. Escreva "vi as capturas" apenas se for verdade.
3. **Sem placeholder.** Nunca escreva "(sem alterações)", "TODO" ou "igual ao anterior" dentro de um arquivo. Se mantém um trecho, mantenha o texto completo.
4. **Não altere tokens.** Cores, fontes, raios e sombras ficam como estão (decisão D6).
5. **Estrutura obrigatória:** cards em grade, painéis flutuantes, seções com índice de âncoras, **sem abas e sem tabelas**; o Agente Persona está presente.
6. **Dados:** use só a massa de dados da seção 10 do anexo de produto.
7. **Se algo no prompt contradiz o anexo de produto, pare e pergunte.** O anexo vence em produto; o Design DNA vence em visual.
8. **Se não conseguir cumprir um critério, diga qual e por quê.** Não esconda o problema nem o contorne em silêncio.

## 3. Pré-requisitos (confira antes da T2.1)

| # | Pré-requisito | Quem confirma |
|---|---|---|
| P1 | As regras permanentes **v2.2** foram coladas (resposta "ok, regras registradas (v2.2)") | Yan |
| P2 | T1.2 e T1.2b concluídas: o Readme não tem "(sem alterações)" nem resíduos de chat aberto, 6 tiles ou Xisto | Yan, abrindo o Readme |
| P3 | T1.3 concluída (SKILL.md, github.md, thumbnail) | Yan |
| P4 | U0.1 feita: "Padrão da organização" removido e o Persona Design System fixado no projeto | Yan |
| P5 | Anexos no chat: `persona-fluxos-e-features.md` v1.2 e este guia | Yan |

Se algum pré-requisito falhar, a Etapa 2 **não começa**.

## 4. Tarefas, evidências e checkpoints

### Etapa 2 — Componentes

| ID | Tarefa (prompt no plano) | Evidência obrigatória | Checkpoint |
|---|---|---|---|
| T2.1 | SourceCard → EvidenceCard (3 variantes: card de grade, sugestão, selecionável) | Captura do @dsCard com as 3 variantes; resultado da busca por `SourceCard` (deve ser zero); razões de contraste dos badges | `CHECKPOINT T2.1 — aguardo seu ok` |
| T2.2 | Variantes de status (Registrada, Documentada, Para revisar, Rascunho, Revisado, Lacuna) | Tabela com a razão de contraste calculada de cada par, **sem arredondamento intermediário**, todas ≥ 4,5:1 | `CHECKPOINT T2.2 — aguardo seu ok` |
| T2.3 | EntryCard, CaptureEditor e núcleo do Agente (AgentPrompt, AgentPanel, Composer, MessageBubble) | Capturas dos 5 @dsCards; busca por `ConversationRow` (zero); lista de quem importa `Composer` e `MessageBubble` (só `AgentPanel` e a conversa central do Início); confirmação de que o `CaptureEditor` não parece chat | `CHECKPOINT T2.3 — aguardo seu ok` |
| T2.4 | Oito componentes novos: DimensionRow, StepFlow, ArgumentPanel, DraftPanel, ArtifactCard, TraceLine, FloatingPanel, SectionIndex | Oito @dsCards com estados padrão, foco, preenchido, erro e desabilitado; anel de foco de 2 px `#A78BFA` visível; SectionIndex sem aparência de abas | `CHECKPOINT T2.4 — aguardo seu ok` |
| T2.5 | Navegação sem itens vazios, com "Buscar ou perguntar" e botão "Agente" no cabeçalho | Capturas da lateral expandida e em rail; os cinco itens mais Configurações; cabeçalho com o campo e o botão | `CHECKPOINT T2.5 — aguardo seu ok` |

**Fechamento da Etapa 2:** depois do "ok" da T2.5, o Claude Design lista os componentes que existem agora e confirma que nenhum arquivo importa `SourceCard` ou `ConversationRow`. Escreva: `ETAPA 2 CONCLUÍDA — aguardo seu ok para a Etapa 3`.

### Etapa 3 — Shell e layout

| ID | Tarefa (prompt no plano) | Evidência obrigatória | Checkpoint |
|---|---|---|---|
| T3.1 | Cabeçalho fixo e opaco | Capturas no topo e no meio da rolagem de uma grade de cards em 1280 px; nenhum texto atrás do cabeçalho | `CHECKPOINT T3.1 — aguardo seu ok` |
| T3.2 | Grade de 4 tiles por largura do container | Capturas em 1024, 1280 e 1440 px: sempre 4 em linha ou 2 × 2, nenhum tile sozinho | `CHECKPOINT T3.2 — aguardo seu ok` |
| T3.3 | FocalCard sem estouro | Capturas nas três larguras com o CTA inteiro, sem sobreposição e sem rolagem horizontal | `CHECKPOINT T3.3 — aguardo seu ok` |
| T3.4 | Hierarquia de botões | Tabela tela × botão × nível, antes e depois; um botão de marca por tela | `CHECKPOINT T3.4 — aguardo seu ok` |
| T3.5 | Casca com AgentPanel e FloatingPanel | Capturas em 1024, 1280 e 1440 px com o painel do agente aberto e fechado; FloatingPanel aberto com o agente aberto; sem rolagem horizontal | `CHECKPOINT T3.5 — aguardo seu ok` |

**Fechamento da Etapa 3:** escreva `ETAPA 3 CONCLUÍDA — design system pronto para as telas` e liste, em uma tabela, cada critério de aceite do plano com o resultado (cumprido ou não).

## 5. Formato do checkpoint

Ao terminar cada tarefa, o Claude Design responde exatamente nesta forma:

```text
TAREFA <ID> — <nome>
O que mudou: <2 a 4 linhas>
Evidência: <capturas, tabelas ou buscas pedidas>
Critérios de aceite: <cada critério do plano, marcado como cumprido ou não, com a prova>
Pendências ou dúvidas: <ou "nenhuma">
CHECKPOINT <ID> — aguardo seu ok
```

Depois dessa mensagem, **nenhuma ação** até a resposta de Yan.

## 6. Como Yan deve conferir (3 minutos por checkpoint)

- Olhe as capturas, não o texto: o Claude Design já declarou "feito" sem ter visto o resultado.
- Procure os defeitos de sempre: texto cortado, sobreposição, rolagem horizontal, tile sozinho, dois botões de marca, abas, tabelas, bolhas de chat fora do Agente.
- Em caso de dúvida, responda com o defeito exato e a largura em que aparece. Não responda "ok" por cansaço: um erro aceito aqui se repete em todas as telas da Etapa 4.

## 7. O que este guia não cobre

- **Etapa 0** (manual) e **Etapa 1** (escopo): já estão no plano.
- **Etapa 4** (telas), **5** (responsivo e acessibilidade) e **6** (fechamento): guia próprio depois do "ok" da Etapa 3.
- **Decisão pendente D3 (mascote Xisto):** suspenso até existirem arquivos-fonte.
