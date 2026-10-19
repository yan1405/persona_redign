# Plano de correção do Claude Design — Persona

> **Versão:** 1.0 · 19/10/2026
> **Projeto:** https://claude.ai/design/p/ff1a7bce-a6f2-4fa9-af99-a6196b748678
> **Decisão vigente (Opção A):** o Persona continua sendo um SaaS de **narrativa profissional**. O kit "Persona Acadêmico" gerado pelo Claude Design foi um erro de escopo e deve ser substituído.
> **Origem dos erros:** auditoria do projeto em 19/10/2026 e o Design DNA em `docs/design-dna-persona.md`.

---

## Como usar este arquivo

1. Execute as etapas **em ordem**. Cada etapa depende da anterior.
2. **Uma tarefa = um prompt.** Cole o bloco "Prompt" no chat do Claude Design e aguarde a conclusão antes de colar o próximo.
3. Antes de avançar, confira o **Critério de aceite** da tarefa com os seus próprios olhos nas capturas. Na auditoria, o Claude Design declarou duas vezes que não tinha visto o resultado de uma correção: não aceite "feito" sem imagem.
4. Tarefas marcadas **[MANUAL]** são suas: o Claude Design não as executa.

---

## Painel de erros e etapa que corrige cada um

| # | Erro encontrado | Onde | Etapa |
|---|---|---|---|
| E0 | Escopo errado: kit de plataforma acadêmica com tutores, ABNT e persona "Yan Lima · UFPE" | Readme, componentes, telas, dados | 1, 2, 4 |
| E1 | Painel "Próximo passo" do card escuro estoura em ~1100 px: texto espremido, CTA cortado, rótulo sobreposto ao título | Início | 3 (T3.3) |
| E2 | Seis tiles quebram em 5 + 1, deixando um tile sozinho | Início | 3 (T3.2) |
| E3 | Conteúdo rola por baixo da barra de busca, que não tem fundo opaco; abas cortadas | Biblioteca | 3 (T3.1) |
| E4 | Dados de exemplo repetidos ("Citada em 2 conversas" em todas as fontes) | Biblioteca | 4 (T4.3) |
| E5 | Botões de mesma ênfase competem: vários botões Ink por tela e CTA de marca ausente nas demais telas | Conversas, diálogo, shell | 3 (T3.4) |
| E6 | Itens de navegação com tela vazia ("Tela fora do escopo deste UI kit") | Leituras, Fichamentos, Projetos | 2 (T2.5), 4 |
| E7 | Correção do layout estreito (< 900 px) entregue sem verificação visual | Conversas | 5 (T5.2) |
| E8 | Sistema publicado como **padrão da organização**: todo projeto novo da equipe herda um kit com escopo errado | Configuração | 0 |

---

## Decisões assumidas neste plano (você pode vetar qualquer uma)

| # | Decisão | Justificativa |
|---|---|---|
| D1 | **Seis destinos:** Início · Registro diário · Evidências · Narrative Score · Artefatos · Perfil e plano | Mapeia a arquitetura do Design DNA (seção 1) |
| D2 | O chat deixa de ser o centro do produto. `Composer` e `MessageBubble` ficam **só** no gerador de artefatos, para refinar o texto | O Persona não é uma plataforma de conversas; o registro diário é um fluxo guiado de uma pergunta por passo |
| D3 | **Sem o mascote Xisto por enquanto**: usar ícones Lucide | Os arquivos-fonte do Xisto não existem fora do código (pendência registrada no projeto) |
| D4 | Rótulos honestos de status: **Declarada** (sem prova) e **Documentada** (com prova vinculada) | Já existem no app atual (dimensão "Declarada") e sustentam a dimensão de credibilidade |
| D5 | Rótulos de nível ("Básico · Intermediário · Avançado") são fictícios | **Confirmar** com os rótulos reais do app antes de implementar |
| D6 | Tudo o que é visual (cores, fontes, raios, sombras) **permanece como está** | O resultado visual foi aprovado por você; o erro é de conteúdo e de layout |

---

## Massa de dados fictícia (usada em todas as telas)

Os valores são coerentes entre si e com o app atual: 75 + 50 + 70 = 195; 195 ÷ 3 = **65**.

| Item | Valor |
|---|---|
| Usuário | Yan · estagiário em IA generativa |
| Narrative Score | **65 / 100** · baseado em dados declarados |
| Dimensões | Consistência **50** · Coerência **75** · Credibilidade **70** |
| Jornada (5 etapas) | Diagnóstico ✓ · Primeiro registro ✓ · **Evidências (em andamento)** · Score documentado (bloqueado até 5 evidências documentadas) · Primeiro artefato (bloqueado) |
| Evidências | 6 no total, 4 documentadas e 2 declaradas |
| Plano | Free · 1 artefato por mês (0 de 1 usado) |

**Evidências fictícias** (competência · status · provas):

1. Automação de relatórios semanais com IA generativa — Análise · Documentada · 2 provas
2. Pitch de 5 minutos para banca de empreendedorismo — Comunicação · Documentada · 1 prova
3. Organização do cronograma de entregas do semestre — Organização · **Declarada** · 0 provas
4. Entrevistas com 8 usuários para validar o problema — Análise · Documentada · 3 provas
5. Oficina de Python para calouros — Liderança · **Declarada** · 0 provas
6. Protótipo de interface para app de carreira — Técnica · Documentada · 1 prova

---

## Regras permanentes (cole uma vez, na tarefa T1.1)

```text
REGRAS PERMANENTES DO PROJETO — valem para todo prompt seguinte.
1. Produto: Persona é um SaaS B2C de NARRATIVA PROFISSIONAL. A pessoa registra o que fez, isso vira evidência, o sistema calcula o Narrative Score (consistência, coerência, credibilidade) e gera artefatos de carreira (resposta STAR, pitch, carta de apresentação, portfólio). NÃO é plataforma acadêmica, de tutores de IA, de TCC nem de ABNT. Se aparecer algo disso, remova.
2. Visual: não altere nenhum token. Mantenha Indigo + Slate, Plus Jakarta Sans + Inter, raios 16/22/28/pill, sombras Soft/Float/Slab. Sem laranja, sem emoji, sem ícones 3D, sem mascote.
3. Hierarquia: no máximo UM botão de marca (gradiente Indigo) por tela e UM bloco focal escuro por tela. Botão Ink: no máximo um por card.
4. Honestidade: nunca mostre uma conquista sem a evidência que a sustenta. Status possíveis: Declarada, Documentada, Para revisar.
5. Texto: português do Brasil, "você", sentence case, títulos terminando em ponto, números tabulares. Estados vazios sempre apontam o próximo passo.
6. Dados: use apenas a massa de dados fictícia que eu enviei. Nunca invente cliente, empresa ou pessoa reais.
7. Verificação: depois de cada alteração, abra o resultado em 1024, 1280 e 1440 px, tire capturas e me mostre. Não diga "feito" sem ter visto.
8. Uma tarefa por vez. Não altere nada fora do escopo do prompt.
Responda apenas "ok, regras registradas" e aguarde.
```

---

## Etapa 0 — Preparação [MANUAL] · ≈ 15 min

**Objetivo:** impedir que o erro se propague e dar ao Claude Design o contexto correto.

| ID | Tarefa | Critério de aceite |
|---|---|---|
| U0.1 | No Claude Design, abra o Design System e clique em **"Remove as org default"** | O aviso "Currently org default" desaparece |
| U0.2 | Anexe, pelo botão **+** do chat, estes prints do app atual **somente como referência de conteúdo e de fluxo**: `inicio-1440.png`, `biblioteca-1440.png`, `onboarding-autenticado.png`, `etapa-4-daily-log.png`, `detalhe-provas-1440.png`, `evidencia-confirmada-1440.jpg` (estão em `Persona_Geral/persona_mvp_v2/docs/`) | Os seis arquivos aparecem em `uploads/` |
| U0.3 | Registre quais anexos são de visual descartado: o app atual é a interface de que você não gostou | Você sabe que o prompt da T1.1 repete essa ressalva |
| U0.4 | Confirme os rótulos reais de nível e as competências do app atual (decisão D5) | Lista confirmada e anotada, ou "aceito os fictícios" |

---

## Etapa 1 — Reorientar o escopo do design system

**Objetivo:** corrigir E0 na raiz (documentação), antes de mexer em componentes e telas. É a etapa mais importante: tudo o que vier depois herda o Readme.

### T1.1 — Registrar as regras permanentes e o produto correto

**Prompt:** cole o bloco "Regras permanentes" da seção anterior.

**Critério de aceite:** o Claude Design responde "ok, regras registradas" e não altera nenhum arquivo.

### T1.2 — Reescrever o Readme

```text
Reescreva o Readme do design system. O produto correto é o Persona (narrativa profissional); o brief anterior, "Persona Acadêmico", estava errado e deve ser removido por completo.

Altere somente estas seções:
1. Visão geral: descreva o Persona como definido nas regras permanentes. A fonte estrutural continua sendo o case iStudio, usada só para estrutura.
2. Fontes: mantenha o repositório https://github.com/yan1405/persona_redign (docs/design-dna-persona.md) e o case iStudio. Acrescente que os seis prints do app atual em uploads/ servem apenas de referência de conteúdo e de fluxo; o visual deles está descartado.
3. Content fundamentals: troque TODOS os exemplos acadêmicos. Substitua por: "Bom dia, Yan. Vamos fazer hoje contar." / "Hoje, de relance." / "Tudo o que sustenta a sua história." Linhas de status por destino, por exemplo "2 evidências sem prova" e "Score 65 · declarado". CTAs: "Registrar agora", "Anexar prova", "Gerar resposta STAR", "Continuar o registro". Erro calmo, por exemplo "Não foi possível anexar o arquivo — confira o formato e tente de novo".
4. Substitua a frase sobre "honestidade acadêmica e fontes citadas" por: "A honestidade é parte da voz: o Persona nunca inventa conquista. Todo artefato cita as evidências do usuário, e o que não tem prova aparece como Declarada."
5. Remova o parágrafo "The current brief extends it to a desktop conversation platform...".
6. Remova "Yan Lima · Pedagogia · UFPE" e qualquer menção a ABNT, DOI, tutores, TCC, disciplinas e orientadora.

Mantenha intactas as seções Visual foundations, Iconography, Index (exceto nomes de pasta que mudarem) e Components (a lista será ajustada na Etapa 2). Mostre o texto final do Readme.
```

**Critério de aceite:**
- [ ] Nenhuma ocorrência de "Acadêmico", "tutor", "ABNT", "DOI", "TCC", "UFPE", "orientadora" ou "Lima" no Readme.
- [ ] Visual foundations idêntico ao anterior.
- [ ] O Claude Design mostrou o texto final.

### T1.3 — Atualizar SKILL.md, github.md e miniatura

```text
Atualize três arquivos para refletir o produto correto (Persona, narrativa profissional):
1. SKILL.md: descrição do sistema, quando usar e regras de voz, sem nenhuma referência ao nicho acadêmico.
2. github.md: registre a fonte (yan1405/persona_redign, branch main), a data real da sincronização e a seção "Screen map" com as telas atuais do kit, que ainda serão refeitas (marque como "em reconstrução").
3. thumbnail.html: troque o conteúdo de exemplo acadêmico pelo Início do Persona (saudação, tiles e card de jornada), usando a massa de dados fictícia.
Não altere tokens. Mostre o diff resumido de cada arquivo.
```

**Critério de aceite:** os três arquivos não citam o nicho acadêmico; `github.md` tem a data do dia, sem inventar commit.

---

## Etapa 2 — Reorientar os componentes

**Objetivo:** corrigir E0 e E6 no nível dos componentes. Os tokens não mudam.

### T2.1 — SourceCard → EvidenceCard

```text
Renomeie o componente SourceCard para EvidenceCard e adapte-o ao Persona. Ele representa uma evidência profissional numerada, com: número, título, competência, nível, status (Declarada / Documentada), quantidade de provas e ícone de link/abrir. Remova qualquer referência a DOI, periódico, ano de publicação ou ABNT. Atualize o cartão @dsCard e a documentação do componente, mostrando três estados: Documentada com provas, Declarada sem prova e Para revisar. Use as evidências 1, 3 e 4 da massa de dados fictícia. Atualize todas as importações.
```

**Critério de aceite:** nenhum arquivo importa `SourceCard`; o cartão mostra os três estados com contraste AA.

### T2.2 — Variantes de status

```text
Nos componentes Badge e Chip, crie as variantes de status: Declarada (neutra, Slate), Documentada (sucesso, texto #064E3B sobre #ECFDF5) e Para revisar (atenção, texto #78350F sobre #FFFBEB). Todas com contraste mínimo de 4,5:1; informe a razão calculada de cada par. Documente no cartão de Badge.
```

**Critério de aceite:** as razões de contraste calculadas aparecem e são ≥ 4,5:1.

### T2.3 — ConversationRow → EntryRow; Composer e MessageBubble restritos

```text
1. Renomeie ConversationRow para EntryRow (linha de registro do dia): data, título, competências e status. Ajuste exemplos e documentação.
2. Mantenha Composer e MessageBubble apenas para refinar um artefato gerado (por exemplo "Deixe mais curto", "Troque o resultado por um número"). Troque os chips de exemplo por esses. Remova "Cite em ABNT", "Quantos entrevistados preciso?" e "Resuma em 3 tópicos" quando acadêmicos. Troque o aviso do rodapé por: "O Persona só usa as evidências que você registrou."
3. Remova o avatar de tutor (Avatar variant="ai") se ficar sem uso; se for mantido, rotule como "Assistente de redação".
```

**Critério de aceite:** nenhum exemplo menciona tutor ou ABNT; o Composer só aparece no contexto de artefato.

### T2.4 — Novos componentes do Persona

```text
Crie estes componentes, seguindo os tokens existentes, cada um com seu @dsCard e dados fictícios da massa de dados:
1. DimensionRow: linha de uma dimensão do Narrative Score (Consistência, Coerência, Credibilidade) com nome, valor 0–100 tabular, ProgressBar e badge Declarada/Documentada.
2. GuidedStep: uma pergunta por tela, com contador "Passo 2 de 4", título em Plus Jakarta Sans, campo de resposta, botão "Voltar" (ghost) e botão de avançar (marca). Sem rolagem.
3. ArtifactCard: cartão de artefato gerado (tipo STAR/pitch/carta, título, data, quantidade de evidências citadas, ações copiar e abrir).
Documente estados: padrão, foco, preenchido e erro.
```

**Critério de aceite:** três novos @dsCards visíveis; foco com anel de 2 px #A78BFA.

### T2.5 — Navegação sem itens vazios

```text
Refaça o NavItem e a navegação lateral para os seis destinos do Persona, nesta ordem: Início, Registro diário, Evidências, Narrative Score, Artefatos, Perfil e plano. Remova Leituras, Fichamentos, Projetos e Conversas. Regra: nenhum item de navegação pode levar a uma tela vazia ou com a frase "fora do escopo"; se a tela ainda não existir, o item não aparece. A ação global da lateral é "Registrar agora" (botão Ink). O card "Continue de onde parou" passa a mostrar o último registro incompleto, com botão outline. Atualize o cartão de Navigation, incluindo o modo recolhido (rail).
```

**Critério de aceite:** seis itens; nenhum placeholder; rail recolhido funcionando.

---

## Etapa 3 — Corrigir shell e layout

**Objetivo:** corrigir E1, E2, E3 e E5. Os componentes compartilhados são corrigidos **antes** das telas para que o erro não se repita em cada uma.

### T3.1 — Cabeçalho fixo e opaco (E3)

```text
Corrija o cabeçalho do shell (busca e ações). O conteúdo está rolando por baixo da busca, sem fundo, e cortando abas e filtros. Faça: (1) cabeçalho fixo com fundo opaco #FAFAFC e uma sombra Soft sutil só quando houver rolagem; (2) a área de conteúdo começa abaixo do cabeçalho, com scroll-padding-top para que âncoras e abas não fiquem cortadas; (3) placeholder da busca: "Buscar evidências, registros, artefatos". Valide rolando a Biblioteca em 1280 px e mostre capturas no topo e no meio da rolagem.
```

**Critério de aceite:** em nenhuma posição de rolagem o texto aparece atrás da busca ou cortado.

### T3.2 — Grade de tiles por largura do container (E2)

```text
Corrija o grid dos DestinationTile. Hoje seis tiles quebram em 5 + 1. Use container queries (a largura que importa é a do painel principal, não a da janela): painel ≥ 1000 px = 6 colunas em uma linha; 640–999 px = 3 colunas × 2 linhas; < 640 px = 2 colunas × 3 linhas. Nunca deixe um tile sozinho numa linha. Mantenha a altura uniforme dos tiles e a linha de status em uma única linha com reticências. Valide em janelas de 1024, 1280 e 1440 px.
```

**Critério de aceite:** nas três larguras a grade é 6, 3×2 ou 2×3 — nunca 5 + 1.

### T3.3 — FocalCard sem estouro (E1)

```text
Corrija o FocalCard (card escuro de jornada). Hoje, com o painel em torno de 1100 px, o bloco "Próximo passo" é espremido numa coluna estreita: o texto quebra palavra a palavra, o botão é cortado e o rótulo se sobrepõe ao título. Faça: (1) duas colunas (stepper à esquerda, próximo passo à direita) só quando o container tiver ≥ 1000 px, com largura mínima de 320 px para o próximo passo; (2) abaixo disso, empilhe o próximo passo sob o stepper, em largura total; (3) o botão de marca nunca é cortado nem comprimido: o texto dele não quebra e o container cresce; (4) remova o rótulo "Orientadora"; (5) texto longo usa quebra normal, sem overflow horizontal. Valide em 1024, 1280 e 1440 px e mostre capturas.
```

**Critério de aceite:** nas três larguras o CTA aparece inteiro, o título não é sobreposto e não há rolagem horizontal.

### T3.4 — Hierarquia de botões (E5)

```text
Faça uma auditoria de todos os botões do kit e aplique a hierarquia: (1) Marca (gradiente Indigo): uma ação principal por tela; (2) Ink sólido: no máximo um por card; a ação global "Registrar agora" da lateral é Ink; (3) Outline: ações secundárias, inclusive o botão do card "Continue de onde parou"; (4) Ghost: ações terciárias. Entregue uma tabela tela × botão × nível antes e depois, e aplique as correções. Em nenhuma tela dois botões de mesma ênfase podem competir na mesma região.
```

**Critério de aceite:** a tabela existe; cada tela tem exatamente um botão de marca.

---

## Etapa 4 — Reconstruir as telas do kit

**Objetivo:** substituir `ui_kits/academico` por `ui_kits/persona`. Faça **uma tela por prompt**; aceite cada uma antes da seguinte.

### T4.1 — Início

```text
Crie ui_kits/persona e a tela Início, usando apenas componentes existentes. Estrutura: saudação "Bom dia, Yan." com a linha "Você tem 2 evidências sem prova. Vamos fazer hoje contar."; seis DestinationTile (Registro diário, Evidências, Narrative Score, Artefatos, Histórico, Plano) cada um com UMA linha de status viva; FocalCard "Sua narrativa" com a jornada de 5 etapas e o próximo passo "Anexe uma prova à evidência 'Organização do cronograma'" com botão de marca "Anexar prova"; e a lista "Registros recentes" com EntryRow. Use a massa de dados fictícia. Não use as palavras tutor, disciplina ou conversa. Valide em 1024, 1280 e 1440 px.
```

**Critério de aceite:** um único botão de marca; tiles em 6 / 3×2; CTA inteiro; sem vocabulário acadêmico.

### T4.2 — Registro diário

```text
Crie a tela Registro diário como fluxo guiado de uma pergunta por passo, com GuidedStep, em 4 passos: (1) Contexto — "O que você fez hoje?"; (2) Ação — "Qual foi o seu papel?"; (3) Resultado — "O que mudou por causa disso?"; (4) Prova — "Você tem algo que comprove? Link, arquivo ou print." com a opção "Registrar sem prova", que marca a evidência como Declarada. Termine com uma tela de confirmação que mostra o efeito no Narrative Score e um botão de marca "Ver evidência". Sem rolagem dentro de cada passo; teclado: Enter avança.
```

**Critério de aceite:** quatro passos mais confirmação; "sem prova" gera status Declarada.

### T4.3 — Evidências (lista e detalhe) — corrige E4

```text
Crie a tela Evidências. Lista em CARTÕES (EvidenceCard), não em tabela. Controles: busca, um seletor de competência e abas Todas / Documentadas / Declaradas / Para revisar — no máximo estes, sem filtros de data nem de nível no topo. Use as seis evidências da massa de dados, cada uma com dados DIFERENTES (competência, nível, provas e status variados; nenhum texto repetido entre cartões). Ao selecionar um cartão, abra o detalhe ao lado: descrição, linha do tempo do registro, lista de provas e botão de marca "Anexar prova" quando for Declarada. Estado vazio: "Nenhuma evidência com esse filtro. Registre o que você fez hoje." com o botão de marca "Registrar agora".
```

**Critério de aceite:** seis cartões sem repetição; três controles; detalhe ao lado.

### T4.4 — Narrative Score

```text
Crie a tela Narrative Score. ScoreRing com 65 em destaque e a legenda "baseado em dados declarados". Abaixo, três DimensionRow (Consistência 50, Coerência 75, Credibilidade 70) com a explicação de uma frase de cada uma. Em seguida, o bloco "O que sobe o seu score" com três ações concretas e o ganho esperado de cada uma, calculado sem arredondamento intermediário. A ação principal é o único botão de marca. O bloco focal escuro mostra: "Score documentado: faltam 1 de 5 evidências com prova".
```

**Critério de aceite:** 65 = (50 + 75 + 70) ÷ 3 exatamente; o ganho por ação é coerente; um botão de marca.

### T4.5 — Artefatos (gerador e biblioteca)

```text
Crie a tela Artefatos com duas áreas: (1) Gerador — seletor de tipo (Resposta STAR, Pitch, Carta de apresentação), seleção das evidências a usar (EvidenceCard selecionáveis) e botão de marca "Gerar resposta STAR"; resultado em quatro blocos S/T/A/R, cada um com chips que apontam a evidência de origem; Composer para refinar. (2) Biblioteca — ArtifactCard em grade. Regra de honestidade: só é possível citar evidências do usuário; evidência Declarada gera o aviso "sem prova vinculada". Mostre o limite do plano Free: "0 de 1 artefato usado este mês".
```

**Critério de aceite:** nenhum artefato cita algo que não esteja nas evidências; o aviso de "sem prova" aparece.

### T4.6 — Perfil e plano

```text
Crie a tela Perfil e plano: dados do perfil, horário do lembrete diário, plano atual (Free, 1 artefato por mês) com o comparativo resumido Free · Pro · Premium e, no rodapé, as ações de privacidade (exportar dados e excluir conta). Um único botão de marca: "Conhecer o Pro". Sem valores inventados: use "R$ 29,90/mês" para Pro e "R$ 59,90/mês" para Premium.
```

**Critério de aceite:** preços exatamente como informados; ações de privacidade visíveis.

---

## Etapa 5 — Responsivo, estados e acessibilidade

**Objetivo:** corrigir E7 e verificar de verdade tudo o que foi feito.

### T5.1 — Verificação visual completa

```text
Abra cada uma das seis telas do kit em 1024, 1280 e 1440 px e me mostre as 18 capturas. Em cada uma, liste problemas que você encontrar (corte, sobreposição, rolagem horizontal, tile órfão, botão competindo) e corrija. Só encerre quando nenhuma captura tiver problema; diga explicitamente "vi todas as capturas".
```

### T5.2 — Layouts estreitos (E7)

```text
Verifique e corrija os layouts abaixo de 900 px: em Evidências, a lista e o detalhe aparecem uma de cada vez, com seta de voltar no detalhe; título, subtítulo e barra de contexto ficam em uma linha, com reticências. Em 768 px, a lateral vira rail. Em 375 px, a lateral vira drawer e surge uma tab bar inferior com os seis destinos (ícone + rótulo). Mostre capturas em 768 e 375 px das seis telas. A correção anterior nunca foi vista por você: confirme olhando.
```

**Critério de aceite:** nenhuma rolagem horizontal em 375 px; tab bar com seis itens.

### T5.3 — Estados vazio, carregando e erro

```text
Para Início, Evidências, Registro diário e Narrative Score, crie os estados: vazio (sempre com o próximo passo e o botão de marca correto), carregando (skeleton com a forma dos cartões) e erro (tom calmo, sem culpar). Disponibilize-os por um controle de estados no kit.
```

### T5.4 — Acessibilidade (WCAG 2.1 AA)

```text
Audite as seis telas: contraste mínimo de 4,5:1 para texto normal e 3:1 para texto grande (informe as razões dos pares que você mudar); anel de foco visível em todo elemento interativo; alvos de toque de pelo menos 44 px no mobile; ordem de tabulação lógica; rótulos acessíveis nos ícones; prefers-reduced-motion desligando entrada escalonada, pulso e brilho. Lembrete: branco sobre #10B981 reprova (2,5367:1); status de sucesso usa texto #064E3B sobre #ECFDF5. Entregue a lista de correções aplicadas.
```

**Critério de aceite:** lista de correções com razões calculadas; nenhum par reprovado.

---

## Etapa 6 — Fechamento e sincronização

| ID | Tarefa | Quem | Critério de aceite |
|---|---|---|---|
| T6.1 | Atualizar o Readme (Índice, Componentes, Telas), o `github.md` (Screen map final, data real) e a miniatura | Claude Design | Documentação sem resíduo acadêmico; Screen map lista as seis telas |
| T6.2 | Apagar `ui_kits/academico` e qualquer componente órfão | Claude Design | Nenhum arquivo importa os removidos |
| U6.3 | Exportar o kit (PDF e HTML) e guardar em `Persona_Geral` | [MANUAL] Yan | Arquivos salvos; versão anotada |
| U6.4 | Atualizar `docs/design-dna-persona.md` no repositório `persona_redign` com a lista final de telas e as decisões D1–D6 | [MANUAL] Yan, ou peça a mim | Commit na `main` |
| U6.5 | Reativar "org default" **somente** depois de a revisão final estar aprovada por você | [MANUAL] Yan | Decisão sua |

```text
Prompt T6.1/T6.2 (colar junto):
Finalize o projeto: (1) atualize Readme, github.md e a miniatura com o estado final, incluindo o Screen map real; (2) apague ui_kits/academico e qualquer componente que ninguém mais importe, listando o que foi removido; (3) faça uma busca em todo o projeto pelas palavras acadêmico, tutor, ABNT, DOI, TCC, UFPE, orientadora, disciplina, fichamento e Lima, e me mostre o resultado, que deve ser zero.
```

---

## Backlog — telas ainda não cobertas (fora desta correção)

Peça depois da Etapa 6, uma por prompt, na ordem sugerida:

| Prioridade | Tela | Observação |
|---|---|---|
| 1 | Onboarding (4 passos, incluindo primeiro registro) | Reaproveita `GuidedStep` |
| 2 | Cadastro, Login e Recuperação de senha (com confirmação) | Fluxo de entrada |
| 3 | **Consentimento LGPD** | Obrigatório pelas restrições do projeto |
| 4 | Configuração de lembrete | Pode virar parte do onboarding |
| 5 | Histórico e Detalhe do registro | Reaproveita `EntryRow` |
| 6 | Paywall | Free · Pro · Premium · Business (sob consulta) |
| 7 | Splash / landing | Só depois de validar o produto |

---

## Definição de pronto (checklist final)

- [ ] Nenhuma menção ao nicho acadêmico em nenhum arquivo do projeto.
- [ ] Seis telas do kit, sem placeholder, sem item de navegação vazio.
- [ ] Cada tela tem exatamente um botão de marca e um bloco focal escuro.
- [ ] 18 capturas (6 telas × 3 larguras) vistas e sem defeito; capturas de 768 e 375 px aprovadas.
- [ ] Auditoria WCAG AA concluída, com as razões de contraste informadas.
- [ ] Dados fictícios coerentes e sem repetição.
- [ ] "Org default" desativado até a aprovação final.
- [ ] Documentação sincronizada com o repositório `persona_redign`.
