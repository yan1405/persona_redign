# Plano de correção do Claude Design — Persona

> **Versão:** 2.2 · 19/10/2026 (substitui a v2.1, a v2.0 e a v1.0; a v2.2 adota a direção **plataforma com agente de IA, não CRM**: agente central, cards, painéis flutuantes e seções)
> **Projeto:** https://claude.ai/design/p/ff1a7bce-a6f2-4fa9-af99-a6196b748678
> **Decisão vigente (Opção A):** o Persona continua sendo um SaaS de **narrativa profissional**. O kit "Persona Acadêmico" gerado pelo Claude Design foi um erro de escopo e deve ser substituído.
> **Fontes da verdade, em ordem de precedência:**
> 1. [`persona-fluxos-e-features.md`](persona-fluxos-e-features.md) — produto, fluxos, features validadas e massa de dados;
> 2. [`design-dna-persona.md`](design-dna-persona.md) — visual;
> 3. este plano — ordem de execução.
>
> **Execução com checkpoints:** as Etapas 2 e 3 têm um guia próprio, [`guia-execucao-design-system.md`](guia-execucao-design-system.md), que o Claude Design segue parando a cada checkpoint e esperando o seu "ok".

---

## O que mudou da v2.1 para a v2.2 (decisão de Yan, 19/10/2026)

"Não estamos montando um CRM, e sim uma plataforma com agente de IA." A estrutura herdada da referência (listas densas, tabelas, painéis laterais, abas, chat escondido) foi descartada.

| Ponto | v2.1 | v2.2 |
|---|---|---|
| Papel do agente | Painel experimental, aberto por botão | **Eixo da plataforma**: campo "Buscar ou perguntar" no Início e painel acoplado em todas as telas |
| Listas | Linhas compactas e tabelas | **Grades de cards** (2–3 colunas) |
| Detalhes | Painel lateral com abas | **Painel flutuante** ancorado com **seções** e índice de âncoras; Artefatos em workspace de página inteira |
| Abas | `PillTabs` em Evidências, detalhes e Score | **Sem abas**: visões viram chips; detalhes viram seções |
| Filtros | Seis controles no topo | Recolhidos atrás de um botão "Filtros" |
| Honestidade | Chat só no painel experimental | Agente central, mas **sem chat dentro** do Live e dos Artefatos; o agente prepara e abre, a pessoa confirma |

**Divergência consciente:** o agente (LD-026) não está implementado e os contratos das Fases 7 e 8 não preveem chat aberto. Isto é um protótipo de direção; o app real não muda sem atualizar esses contratos.

---

## O que mudou da v1.0 para a v2.0

A v1.0 foi escrita a partir do Design DNA, sem conferir os documentos aprovados do app. Na conferência de 19/10/2026, oito pontos divergiam do produto real:

| Ponto | v1.0 (errado) | v2.0 (produto aprovado) |
|---|---|---|
| Navegação | 6 destinos com "Narrative Score" e "Perfil e plano" | 5 destinos (Início, Diário, Evidências, **Persona Live**, Artefatos) + Configurações no rodapé; o Score abre em painel a partir do Início |
| Persona Live | Ausente | Diferencial do produto: tela e componentes próprios |
| Diário | Fluxo guiado de 4 passos | Editor livre "O que aconteceu hoje?"; a IA sugere e a pessoa confirma. Os passos guiados pertencem ao onboarding |
| Chat | `Composer`/`MessageBubble` no gerador de artefatos | Sem chat dentro do Live e dos Artefatos (ações fechadas). A conversa pertence ao **Agente Persona**, eixo da plataforma (v2.2) |
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
| E9 | Estrutura de CRM herdada da referência: listas densas, tabelas, painéis laterais, abas | Todas as telas | 2, 3, 4 |
| E10 | Readme com "(sem alterações)" no lugar de seções e resíduos de chat, 6 tiles, Xisto e Persona Acadêmico | Readme | 1 (T1.2b) |

---

## Decisões deste plano (você pode vetar qualquer uma)

| # | Decisão | Justificativa |
|---|---|---|
| D1 | **Navegação:** Início · Diário · Evidências · Persona Live · Artefatos, mais Configurações no rodapé, mais o Agente Persona presente em todas as telas. O Narrative Score é uma faixa de KPIs no Início e abre em painel flutuante | `INFORMATION_ARCHITECTURE.md` §2 (aprovado) |
| D2 | **Agente no centro, sem CRM.** O Agente Persona é o eixo: campo "Buscar ou perguntar" no Início e painel acoplado em todas as telas. `Composer` e `MessageBubble` pertencem a ele; o Diário tem `CaptureEditor` próprio. Dentro do Live e dos Artefatos a IA age por ações nomeadas, sem bolhas de chat. Listas viram cards, detalhes viram painéis flutuantes com seções e não há abas | Decisão de Yan, 19/10/2026 ("não estamos montando um CRM e sim uma plataforma com agente de AI"). Divergência consciente das Fases 7 e 8 (ver acima) |
| D3 | **Sem o mascote Xisto**: só ícones Lucide | Decisão de Yan, 19/10/2026: o Xisto fica fora do redesign |
| D4 | **Níveis de evidência:** Registrada (sem link) e Documentada (≥ 1 link). Validada e Certificada aparecem só como explicação "indisponível". "Para revisar" = sugestão não confirmada | Fase 5 e `PRODUCT_BRIEF.md` §5 |
| D5 | **Competências em texto livre**, sem taxonomia e sem níveis de habilidade | A Fase 5 deixa a taxonomia global fora do escopo. Resolve a antiga pendência U0.4 |
| D6 | **Tokens visuais permanecem** (cores, fontes, raios, sombras) | O resultado visual foi aprovado; o erro é de conteúdo e de layout |
| D7 | **Fora do desenho:** CRM (funil, pipeline, leads, contatos), planos e preços, paywall, carta de apresentação, cadastro/senha, upload de arquivo, áudio no Live, app mobile dedicado | `PRODUCT_BRIEF.md` §10 e `INFORMATION_ARCHITECTURE.md` §6 |

**Massa de dados:** use **exclusivamente** a seção 10 de `persona-fluxos-e-features.md`.

---

## Regras permanentes (cole uma vez, na tarefa T1.1)

> Se você já colou a versão da v2.1, **cole esta de novo**: ela substitui a anterior. Ao final o Claude Design deve responder "ok, regras registradas (v2.2)".

```text
REGRAS PERMANENTES DO PROJETO — valem para todo prompt seguinte.
0. Fonte da verdade de produto: o anexo persona-fluxos-e-features.md (também em github.com/yan1405/persona_redign/docs). Em qualquer dúvida de fluxo, feature, texto ou dado, ele vence.
1. Produto: Persona é uma PLATAFORMA COM AGENTE DE IA para narrativa profissional. NÃO é CRM. Ciclo: Diário (texto livre) → sugestões da IA → a pessoa confirma → Evidência (Registrada ou Documentada) → Narrative Score explicável → ativação no Persona Live (argumentos reais + rascunho para entrevista) e nos Artefatos (Resposta STAR, Pitch pessoal, Currículo ATS, Portfólio). NÃO é plataforma acadêmica, de tutores nem de ABNT, e NÃO é CRM (sem funil, pipeline, leads ou tabelas de gestão). Se aparecer algo disso, remova.
2. Navegação: Início, Diário, Evidências, Persona Live, Artefatos; Configurações no rodapé; o Agente Persona fica presente em todas as telas. O Narrative Score fica no Início e abre em painel flutuante. Não crie outros destinos.
3. Agente central: o Agente Persona é o eixo da plataforma. No Início, o campo "Buscar ou perguntar" e a conversa ocupam a área central; nas demais telas, um painel acoplado à direita (380–420 px, recolhível) abre pelo botão "Agente" ou por Ctrl/⌘+K. Ele só usa evidências registradas, cita a origem de cada afirmação, nunca salva nada sem confirmação, nunca autoriza evidências no Live e nunca escreve a resposta final de entrevista fora do Live. Dentro dos workspaces do Persona Live e dos Artefatos NÃO há bolhas de mensagem: a IA age por ações nomeadas (Encurtar, Aprofundar, Outra experiência, Adaptar ao objetivo, Gerar alternativa).
4. Visual: não altere nenhum token. Indigo + Slate, Plus Jakarta Sans + Inter, raios 16/22/28/pill, sombras Soft/Float/Slab. Sem laranja, sem emoji, sem ícones 3D, sem mascote.
5. Hierarquia: no máximo UM botão de marca (gradiente Indigo) por tela e UM bloco focal escuro por tela. Botão Ink: no máximo um por card.
6. Honestidade: nunca mostre conquista sem a evidência que a sustenta. Níveis: Registrada e Documentada; "Para revisar" para sugestões. Credibilidade = "Ainda não avaliada". Sem fato suficiente, mostre uma lacuna, nunca um texto genérico. Todo texto gerado aponta a evidência de origem.
7. Fora do escopo: planos, preços, paywall, carta de apresentação, cadastro/senha (a entrada é só "Entrar com Microsoft"), upload de arquivo, áudio.
8. Texto: português do Brasil, "você", sentence case, títulos terminando em ponto, números tabulares. Estados vazios sempre apontam o próximo passo.
9. Dados: use apenas a massa de dados da seção 10 do anexo. Nunca invente cliente, empresa ou pessoa reais.
10. Verificação: depois de cada alteração, abra o resultado em 1024, 1280 e 1440 px, tire capturas e me mostre. Não diga "feito" sem ter visto.
11. Uma tarefa por vez. Não altere nada fora do escopo do prompt.
12. Estrutura: listas são GRADES DE CARDS (2–3 colunas), nunca tabelas nem linhas densas. Todo detalhe abre em PAINEL FLUTUANTE ancorado (560–640 px, raio 28, sombra Float, um por vez); detalhes longos usam SEÇÕES empilhadas com índice de âncoras. NÃO use abas. Visões viram chips; filtros ficam recolhidos atrás de um botão "Filtros". Artefatos usam workspace de página inteira.
Estas regras SUBSTITUEM qualquer versão anterior. Responda apenas "ok, regras registradas (v2.2)" e aguarde.
```

---

## Etapa 0 — Preparação [MANUAL] · ≈ 10 min

| ID | Tarefa | Critério de aceite |
|---|---|---|
| U0.1 | No Claude Design, abra o Design System e clique em **"Remove as org default"**. Antes disso, no seletor de design system do projeto, fixe o próprio "Persona Design System" (não "Padrão da organização") | O aviso "Currently org default" desaparece e o projeto continua apontando para o Persona |
| U0.2 | Anexe pelo botão **+** do chat o arquivo `persona-fluxos-e-features.md` (pasta `C:\Users\yansi\OneDrive\ref_redisgn_persona\docs\` ou repositório `docs/`). **Não anexe prints do app atual** | O arquivo aparece em `uploads/` |
| U0.3 | Confirme ou vete as decisões D1–D7, (a D3, Xisto fora, já foi decidida). A D2 (agente no centro, sem CRM) já foi decidida por você em 19/10/2026 | Decisões anotadas |

---

## Etapa 1 — Reorientar o escopo do design system

### T1.1 — Registrar as regras permanentes

**Prompt:** cole o bloco "Regras permanentes".
**Critério de aceite:** o Claude Design responde "ok, regras registradas (v2.2)" e não altera arquivos.

### T1.2 — Reescrever o Readme

```text
Leia uploads/persona-fluxos-e-features.md por inteiro. Depois reescreva o Readme do design system. O produto correto é o Persona (narrativa profissional); o brief "Persona Acadêmico" estava errado e deve ser removido por completo.

Altere somente estas seções:
1. Visão geral: descreva o Persona com as seções 1 e 2 do anexo (o que é, promessas, ciclo Diário → Evidência → Score → Persona Live/Artefatos). O case iStudio continua só como referência de estrutura.
2. Fontes: o repositório https://github.com/yan1405/persona_redign (docs/persona-fluxos-e-features.md = produto; docs/design-dna-persona.md = visual) e o case iStudio. Remova qualquer menção a prints do app atual.
3. Content fundamentals: troque TODOS os exemplos acadêmicos. Use: "Bom dia, Yan." / "Hoje, de relance." / "Tudo o que sustenta a sua história." Linhas de status: "4 confirmadas · 2 para revisar", "Score 65 · base declarada", "1 sessão encerrada". CTAs: "Salvar registro", "Revisar sugestões", "Confirmar evidência", "Adicionar link de prova", "Iniciar sessão", "Novo Artefato". Lacuna: "Ainda não há evidência para sustentar esta resposta. Registre a situação no Diário." Erro calmo: "Não foi possível gerar sugestões agora — seu registro está salvo e você pode estruturar manualmente."
4. Troque a frase sobre "honestidade acadêmica" por: "A honestidade é parte da voz: a IA sugere e você confirma. O Persona nunca inventa conquista, todo texto gerado cita a evidência de origem e o que não tem prova aparece como Registrada."
5. Remova o parágrafo "The current brief extends it to a desktop conversation platform..." e reescreva a seção "Intentional additions": remova SourceCard e o Switch para ABNT; mantenha MessageBubble e Avatar do agente, descritos como "núcleo do Agente Persona, eixo da plataforma (protótipo do agente colaborativo LD-026, ainda não implementado)". Troque "not an open AI chat" por "not a CRM: it is a platform built around an AI agent that only uses the person's registered evidence".
6. Remova "Yan Lima · Pedagogia · UFPE" e qualquer menção a ABNT, DOI, tutores, TCC, disciplinas e orientadora.

Mantenha intactas as seções Visual foundations e Iconography (os textos completos, nunca a expressão "sem alterações"). Mostre o texto final do Readme.
```

**Critério de aceite:**
- [ ] Nenhuma ocorrência de "Acadêmico", "tutor", "ABNT", "DOI", "TCC", "UFPE", "orientadora" ou "Lima" no Readme; o Agente descrito como eixo da plataforma, não como chat aberto.
- [ ] Nenhuma ocorrência de "(sem alterações)" ou de qualquer placeholder no Readme.
- [ ] O Readme cita o Persona Live e os quatro tipos de Artefato.
- [ ] Visual foundations e Iconography com o texto completo.

### T1.2b — Restaurar seções e corrigir resíduos do Readme

Na entrega da T1.2, o Claude Design deixou "(sem alterações)" no lugar de Visual foundations, Iconography e Index e apontou resíduos de chat, 6 tiles, Xisto e Persona Acadêmico. Esta tarefa fecha esse ponto.

```text
Corrija o Readme do design system. Não altere tokens nem componentes.
1. Visual foundations: escreva a seção por completo (cores, tipografia, raios, sombras, espaçamento, movimento, contraste e regras de hierarquia: um botão de marca e um bloco focal escuro por tela, Ink no máximo um por card), com base em styles.css e em docs/design-dna-persona.md. Nunca use "sem alterações" ou qualquer placeholder. Troque "Six destination tiles" por "Four destination tiles", "user's chat bubbles" por "the person's bubbles in the Agente Persona" e acrescente: cards em grade de 2–3 colunas, painéis flutuantes de 560–640 px, seções com índice de âncoras e nenhuma aba.
2. Iconography: escreva a seção por completo (Lucide, traço 1.75, tamanhos, uso em tiles e navegação). Remova o mascote Xisto: ele está fora do redesign (decisão de Yan).
3. Index: liste o que existe hoje (styles.css, fonts/, assets/, guidelines/, components/, SKILL.md, github.md, thumbnail.html) e marque ui_kits/academico/ como "legado — será removido na T6.2", SourceCard e a pasta chat/ como "serão renomeados/reorganizados nas T2.1 e T2.3". Sem "(sem alterações)".
4. Em "Components", descreva o estado atual e o previsto: EvidenceCard, EntryCard, ArtifactCard, AgentPrompt, AgentPanel, FloatingPanel, SectionIndex.
Mostre o texto final do Readme.
```

**Critério de aceite:**
- [ ] Zero ocorrências de "sem alterações", "Six destination tiles", "Xisto" e "user's chat bubbles".
- [ ] As três seções têm texto completo.

### T1.3 — Atualizar SKILL.md, github.md e miniatura

```text
Atualize três arquivos para o produto correto:
1. SKILL.md: descrição, quando usar e regras de voz, sem nicho acadêmico e sem CRM; o Agente Persona como eixo da plataforma (conversa só nele, não dentro do Live e dos Artefatos); estrutura de cards, painéis flutuantes e seções, sem abas.
2. github.md: fonte yan1405/persona_redign, branch main, arquivos docs/persona-fluxos-e-features.md e docs/design-dna-persona.md, data real desta sincronização e seção "Screen map" com as telas da seção 6 do anexo (Início, Diário, Evidências, Persona Live, Artefatos, painel do Score, Configurações e o Agente Persona) marcadas "em reconstrução". Não invente hash de commit.
3. thumbnail.html: troque o exemplo acadêmico pelo Início do Persona (saudação, campo "Buscar ou perguntar", faixa de KPIs com 65, 4 tiles e o FocalCard), usando a massa de dados do anexo.
Não altere tokens. Mostre o diff resumido de cada arquivo.
```

**Critério de aceite:** os três arquivos não citam o nicho acadêmico; o `github.md` traz a data do dia.

---

## Etapa 2 — Reorientar os componentes

### T2.1 — SourceCard → EvidenceCard

```text
Renomeie SourceCard para EvidenceCard (seção 7 do anexo). É um CARD, não uma linha de tabela. Campos: título, competências (chips), nível (Registrada / Documentada), quantidade de links de prova, origem (Diário ou manual) e data de atualização. Três variantes:
(a) card de grade — para a grade de Evidências (2–3 colunas, raio 22, sombra Soft);
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

### T2.3 — EntryCard, CaptureEditor e o núcleo do Agente (AgentPrompt, AgentPanel, Composer, MessageBubble)

```text
1. Renomeie ConversationRow para EntryCard: card com data + título + metadado + status. Variantes: registro do Diário, sessão do Persona Live e versão de Artefato.
2. Crie o componente novo CaptureEditor: o editor do Diário com o rótulo "O que aconteceu hoje?", contador (40 a 2.000 caracteres), data e contexto opcionais e botão de marca "Salvar registro". Sem chips de prompt e sem aparência de chat.
3. Mantenha Composer e MessageBubble como núcleo do Agente Persona (anexo, ficha 6.8). Composer: chips contextuais ("O que falta para o score observado?", "Organize minhas evidências", "Preparar uma entrevista"); botão de enviar Ink (não de marca); rodapé "O agente só usa as evidências que você registrou. Confira sempre a origem.". MessageBubble: pessoa em Ink; agente em branco, com chips de evidência citada e uma linha de ações ("Revisar sugestões", "Abrir no Persona Live", "Criar Artefato"). Avatar do agente com o rótulo "Agente Persona" (sem selo "Experimental"). Remova todos os chips e textos acadêmicos.
4. Crie AgentPrompt: campo grande "Buscar ou perguntar" em pill branca com ícone, até 4 chips de sugestão e botão de enviar Ink. Ele é o campo do Início e também o campo do cabeçalho (versão compacta).
5. Crie AgentPanel: painel acoplado à direita, 380–420 px, raio 28, sombra Float, recolhível; cabeçalho com "Agente Persona", a linha "Você está em: <tela>" e o botão de recolher; contém MessageBubble e Composer.
6. Mantenha Switch para as Configurações.
Atualize os @dsCards e a lista de componentes do Readme.
```

**Critério de aceite:** busca por `ConversationRow` = zero; `Composer` e `MessageBubble` usados **só** por `AgentPanel` e pela conversa central do Início; o `CaptureEditor` não parece um chat; nenhum selo "Experimental".

### T2.4 — Novos componentes do Persona

```text
Crie estes componentes com os tokens existentes, cada um com @dsCard e dados da massa de dados do anexo:
1. DimensionRow: dimensão do Narrative Score com nome, valor 0–100 tabular, ProgressBar, origem (Declarada/Observada) e progresso rumo ao dado observado ("4 de 6 registros · 2 de 3 semanas"). Estado especial "Ainda não avaliada" sem número (Credibilidade).
2. StepFlow: "Etapa N de M", título em Plus Jakarta Sans, conteúdo, "Voltar" (ghost) e "Continuar" (marca). Usado no onboarding, no diagnóstico e no Novo Artefato.
3. ArgumentPanel: painel "Argumentos reais" do Persona Live — itens com o fato, o campo de origem (ação, resultado, competência…), a evidência citada (link) e o alerta "não afirme…". Estado lacuna: fatos que faltam e a ação "Registrar no Diário".
4. DraftPanel: painel "Rascunho sugerido" — texto, duração-alvo ("30–45 s · comportamental"), versão e ações Encurtar, Aprofundar, Outra experiência e Copiar.
5. ArtifactCard: card com tipo (STAR, Pitch, Currículo, Portfólio), objetivo, estado (Rascunho/Revisado), atualização e principais evidências.
6. TraceLine: linha de rastreabilidade "registro → sugestão → evidência → prova → uso", com os nós clicáveis. É o elemento-assinatura do produto.
7. FloatingPanel: painel de detalhe ancorado, 560–640 px, raio 28, sombra Float, fundo apenas esmaecido, cabeçalho com título e fechar, corpo rolável, Esc fecha, um por vez, foco preso enquanto aberto.
8. SectionIndex: índice de âncoras (rótulos como Resumo · Provas · Uso) que rola até a seção e marca a seção atual. Substitui qualquer aba; não use PillTabs como navegação.
Documente os estados padrão, foco, preenchido, erro e desabilitado.
```

**Critério de aceite:** oito novos @dsCards; foco com anel de 2 px `#A78BFA`; SectionIndex sem aparência de abas.

### T2.5 — Navegação sem itens vazios

```text
Refaça o NavItem e a lateral com: Início, Diário, Evidências, Persona Live, Artefatos e, isolado no rodapé, Configurações. Remova Leituras, Fichamentos, Projetos e Conversas. Nenhum item pode levar a uma tela vazia ou "fora do escopo". A ação global da lateral é "Registrar agora" (botão Ink, abre o Diário). O card "Continue de onde parou" mostra o último registro com sugestões pendentes, com botão outline. Inclua o modo recolhido (rail). No cabeçalho do shell, coloque o AgentPrompt compacto ("Buscar ou perguntar") e o IconButton "Agente" que abre o AgentPanel.
```

**Critério de aceite:** cinco itens mais Configurações; nenhum placeholder; rail funcionando; cabeçalho com o campo "Buscar ou perguntar" e o botão "Agente".

---

## Etapa 3 — Corrigir shell e layout

### T3.1 — Cabeçalho fixo e opaco (E3)

```text
Corrija o cabeçalho do shell. Faça: (1) cabeçalho fixo com fundo opaco #FAFAFC e sombra Soft só quando houver rolagem; (2) conteúdo começa abaixo do cabeçalho, com scroll-padding-top para que chips e filtros não fiquem cortados; (3) o campo do cabeçalho é o "Buscar ou perguntar" (AgentPrompt compacto), com o IconButton "Agente" ao lado. Valide rolando Evidências em 1280 px e mostre capturas no topo e no meio da rolagem.
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
Audite todos os botões e aplique: (1) Marca: uma ação principal por tela, conforme a seção 6 do anexo; (2) Ink: no máximo um por card; o "Registrar agora" da lateral e o enviar do Agente são Ink; (3) Outline: secundárias; (4) Ghost: terciárias. Entregue uma tabela tela × botão × nível antes e depois e aplique as correções.
```

**Critério de aceite:** a tabela existe; cada tela tem exatamente um botão de marca.

### T3.5 — Casca com painel do Agente e painéis flutuantes

```text
No shell, implemente o comportamento do AgentPanel e do FloatingPanel (sem criar telas novas): (1) o AgentPanel acoplado empurra o conteúdo em vez de cobri-lo, recolhe para um botão e lembra se estava aberto; (2) abaixo de 1024 px ele vira uma folha sobre a tela; (3) o FloatingPanel abre ancorado sobre o conteúdo, com fundo esmaecido, um por vez, Esc fecha; (4) com os dois abertos, o FloatingPanel fica à esquerda do AgentPanel sem sobreposição. Valide em 1024, 1280 e 1440 px com o painel do agente aberto e fechado e mostre as capturas.
```

**Critério de aceite:** em 1024 px com o agente aberto não há rolagem horizontal nem corte; o conteúdo nunca fica atrás do AgentPanel.

---

## Etapa 4 — Reconstruir as telas do kit

**Objetivo:** substituir `ui_kits/academico` por `ui_kits/persona`. **Uma tela por prompt**; aceite cada uma antes da seguinte. Cada prompt remete à ficha correspondente da seção 6 do anexo. Estrutura obrigatória: cards em grade, painéis flutuantes, seções, sem abas, agente presente.

### T4.1 — Início (hub do agente)

```text
Crie ui_kits/persona e a tela Início seguindo a ficha 6.1 do anexo: saudação; AgentPrompt grande "Buscar ou perguntar" com 4 chips; FocalCard (único bloco escuro) com o briefing do agente — stepper "Do score declarado ao observado", próxima ação "Revise as 2 sugestões do Diário" e o botão de marca "Revisar sugestões"; faixa de KPIs com ScoreRing 65 · "Base declarada" e três DimensionRow (Coerência 75, Consistência 50, Credibilidade "Ainda não avaliada"); quatro DestinationTile com as linhas vivas da ficha; uma linha de 3 cards recentes (EntryCard e EvidenceCard); competências recorrentes e lacunas. Ao enviar uma pergunta, a conversa abre na área central (use a conversa-exemplo da seção 10) e os demais blocos recuam. Clicar no score abre o painel do Narrative Score (T4.6). Sem tabelas, sem abas. Valide em 1024, 1280 e 1440 px.
```

**Critério de aceite:** um botão de marca; um bloco escuro; o campo do agente é o elemento mais visível; 0,6 × 75 + 0,4 × 50 = 65 citado no método; Credibilidade sem número.

### T4.2 — Diário

```text
Crie a tela Diário seguindo a ficha 6.2: CaptureEditor em primeiro plano ("O que aconteceu hoje?"), histórico em GRADE de EntryCard com o campo "Buscar ou perguntar" e o período atrás de "Filtros", e o detalhe em FloatingPanel com as seções Registro (texto original, data, contexto, editar, excluir) e Sugestões (2 sugestões em EvidenceCard variante "sugestão", com "Confirmar evidência" e "Descartar"; botão "Estruturar manualmente"), com SectionIndex. Mostre a TraceLine. NÃO é um fluxo de perguntas guiadas, NÃO é chat e NÃO tem abas. Inclua os estados: gerando sugestões, nenhuma sugestão útil, falha da IA com modo manual e exclusão bloqueada.
```

**Critério de aceite:** editor livre; o texto original nunca é substituído; os quatro estados existem; histórico em cards.

### T4.3 — Evidências (grade e detalhe) — corrige E4

```text
Crie a tela Evidências seguindo a ficha 6.3: campo "Buscar ou perguntar", chips de visão Todas e Para revisar, um botão "Filtros" (competência, período, nível) e uma GRADE de 2–3 colunas de EvidenceCard — as 4 evidências e as 2 sugestões da massa de dados, sem nenhum texto repetido entre cards. O detalhe abre em FloatingPanel com as seções Resumo, Provas (links, nível calculado, "Adicionar link de prova" como botão de marca para a evidência 4) e Uso (onde foi usada no Live e nos Artefatos), com SectionIndex e TraceLine. Validada e Certificada aparecem só como explicação "indisponível nesta fase". Estado vazio: "Nenhuma evidência ainda. Comece pelo Diário."
```

**Critério de aceite:** seis cards sem repetição; nível Registrada/Documentada coerente com os links; detalhe em painel flutuante, sem abas, sem tabela.

### T4.4 — Persona Live

```text
Crie a tela Persona Live seguindo a ficha 6.4 e o fluxo 4 do anexo, em três vistas:
(1) Sessões: cards de sessão (EntryCard) com a sessão encerrada e o botão de marca "Nova sessão".
(2) Preparação: vaga/objetivo e empresa (obrigatórios), descrição opcional, evidências recomendadas em EvidenceCard selecionável, com o motivo da recomendação, seleção de 1 a 8 e o botão de marca "Iniciar sessão".
(3) Workspace: cabeçalho com empresa, vaga e estado; campo de pergunta; histórico de perguntas; ArgumentPanel e DraftPanel lado a lado (Argumentos antes quando a área útil for menor que 1280 px ou com o AgentPanel aberto); controles Encurtar, Aprofundar, Outra experiência, Copiar, "Salvar nos Artefatos", Pausar e Encerrar. Mostre a pergunta-exemplo respondida e a pergunta com lacuna da massa de dados.
Sem bolhas de chat no workspace. O AgentPanel começa recolhido. Inclua o aviso: "O Persona não responde por você. Processos seletivos podem restringir assistência externa."
```

**Critério de aceite:** argumentos e rascunho separados; cada argumento cita uma evidência; o estado de lacuna existe; zero bolhas no workspace.

### T4.5 — Artefatos (biblioteca, criação e detalhe)

```text
Crie a tela Artefatos seguindo a ficha 6.5 e o fluxo 5: (1) biblioteca em GRADE de ArtifactCard com os 2 artefatos da massa de dados, filtros por tipo, estado e data atrás de "Filtros", e o botão de marca "Novo Artefato"; (2) criação em StepFlow de 6 etapas (tipo e objetivo; contexto; dados complementares; selecionar evidências; gerar; revisar), com os quatro tipos: Resposta STAR, Pitch pessoal (30/60/90 s), Currículo ATS e Portfólio por casos; (3) detalhe em workspace de página inteira com as seções Conteúdo (editor por seção, ações fechadas Encurtar, Aprofundar, Adaptar ao objetivo, Gerar alternativa), Evidências (correspondência dos fatos) e Versões (EntryCard com restauração) e SectionIndex. Currículo e Portfólio mostram pré-visualização e "Exportar PDF". Dados complementares aparecem como "declaração manual". Sem chat dentro do editor, sem abas e sem carta de apresentação.
```

**Critério de aceite:** quatro tipos; todo trecho cita uma evidência; nenhum campo de chat no editor.

### T4.6 — Painel do Narrative Score

```text
Crie o painel do Narrative Score como FloatingPanel, seguindo a ficha 6.6 e o fluxo 6: seções Resumo (ScoreRing 65, origem "Base declarada", confiança Inicial, período, três DimensionRow e o progresso para o dado observado), Histórico (evolução e eventos) e Como é calculado (Score = 0,6 × Coerência + 0,4 × Consistência; Credibilidade fora do total; limiares: Consistência observada após 21 dias, 6 registros e 3 semanas; Coerência observada após 5 evidências, 2 contextos e 3 competências), com SectionIndex. Ação de marca: "Registrar no Diário".
```

**Critério de aceite:** 0,6 × 75 + 0,4 × 50 = 65 exato; limiares exatamente como informados; sem abas.

### T4.7 — Configurações

```text
Crie a tela Configurações seguindo a ficha 6.7: navegação secundária com Perfil, Preferências (lembrete com Switch e horário, comunicações opcionais), Dados e privacidade (Exportar dados em JSON; Excluir conta com reautenticação Microsoft e a confirmação digitando "EXCLUIR") e Conta Microsoft (e-mail conectado, Sair). Botão de marca: "Salvar alterações". Sem planos, sem preços, sem "Conhecer o Pro".
```

**Critério de aceite:** nenhuma menção a plano ou preço; exclusão com confirmação forte.

### T4.8 — Agente Persona (estados e integração)

```text
Complete o Agente Persona seguindo a ficha 6.8 e o fluxo 8 do anexo. Mostre: (a) a conversa central no Início e (b) o AgentPanel acoplado sobre Evidências e sobre Persona Live (recolhido e aberto). Use Composer e MessageBubble com a conversa-exemplo da seção 10 do anexo, incluindo chips de evidência citada e a ação "Revisar sugestões". Estados: vazio (com chips contextuais), respondendo, resposta com citações, sem evidência (lacuna + "Registrar no Diário"), falha ("Não consegui responder agora. Nada foi alterado."), recolhido e agente indisponível (o campo vira busca simples). O botão de enviar é Ink: o painel não pode ter botão de marca. O agente não substitui Persona Live nem Artefatos: quando o assunto for entrevista ou material, ofereça "Abrir no Persona Live" ou "Criar Artefato", sem gerar a resposta final.
```

**Critério de aceite:** toda afirmação do agente cita uma evidência ou declara a lacuna; nenhum botão de marca no painel; os números batem com a massa de dados (faltam 2 registros, 1 semana e 1 evidência); o agente nunca autoriza evidência no Live.

---

## Etapa 5 — Responsivo, estados e acessibilidade

### T5.1 — Verificação visual completa

```text
Abra cada uma das sete telas do kit (e o Agente Persona) em 1024, 1280 e 1440 px e me mostre as capturas. Confira também com o AgentPanel aberto. Liste e corrija problemas (corte, sobreposição, rolagem horizontal, tile órfão, botão competindo). Só encerre quando nenhuma captura tiver problema; diga explicitamente "vi todas as capturas".
```

### T5.2 — Larguras menores (E7)

```text
O produto é desktop-first (a partir de 1024 px) e não tem app mobile dedicado. Verifique que em 768 px a lateral vira rail, os painéis flutuantes ocupam a largura toda com seta de voltar e o AgentPanel vira uma folha; e que em 375 px nada rola na horizontal (a lateral vira drawer). Não crie tab bar inferior. Mostre capturas em 768 e 375 px das sete telas. A correção anterior nunca foi vista por você: confirme olhando.
```

**Critério de aceite:** nenhuma rolagem horizontal em 375 px; sem tab bar.

### T5.3 — Estados vazio, carregando e erro

```text
Para Início, Diário, Evidências, Persona Live e Artefatos, crie os estados vazio (com o próximo passo e o botão de marca correto), carregando (skeleton com a forma dos itens) e erro (tom calmo, sem culpar, com a garantia de que nada foi perdido quando for o caso). Use os estados listados nas fichas da seção 6 do anexo, incluindo agente indisponível. Disponibilize-os por um controle de estados no kit.
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
Finalize o projeto: (1) atualize Readme, github.md e miniatura com o estado final, incluindo o Screen map real; (2) apague ui_kits/academico e qualquer componente que ninguém mais importe, listando o que foi removido; (3) busque em todo o projeto: acadêmico, tutor, ABNT, DOI, TCC, UFPE, orientadora, disciplina, fichamento, Lima, carta de apresentação, Premium, "Perfil e plano", "R$", Básico, Intermediário, Avançado. Mostre o resultado, que deve ser zero. Busque também: CRM, pipeline, funil, lead, "Experimental", PillTabs usado como aba e componentes de tabela (table, thead): devem ser zero. Liste também onde Composer e MessageBubble são importados: só AgentPanel e a conversa central do Início podem aparecer. Busque também "Declarada" usada como nível de evidência: deve ser zero (o termo só é permitido como origem do score, em "Base declarada").
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

- [ ] Nenhuma menção ao nicho acadêmico, a CRM, a planos e preços ou a carta de apresentação; conversa somente no Agente Persona.
- [ ] Sete telas no kit (Início, Diário, Evidências, Persona Live, Artefatos, painel do Score, Configurações) mais o Agente Persona (conversa central e painel acoplado), sem placeholder.
- [ ] Navegação com cinco destinos mais Configurações; campo "Buscar ou perguntar" e botão "Agente" no cabeçalho.
- [ ] Listas em grade de cards, detalhes em painéis flutuantes com seções, zero abas e zero tabelas.
- [ ] Cada tela tem exatamente um botão de marca e no máximo um bloco focal escuro.
- [ ] O Persona Live mostra Argumentos reais e Rascunho separados, com a evidência citada.
- [ ] Score 65 = 0,6 × 75 + 0,4 × 50; Credibilidade "Ainda não avaliada".
- [ ] 21 capturas (7 telas × 3 larguras) vistas e sem defeito; 768 e 375 px sem rolagem horizontal.
- [ ] Auditoria WCAG AA concluída, com as razões de contraste informadas.
- [ ] "Org default" desativado até a aprovação final.
- [ ] Documentação sincronizada com o repositório `persona_redign`.
