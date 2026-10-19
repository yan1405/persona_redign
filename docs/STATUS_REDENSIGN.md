# Persona redesign — estado canônico

> **Data:** 19/10/2026  
> **Status geral:** documentação corrigida; reconstrução no Claude Design ainda não comprovada  
> **Uso:** leia este arquivo antes de abrir, avaliar ou continuar o redesign

## 1. O que está decidido

- O Persona é uma plataforma pessoal de narrativa profissional, não um produto acadêmico e não um CRM.
- O ciclo funcional continua: Diário → sugestões da IA → confirmação humana → Evidências → Narrative Score → Persona Live e Artefatos.
- O Agente Persona é uma direção aprovada para o protótipo; ainda não deve ser apresentado como funcionalidade implementada no app.
- O redesign usa a estrutura visual da referência do Behance como inspiração, sem copiar seu conteúdo.
- **Plus Jakarta Sans + Inter são escolhas intencionais deste redesign.** Elas podem diferir da tipografia do projeto inicial e não devem ser revertidas para Geist por esse motivo.
- A paleta continua Persona: Indigo + Slate.
- O Xisto está fora deste redesign. Use ícones Lucide.
- Não usar tutores, ABNT, DOI, TCC, UFPE, conteúdo acadêmico, funil, pipeline, leads, tabelas de CRM, planos ou preços.

## 2. Fontes da verdade

1. `persona-fluxos-e-features.md`: produto, fluxos, estados e separação entre comprovado e protótipo.
2. `design-dna-persona.md`: linguagem visual, tokens e componentes.
3. `plano-correcao-claude-design.md`: ordem de reconstrução e critérios de aceite.
4. `guia-execucao-design-system.md`: gates e forma de execução.

Em caso de conflito, produto vence visual. Um protótipo visual nunca comprova implementação.

## 3. Estado dos artefatos

| Artefato | Estado | Pode ser usado? |
|---|---|---|
| `docs/` | Corrigido e canônico | Sim |
| GitHub `yan1405/persona_redign` | Deve espelhar estes documentos | Sim, depois de conferir o commit mais recente |
| `Persona Design System/` | Exportação acadêmica obsoleta | Não |
| `Persona Design System.pdf` | Exportação acadêmica obsoleta | Não |
| Projeto ao vivo no Claude Design | Reconstrução ainda não verificada | Não como prova de conclusão |
| `Persona_Geral/persona_mvp_v2` | Base funcional do produto | Sim para comportamento; não para copiar a aparência antiga |

## 4. Gates atuais

| Gate | Estado | Evidência necessária para concluir |
|---|---|---|
| G0 — documentação sem contradições | Concluído localmente | JSON válido; decisões de fonte e Xisto explícitas |
| G1 — fundação do Claude Design | Pendente de verificação | Readme, assets e componentes sem nenhum resíduo acadêmico |
| G2 — componentes | Pendente | Componentes acessíveis e alinhados aos fluxos reais |
| G3 — telas | Pendente | Sete superfícies e Agente reconstruídos com os estados previstos |
| G4 — QA | Pendente | Busca de resíduos igual a zero, navegação e contraste verificados |
| G5 — nova exportação | Pendente | HTML/PDF gerados novamente e comparados com os documentos canônicos |

## 5. Próxima ação correta

Executar o plano v2.3 no Claude Design a partir da Etapa 0. Não remendar a exportação acadêmica atual como se ela já fosse a entrega final. Ao final de cada tarefa, registrar evidência visual e só então avançar para o gate seguinte.

## 6. Critério de conclusão

O trabalho só pode ser chamado de concluído quando:

- a busca global não encontrar resíduos acadêmicos, CRM, Xisto ou componentes obsoletos;
- o Agente estiver rotulado como direção de protótipo, sem alegação falsa de implementação;
- as fontes Plus Jakarta Sans + Inter estiverem aplicadas de forma consistente;
- os componentes interativos tiverem foco, teclado e semântica acessível;
- a nova exportação substituir explicitamente os artefatos obsoletos;
- os documentos locais e o GitHub tiverem o mesmo conteúdo.

