# Design DNA — Persona Redesign (referência iStudio)

> **Status:** v1.0 · 18/10/2026 · gerado com a skill `design-dna` (Fase 2 — análise)
> **Referência:** [Student Career Dashboard | UI/UX Design Case Study 2026 (Behance)](https://www.behance.net/gallery/257051775/Student-Career-Dashboard-UIUX-Design-Case-Study-2026)
> **Decisões fixadas:** cores = paleta Persona (Indigo + Slate, D-026) · tipografia = da referência (Plus Jakarta Sans + Inter) · Geist/Geist Mono descontinuadas no redesign.

As imagens da referência **não** são versionadas neste repositório (obra de terceiros, repositório público). Use o link acima.

---

## 1. Por que esta referência

O problema do Persona atual não é a cor — é a arquitetura da informação: o Início é um relatório (score gigante + contadores zerados) e a Biblioteca é uma tabela com seis filtros, padrão de painel administrativo. A referência resolve exatamente isso:

- **"Today, at a glance"** — a primeira tela responde *"o que faço agora?"*.
- **"Six destinations. One shell."** — seis destinos, cada um com uma única linha viva de status.
- **"Verified by the platform, owned by the student"** — mesmo modelo das evidências confirmadas do Persona.
- **"Calm, on purpose"** — cor apenas onde há informação (presença, contagem, CTA).

### Tradução da arquitetura para o Persona

| Referência (iStudio) | Persona |
|---|---|
| Home — tiles de destino | Início — "Bom dia, Yan" + 6 destinos |
| iCAT Journey (card escuro com stepper) | Jornada narrativa: Diagnóstico → Registros → Evidências → Score → Artefato |
| Training / Skill sim | Registro diário (Daily Log) |
| Profile verificado | Biblioteca de evidências |
| Resume builder com score ATS | Gerador de artefatos (STAR, pitch, carta) + Narrative Score |
| Career tools / Profile | Score detalhado · Perfil e plano |

---

## 2. Tokens extraídos da referência (publicados no próprio case)

| Item | Valor na referência |
|---|---|
| Tipografia | Plus Jakarta Sans (títulos 600–800) + Inter (leitura 400–700) |
| Escala | 40 Hero · 28 Page title · 22 Section · 18 Card · 15 Body · 13 Meta |
| Raios | 16 · 22 · 28 · pill |
| Ritmo | 32 px entre seções (mobile) · 40 px (desktop) |
| Botões | Brand (o único CTA) · Solid (um por card) · Outline (secundário) · Ghost (terciário) |
| Profundidade | Soft (cards) · Float (objeto focal) · Slab (tiles elevados) |
| Cores originais | Brand `#FF8A1F→#E0761F` · Plum deep `#1A1130` · Ink `#14161C` · Paper `#F6F5F2` · OK `#1FA868` · Rose `#C2255C` · Info `#2F5BEA` · Plum `#6741D9` |

## 3. Mapeamento de cor para o Persona + contraste (WCAG 2.1)

Contrastes calculados por luminância relativa WCAG, sem arredondamento intermediário (valores exibidos com 4 casas).

| Papel | Referência | Persona | Contraste |
|---|---|---|---|
| Brand · o único CTA | `#FF8A1F→#E0761F` | `#7C3AED→#6D28D9` | branco s/ `#7C3AED` = **5,6986:1** (AA) · s/ `#6D28D9` = 7,1049:1 |
| Ink · texto e botão sólido | `#14161C` | `#1A1726` | s/ branco = **17,581:1** |
| Paper · fundo | `#F6F5F2` | `#F2F1F7` | ink s/ fundo = **15,656:1** |
| Superfície focal escura | `#1A1130` | `#1A1726 → #2E1A6B` | `#C4B5FD` s/ `#1A1726` = **9,5231:1** |
| Texto secundário | — | `#6D5BA6` | s/ branco = 5,6798:1 · s/ `#F2F1F7` = 5,0579:1 |
| Desabilitado | — | `#888291` | s/ branco = 3,7176:1 → só ≥18 px ou desabilitado |
| Sucesso | `#1FA868` | `#10B981` | ⚠ branco s/ `#10B981` = **2,5367:1 (reprova)** → usar `#064E3B` s/ `#ECFDF5` = 9,2265:1 |
| Atenção | — | `#F59E0B` | `#78350F` s/ `#FFFBEB` = 8,7485:1 |
| Erro / prazo | `#C2255C` | `#EF4444` | `#7F1D1D` s/ `#FEF2F2` = 9,1594:1 |
| Info | `#2F5BEA` | `#3B82F6` | `#1E3A8A` s/ `#EFF6FF` = 9,5177:1 |
| Plum (hiring accent) | `#6741D9` | **removido** | colide com o primário do Persona |

---

## 4. Design DNA (JSON)

```json
{
  "meta": {
    "name": "Persona Redesign — DNA iStudio",
    "description": "Shell de dashboard de carreira orientado à ação ('o que faço agora?'), fundo claro neutro, cards brancos arredondados, um único CTA de marca e um card escuro de jornada. Cores da paleta Persona (Indigo + Slate); tipografia da referência.",
    "source_references": ["https://www.behance.net/gallery/257051775/Student-Career-Dashboard-UIUX-Design-Case-Study-2026"],
    "created_at": "2026-10-18"
  },
  "design_system": {
    "color": {
      "palette_type": "monochromatic com acentos semânticos (Indigo como única cor de marca; matizes semânticas só nos tiles de destino e estados)",
      "primary": { "hex": "#7C3AED", "role": "O único CTA por tela (gradiente #7C3AED → #6D28D9), passo ativo da jornada, item ativo da navegação" },
      "secondary": { "hex": "#1A1726", "role": "Ink — texto principal, botão sólido (um por card), balões de mensagem do usuário" },
      "accent": { "hex": "#2E1A6B", "role": "Fim do gradiente do card escuro de jornada (Indigo 900) — apenas na superfície focal" },
      "neutral": {
        "scale": ["#FFFFFF", "#FAFAFC", "#F2F1F7", "#E4E2EE", "#C9C5D8", "#888291", "#6D5BA6", "#4F4866", "#2E2A3D", "#1A1726"],
        "usage": "F2F1F7 = fundo da aplicação; FFFFFF = cards/painéis; E4E2EE = divisores e bordas de outline; 6D5BA6 = texto secundário; 888291 = só desabilitado ou texto >= 18px; 1A1726 = texto principal"
      },
      "semantic": {
        "success": "#10B981 (preenchimento/ponto); texto #064E3B sobre #ECFDF5",
        "warning": "#F59E0B (streak, atenção); texto #78350F sobre #FFFBEB",
        "error": "#EF4444 (prazos, erro); texto #7F1D1D sobre #FEF2F2",
        "info": "#3B82F6 (em andamento); texto #1E3A8A sobre #EFF6FF"
      },
      "surface": {
        "background": "#F2F1F7",
        "card": "#FFFFFF",
        "elevated": "#FFFFFF com sombra Float; superfície focal escura: linear-gradient(135deg, #1A1726 0%, #2E1A6B 100%)"
      },
      "contrast_strategy": "Escuro sobre claro dominante; uma única superfície escura focal por tela (jornada); cor de marca restrita ao CTA e ao passo ativo"
    },
    "typography": {
      "type_scale": {
        "display": { "size": "40px", "weight": "800", "line_height": "1.1", "tracking": "-0.03em" },
        "heading_1": { "size": "28px", "weight": "700", "line_height": "1.2", "tracking": "-0.02em" },
        "heading_2": { "size": "22px", "weight": "700", "line_height": "1.25", "tracking": "-0.015em" },
        "heading_3": { "size": "18px", "weight": "600", "line_height": "1.3", "tracking": "-0.01em" },
        "body": { "size": "15px", "weight": "400", "line_height": "1.55", "tracking": "0" },
        "body_small": { "size": "14px", "weight": "400", "line_height": "1.5", "tracking": "0" },
        "caption": { "size": "13px", "weight": "500", "line_height": "1.4", "tracking": "0" },
        "overline": { "size": "12px", "weight": "600", "line_height": "1.3", "tracking": "0.08em" }
      },
      "font_families": {
        "heading": "Plus Jakarta Sans (600–800)",
        "body": "Inter (400–700)",
        "mono": "Não utilizada — números em Inter com tabular-nums (font-feature-settings: 'tnum')"
      },
      "font_style_notes": "Títulos em grotesca geométrica pesada, tracking negativo, terminados em ponto final ('Hoje, de relance.'); corpo em grotesca neutra; overline em caixa alta numerada ('06 INÍCIO'). Geist/Geist Mono descontinuadas."
    },
    "spacing": {
      "base_unit": "4px",
      "scale": ["4", "8", "12", "16", "20", "24", "32", "40", "56", "72"],
      "content_density": "comfortable",
      "section_rhythm": "32px entre seções no mobile, 40px no desktop; 12–16px entre tiles; 20–24px de padding interno em cards"
    },
    "layout": {
      "grid_system": "App shell de duas colunas: sidebar flutuante + painel principal, ambos como cards brancos sobre o fundo F2F1F7 com 16px de respiro",
      "max_content_width": "1280px (painel principal)",
      "columns": "12 colunas; linha de 6 tiles de destino (2 colunas no mobile com swipe)",
      "gutter": "16px",
      "breakpoints": ["360px", "375px", "768px", "1024px", "1280px", "1440px"],
      "alignment_tendency": "strict grid"
    },
    "shape": {
      "border_radius": { "small": "16px", "medium": "22px", "large": "28px", "pill": "999px" },
      "border_usage": "subtle 1px #E4E2EE apenas em botões outline, inputs e cards em estado neutro",
      "divider_style": "Linha 1px #E4E2EE full-bleed, apenas em listas"
    },
    "elevation": {
      "shadow_style": "soft diffused",
      "levels": {
        "low": "Soft — 0 1px 2px rgb(26 23 38 / 0.04), 0 4px 12px rgb(26 23 38 / 0.05)",
        "medium": "Float — 0 12px 32px -8px rgb(26 23 38 / 0.14)",
        "high": "Slab — 0 2px 0 rgb(26 23 38 / 0.06), 0 20px 40px -12px rgb(46 26 107 / 0.25)"
      },
      "depth_cues": "Sombras suaves, cards brancos sobre fundo tingido, glow do CTA de marca (0 8px 20px -6px rgb(124 58 237 / 0.45))"
    },
    "iconography": {
      "style": "Outline linear na navegação; ilustração própria (Xisto ou set autoral) apenas dentro dos tiles de destino",
      "stroke_weight": "1.75px",
      "size_scale": ["16px", "18px", "20px", "24px"],
      "preferred_set": "Lucide"
    },
    "motion": {
      "easing": "cubic-bezier(0.16, 1, 0.3, 1)",
      "duration_scale": { "micro": "140ms", "normal": "220ms", "macro": "360ms" },
      "entrance_pattern": "fade + translateY(8px) com stagger de 40ms nos tiles",
      "exit_pattern": "fade 140ms",
      "philosophy": "minimal functional"
    },
    "components": {
      "button_style": "Todos pill. Brand: gradiente Indigo com glow, um por tela. Solid: Ink #1A1726, um por card. Outline: borda E4E2EE. Ghost: só texto.",
      "input_style": "Busca em pill branca com ícone à esquerda; campos raio 16px, borda 1px E4E2EE, foco com anel 2px #A78BFA",
      "card_style": "Branco, raio 22–28px, sombra Soft; tiles de destino com fundo pastel semântico, raio 22px, título + uma 'linha viva' de status + seta ↗ + ilustração no canto",
      "navigation_pattern": "Sidebar com logo, ícone + rótulo, item ativo em pill #ECEAFB; card de 'continuar' fixado no rodapé. Mobile: drawer + tab bar inferior.",
      "modal_style": "Painel flutuante ancorado, raio 28px, sombra Float, sem overlay escuro pesado",
      "list_style": "Linhas com avatar/monograma, título 15/600, prévia 13/400, horário à direita, badge de contagem na cor de marca",
      "component_notes": "Stepper de jornada com nós circulares: concluído / ativo (anel + glow) / bloqueado (cadeado). Chips de verificação ('✓ 3 evidências'). Badge 'Aberto agora' com ponto verde."
    }
  },
  "design_style": {
    "aesthetic": {
      "mood": ["calmo", "encorajador", "confiável", "focado"],
      "visual_metaphor": "Painel de bordo pessoal — 'o que faço agora?' respondido no primeiro olhar",
      "era_influence": "SaaS de consumo 2025–2026 (cards suaves, pills, glow sutil)",
      "genre": "consumer SaaS / edtech de carreira",
      "personality_traits": ["direto", "acolhedor", "organizado", "motivador sem ser infantil"],
      "adjectives": ["limpo", "arredondado", "orientado à ação", "leve", "seguro"]
    },
    "visual_language": {
      "complexity": "moderate",
      "ornamentation": "subtle accents",
      "whitespace_usage": "Generoso entre seções; mais justo dentro dos tiles",
      "visual_weight_distribution": "Topo leve (saudação + tiles claros), peso concentrado no card escuro de jornada no centro",
      "focal_strategy": "single hero element (card escuro de jornada com próximo passo e um único CTA)",
      "contrast_level": "Médio no geral, alto apenas na superfície focal",
      "texture_usage": "Nenhuma no produto"
    },
    "composition": {
      "hierarchy_method": "Contraste de escala tipográfica + isolamento de cor (uma superfície escura, um CTA de marca)",
      "balance_type": "asymmetric",
      "flow_direction": "Saudação → destinos → jornada → ação (cima para baixo)",
      "grouping_strategy": "Cards contidos; cada destino com uma única linha viva de status",
      "negative_space_role": "Separar níveis de decisão (onde ir / o que fazer agora)"
    },
    "imagery": {
      "photo_treatment": "Somente avatares circulares",
      "illustration_style": "Substituir os objetos 3D 'clay' da referência pelo mascote Xisto ou ícones autorais",
      "graphic_elements": "Barras de progresso finas, anéis de score, nós de stepper, pontos de presença",
      "pattern_usage": "Nenhum no produto",
      "image_shape": "Círculo (avatares) e retângulo arredondado"
    },
    "interaction_feel": {
      "feedback_style": "Estados claros (concluído/aberto/bloqueado), badges de contagem, toasts discretos",
      "hover_behavior": "Tile sobe 2px e troca sombra Soft → Float; seta ↗ desloca 2px",
      "transition_personality": "smooth glide",
      "loading_style": "Skeletons com formas dos cards",
      "microinteraction_density": "Baixa a média"
    },
    "brand_voice_in_ui": {
      "tone": "Humano e encorajador ('Bom dia, Yan. Vamos fazer hoje contar.')",
      "formality": "Informal-profissional (você)",
      "cta_style": "direct imperative ('Registrar agora', 'Gerar resposta STAR')",
      "empty_state_approach": "Sempre aponta o próximo passo; nunca mostra '0 ativos' isolado",
      "error_tone": "Calmo e explicativo, sem culpar"
    }
  },
  "visual_effects": {
    "overview": { "effect_intensity": "subtle-accent", "performance_tier": "lightweight", "fallback_strategy": "reduce to CSS (prefers-reduced-motion desliga stagger e glow animado)", "primary_technology": "CSS only" },
    "background_effects": { "type": "mesh-gradient", "description": "Brilho radial suave no card escuro de jornada", "technology": "CSS radial-gradient", "params": { "color_palette": ["#1A1726", "#2E1A6B", "#7C3AED"], "speed": "estático", "density": "baixa", "opacity": "0.35 no brilho", "blend_mode": "normal" } },
    "particle_systems": { "enabled": false, "type": "none", "description": "Ausente", "technology": "none", "params": { "count": "0", "shape": "none", "size_range": "none", "movement_pattern": "none", "color_behavior": "none", "interaction": "none", "spawn_area": "none" } },
    "3d_elements": { "enabled": false, "type": "none", "description": "Ícones 3D da referência são imagens estáticas, não renderização 3D", "technology": "none", "params": { "renderer": "none", "lighting": "none", "camera": "none", "materials": "none", "geometry": "none", "post_processing": [], "interaction_model": "none" } },
    "shader_effects": { "enabled": false, "type": "none", "description": "Ausente", "technology": "none", "params": { "uniforms": "none", "vertex_manipulation": "none", "fragment_output": "none", "noise_type": "none", "distortion": "none" } },
    "scroll_effects": {
      "parallax": { "enabled": false, "layers": "0", "depth_range": "none", "speed_curve": "none" },
      "scroll_triggered_animations": { "enabled": false, "trigger_points": "none", "animation_type": "none", "scrub_behavior": "none" },
      "scroll_morphing": { "enabled": false, "description": "Ausente" }
    },
    "text_effects": { "type": "none", "description": "Ausente", "technology": "none", "params": { "split_strategy": "none", "animation_per_unit": "none", "stagger": "none", "effect_style": "none" } },
    "cursor_effects": { "enabled": false, "type": "none", "description": "Ausente", "params": { "shape": "none", "size": "none", "blend_mode": "none", "trail": "none", "interaction_zone": "none" } },
    "image_effects": { "type": "none", "description": "Ausente", "technology": "none", "params": { "filter_pipeline": "none", "hover_transform": "none", "reveal_animation": "none", "distortion_type": "none" } },
    "glassmorphism_neumorphism": { "enabled": false, "style": "none", "params": { "blur_radius": "0", "transparency": "0", "border_treatment": "none", "shadow_type": "none", "light_source_angle": "none" } },
    "canvas_drawings": { "enabled": false, "type": "none", "description": "Ausente", "technology": "none", "params": { "draw_method": "none", "animation_loop": "none", "color_scheme": "none", "responsiveness": "none", "interaction": "none" } },
    "svg_animations": { "enabled": true, "type": "decorative-loop", "description": "Anel do passo ativo da jornada com pulso suave; anel do Narrative Score desenhado na entrada", "params": { "animation_method": "CSS keyframes + stroke-dashoffset", "path_morphing": "none", "stroke_animation": "draw na entrada (360ms)", "filter_effects": "drop-shadow glow Indigo" } },
    "composite_notes": "Efeitos limitados a: glow do CTA de marca, brilho radial no card de jornada, pulso do passo ativo. A grade de pontos e os fundos laranja/roxo do case são material de apresentação — não levar para o produto."
  }
}
```

---

## 5. Ressalvas críticas

1. **Risco de monotonia cromática.** A referência funciona por contraste de temperatura (laranja quente × papel neutro × roxo frio). No Persona, primário e neutros têm o mesmo matiz violeta → tende a ficar "tudo lavanda". Mitigação: tiles de destino com tons semânticos e Indigo restrito ao CTA e ao passo ativo. Se ainda ficar chapado, a correção é um neutro quente — não uma segunda cor de marca.
2. **Ícones 3D genéricos.** Os objetos "clay" da referência são o elemento mais "template". No Persona, substituir pelo Xisto ou set autoral.
3. **Verde com texto branco reprova AA** (2,5367:1). Badges de sucesso usam `#064E3B` sobre `#ECFDF5`.
4. **Inter é a fonte mais genérica do mercado.** Mantida por fidelidade à referência (decisão de 18/10/2026); reavaliar se o resultado parecer genérico.
