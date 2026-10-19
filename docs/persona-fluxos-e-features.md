# Persona — Fluxos de uso e features validadas

> **Versão:** 1.2 · 19/10/2026 (v1.2 reorienta o redesign: **plataforma com agente de IA**, não CRM. O Agente Persona passa a ser o eixo da experiência; cards, painéis flutuantes e seções substituem listas densas, painéis laterais e abas)
> **Papel deste arquivo:** é o **anexo de produto** do redesign. Ele substitui os prints do app atual: descreve o que o Persona faz, em que ordem a pessoa usa e como cada feature validada se encaixa no novo design system. O visual antigo está descartado; **o comportamento descrito aqui não**.
> **Precedência:** em conflito, vale este arquivo para produto e fluxo; `design-dna-persona.md` para visual; `plano-correcao-claude-design.md` para a ordem de execução.
> **Fontes:** documentos aprovados do app em `Persona_Geral/persona_mvp_v2/docs/` — `PRODUCT_BRIEF.md` (16/09/2026), `architecture/INFORMATION_ARCHITECTURE.md`, `handoff/PRODUCT_SURFACE.md`, `handoff/CURRENT_STATE.md` e os contratos das Fases 3 a 9 em `plans/`.

---

## 1. O produto em quatro linhas

- **O que é:** plataforma de inteligência profissional. A pessoa registra experiências reais, o Persona identifica o que elas demonstram e organiza uma memória profissional rastreável.
- **Proposta:** "Sua história profissional, organizada para trabalhar a seu favor."
- **Promessa funcional:** "Registre uma vez. Prove sempre."
- **Diferenciação:** "O Persona não começa pela resposta. Começa pela evidência."

O Persona **não** é plataforma acadêmica, de tutores, rede social **nem CRM**: não há funil, pipeline, leads ou tabelas de gestão. É uma **plataforma com agente de IA**: a pessoa pergunta ou pede, o **Agente Persona** responde com base nas evidências registradas e leva até a superfície certa (Diário, Evidências, Persona Live, Artefatos), onde o resultado fica guardado e a pessoa confirma. O agente não responde pela pessoa e não inventa fatos.

> **Status honesto e divergência consciente:** o agente colaborativo (LD-026, aprovado em 16/09/2026) **ainda não está implementado** no app, e os contratos das Fases 7 e 8 definem Live e Artefatos sem chat aberto. Este redesign é um **protótipo de direção**: o agente é o eixo da navegação e da conversa, mas **dentro dos workspaces do Live e dos Artefatos a IA continua agindo por ações nomeadas e fechadas**. Qualquer adoção no app real exige atualizar esses contratos antes.

## 2. O ciclo do produto

Imagine uma biblioteca pessoal: o Diário é a caixa de entrada onde tudo chega, as Evidências são os livros já catalogados, o Narrative Score é o relatório da estante e o Persona Live e os Artefatos são o empréstimo do livro certo na hora certa.

```text
MEMÓRIA          EVIDÊNCIA              SÍNTESE              ATIVAÇÃO
Diário     →     fatos revisados   →    Narrative Score  →   Persona Live / Artefatos
(texto livre)    (Registrada /          (explicável,         (argumentos reais +
                  Documentada)           com origem)          rascunho rastreável)
```

Regra que atravessa o ciclo: **a IA sugere, a pessoa confirma.** Nada vira fato sem revisão humana, e todo texto gerado aponta para a evidência de origem.

## 3. Mapa de navegação

| Ordem | Destino | Rota | Padrão |
|---|---|---|---|
| 1 | **Início** | `/app/inicio` | Hub do agente: campo "Buscar ou perguntar", briefing do dia, KPIs e tiles |
| 2 | **Diário** | `/app/diario` | Página; histórico em grade de cards; detalhe em painel flutuante |
| 3 | **Evidências** | `/app/evidencias` | Página em grade de cards; detalhe em painel flutuante |
| 4 | **Persona Live** | `/app/live` | Workspace dedicado |
| 5 | **Artefatos** | `/app/artefatos` | Biblioteca em grade de cards; criação e edição em workspace de página inteira |
| rodapé | **Configurações** | `/app/configuracoes` | Página com navegação secundária |

- O **Agente Persona está em todas as telas**: botão "Agente" fixo no cabeçalho e atalho Ctrl/⌘+K. Em telas internas ele é um **painel acoplado à direita** (380–420 px, recolhível, que empurra o conteúdo em vez de cobri-lo); no Início a conversa ocupa a **área central**. O agente sabe em que tela a pessoa está e oferece chips contextuais.
- Um único campo **"Buscar ou perguntar"** no cabeçalho: busca registros e evidências; se for uma pergunta, encaminha ao agente. Filtros ficam **recolhidos** atrás do botão "Filtros".
- Detalhes abrem em **painel flutuante ancorado** (560–640 px, raio 28, sombra Float, fundo levemente esmaecido), preservando a tela abaixo. Um painel flutuante por vez; `Esc` fecha.
- **Sem abas.** Detalhes longos usam **seções empilhadas** numa só página com índice de âncoras (`SectionIndex`). Visões irmãs de lista (Todas · Para revisar) são chips de visão.
- Listas são **grades de cards** (2–3 colunas), nunca tabelas nem linhas densas.
- O **Narrative Score não é destino de navegação**: aparece como faixa de KPIs no Início e abre `/app/score` em painel flutuante.
- O **Diagnóstico** (`/app/diagnostico`) é um fluxo sequencial acionado pelo Início, não item de menu.
- Desktop-first, a partir de 1024 px. Não há app mobile dedicado nesta fase.

## 4. Features validadas — o que o redesign precisa representar

Status de acordo com `CURRENT_STATE.md` (snapshot técnico de 02/09/2026, atualização de produto em 16/09/2026).

| # | Feature | O que faz | Status no app | Tela do redesign | Componentes do DS |
|---|---|---|---|---|---|
| F-01 | **Entrada Microsoft** | Login único "Entrar com Microsoft" (OAuth PKCE). Sem cadastro e sem senha próprios. | Validada em produção | Entrar (backlog) | `Button` |
| F-02 | **Onboarding em 4 etapas** | Contexto → Privacidade (consentimento obrigatório separado de comunicações opcionais) → Rotina (lembrete opcional, desligado por padrão) → Primeiro registro real | Implementada | Onboarding (backlog) | `StepFlow`, `Input`, `Switch` |
| F-03 | **Diário (Daily Log)** | Editor livre "O que aconteceu hoje?", 40 a 2.000 caracteres, data e contexto opcionais, histórico em cards com busca e filtros recolhidos | Implementada (Fase 4) | Diário | `CaptureEditor`, `EntryCard`, `Input` |
| F-04 | **Estruturação assistida** | A IA propõe de 1 a 3 sugestões de evidência (contexto, desafio, ação, resultado, competências, aprendizado). Modo manual sempre disponível. O texto original nunca é substituído. | Implementada | Diário › detalhe › seção Sugestões | `EvidenceCard` (variante sugestão), `TraceLine` |
| F-05 | **Revisão e confirmação** | Cada campo é revisável; a evidência só nasce por confirmação explícita | Implementada | Diário e Evidências | `Button` (marca: "Confirmar evidência") |
| F-06 | **Biblioteca de Evidências** | Grade de cards com busca, visões (chips) (Todas, Para revisar) e filtros por competência, período e nível. Registro manual permitido. Arquivar preserva a rastreabilidade. | Implementada (Fase 5) | Evidências | `EvidenceCard`, `Chip` (visões), `Input` |
| F-07 | **Provas por link** | Link HTTP/HTTPS validado. Com ao menos 1 link, a evidência sobe de **Registrada** para **Documentada**; sem link, volta para Registrada. | Implementada | Evidências › detalhe › seção Provas | `Badge`, `Chip`, `TraceLine` |
| F-08 | **Diagnóstico declarado** | 3 etapas e 10 perguntas, com rascunho salvo e retomada; gera o score inicial "Base declarada" | Implementada (Fase 6) | Diagnóstico (backlog) | `StepFlow` |
| F-09 | **Narrative Score explicável** | Total = 0,6 × Coerência + 0,4 × Consistência. Credibilidade fica fora do total e aparece como "Ainda não avaliada". Origem: Base declarada → Parcialmente observado → Observado. | Implementada | Início (KPIs) e painel Score | `ScoreRing`, `DimensionRow`, `ProgressBar` |
| F-10 | **Painel do Score** | Seções Resumo, Histórico e Como é calculado (método, limiares, uso de IA e limitações) | Implementada | Painel Score | `SectionIndex`, `DimensionRow` |
| F-11 | **Persona Live (manual)** ⭐ | Prepara uma oportunidade (vaga e empresa), recomenda evidências, a pessoa autoriza de 1 a 8, digita a pergunta e recebe **Argumentos reais** e **Rascunho sugerido** lado a lado | Validada em produção ponta a ponta (Fase 7) | Persona Live | `ArgumentPanel`, `DraftPanel`, `EvidenceCard` (selecionável), `Input` |
| F-12 | **Controles do Live** | Encurtar · Aprofundar · Outra experiência · Copiar (só o rascunho) · Pausar e revisar evidências · Encerrar (somente leitura) · Duplicar sessão | Validada | Persona Live | `Button`, `IconButton` |
| F-13 | **Lacuna honesta** | Sem evidência suficiente, o Live não gera resposta genérica: mostra a lacuna e sugere o que registrar | Validada | Persona Live | `ArgumentPanel` (estado lacuna) |
| F-14 | **Artefatos profissionais** | 4 tipos: **Resposta STAR**, **Pitch pessoal** (30/60/90 s), **Currículo ATS**, **Portfólio por casos**. Criação em etapas, seções Conteúdo, Evidências e Versões, estados Rascunho e Revisado. | Aprovada visualmente em 30/08/2026 (Fase 8) | Artefatos | `ArtifactCard`, `StepFlow`, `TraceLine` |
| F-15 | **Ações fechadas de IA nos Artefatos** | Encurtar · Aprofundar · Adaptar ao objetivo · Gerar alternativa, sempre sobre a seção ou duração selecionada. **Sem chat aberto.** | Implementada | Artefatos › detalhe | `Button` |
| F-16 | **Salvar do Live nos Artefatos** | Uma resposta do Live vira Resposta STAR em rascunho (não é um tipo novo) | Implementada | Live → Artefatos | `Button` |
| F-17 | **Exportação PDF** | Currículo e Portfólio: pré-visualização e PDF. STAR e Pitch: copiar. | Implementada | Artefatos › detalhe | `Button` |
| F-18 | **Versões** | Snapshots de geração e revisão com restauração; nada sobrescreve silenciosamente uma edição manual | Implementada | Artefatos › seção Versões | `EntryCard` |
| F-19 | **Configurações** | Perfil · Preferências (lembrete, comunicação opcional) · Dados e privacidade (exportar JSON, excluir conta com reautenticação Microsoft e a confirmação "EXCLUIR") · Conta Microsoft | Implementada e validada visualmente em 31/08/2026; migração pendente no Supabase | Configurações | `Switch`, `Input`, `Button` |
| F-20 | **Rastreabilidade visível** | Linha `registro → sugestão → evidência → prova → uso` em todo detalhe: é o **elemento-assinatura** do produto | Implementada | Todas as telas de detalhe | `TraceLine` |
| F-21 | **Agente Persona** 🧭 | Eixo da plataforma. Conversa que segue o ciclo do agente colaborativo: Compreender → Organizar → Ativar → Acompanhar. Responde só com base nas evidências registradas, cita a origem de cada afirmação, nunca cria evidência sem confirmação e leva até Diário, Evidências, Persona Live ou Artefatos | **Não implementada.** Protótipo de direção de LD-026 (16/09/2026) neste redesign | Início (central) e painel acoplado em todas as telas | `AgentPrompt`, `AgentPanel`, `Composer`, `MessageBubble`, `EvidenceCard` (sugestão), `Chip` |

**Fora da superfície atual (não desenhar como funcional):**
- planos, preços, paywall e billing;
- carta de apresentação e DOCX;
- cadastro e senha próprios;
- upload de arquivo (as provas são só por link);
- níveis Validada e Certificada (aparecem só como explicação "indisponível");
- áudio, escuta, transcrição ou modo automático do Live;
- integração com Meet, Zoom ou Teams;
- voz própria no Diário;
- o agente colaborativo **como funcionalidade implementada**: no redesign ele é a direção do produto (F-21), mas o texto das telas nunca afirma que já existe no app;
- CRM: funil, pipeline, leads, contatos, tabelas de gestão e automações de vendas;
- landing page, rede social, painel administrativo e app mobile dedicado.

## 5. Fluxos de ponta a ponta

### Fluxo 1 — Primeiro valor (primeiro uso)

`Entrar com Microsoft → Onboarding (4 etapas) → primeiro registro no Diário → sugestões → revisão → evidência confirmada → Início com KPIs iniciais`

| Passo | Tela | O que a pessoa vê e faz | Regra |
|---|---|---|---|
| 1 | Entrar | Promessa, demonstração de rastreabilidade e botão único "Entrar com Microsoft" | Não é landing de marketing: sem preços nem depoimentos |
| 2 | Onboarding 1/4 · Contexto | Confirma o nome vindo da Microsoft, o momento profissional e o objetivo | "Etapa 1 de 4", sem abas nem painel do agente |
| 3 | Onboarding 2/4 · Privacidade | Consentimento obrigatório; comunicações opcionais em controle separado | Nunca agregar os dois |
| 4 | Onboarding 3/4 · Rotina | Lembrete opcional (o horário só aparece se ligado) | Nunca bloqueia o avanço |
| 5 | Onboarding 4/4 · Primeiro registro | Escreve um Daily Log real | Não é tour promocional |
| 6 | Início | KPIs em estado "dados insuficientes" e a próxima ação "Fazer diagnóstico" ou "Revisar sugestões" | Nunca mostrar score inventado |

### Fluxo 2 — Rotina diária (Diário → evidência)

`Diário → escrever → Salvar registro → Sugestões da IA (1 a 3) → revisar campos → Confirmar evidência → Evidências`

- O editor fica em primeiro plano, sem formulário burocrático; o histórico aparece logo abaixo, em cards.
- Depois de salvar, o detalhe do registro abre em painel flutuante com as seções **Registro** e **Sugestões**.
- Se a IA falhar: o registro permanece salvo e o modo manual continua disponível. Mensagem calma, sem culpar.
- Excluir um registro que já originou uma evidência confirmada é **bloqueado**, com a explicação do motivo.

### Fluxo 3 — Documentar uma evidência

`Evidências → visão "Para revisar" ou "Todas" → abrir evidência (painel flutuante) → seção Provas → Adicionar link → nível muda de Registrada para Documentada`

- Seções do detalhe: **Resumo** · **Provas** · **Uso** (onde a evidência foi usada no Live e nos Artefatos).
- Ações: editar, confirmar sugestão, adicionar ou remover link, arquivar, "Testar no Persona Live".
- Validada e Certificada aparecem apenas como explicação de níveis futuros, nunca como estado alcançável.

### Fluxo 4 — Entrevista com o Persona Live ⭐ (diferencial)

`Persona Live → Nova sessão → vaga/objetivo + empresa (+ descrição opcional) → evidências recomendadas com o motivo → autorizar de 1 a 8 → Iniciar → digitar a pergunta → Argumentos reais + Rascunho sugerido → Encurtar / Aprofundar / Outra experiência → Copiar ou Salvar nos Artefatos → Encerrar`

| Estado do workspace | O que aparece |
|---|---|
| Preparação | Contexto da oportunidade, lista de evidências recomendadas (título, competências, nível e **motivo da recomendação**) e controle explícito de autorização |
| Pronto | Campo de pergunta em foco (a ação principal) |
| Processando | Pergunta preservada e indicador discreto |
| Resposta | **Argumentos reais** (fatos, ação, resultado, competências, evidência de origem, alerta do que não afirmar) e **Rascunho sugerido** (resposta curta para apoio, não para leitura literal) |
| Lacuna | "Ainda não há evidência para sustentar esta resposta", com os fatos que faltam e a ação "Registrar no Diário" |
| Encerrada | Somente leitura, com a ação "Duplicar sessão" |

- Duração do rascunho: objetiva 15–25 s · comportamental/STAR 30–45 s · complexa até 60 s. Nunca há resposta automática de 90 s.
- Em largura compacta, os Argumentos vêm **antes** do Rascunho; em largura expandida, lado a lado.
- **Argumentos e Rascunho não usam bolhas de chat.** A composição é editorial e operacional. O Agente Persona pode preparar a sessão (oportunidade e evidências recomendadas), mas a **autorização das evidências é sempre da pessoa**.
- Avisos fixos: o Persona não responde por você, não é indetectável e processos seletivos podem restringir assistência externa.

### Fluxo 5 — Criar um Artefato

`Artefatos → Novo Artefato → 1 tipo e objetivo → 2 contexto da oportunidade → 3 dados complementares → 4 selecionar e autorizar evidências → 5 gerar → 6 revisar no editor → marcar como Revisado → Copiar ou Exportar PDF`

| Tipo | Estrutura | Saída |
|---|---|---|
| Resposta STAR | Situação · Tarefa · Ação · Resultado · Aprendizado (opcional) | Salvar e copiar |
| Pitch pessoal | Três versões: 30 s · 60 s · 90 s, editáveis de forma independente | Salvar e copiar |
| Currículo ATS | Identificação · Objetivo · Resumo · Experiências e projetos · Formação · Competências e idiomas | Pré-visualização e PDF |
| Portfólio por casos | Capa · Apresentação · Competências · Projetos · Casos (contexto, ação, resultado, aprendizado, provas) · Contato | Pré-visualização e PDF |

- Seções do detalhe: **Conteúdo** · **Evidências** (correspondência dos fatos) · **Versões**. O Agente Persona pode pré-preencher tipo e objetivo, nunca o conteúdo sem fonte.
- Dados complementares (contato, formação, idiomas) aparecem marcados como "declaração manual", não como evidência.
- Sem fatos suficientes, o artefato mostra uma **lacuna explícita**, nunca um texto genérico.

### Fluxo 6 — Entender o Narrative Score

`Início (faixa de KPIs ou pergunta ao agente) → abrir painel do Score → Resumo / Histórico / Como é calculado → próxima ação para sair da "Base declarada"`

- Mostrar sempre: total, **origem** (Base declarada, Parcialmente observado ou Observado), período, confiança e última atualização.
- Progresso concreto rumo ao dado observado: "4 de 6 registros · 2 de 3 semanas" (Consistência) e "4 de 5 evidências confirmadas" (Coerência).
- A Coerência observada é recalculada sob demanda, pelo botão "Atualizar análise".

### Fluxo 7 — Controle de dados

`Configurações → Dados e privacidade → Exportar dados (JSON completo) | Excluir conta → reautenticação Microsoft → digitar "EXCLUIR" → confirmação forte`

### Fluxo 8 — Pedir e agir com o Agente Persona (fluxo central)

`Início ou qualquer tela → "Buscar ou perguntar" ou botão Agente → pergunta livre ou chip → resposta com evidências citadas → ação proposta → superfície (Diário, Evidências, Persona Live, Artefatos) → confirmação da pessoa`

| Etapa do agente (LD-026) | Exemplo |
|---|---|
| Compreender | "Qual oportunidade você quer preparar agora?" |
| Organizar | "Organize minhas evidências por competência." → grupos de cards, cada um com link para a evidência |
| Ativar | "Quero treinar para a entrevista na Aurora." → "Abrir no Persona Live", com a sessão preparada e a autorização das evidências pendente da pessoa |
| Acompanhar | "O que falta para meu score sair da base declarada?" → lacunas e progresso, com a origem dos números |

Ações que o agente pode propor: abrir uma evidência, revisar sugestões, preparar uma sessão no Live, iniciar um Artefato (tipo e objetivo pré-preenchidos) e registrar no Diário (abre o editor, e a pessoa escreve).

Regras:
- o agente é a **porta de entrada**, não o substituto das superfícies: ele prepara e abre; geração, revisão e confirmação acontecem no Diário, nas Evidências, no Live e nos Artefatos, por ações nomeadas;
- cada afirmação traz um `Chip` com a evidência de origem; sem evidência, o agente diz "ainda não há registro sobre isso" e sugere o Diário;
- uma evidência sugerida pelo agente aparece como `EvidenceCard` variante sugestão, com "Confirmar evidência"; nada é salvo sem confirmação;
- o agente nunca autoriza evidências no Live, nunca escreve a resposta final de entrevista fora do Live e nunca marca um Artefato como Revisado;
- o rodapé "O agente só usa as evidências que você registrou. Confira sempre a origem." fica sempre visível;
- o botão de enviar é Ink, nunca de marca: a conversa não compete com a ação principal da tela.

## 6. Fichas por tela (kit do redesign)

Regras comuns a todas as telas:
- **um** botão de marca;
- **um** bloco focal escuro, apenas quando a tela tiver um "o que faço agora?";
- botão Ink: no máximo um por card;
- estados vazio, carregando e erro definidos.

### 6.1 Início
- **Objetivo:** ser o ponto de partida com o agente e responder "o que faço agora?".
- **Estrutura:**
  - saudação, por exemplo "Bom dia, Yan." com a linha "2 sugestões esperando sua revisão.";
  - **campo do agente** (`AgentPrompt`) grande, com o texto "Buscar ou perguntar" e 4 chips: "O que falta para o score observado?", "Organize minhas evidências", "Preparar uma entrevista", "Criar um Artefato";
  - **FocalCard** (o único bloco escuro) com o briefing do agente: stepper "Do score declarado ao observado" e a próxima ação;
  - **faixa de KPIs** com `ScoreRing` 65 · "Base declarada" e `DimensionRow` para Coerência 75, Consistência 50 e Credibilidade "Ainda não avaliada";
  - **4 tiles de destino**: Diário — "Último registro ontem"; Evidências — "4 confirmadas · 2 para revisar"; Persona Live — "1 sessão encerrada"; Artefatos — "1 revisado · 1 rascunho";
  - uma linha de 3 cards recentes (`EntryCard` e `EvidenceCard`) e as competências recorrentes e lacunas.
- **Ao enviar uma pergunta**, a conversa abre na área central e os demais blocos recuam para baixo; o briefing continua acessível.
- **Ação de marca:** "Revisar sugestões".
- **Estados:** sem registros · dados insuficientes · calculando · disponível · agente indisponível (o campo vira busca simples) · falha parcial (o restante do Início continua funcionando).

### 6.2 Diário
- **Objetivo:** registrar rápido.
- **Estrutura:**
  - `CaptureEditor` "O que aconteceu hoje?", com data e contexto opcionais;
  - histórico em **grade de `EntryCard`**, com o campo "Buscar ou perguntar"; o período fica atrás de "Filtros";
  - o detalhe abre em painel flutuante, com as seções Registro e Sugestões.
- **Ação de marca:** "Salvar registro"; no detalhe, "Confirmar evidência".
- **Sem bloco focal escuro** (o editor é o foco).
- **Estados:** vazio inicial · nenhum resultado · salvando · salvo · gerando sugestões · nenhuma sugestão útil · falha da IA com modo manual · exclusão bloqueada.

### 6.3 Evidências
- **Objetivo:** encontrar, revisar e documentar.
- **Estrutura:**
  - campo "Buscar ou perguntar";
  - chips de visão Todas e Para revisar;
  - botão "Filtros" que abre competência, período e nível (recolhidos, não seis controles no topo);
  - **grade de `EvidenceCard`** (2–3 colunas), sem tabela;
  - detalhe em painel flutuante com as seções Resumo, Provas e Uso, mais a `TraceLine`.
- **Ação de marca:** "Registrar evidência" na grade; "Adicionar link de prova" no detalhe de uma evidência Registrada.
- **Estados:** vazio inicial ("Nenhuma evidência ainda. Comece pelo Diário.") · nenhum resultado com "Limpar filtros" · link inválido · arquivada.

### 6.4 Persona Live ⭐
- **Objetivo:** apoiar a resposta de entrevista com fatos reais.
- **Estrutura:**
  - **Lista de sessões:** cards de sessões recentes e "Nova sessão".
  - **Preparação:** formulário da oportunidade e evidências recomendadas, com motivo e seleção (de 1 a 8).
  - **Workspace:** cabeçalho com empresa, vaga e estado; campo de pergunta; histórico cronológico de perguntas; `ArgumentPanel` + `DraftPanel`; controles; fontes e alertas.
- **Painel do agente:** começa recolhido neste workspace. Se for aberto, Argumentos e Rascunho empilham (Argumentos primeiro) quando a área útil ficar abaixo de 1280 px.
- **Ação de marca:** "Iniciar sessão" na preparação; "Gerar apoio" no workspace.
- **Bloco focal escuro:** opcional, apenas no cabeçalho da sessão ativa.
- **Estados:** nenhuma evidência disponível · seleção insuficiente · processando · resposta sustentada · lacuna · falha parcial · pausada · encerrada.

### 6.5 Artefatos
- **Objetivo:** produzir material profissional rastreável.
- **Estrutura:**
  - biblioteca em **grade de `ArtifactCard`** (tipo, objetivo, estado, atualização, principais fontes); filtros por tipo, estado e data recolhidos atrás de "Filtros";
  - "Novo Artefato" em `StepFlow` de 6 etapas;
  - detalhe em workspace de página inteira (editor longo), com as seções Conteúdo, Evidências e Versões e índice de âncoras.
- **Ação de marca:** "Novo Artefato" na biblioteca; "Gerar rascunho" na criação; "Marcar como revisado" no detalhe.
- **Estados:** vazio · sem resultado · gerando · lacuna · conflito de versão · fonte indisponível · falha recuperável.

### 6.6 Painel do Narrative Score
- **Objetivo:** explicar o número.
- **Estrutura:**
  - painel flutuante com as seções Resumo, Histórico e Como é calculado (`SectionIndex`);
  - o Resumo traz origem, período, confiança, as três `DimensionRow` e o progresso para o dado observado;
  - o Método traz as fórmulas em linguagem simples.
- **Ação de marca:** "Registrar no Diário" ou "Atualizar análise", conforme o estado.
- **Estados:** diagnóstico não iniciado · base declarada · parcialmente observado · observado · falha da análise.

### 6.7 Configurações
- **Objetivo:** dar controle à pessoa.
- **Estrutura:** navegação secundária com Perfil, Preferências, Dados e privacidade e Conta Microsoft.
- **Ação de marca:** "Salvar alterações". A exclusão de conta é ação destrutiva separada, nunca escondida em hover, com confirmação forte.
- **Sem planos e sem preços.**

### 6.8 Agente Persona
- **Objetivo:** ser o eixo da plataforma: receber a pergunta, responder com evidências citadas e levar à superfície certa.
- **Estrutura:**
  - **Início:** conversa na área central, a partir do `AgentPrompt`;
  - **demais telas:** `AgentPanel` acoplado à direita, 380–420 px, recolhível, raio 28, sombra Float, empurrando o conteúdo;
  - cabeçalho com "Agente Persona", a linha "Você está em: Evidências" e o botão de recolher;
  - conversa em `MessageBubble`: pessoa em Ink, agente em branco, com chips de evidência e uma linha de ações;
  - `Composer` com chips contextuais (no Início: "O que falta para o score observado?", "Organize minhas evidências", "Preparar uma entrevista");
  - rodapé com o aviso fixo.
- **Ação de marca:** nenhuma (a tela de fundo mantém a sua); enviar é Ink.
- **Estados:** vazio (apresentação curta e os chips) · respondendo (indicador discreto) · resposta com citações · sem evidência (lacuna e "Registrar no Diário") · falha ("Não consegui responder agora. Nada foi alterado.") · recolhido.

## 7. Componentes do design system

| Situação | Componentes |
|---|---|
| Mantidos | `Icon`, `Button`, `IconButton`, `Badge`, `Chip`, `Avatar` (só para pessoas e o agente rotulado), `Input`, `Switch`, `Card`, `FocalCard`, `DestinationTile`, `JourneyStepper`, `ProgressBar`, `ScoreRing`, `NavItem` |
| Renomeados ou adaptados | `SourceCard` → **`EvidenceCard`** (variantes: card de grade, sugestão para revisar, selecionável) · `ConversationRow` → **`EntryCard`** (registro, sessão, versão) · `Composer` e `MessageBubble` → núcleo do **Agente Persona** (Início e painel acoplado; avatar do agente rotulado "Agente Persona") |
| Removidos de uso nas telas | `PillTabs` como navegação (abas estão proibidas; visões viram `Chip`) · tabelas e linhas densas · painéis laterais de detalhe |
| Novos | **`AgentPrompt`** (campo "Buscar ou perguntar" com chips) · **`AgentPanel`** (painel acoplado) · **`FloatingPanel`** (detalhe ancorado) · **`SectionIndex`** (índice de âncoras) · **`DimensionRow`** · **`StepFlow`** ("Etapa N de M", Voltar/Continuar) · **`ArgumentPanel`** · **`DraftPanel`** (duração-alvo e controles) · **`ArtifactCard`** · **`TraceLine`** (rastreabilidade, o elemento-assinatura) · **`CaptureEditor`** (editor do Diário; não é chat) |

## 8. Regras de honestidade e de IA (inegociáveis)

1. A IA sugere e a pessoa confirma. Nada vira evidência sem revisão.
2. Nenhum número, responsabilidade, resultado ou competência inventados. Sem fato suficiente, o produto mostra uma **lacuna**, nunca texto genérico.
3. Todo argumento e todo trecho de artefato apontam para a evidência de origem.
4. O vocabulário de níveis é **Registrada** (sem prova) e **Documentada** (com link). Nunca usar "verificada" sem verificação real.
5. A Credibilidade não recebe número enquanto não houver validação real: aparece como "Ainda não avaliada".
6. Poucos dados produzem estado de insuficiência, não pontuação artificial.
7. O Persona não responde pela pessoa, não é indetectável e não promete aprovação.
8. O Agente Persona é a camada de conversa da plataforma e segue as regras 1 a 7: cita a origem de cada afirmação, não cria evidência sem confirmação, não autoriza evidências no Live e não escreve a resposta final de entrevista nem revisa Artefatos. Dentro dos workspaces do Live e dos Artefatos a IA atua por ações nomeadas e fechadas, sem bolhas de chat entre os Argumentos e o Rascunho.

## 9. Matriz fluxo × tela × componente

| Fluxo | Entrar | Onboarding | Início | Diário | Evidências | Score | Live | Artefatos | Config. |
|---|---|---|---|---|---|---|---|---|---|
| 1 Primeiro valor | ● | ● StepFlow | ● ScoreRing | ● CaptureEditor | ● EvidenceCard | | | | |
| 2 Rotina diária | | | ● EntryCard | ● CaptureEditor · EvidenceCard | ● | | | | |
| 3 Documentar | | | ● FocalCard | | ● EvidenceCard · TraceLine | | | | |
| 4 Persona Live ⭐ | | | ● DestinationTile | | ● "Testar no Live" | | ● ArgumentPanel · DraftPanel | ● Salvar STAR | |
| 5 Artefato | | | ● DestinationTile | | ● EvidenceCard selecionável | | | ● StepFlow · ArtifactCard · TraceLine | |
| 6 Score | | | ● ScoreRing · DimensionRow | ● | ● | ● DimensionRow · SectionIndex | | | |
| 7 Dados | | | | | | | | | ● Switch · Button |
| 8 Agente (central) | | | ● AgentPrompt | ● AgentPanel | ● AgentPanel | ● AgentPanel | ● AgentPanel ("Abrir no Live") | ● AgentPanel (pré-preenche tipo e objetivo) | |

## 10. Massa de dados fictícia (usada em todas as telas)

**Pessoa:** Yan · estagiário em IA generativa · objetivo: "Vaga de analista júnior de IA generativa".

**Narrative Score: 65 / 100 · Base declarada · confiança Inicial**

| Dimensão | Valor | Situação |
|---|---|---|
| Coerência | 75 | declarada · rumo ao dado observado: 4 de 5 evidências confirmadas |
| Consistência | 50 | declarada · rumo ao dado observado: 4 de 6 registros · 2 de 3 semanas |
| Credibilidade | — | Ainda não avaliada (fora do total) |

Conferência: 0,6 × 75 + 0,4 × 50 = 45 + 20 = **65** (exato).

**Evidências confirmadas (4)**

| # | Título | Competências | Nível | Provas |
|---|---|---|---|---|
| 1 | Automação de relatórios semanais com IA generativa | Automação · Análise de dados | Documentada | 2 links |
| 2 | Pitch de 5 minutos para banca de empreendedorismo | Comunicação · Storytelling | Documentada | 1 link |
| 3 | Entrevistas com 8 usuários para validar o problema | Pesquisa com usuários · Análise | Documentada | 1 link |
| 4 | Oficina de Python para calouros | Ensino · Liderança | **Registrada** | 0 |

**Sugestões para revisar (2)**, vindas do registro de ontem no Diário:
- Organização do cronograma de entregas do semestre;
- Protótipo de interface para app de carreira.

**Diário:** 4 registros em 2 semanas; último registro ontem.

**Persona Live:** 1 sessão encerrada.
- Oportunidade: "Analista júnior de IA generativa · Empresa Aurora (fictícia)", com as evidências 1, 2 e 3 autorizadas.
- Pergunta-exemplo: "Conte sobre uma vez em que você automatizou um processo." → o argumento principal vem da evidência 1; o rascunho é comportamental, com 30–45 s.
- Pergunta-exemplo com lacuna: "Fale de um conflito em equipe." → "Ainda não há evidência para sustentar esta resposta. Registre uma situação de conflito no Diário."

**Artefatos (2)**
- Resposta STAR "Problema resolvido com dados" · **Revisado** · cita a evidência 1.
- Pitch pessoal · **Rascunho** · cita as evidências 1, 2 e 3.

**Agente Persona, conversa-exemplo:**
- Você: "O que falta para meu score sair da base declarada?"
- Agente: "Para a Consistência observada faltam 2 registros e 1 semana (hoje: 4 de 6 registros · 2 de 3 semanas). Para a Coerência observada falta 1 evidência confirmada (hoje: 4 de 5). Revisar as 2 sugestões do Diário resolve a Coerência." · chips: [Sugestões do Diário] [Como é calculado] · ação: "Revisar sugestões".
- Conferência: 6 − 4 = 2 registros; 3 − 2 = 1 semana; 5 − 4 = 1 evidência; 4 + 2 = 6 ≥ 5.

**Stepper do FocalCard — "Do score declarado ao observado"**
- Diagnóstico ✓
- Primeiro registro ✓
- **5 evidências confirmadas (4 de 5, em andamento)**
- Score observado (bloqueado)

Próxima ação: "Revise as 2 sugestões do Diário" → botão de marca "Revisar sugestões".

## 11. Glossário — termos corretos e proibidos

| Use | Não use |
|---|---|
| Diário, registro, Daily Log | conversa, chat, mensagem (fora do Agente Persona) |
| evidência, prova, link de prova | fonte acadêmica, DOI, referência ABNT |
| Registrada, Documentada, Para revisar (níveis de evidência) · "Base declarada" (só como origem do score) | Declarada como nível de evidência, verificada (sem verificação), Básico / Intermediário / Avançado |
| Persona Live, Argumentos reais, Rascunho sugerido · Agente Persona | tutor, assistente que responde por você |
| Artefato: Resposta STAR, Pitch pessoal, Currículo, Portfólio | carta de apresentação, produções |
| Configurações | Perfil e plano, Pro, Premium, preço |
| Entrar com Microsoft | cadastro, senha, recuperar senha |
| Cards, painel flutuante, seção, "Buscar ou perguntar" | CRM, pipeline, funil, leads, contatos, aba, tabela de gestão |
