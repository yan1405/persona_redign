# Plano de correção do Claude Design — Persona

> **Versão:** 2.1 · 19/10/2026 (substitui a v2.0 e a v1.0; a v2.1 acrescenta o painel experimental do Agente Persona)
> **Projeto:** https://claude.ai/design/p/ff1a7bce-a6f2-4fa9-af99-a6196b748678
> **Decisão vigente (Opção A):** o Persona continua sendo um SaaS de **narrativa profissional**. O kit "Persona Acadêmico" gerado pelo Claude Design foi um erro de escopo e deve ser substituído.
> **Fontes da verdade, em ordem de precedência:**
> 1. [`persona-fluxos-e-features.md`](persona-fluxos-e-features.md) — produto, fluxos, features validadas e massa de dados;
> 2. [`design-dna-persona.md`](design-dna-persona.md) — visual;
> 3. este plano — ordem de execução.

---

## O que mudou da v1.0 para a v2.0

A v1.0 foi escrita a partir do Design DNA, sem conferir os documentos aprovados do app. Na conferência de 19/10/2026, oito pontos divergiam do produto real:

| Ponto | v1.0 (errado) | v2.0 (produto aprovado) |
|---|---|---|
| Navegação | 6 destinos com "Narrative Score" e "Perfil e plano" | 5 destinos (Início, Diário, Evidências, **Persona Live**, Artefatos) + Configurações no rodapé; o Score abre em painel a partir do Início |
| Persona Live | Ausente | Diferencial do produto: tela e componentes próprios |
| Diário | Fluxo guiado de 4 passos | Editor livre "O que aconteceu hoje?"; a IA sugere e a pessoa confirma. Os passos guiados pertencem ao onboarding |
| Chat | `Composer`/`MessageBubble` no gerador de artefatos | Sem chat nos fluxos validados (ações fechadas no Live e nos Artefatos). A conversa fica só no **painel experimental do Agente Persona** (v2.1, decisão de Yan em 19/10/2026) |
| Status da evidência | Declarada / Documentada | **Registrada** / Documentada; "Para revisar" é a sugestão ainda não confirmada |
| Níveis de habilidade | Básico / Intermediário / Avançado (fictícios) | Não existem no produto. As competências são texto livre |
| Score | (75 + 50 + 70) ÷ 3 = 65 | 0,6 × Coerência + 0,4 × Consistência = 0,6 × 75 + 0,4 × 50 = **65**; a Credibilidade fica fora do total ("Ainda não avaliada") |
| Artefatos | STAR, Pitch, **Carta** | STAR, Pitch (30/60/90 s), **Currículo ATS**, **Portfólio** |
| Planos e preços | Free/Pro/Premium com valores em R$ | Não há planos, preços nem paywall nesta fase |
| Entrada | Cadastro, Login e Senha | Somente "Entrar com Microsoft" |
| Contexto da Etapa 0 | Seis prints do app atual | Um anexo único: `persona-fluxos-e-features.md` |

---

## Como usar este arquivo

1. Execute as etapas **em ordem**. Cada etapa depende da anterior.
2. **Uma tarefa = um prompt.** Cole o bloco "Prompt" no chat do Claude Design e aguarde a conclusão antes de colar o próximo.
3. Antes de avançar, confira o **critério de aceite** com os próprios olhos nas capturas. O Claude Design já declarou "feito" sem ter visto o resultado; não aceite sem imagem.
4. Tarefas marcadas **[MANUAL]** são suas: o Claude Design não as executa.

---

## Painel de erros e etapa que corrige cada um

| # | Erro encontrado | Onde | Etapa |
|---|---|---|---|
| E0 | Escopo errado: kit acadêmico com tutores, ABNT e a persona "Yan Lima · UFPE" | Readme, componentes, telas, dados | 1, 2, 4 |
| E1 | Painel "Próximo passo" do card escuro estoura em ~1100 px | Início | 3 (T3.3) |
| E2 | Tiles quebram com um tile sozinho na última linha | Início | 3 (T3.2) |
| E3 | Conteúdo rola por baixo da busca, que não tem fundo opaco | Biblioteca | 3 (T3.1) |
| E4 | Dados de exemplo repetidos entre cartões | Biblioteca | 4 (T4.3) |
| E5 | Botões de mesma ênfase competem na mesma tela | Conversas, diálogo, shell | 3 (T3.4) |
| E6 | Itens de navegação levam a tela vazia ("fora do escopo") | Leituras, Fichamentos, Projetos | 2 (T2.5), 4 |
| E7 | Layout estreito entregue sem verificação visual | Conversas | 5 (T5.2) |
| E8 | Sistema publicado como **padrão da organização** | Configuração | 0 |

---

## Decisões deste plano (você pode vetar qualquer uma)

| # | Decisão | Justificativa |
|---|---|---|
| D1 | **Navegação:** Início · Diário · Evidências · Persona Live · Artefatos, mais Configurações no rodapé. O Narrative Score é uma faixa de KPIs no Início e abre em painel | `INFORMATION_ARCHITECTURE.md` §2 (aprovado) |
| D2 | **Chat só no painel experimental do Agente Persona** (F-21), que abre de qualquer tela. `Composer` e `MessageBubble` ficam restritos a ele; o Diário ganha um `CaptureEditor` próprio. Live e Artefatos continuam sem chat | Fase 7: "o Persona Live não usa bolhas de chat"; Fase 8: "não haverá chat aberto no editor". O painel prototipa o agente colaborativo aprovado em LD-026 sem alterar fluxos validados. Decisão de Yan, 19/10/2026 |
| D3 | **Sem o mascote Xisto por enquanto**: ícones Lucide | Os arquivos-fonte do Xisto não existem fora do código. A decisão é provisória, sujeita a veto |
| D4 | **Níveis de evidência:** Registrada (sem link) e Documentada (≥ 1 link). Validada e Certificada aparecem só como explicação "indisponível". "Para revisar" = sugestão não confirmada | Fase 5 e `PRODUCT_BRIEF.md` §5 |
| D5 | **Competências em texto livre**, sem taxonomia e sem níveis de habilidade | A Fase 5 deixa a taxonomia global fora do escopo. Resolve a antiga pendência U0.4 |
| D6 | **Tokens visuais permanecem** (cores, fontes, raios, sombras) | O resultado visual foi aprovado; o erro é de conteúdo e de layout |
| D7 | **Fora do desenho:** planos e preços, paywall, carta de apresentação, cadastro/senha, upload de arquivo, áudio no Live, app mobile dedicado | `PRODUCT_BRIEF.md` §10 e `INFORMATION_ARCHITECTURE.md` §6 |

**Massa de dados:** use **exclusivamente** a seção 10 de `persona-fluxos-e-features.md`.

---

## Regras permanentes (cole uma vez, na tarefa T1.1)

```text
REGRAS PERMANENTES DO PROJETO — valem para todo prompt seguinte.
0. Fonte da verdade de produto: o anexo persona-fluxos-e-features.md (também em github.com/yan1405/persona_redign/docs). Em qualquer dúvida de fluxo, feature, texto ou dado, ele vence.
1. Produto: Persona é uma plataforma de NARRATIVA PROFISSIONAL. Ciclo: Diário (texto livre) → sugestões da IA → a pessoa confirma → Evidência (Registrada ou Documentada) → Narrative Score explicável → ativação no Persona Live (argumentos reais + rascunho para entrevista) e nos Artefatos (Resposta STAR, Pitch pessoal, Currículo ATS, Portfólio). NÃO é plataforma acadêmica, de tutores nem de ABNT. Se aparecer algo disso, remova.
2. Navegação: Início, Diário, Evidências, Persona Live, Artefatos; Configurações no rodapé. O Narrative Score fica no Início e abre em painel. Não crie outros destinos.
3. Chat restrito: a conversa com IA existe SOMENTE no painel lateral "Agente Persona" (experimental), que abre pelo botão "Agente" no cabeçalho de qualquer tela. Diário, Evidências, Persona Live e Artefatos NÃO têm bolhas de mensagem: lá a IA age por ações nomeadas (Encurtar, Aprofundar, Outra experiência, Adaptar ao objetivo, Gerar alternativa). O agente só usa evidências registradas, cita a origem de cada afirmação e nunca salva nada sem confirmação.
4. Visual: não altere nenhum token. Indigo + Slate, Plus Jakarta Sans + Inter, raios 16/22/28/pill, sombras Soft/Float/Slab. Sem laranja, sem emoji, sem ícones 3D, sem mascote.
5. Hierarquia: no máximo UM botão de marca (gradiente Indigo) por tela e UM bloco focal escuro por tela. Botão Ink: no máximo um por card.
6. Honestidade: nunca mostre conquista sem a evidência que a sustenta. Níveis: Registrada e Documentada; "Para revisar" para sugestões. Credibilidade = "Ainda não avaliada". Sem fato suficiente, mostre uma lacuna, nunca um texto genérico. Todo texto gerado aponta a evidência de origem.
7. Fora do escopo: planos, preços, paywall, carta de apresentação, cadastro/senha (a entrada é só "Entrar com Microsoft"), upload de arquivo, áudio.
8. Texto: português do Brasil, "você", sentence case, títulos terminando em ponto, números tabulares. Estados vazios sempre apontam o próximo passo.
9. Dados: use apenas a massa de dados da seção 10 do anexo. Nunca invente cliente, empresa ou pessoa reais.
10. Verificação: depois de cada alteração, abra o resultado em 1024, 1280 e 1440 px, tire capturas e me mostre. Não diga "feito" sem ter visto.
11. Uma tarefa por vez. Não altere nada fora do escopo do prompt.
Responda apenas "ok, regras registradas" e aguarde.
```

---

## Etapa 0 — Preparação [MANUAL] · ≈ 10 min

| ID | Tarefa | Critério de aceite |
|---|---|---|
| U0.1 | No Claude Design, abra o Design System e clique em **"Remove as org default"**. Antes disso, no seletor de design system do projeto, fixe o próprio "Persona Design System" (não "Padrão da organização") | O aviso "Currently org default" desaparece e o projeto continua apontando para o Persona |
| U0.2 | Anexe pelo botão **+** do chat o arquivo `persona-fluxos-e-features.md` (pasta `C:\Users\yansi\OneDrive\ref_redisgn_persona\docs\` ou repositório `docs/`). **Não anexe prints do app atual** | O arquivo aparece em `uploads/` |
| U0.3 | Confirme ou vete as decisões D1–D7, sobretudo a **D3 (Xisto)**. A D2 (chat só no painel do Agente) já foi decidida por você em 19/10/2026 | Decisões anotadas |

---

## Etapa 1 — Reorientar o escopo do design system

### T1.1 — Registrar as regras permanentes

**Prompt:** cole o bloco "Regras permanentes".
**Critério de aceite:** o Claude Design responde "ok, regras registradas" e não altera arquivos.

### T1.2 — Reescrever o Readme

```text
Leia uploads/persona-fluxos-e-features.md por inteiro. Depois reescreva o Readme do design system. O produto correto é o Persona (narrativa profissional); o brief "Persona Acadêmico" estava errado e deve ser removido por completo.

Altere somente estas seções:
1. Visão geral: descreva o Persona com as seções 1 e 2 do anexo (o que é, promessas, ciclo Diário → Evidência → Score → Persona Live/Artefatos). O case iStudio continua só como referência de estrutura.
2. Fontes: o repositório https://github.com/yan1405/persona_redign (docs/persona-fluxos-e-features.md = produto; docs/design-dna-persona.md = visual) e o case iStudio. Remova qualquer menção a prints do app atual.
3. Content fundamentals: troque TODOS os exemplos acadêmicos. Use: "Bom dia, Yan." / "Hoje, de relance." / "Tudo o que sustenta a sua história." Linhas de status: "4 confirmadas · 2 para revisar", "Score 65 · base declarada", "1 sessão encerrada". CTAs: "Salvar registro", "Revisar sugestões", "Confirmar evidência", "Adicionar link de prova", "Iniciar sessão", "Novo Artefato". Lacuna: "Ainda não há evidência para sustentar esta resposta. Registre a situação no Diário." Erro calmo: "Não foi possível gerar sugestões agora — seu registro está salvo e você pode estruturar manualmente."
4. Troque a frase sobre "honestidade acadêmica" por: "A honestidade é parte da voz: a IA sugere e você confirma. O Persona nunca inventa conquista, todo texto gerado cita a evidência de origem e o que não tem prova aparece como Registrada."
5. Remova o parágrafo "The current brief extends it to a desktop conversation platform..." e reescreva a seção "Intentional additions": remova SourceCard e o Switch para ABNT; mantenha MessageBubble e Avatar do agente, descritos como "exclusivos do painel experimental Agente Persona (protótipo do agente colaborativo LD-026)".
6. Remova "Yan Lima · Pedagogia · UFPE" e qualquer menção a ABNT, DOI, tutores, TCC, disciplinas e orientadora.

Mantenha intactas as seções Visual foundations e Iconography. Mostre o texto final do Readme.
```

**Critério de aceite:**
- [ ] Nenhuma ocorrência de "Acadêmico", "tutor", "ABNT", "DOI", "TCC", "UFPE", "orientadora" ou "Lima" no Readme; chat citado só como painel experimental do Agente.
- [ ] O Readme cita o Persona Live e os quatro tipos de Artefato.
- [ ] Visual foundations idêntico ao anterior.

### T1.3 — Atualizar SKILL.md, github.md e miniatura

```text
Atualize três arquivos para o produto correto:
1. SKILL.md: descrição, quando usar e regras de voz, sem nicho acadêmico; chat apenas no painel experimental do Agente Persona.
2. github.md: fonte yan1405/persona_redign, branch main, arquivos docs/persona-fluxos-e-features.md e docs/design-dna-persona.md, data real desta sincronização e seção "Screen map" com as sete telas da seção 6 do anexo marcadas "em reconstrução". Não invente hash de commit.
3. thumbnail.html: troque o exemplo acadêmico pelo Início do Persona (saudação, faixa de KPIs com 65, 4 tiles e o FocalCard), usando a massa de dados do anexo.
Não altere tokens. Mostre o diff resumido de cada arquivo.
```

**Critério de aceite:** os três arquivos não citam o nicho acadêmico; o `github.md` traz a data do dia.

---

## Etapa 2 — Reorientar os componentes

### T2.1 — SourceCard → EvidenceCard

```text
Renomeie SourceCard para EvidenceCard (seção 7 do anexo). Campos: título, competências (chips), nível (Registrada / Documentada), quantidade de links de prova, origem (Diário ou manual) e data de atualização. Três variantes:
(a) linha — para a lista de Evidências;
(b) sugestão para revisar — campos sugeridos pela IA, ações "Confirmar evidência" e "Descartar";
(c) selecionável — com checkbox e "motivo da recomendação", para o Persona Live e a criação de Artefatos.
Remova DOI, periódico, ano e ABNT. Atualize o @dsCard com as evidências 1 e 4 e com uma sugestão da massa de dados. Atualize todas as importações.
```

**Critério de aceite:** nenhum arquivo importa `SourceCard`; as três variantes aparecem com contraste AA.

### T2.2 — Variantes de status

```text
Em Badge e Chip, crie as variantes: Registrada (neutra, Slate), Documentada (sucesso: texto #064E3B sobre #ECFDF5), Para revisar (atenção: texto #78350F sobre #FFFBEB), Rascunho (neutra), Revisado (sucesso) e Lacuna (atenção). Todas com contraste mínimo de 4,5:1: informe a razão calculada de cada par, sem arredondamento intermediário. Documente no cartão de Badge.
```

**Critério de aceite:** as seis variantes aparecem com as razões calculadas, todas ≥ 4,5:1.

### T2.3 — Restringir o chat ao painel do Agente: EntryRow, CaptureEditor, Composer e MessageBubble

```text
1. Renomeie ConversationRow para EntryRow: linha de data + título + metadado + status. Variantes: registro do Diário, sessão do Persona Live e versão de Artefato.
2. Crie o componente novo CaptureEditor: o editor do Diário com o rótulo "O que aconteceu hoje?", contador (40 a 2.000 caracteres), data e contexto opcionais e botão de marca "Salvar registro". Sem chips de prompt e sem aparência de chat.
3. Mantenha Composer e MessageBubble, mas exclusivos do painel experimental "Agente Persona" (anexo, ficha 6.8). Composer: chips "O que falta para o score observado?", "Organize minhas evidências" e "Preparar uma entrevista"; botão de enviar Ink (não de marca); rodapé "O agente só usa as evidências que você registrou. Confira sempre a origem.". MessageBubble: pessoa em Ink; agente em branco, com chips de evidência citada e uma linha de ações ("Revisar sugestões", "Abrir no Persona Live"). Troque o Avatar variant="ai" pelo rótulo "Agente Persona" com selo "Experimental". Remova todos os chips e textos acadêmicos (ABNT, fontes, tutor).
4. Mantenha Switch para as Configurações (lembrete, comunicações opcionais).
Atualize os @dsCards e a lista de componentes do Readme.
```

**Critério de aceite:** busca por `ConversationRow` = zero; `Composer` e `MessageBubble` importados **só** pelo painel do Agente; o `CaptureEditor` não parece um chat.

### T2.4 — Novos componentes do Persona

```text
Crie estes componentes com os tokens existentes, cada um com @dsCard e dados da massa de dados do anexo:
1. DimensionRow: dimensão do Narrative Score com nome, valor 0–100 tabular, ProgressBar, origem (Declarada/Observada) e progresso rumo ao dado observado ("4 de 6 registros · 2 de 3 semanas"). Estado especial "Ainda não avaliada" sem número (Credibilidade).
2. StepFlow: "Etapa N de M", título em Plus Jakarta Sans, conteúdo, "Voltar" (ghost) e "Continuar" (marca). Usado no onboarding, no diagnóstico e no Novo Artefato.
3. ArgumentPanel: painel "Argumentos reais" do Persona Live — itens com o fato, o campo de origem (ação, resultado, competência…), a evidência citada (link) e o alerta "não afirme…". Estado lacuna: fatos que faltam e a ação "Registrar no Diário".
4. DraftPanel: painel "Rascunho sugerido" — texto, duração-alvo ("30–45 s · comportamental"), versão e ações Encurtar, Aprofundar, Outra experiência e Copiar.
5. ArtifactRow: tipo (STAR, Pitch, Currículo, Portfólio), objetivo, estado (Rascunho/Revisado), atualização e principais evidências.
6. TraceLine: linha de rastreabilidade "registro → sugestão → evidência → prova → uso", com os nós clicáveis. É o elemento-assinatura do produto.
Documente os estados padrão, foco, preenchido, erro e desabilitado.
```

**Critério de aceite:** seis novos @dsCards; foco com anel de 2 px `#A78BFA`.

### T2.5 — Navegação sem itens vazios

```text
Refaça o NavItem e a lateral com: Início, Diário, Evidências, Persona Live, Artefatos e, isolado no rodapé, Configurações. Remova Leituras, Fichamentos, Projetos e Conversas. Nenhum item pode levar a uma tela vazia ou "fora do escopo". A ação global da lateral é "Registrar agora" (botão Ink, abre o Diário). O card "Continue de onde parou" mostra o último registro com sugestões pendentes, com botão outline. Inclua o modo recolhido (rail).
```

**Critério de aceite:** cinco itens mais Configurações; nenhum placeholder; rail funcionando.

---

## Etapa 3 — Corrigir shell e layout

### T3.1 — Cabeçalho fixo e opaco (E3)

```text
Corrija o cabeçalho do shell. Faça: (1) cabeçalho fixo com fundo opaco #FAFAFC e sombra Soft só quando houver rolagem; (2) conteúdo começa abaixo do cabeçalho, com scroll-padding-top para que abas e filtros não fiquem cortados; (3) placeholder da busca: "Buscar registros, evidências, artefatos". Valide rolando Evidências em 1280 px e mostre capturas no topo e no meio da rolagem.
```

**Critério de aceite:** em nenhuma posição de rolagem o texto aparece atrás da busca.

### T3.2 — Grade de tiles por largura do container (E2)

```text
O Início agora tem QUATRO DestinationTile (Diário, Evidências, Persona Live, Artefatos). Use container queries sobre o painel principal: ≥ 900 px = 4 colunas em uma linha; < 900 px = 2 × 2. Nunca deixe um tile sozinho numa linha. Altura uniforme; linha de status em uma linha com reticências. Valide em 1024, 1280 e 1440 px.
```

**Critério de aceite:** nas três larguras a grade é 4 ou 2 × 2.

### T3.3 — FocalCard sem estouro (E1)

```text
Corrija o FocalCard (card escuro "Do score declarado ao observado"). Faça: (1) duas colunas (stepper à esquerda, próxima ação à direita) só com o container ≥ 1000 px, mínimo de 320 px para a próxima ação; (2) abaixo disso, empilhe; (3) o botão de marca nunca é cortado nem comprimido; (4) remova o rótulo "Orientadora"; (5) sem overflow horizontal. Use o stepper e a próxima ação da seção 10 do anexo. Valide em 1024, 1280 e 1440 px.
```

**Critério de aceite:** o CTA aparece inteiro nas três larguras; sem sobreposição; sem rolagem horizontal.

### T3.4 — Hierarquia de botões (E5)

```text
Audite todos os botões e aplique: (1) Marca: uma ação principal por tela, conforme a seção 6 do anexo; (2) Ink: no máximo um por card; o "Registrar agora" da lateral é Ink; (3) Outline: secundárias; (4) Ghost: terciárias. Entregue uma tabela tela × botão × nível antes e depois e aplique as correções.
```

**Critério de aceite:** a tabela existe; cada tela tem exatamente um botão de marca.

---

## Etapa 4 — Reconstruir as telas do kit

**Objetivo:** substituir `ui_kits/academico` por `ui_kits/persona`. **Uma tela por prompt**; aceite cada uma antes da seguinte. Cada prompt remete à ficha correspondente da seção 6 do anexo.

### T4.1 — Início

```text
Crie ui_kits/persona e a tela Início seguindo a ficha 6.1 do anexo: saudação; faixa de KPIs com ScoreRing 65 · "Base declarada" e três DimensionRow (Coerência 75, Consistência 50, Credibilidade "Ainda não avaliada"); quatro DestinationTile com as linhas vivas da ficha; FocalCard com o stepper e a próxima ação "Revise as 2 sugestões do Diário" e o botão de marca "Revisar sugestões"; registros e evidências recentes em EntryRow; competências recorrentes e lacunas. Clicar no score abre o painel do Narrative Score (T4.6). Valide em 1024, 1280 e 1440 px.
```

**Critério de aceite:** um botão de marca; 0,6 × 75 + 0,4 × 50 = 65 citado no método; Credibilidade sem número.

### T4.2 — Diário

```text
Crie a tela Diário seguindo a ficha 6.2: CaptureEditor em primeiro plano ("O que aconteceu hoje?"), histórico em EntryRow com busca e período, e o detalhe em painel lateral com abas Registro (texto original, data, contexto, editar, excluir) e Sugestões (2 sugestões em EvidenceCard variante "sugestão", com "Confirmar evidência" e "Descartar"; botão "Estruturar manualmente"). Mostre a TraceLine. NÃO é um fluxo de perguntas guiadas e NÃO é chat. Inclua os estados: gerando sugestões, nenhuma sugestão útil, falha da IA com modo manual e exclusão bloqueada.
```

**Critério de aceite:** editor livre; o texto original nunca é substituído; os quatro estados existem.

### T4.3 — Evidências (lista e detalhe) — corrige E4

```text
Crie a tela Evidências seguindo a ficha 6.3: busca, PillTabs com as visões Todas e Para revisar, um botão "Filtros" (competência, período, nível) e a lista de EvidenceCard variante linha — as 4 evidências e as 2 sugestões da massa de dados, sem nenhum texto repetido entre itens. O detalhe abre em painel com abas Resumo, Provas (links, nível calculado, "Adicionar link de prova" como botão de marca para a evidência 4) e Uso (onde foi usada no Live e nos Artefatos). Validada e Certificada aparecem só como explicação "indisponível nesta fase". Estado vazio: "Nenhuma evidência ainda. Comece pelo Diário."
```

**Critério de aceite:** seis itens sem repetição; nível Registrada/Documentada coerente com os links; detalhe ao lado.

### T4.4 — Persona Live

```text
Crie a tela Persona Live seguindo a ficha 6.4 e o fluxo 4 do anexo, em três vistas:
(1) Sessões: lista em EntryRow com a sessão encerrada e o botão de marca "Nova sessão".
(2) Preparação: vaga/objetivo e empresa (obrigatórios), descrição opcional, evidências recomendadas em EvidenceCard selecionável, com o motivo da recomendação, seleção de 1 a 8 e o botão de marca "Iniciar sessão".
(3) Workspace: cabeçalho com empresa, vaga e estado; campo de pergunta; histórico de perguntas; ArgumentPanel e DraftPanel lado a lado (Argumentos antes em largura compacta); controles Encurtar, Aprofundar, Outra experiência, Copiar, "Salvar nos Artefatos", Pausar e Encerrar. Mostre a pergunta-exemplo respondida e a pergunta com lacuna da massa de dados.
Sem bolhas de chat. Inclua o aviso: "O Persona não responde por você. Processos seletivos podem restringir assistência externa."
```

**Critério de aceite:** argumentos e rascunho separados; cada argumento cita uma evidência; o estado de lacuna existe; zero bolhas.

### T4.5 — Artefatos (biblioteca, criação e detalhe)

```text
Crie a tela Artefatos seguindo a ficha 6.5 e o fluxo 5: (1) biblioteca em ArtifactRow com os 2 artefatos da massa de dados, filtros por tipo, estado e data, e o botão de marca "Novo Artefato"; (2) criação em StepFlow de 6 etapas (tipo e objetivo; contexto; dados complementares; selecionar evidências; gerar; revisar), com os quatro tipos: Resposta STAR, Pitch pessoal (30/60/90 s), Currículo ATS e Portfólio por casos; (3) detalhe com abas Conteúdo (editor por seção, ações fechadas Encurtar, Aprofundar, Adaptar ao objetivo, Gerar alternativa), Evidências (correspondência dos fatos) e Versões (EntryRow com restauração). Currículo e Portfólio mostram pré-visualização e "Exportar PDF". Dados complementares aparecem como "declaração manual". Sem chat e sem carta de apresentação.
```

**Critério de aceite:** quatro tipos; todo trecho cita uma evidência; nenhum campo de chat.

### T4.6 — Painel do Narrative Score

```text
Crie o painel lateral do Narrative Score seguindo a ficha 6.6 e o fluxo 6: abas Resumo (ScoreRing 65, origem "Base declarada", confiança Inicial, período, três DimensionRow e o progresso para o dado observado), Histórico (evolução e eventos) e Como é calculado (Score = 0,6 × Coerência + 0,4 × Consistência; Credibilidade fora do total; limiares: Consistência observada após 21 dias, 6 registros e 3 semanas; Coerência observada após 5 evidências, 2 contextos e 3 competências). Ação de marca: "Registrar no Diário".
```

**Critério de aceite:** 0,6 × 75 + 0,4 × 50 = 65 exato; limiares exatamente como informados.

### T4.7 — Configurações

```text
Crie a tela Configurações seguindo a ficha 6.7: navegação secundária com Perfil, Preferências (lembrete com Switch e horário, comunicações opcionais), Dados e privacidade (Exportar dados em JSON; Excluir conta com reautenticação Microsoft e a confirmação digitando "EXCLUIR") e Conta Microsoft (e-mail conectado, Sair). Botão de marca: "Salvar alterações". Sem planos, sem preços, sem "Conhecer o Pro".
```

**Critério de aceite:** nenhuma menção a plano ou preço; exclusão com confirmação forte.

### T4.8 — Painel do Agente Persona (experimental)

```text
Crie o painel lateral "Agente Persona" seguindo a ficha 6.8 e o fluxo 8 do anexo. Ele abre pelo botão "Agente" (IconButton) no cabeçalho do shell, em qualquer tela, sobre o conteúdo (400–440 px, sombra Float, raio 28), com selo "Experimental" e botão de fechar. Use Composer e MessageBubble com a conversa-exemplo da seção 10 do anexo, incluindo chips de evidência citada e a ação "Revisar sugestões". Mostre os estados: vazio (com 3 chips), respondendo, resposta com citações, sem evidência (lacuna + "Registrar no Diário") e falha ("Não consegui responder agora. Nada foi alterado."). O botão de enviar é Ink: o painel não pode ter botão de marca. O painel não substitui Persona Live nem Artefatos: quando o assunto for entrevista ou material, ofereça "Abrir no Persona Live" ou "Criar Artefato". Mostre o painel aberto sobre o Início e sobre Evidências.
```

**Critério de aceite:** toda afirmação do agente cita uma evidência ou declara a lacuna; selo "Experimental" visível; nenhum botão de marca no painel; os números batem com a massa de dados (faltam 2 registros, 1 semana e 1 evidência).

---

## Etapa 5 — Responsivo, estados e acessibilidade

### T5.1 — Verificação visual completa

```text
Abra cada uma das sete telas do kit em 1024, 1280 e 1440 px e me mostre as 21 capturas. Liste e corrija problemas (corte, sobreposição, rolagem horizontal, tile órfão, botão competindo). Só encerre quando nenhuma captura tiver problema; diga explicitamente "vi todas as capturas".
```

### T5.2 — Larguras menores (E7)

```text
O produto é desktop-first (a partir de 1024 px) e não tem app mobile dedicado. Verifique que em 768 px a lateral vira rail e os painéis de detalhe ocupam a largura toda com seta de voltar; e que em 375 px nada rola na horizontal (a lateral vira drawer). Não crie tab bar inferior. Mostre capturas em 768 e 375 px das sete telas. A correção anterior nunca foi vista por você: confirme olhando.
```

**Critério de aceite:** nenhuma rolagem horizontal em 375 px; sem tab bar.

### T5.3 — Estados vazio, carregando e erro

```text
Para Início, Diário, Evidências, Persona Live e Artefatos, crie os estados vazio (com o próximo passo e o botão de marca correto), carregando (skeleton com a forma dos itens) e erro (tom calmo, sem culpar, com a garantia de que nada foi perdido quando for o caso). Use os estados listados nas fichas da seção 6 do anexo. Disponibilize-os por um controle de estados no kit.
```

### T5.4 — Acessibilidade (WCAG 2.1 AA)

```text
Audite as sete telas: contraste mínimo de 4,5:1 para texto normal e 3:1 para texto grande (informe as razões dos pares que você mudar); anel de foco visível; ordem de tabulação lógica; rótulos acessíveis nos ícones; estados que não dependem só de cor; atualizações do Persona Live anunciadas a leitores de tela; prefers-reduced-motion desligando entrada escalonada, pulso e brilho. Branco sobre #10B981 reprova (2,5367:1): o status de sucesso usa #064E3B sobre #ECFDF5. Entregue a lista de correções aplicadas.
```

**Critério de aceite:** lista de correções com razões calculadas; nenhum par reprovado.

---

## Etapa 6 — Fechamento e sincronização

| ID | Tarefa | Quem | Critério de aceite |
|---|---|---|---|
| T6.1 | Atualizar Readme (Índice, Componentes, Telas), `github.md` (Screen map final, data real) e miniatura | Claude Design | Documentação sem resíduo acadêmico; o Screen map lista as sete telas |
| T6.2 | Apagar `ui_kits/academico` e componentes órfãos | Claude Design | Nenhum arquivo importa os removidos |
| U6.3 | Exportar o kit (PDF e HTML) para `C:\Users\yansi\OneDrive\ref_redisgn_persona\exports\` **antes de 14/12/2026** (encerramento do Claude Design avulso) | [MANUAL] Yan | Arquivos salvos; versão anotada |
| U6.4 | Atualizar `docs/design-dna-persona.md` no repositório com a lista final de telas | [MANUAL] Yan, ou peça ao Claude | Commit na `main` |
| U6.5 | Reativar "org default" **somente** depois da revisão final aprovada | [MANUAL] Yan | Decisão sua |

```text
Prompt T6.1/T6.2 (colar junto):
Finalize o projeto: (1) atualize Readme, github.md e miniatura com o estado final, incluindo o Screen map real; (2) apague ui_kits/academico e qualquer componente que ninguém mais importe, listando o que foi removido; (3) busque em todo o projeto: acadêmico, tutor, ABNT, DOI, TCC, UFPE, orientadora, disciplina, fichamento, Lima, carta de apresentação, Premium, "Perfil e plano", "R$", Básico, Intermediário, Avançado. Mostre o resultado, que deve ser zero. Liste também onde Composer e MessageBubble são importados: só o painel do Agente pode aparecer. Busque também "Declarada" usada como nível de evidência: deve ser zero (o termo só é permitido como origem do score, em "Base declarada").
```

---

## Backlog — telas fora desta correção

Peça depois da Etapa 6, uma por prompt, nesta ordem:

| Prioridade | Tela | Observação |
|---|---|---|
| 1 | **Onboarding** (Contexto · Privacidade · Rotina · Primeiro registro) | Usa `StepFlow`; consentimento obrigatório separado do opcional (LGPD) |
| 2 | **Diagnóstico** (3 etapas, 10 perguntas, escala de 5 rótulos) | Usa `StepFlow`; gera a "Base declarada" |
| 3 | **Entrar** | Botão único "Entrar com Microsoft", sem landing de marketing |
| 4 | Erro de autenticação · Termos · Privacidade | Páginas simples |

**Não pedir:** cadastro, recuperação de senha, paywall, splash/landing.

---

## Definição de pronto (checklist final)

- [ ] Nenhuma menção ao nicho acadêmico, a planos e preços ou a carta de apresentação; chat somente no painel experimental do Agente.
- [ ] Sete telas no kit (Início, Diário, Evidências, Persona Live, Artefatos, painel do Score, Configurações) mais o painel experimental do Agente, sem placeholder.
- [ ] Navegação com cinco destinos mais Configurações.
- [ ] Cada tela tem exatamente um botão de marca e no máximo um bloco focal escuro.
- [ ] O Persona Live mostra Argumentos reais e Rascunho separados, com a evidência citada.
- [ ] Score 65 = 0,6 × 75 + 0,4 × 50; Credibilidade "Ainda não avaliada".
- [ ] 21 capturas (7 telas × 3 larguras) vistas e sem defeito; 768 e 375 px sem rolagem horizontal.
- [ ] Auditoria WCAG AA concluída, com as razões de contraste informadas.
- [ ] "Org default" desativado até a aprovação final.
- [ ] Documentação sincronizada com o repositório `persona_redign`.
