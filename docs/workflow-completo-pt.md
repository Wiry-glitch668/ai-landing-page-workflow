# Workflow Completo: Criação de Landing Pages com IA

> Documentado em 2026-03-31 | Sessão de pesquisa e planejamento
> Stack: Figma Pro + Claude Code CLI (Figma MCP) + React/Tailwind/Vite + VPS Hostinger

---

## Visão Geral

Pipeline completo para criar landing pages de alta conversão usando IA como acelerador
e humano como estrategista/diretor criativo. Baseado em pesquisa de melhores práticas
de CRO, Core Web Vitals, LGPD e workflows de agências top em 2026.

**Tempo estimado da primeira versão no ar:** ~2.5h (inclui decisões prévias)
**Tempo para cada variação nova:** ~20 min (decisões já tomadas)
**Economia vs processo 100% manual:** 40-60%

### Pipeline Visual

```
FASE 0 ─── FASE 0.5 ─── FASE 1 ─── FASE 2 ─── FASE 3 ─── FASE 4 ─── FASE 5 ─── FASE 6 ─── FASE 7
Brief      Decisões     Copy       Wireframe   Design     Código     Pre-launch  Deploy     Otimizar
(5 min)    (10 min)     (15 min)   (10 min)    (30 min)   (20 min)   (15 min)    (5 min)    (contínuo)
HUMANO     HUMANO       IA+HUMANO  HUMANO      HUMANO+IA  IA+HUMANO  HUMANO      IA+HUMANO  IA+HUMANO
```

> **A Fase 0.5 é a mais importante.** Cada decisão não tomada aqui = retrabalho caro depois.
> Definir responsivo, cores, fontes, CTA, formulário, tracking ANTES de tocar no Figma.

---

## Stack Definida (o que já temos)

| Necessidade | Ferramenta | Status |
|-------------|-----------|--------|
| Design + Wireframes | Figma Pro (100+ refs) | Já temos |
| Figma → Código | Claude Code CLI + Figma MCP | Já temos |
| Código | React + TypeScript + TailwindCSS + Vite | Já temos |
| Deploy | VPS Hostinger (claude-server) + nginx | Já temos |
| Copy | Claude (Pro/Code) | Já temos |
| Imagens de campanha | Midjourney / DALL-E / Firefly | Avaliar qual assinar |
| Analytics | GA4 + GTM | Setup por cliente |
| Heatmaps | Microsoft Clarity (grátis) | Implementar |
| Automação | Make.com | Avaliar necessidade |

**Ferramentas extras NÃO necessárias:** Framer, Webflow, Unbounce, Elementor, Leadpages.
O pipeline Figma → Claude Code → VPS é superior para nosso caso (controle total, PageSpeed 95+, custo zero de hosting).

---

## FASE 0: INTAKE — Brief Único (5 min)

Preencher este brief que alimenta todas as fases seguintes:

```markdown
# BRIEF DO PROJETO

## Data: ____
## Responsável: ____

## 1. Cliente
- Nome do negócio:
- Segmento:
- Cidade/Região:
- URL atual (se existe):
- Redes sociais:
- Logo (link/arquivo):
- Cores da marca (hex):
- Fontes da marca (se definidas):

## 2. Oferta
- Produto/serviço principal:
- Preço (ou faixa):
- Diferencial #1:
- Diferencial #2:
- Diferencial #3:
- Garantia/reversão de risco:
- Prova social disponível (reviews, casos, números):

## 3. Público-alvo
- Quem compra (idade, perfil, gênero):
- Maior dor/problema:
- O que já tentaram antes:
- Objeção principal (por que NÃO compraria):
- Momento de compra (urgente? planejado?):
- Nível de consciência (não sabe que tem problema / sabe mas não busca / busca ativamente / comparando opções):

## 4. Tráfego
- Fonte principal (Google Ads, Meta Ads, orgânico):
- Palavras-chave ou interesses:
- Temperatura (frio/morno/quente):
- CTA desejado (WhatsApp, formulário, compra direta):
- Budget mensal de ads:

## 5. Referências
- Sites/páginas que gosta (URLs):
- Tom de voz (formal/casual/técnico/emocional):
- O que NÃO quer (restrições):

## 6. Técnico
- Domínio (já tem? qual?):
- Google Ads ID (se tem):
- Meta Pixel ID (se tem):
- GTM Container ID (se tem):
- WhatsApp número:
- Email para receber leads:
```

---

## FASE 0.5: MATRIZ DE MICRO-DECISÕES — Humano (10 min)

> **POR QUE ISSO EXISTE:** Cada decisão não tomada aqui vira retrabalho depois.
> Preencher ANTES de criar copy, design ou código. Uma vez definido, não muda mais
> (a menos que o teste de otimização prove que deve mudar).

### A. Estratégia de Dispositivos & Responsivo

```markdown
# DECISÕES DE RESPONSIVO

## Approach
- [ ] Mobile-first (padrão — 83% do tráfego pago é mobile)
- [ ] Desktop-first (só se tráfego for majoritariamente desktop, ex: B2B)

## Breakpoints (Tailwind padrão)
- Mobile: 0 - 639px (base)
- Tablet: 640px - 1023px (sm/md)
- Desktop: 1024px - 1279px (lg)
- Wide: 1280px+ (xl)

## Design no Figma — criar 3 frames:
- [ ] Mobile (375px largura) ← ESSE É O PRINCIPAL
- [ ] Tablet (768px largura)
- [ ] Desktop (1440px largura)

## O que MUDA por dispositivo:

| Elemento | Mobile | Tablet | Desktop |
|----------|--------|--------|---------|
| Hero layout | Imagem acima, texto abaixo | Lado a lado | Lado a lado (mais espaço) |
| Colunas de benefícios | 1 coluna (stack) | 2 colunas | 3-4 colunas |
| Testimonials | Carousel (swipe) | 2 cards | 3 cards grid |
| FAQ | Accordion (fechado) | Accordion | Accordion ou aberto |
| Formulário | Full width, campos empilhados | 2 colunas | 2 colunas com sidebar |
| Imagens do hero | Crop quadrado/vertical | Crop 4:3 | Crop 16:9 |
| Vídeo | Thumbnail + play (NÃO autoplay) | Thumbnail + play | Autoplay muted OK |
| Menu/nav | Nenhum (LP) ou hamburger | Anchor links | Anchor links + CTA |
| CTA flutuante (WhatsApp) | Sim, bottom-right, 56px | Sim, menor | Sim ou inline |
| Font size body | 16px | 16px | 18px |
| Font size H1 | 28-32px | 36-40px | 44-52px |
| Espaçamento seções | 48-64px | 64-80px | 80-100px |
| Imagem de fundo | Desabilitar ou simplificar | Usar | Usar com parallax (se quiser) |

## Elementos que SOMEM no mobile:
- [ ] Ícones decorativos grandes
- [ ] Imagens secundárias que não agregam
- [ ] Texto longo em seções de suporte (truncar com "ver mais")
- [ ] Animações pesadas

## Elementos que APARECEM só no mobile:
- [ ] Click-to-call no número de telefone
- [ ] Sticky CTA bar no topo ou bottom
- [ ] Swipe indicators nos carousels
```

### B. Estratégia de Conteúdo & Estrutura

```markdown
# DECISÕES DE CONTEÚDO

## Tipo de página
- [ ] Lead capture (formulário curto)
- [ ] Vendas longo (scroll longo com ancoragem de valor)
- [ ] VSL (vídeo de vendas + CTA)
- [ ] Agendamento (calendário/WhatsApp)
- [ ] Evento/Webinar (countdown + inscrição)

## Ordem das seções (já considerar mobile = scroll vertical)
1. _______________
2. _______________
3. _______________
4. _______________
5. _______________
6. _______________
7. _______________
8. _______________

## A ordem muda no mobile?
- [ ] Não, mesma ordem
- [ ] Sim: _____________ (ex: mover prova social antes de benefícios)

## Número de CTAs na página: ___
## Posições dos CTAs:
- [ ] Hero (obrigatório)
- [ ] Após prova social
- [ ] Após benefícios
- [ ] Antes do FAQ
- [ ] Final da página (obrigatório)
- [ ] Sticky/flutuante

## Prova social — formato:
- [ ] Texto com nome + foto
- [ ] Vídeo depoimento
- [ ] Screenshots de reviews (Google, Instagram)
- [ ] Logos de clientes/parceiros
- [ ] Números/estatísticas (ex: "500+ clientes atendidos")
- [ ] Before/after (fotos)
- [ ] Selos/certificações
```

### C. Estratégia Visual & Design Tokens

```markdown
# DECISÕES VISUAIS

## Paleta de cores
- Primária (CTA, destaques): #______
- Secundária (headers, links): #______
- Accent (badges, alertas): #______
- Background principal: #______
- Background alternativo (seções pares): #______
- Texto principal: #______
- Texto secundário (subtítulos): #______

## O botão de CTA tem contraste suficiente com TODOS os backgrounds?
- [ ] Verificado (usar webaim.org/resources/contrastchecker)

## Tipografia
- Font family heading: _____________ (ex: Inter, Poppins, Montserrat)
- Font family body: _____________ (ex: Inter, system-ui)
- Carregar do Google Fonts? [ ] Sim [ ] Não, usar system font stack (mais rápido)
- Se Google Fonts: font-display: swap (obrigatório)
- Máximo de weights carregados: 2-3 (ex: 400, 600, 700)

## Type scale

| Elemento | Mobile | Desktop | Weight |
|----------|--------|---------|--------|
| H1 | 28-32px | 44-52px | 700-800 |
| H2 (títulos de seção) | 24-28px | 32-40px | 600-700 |
| H3 (subtítulos) | 20-22px | 24-28px | 600 |
| Body | 16px | 18px | 400 |
| Small/caption | 14px | 14px | 400 |
| CTA button text | 16-18px | 18px | 600-700 |

## Max-width de texto (para legibilidade)
- Parágrafos: max-w-prose (65ch / ~600px)
- Página: max-w-7xl (1280px)

## Estilo dos cantos
- [ ] Rounded (rounded-lg / 8-12px) — padrão moderno
- [ ] Muito rounded (rounded-2xl / 16px+) — friendly/casual
- [ ] Sharp (rounded-none) — corporativo/sério

## Sombras
- [ ] Nenhuma (flat)
- [ ] Sutil (shadow-sm)
- [ ] Presente (shadow-md) em cards
- [ ] Elevada (shadow-lg) em CTAs e modais

## Seções alternadas?
- [ ] Sim, alternar bg-white / bg-gray-50 (ou cor secundária suave)
- [ ] Não, fundo único

## Dark section para destaque?
- [ ] Sim, usar em: _____________ (ex: CTA final, pricing)
- [ ] Não
```

### D. Estratégia de Imagens & Media

```markdown
# DECISÕES DE IMAGENS

## Hero image
- Tipo: [ ] Foto real [ ] Foto IA [ ] Ilustração [ ] Vídeo background [ ] Nenhuma (só texto)
- Crop por dispositivo:
  - Mobile: [ ] 1:1 [ ] 3:4 [ ] 4:3
  - Desktop: [ ] 16:9 [ ] 3:2 [ ] hero fullwidth
- Posição: [ ] Background com overlay [ ] Lado a lado com texto [ ] Acima do texto

## Formato de imagens
- [ ] WebP (padrão, ~30% menor que JPG)
- [ ] AVIF (melhor compressão, mas suporte limitado)
- [ ] WebP com fallback JPG (safest)

## Otimização
- Qualidade alvo: 80-85% (bom equilíbrio tamanho/visual)
- Lazy loading: tudo exceto hero + logo
- Tamanhos responsive (srcset):
  - Mobile: 640px width
  - Tablet: 1024px width
  - Desktop: 1440px width
- Placeholder enquanto carrega: [ ] Blur-up [ ] Cor sólida [ ] Skeleton [ ] Nenhum

## Ícones
- [ ] Lucide React (leve, já incluso no shadcn)
- [ ] Heroicons
- [ ] SVG inline custom
- NÃO usar icon fonts (Font Awesome = pesado)

## Vídeo (se aplicável)
- Hospedado em: [ ] YouTube embed [ ] Vimeo [ ] Self-hosted (NÃO recomendado)
- Mobile: thumbnail estática + botão play (NÃO autoplay = economia de dados)
- Desktop: [ ] Autoplay muted [ ] Thumbnail + play
- Posição: [ ] Hero [ ] Seção dedicada
- Aspect ratio: [ ] 16:9 [ ] 4:3

## Budget de performance para imagens
- Peso total de TODAS as imagens: máx 500KB (ideal 300KB)
- Hero image: máx 150KB
- Demais imagens: máx 50-80KB cada
```

### E. Estratégia de Formulário & Conversão

```markdown
# DECISÕES DE FORMULÁRIO / CTA

## CTA principal
- [ ] WhatsApp (melhor para serviços locais)
- [ ] Formulário inline (melhor para lead gen B2B)
- [ ] Formulário em modal/popup
- [ ] Click-to-call
- [ ] Link externo (checkout, agendamento)
- [ ] Combinação: ____________

## Se formulário — campos:
| Campo | Obrigatório? | Tipo input | Placeholder |
|-------|-------------|-----------|-------------|
| Nome | [ ] Sim [ ] Não | text | "Seu nome" |
| Email | [ ] Sim [ ] Não | email | "seu@email.com" |
| WhatsApp | [ ] Sim [ ] Não | tel | "(00) 00000-0000" |
| Cidade | [ ] Sim [ ] Não | text | "Sua cidade" |
| Mensagem | [ ] Sim [ ] Não | textarea | "Como posso ajudar?" |
| _________ | [ ] Sim [ ] Não | _______ | ____________ |

> REGRA: Cada campo a mais reduz conversão em ~7-10%.
> Para primeiro contato: Nome + WhatsApp é suficiente.

## Máscara de input?
- [ ] Telefone: (00) 00000-0000
- [ ] CPF (se necessário): 000.000.000-00

## Validação
- Real-time (ao sair do campo) — NÃO ao submeter
- Mensagens em português: "Por favor, preencha seu nome"
- Highlight vermelho no campo com erro

## Após submit — o que acontece?
- [ ] Redirect para /obrigado (MELHOR para tracking de conversão)
- [ ] Mensagem inline "Recebemos seu contato!"
- [ ] Redirect para WhatsApp
- [ ] Redirect para página de agendamento

## Página /obrigado — conteúdo:
- [ ] Confirmação do recebimento
- [ ] Próximo passo claro ("Vamos entrar em contato em até X horas")
- [ ] CTA secundário (seguir no Instagram, baixar material)
- [ ] NÃO ter menu ou links que tirem da jornada
- [ ] Pixel de conversão dispara NESTA página

## Anti-spam
- [ ] Honeypot field (campo hidden que bots preenchem)
- [ ] Rate limiting (máx 3 submissões por IP/hora)
- [ ] NÃO usar reCAPTCHA visual (mata conversão mobile)
```

### F. Estratégia de Performance & Loading

```markdown
# DECISÕES DE PERFORMANCE

## Budget de performance
- Peso total da página: máx ____KB (target: <1MB, ideal <700KB)
- JS bundle: máx 150KB gzipped
- CSS: máx 50KB gzipped
- Fonts: máx 2 arquivos, máx 100KB total
- Third-party scripts: máx 3 (GTM + Clarity + 1)

## Ordem de carregamento (Critical Rendering Path)
1. HTML + CSS crítico (inline no <head>)
2. Hero image (preload)
3. Fontes (preload, font-display: swap)
4. JS do app
5. GTM (defer)
6. Imagens abaixo do fold (lazy)
7. Clarity/analytics (após load)

## Fontes — estratégia de loading
- [ ] System font stack (MAIS RÁPIDO, sem download)
  font-family: system-ui, -apple-system, sans-serif;
- [ ] Google Fonts com preconnect + swap
- [ ] Self-hosted (download da font, servir da VPS)

## Animações
- [ ] Nenhuma (MAIS RÁPIDO, melhor CLS)
- [ ] Só fade-in suave nas seções (Intersection Observer, CSS-only)
- [ ] Scroll-triggered animations (usar só se marca pede)
- REGRA: Se usar animação, preferir CSS transforms + opacity (GPU-accelerated)
- REGRA: Respeitar prefers-reduced-motion (acessibilidade)

## Scripts third-party
| Script | Necessário? | Quando carrega | Depende de cookie consent? |
|--------|------------|----------------|---------------------------|
| GTM | Sim | defer, <head> | Não (GTM em si é funcional) |
| GA4 | Via GTM | Após consent | Sim |
| Meta Pixel | Via GTM | Após consent | Sim |
| Google Ads tag | Via GTM | Após consent | Sim |
| Microsoft Clarity | Via GTM | Após consent | Sim |
| Chat widget | Talvez | lazy, após 5s | Depende |
| Hotjar | Se precisar | Via GTM | Sim |

## Caching (nginx)
- HTML: no-cache (sempre fresco)
- CSS/JS: 1 ano (com hash no filename)
- Imagens: 1 ano (com hash)
- Fonts: 1 ano
```

### G. Estratégia de SEO & URLs

```markdown
# DECISÕES DE SEO

## URL da landing page
- Estrutura: [ ] /oferta [ ] /lp/nome-campanha [ ] /servico-cidade [ ] custom: _______
- REGRA: Se for LP de tráfego pago → noindex (não poluir o SEO do site principal)
- REGRA: Se for página de serviço orgânico → index, follow

## Indexação
- [ ] noindex, nofollow (LP paga, não quer no Google)
- [ ] index, follow (página de serviço, quer ranquear)

## Subdomínio ou subpasta?
- [ ] dominio.com.br/lp/campanha (melhor para SEO se indexar)
- [ ] lp.dominio.com.br/campanha (isola do site principal)
- [ ] dominio.com.br/servico-cidade (para SEO local)

## Schema markup
- [ ] LocalBusiness (serviço local com endereço)
- [ ] Product (produto com preço)
- [ ] Service (serviço sem endereço fixo)
- [ ] FAQPage (se tem seção FAQ — RECOMENDADO, ganha rich snippets)
- [ ] VideoObject (se tem vídeo)

## Canonical URL: _______________________

## Open Graph
- og:title: _________________________ (máx 60 chars)
- og:description: ____________________ (máx 160 chars)
- og:image: URL de imagem 1200x630px
  - [ ] Criar versão específica para share (não usar hero image direto)
```

### H. Estratégia de Interações & Micro-Decisões de UX

```markdown
# DECISÕES DE UX/INTERAÇÃO

## Navegação na LP
- [ ] Nenhuma (100% foco no CTA — melhor para tráfego pago frio)
- [ ] Anchor links para seções (smooth scroll)
- [ ] Sticky header com logo + CTA button
- [ ] Sticky header que aparece só ao scrollar para cima

## Sticky CTA mobile
- [ ] Não usar
- [ ] Barra fixa no bottom com CTA (sempre visível)
- [ ] Botão WhatsApp flutuante
- [ ] Ambos (barra + WhatsApp) — cuidado com sobreposição

## Scroll behavior
- [ ] Smooth scroll (scroll-behavior: smooth no CSS)
- [ ] Back to top button (aparece após 50% scroll)
- [ ] Progress bar no topo (mostra % da página lida)

## Hover states (desktop only)
- Botões: scale(1.02) + shadow increase
- Cards: subtle lift (translateY(-2px))
- Links: underline ou color change
- REGRA: touch devices NÃO têm hover — não depender dele para info

## Estados de loading
- Botão submit: [ ] Spinner [ ] Texto "Enviando..." [ ] Disable + opacity
- Imagens: [ ] Blur placeholder [ ] Skeleton [ ] Fade in

## Feedback de ações
- Form submit sucesso: [ ] Toast verde [ ] Redirect [ ] Inline message
- Form submit erro: [ ] Toast vermelho [ ] Inline por campo [ ] Ambos
- WhatsApp click: [ ] Abre direto [ ] Confirma "Abrir WhatsApp?"
- Botão pressionado: active:scale(0.98) (feedback tátil)

## Elementos de urgência/escassez (se aplicável)
- [ ] Countdown timer (para eventos/promoções reais)
- [ ] "Últimas X vagas" (só se verdadeiro)
- [ ] "Oferta válida até DD/MM"
- [ ] Nenhum (serviço contínuo)
- REGRA: Escassez falsa destrói confiança. Só usar se real.

## Acessibilidade — checklist rápido
- [ ] Contraste verificado em TODAS as combinações de cor
- [ ] Focus ring visível (outline, não só color change)
- [ ] Tab order lógica (hero → seções → CTA → footer)
- [ ] Skip to content link (hidden, aparece no focus)
- [ ] Aria labels em ícones sem texto
- [ ] Reduced motion: desabilitar animações se prefers-reduced-motion
```

### I. Estratégia de Tracking & Thank You Page

```markdown
# DECISÕES DE TRACKING

## Eventos a rastrear (definir ANTES de codar)

| Evento | GTM Trigger | Quando dispara |
|--------|------------|----------------|
| page_view | Page View | Ao carregar |
| cta_click_hero | Click - CSS selector | Click no CTA do hero |
| cta_click_mid | Click - CSS selector | Click no CTA do meio |
| cta_click_final | Click - CSS selector | Click no CTA final |
| whatsapp_click | Click - CSS selector | Click no botão WhatsApp |
| phone_click | Click - tel: links | Click no telefone |
| form_start | Form Interaction | Primeiro campo preenchido |
| form_submit | Form Submission / Custom Event | Submit com sucesso |
| scroll_25 | Scroll Depth | 25% da página |
| scroll_50 | Scroll Depth | 50% da página |
| scroll_75 | Scroll Depth | 75% da página |
| scroll_100 | Scroll Depth | 100% da página |
| video_play | YouTube/Custom | Click no play |
| video_50 | YouTube/Custom | 50% assistido |
| video_complete | YouTube/Custom | 100% assistido |

## UTM handling
- [ ] Capturar UTMs da URL e salvar em hidden fields do formulário
- [ ] Passar UTMs no link do WhatsApp como query params
- [ ] Salvar UTMs em sessionStorage (para capturar mesmo sem form)

## Thank you page
- URL: /obrigado ou /lp/campanha/obrigado
- Conversão tracked via: [ ] URL match no GTM [ ] dataLayer push
- Conteúdo: confirmação + próximo passo + CTA secundário

## Relatórios automáticos
- [ ] GA4 Explorations configurado para funil (page → scroll → form_start → form_submit)
- [ ] Clarity: filtros por página salvos
```

### J. Estratégia de Entrega & Versionamento

```markdown
# DECISÕES DE ENTREGA

## Estrutura de arquivos por cliente
projetos-lp/
  [cliente-slug]/
    brief.md              ← Brief preenchido
    decisoes.md           ← Esta matriz preenchida
    copy-v1.md            ← Copy aprovada
    figma-url.md          ← Link do Figma
    src/                  ← Código fonte
    dist/                 ← Build para deploy
    docs/
      changelog.md        ← O que mudou em cada versão
      ab-tests.md         ← Registro de testes
      resultados/         ← Screenshots de analytics

## Git
- [ ] 1 repo por cliente
- [ ] Monorepo com pasta por cliente (recomendado se muitos clientes)
- Branch strategy: main (produção) → dev (WIP)

## Nomenclatura de versões
- v1.0 = primeira versão no ar
- v1.1 = ajustes de copy/design
- v1.2 = resultado de A/B test implementado
- v2.0 = redesign significativo

## Backup
- Código: Git (óbvio)
- Design: versões no Figma (histórico nativo)
- Analytics: screenshot mensal do dashboard
```

---

## CHECKLIST RÁPIDO: "Já posso começar a criar?"

Antes de abrir o Figma ou escrever qualquer código, verificar:

- [ ] Brief completo (Fase 0)
- [ ] Dispositivos definidos (3 frames no Figma: 375, 768, 1440)
- [ ] Comportamento por breakpoint decidido (tabela A)
- [ ] Tipo de página e ordem das seções definida (B)
- [ ] Cores, fontes e type scale definidos (C)
- [ ] Formato e budget de imagens definido (D)
- [ ] Tipo de CTA e campos do formulário definidos (E)
- [ ] Budget de performance definido (F)
- [ ] URL e estratégia de indexação definida (G)
- [ ] Interações e estados definidos (H)
- [ ] Eventos de tracking listados (I)
- [ ] Estrutura de pasta/repo criada (J)

**Se algum não estiver definido: parar e definir. Cada indefinição = retrabalho.**

---

## FASE 1: COPY DE VENDAS — IA (15 min)

### Prompt Master para Copy

```
Você é um copywriter direto-resposta especializado em landing pages
de alta conversão para [SEGMENTO] no Brasil.

Com base neste brief:
[COLAR BRIEF COMPLETO]

Gere a copy completa da landing page seguindo esta estrutura
(baseada na sequência psicológica de conversão):

1. HEADLINE (máx 10 palavras) — atacar a dor principal
2. SUBHEADLINE — expandir com benefício + especificidade
3. HERO CTA — texto do botão + micro-copy abaixo dele
4. SEÇÃO "VOCÊ JÁ PASSOU POR ISSO?" (3 bullets de dor)
   → Responde: "Isso é pra mim?"
5. SEÇÃO SOLUÇÃO — apresentar produto/serviço como ponte
   → Responde: "Vale a pena?"
6. BENEFÍCIOS (4-6 bullets com ícone sugerido para cada)
7. COMO FUNCIONA (3 passos simples e numerados)
8. PROVA SOCIAL (formatar 3 depoimentos realistas ou usar os reais do brief)
   → Responde: "Funciona mesmo?"
9. SOBRE / CREDENCIAIS (apresentar quem está por trás)
   → Responde: "Posso confiar?"
10. OFERTA + PREÇO (se aplicável) com ancoragem de valor
11. FAQ (5 perguntas que quebram as objeções do brief)
    → Responde: "E se der errado?"
12. CTA FINAL — urgência + escassez (se aplicável)

Regras:
- Português BR, tom [TOM DO BRIEF]
- Cada seção com headline própria (H2)
- Frases curtas. Parágrafos de 1-2 linhas máximo
- Foco em benefícios, não features
- Incluir pelo menos 3 CTAs distribuídos ao longo da página
- Message match: headline deve espelhar a promessa do anúncio
- Usar números específicos sempre que possível

Gere 2 versões:
A) Mais emocional/storytelling
B) Mais direta/objetiva

Após gerar, avalie cada versão com nota de 1-10 para:
- Clareza da proposta de valor
- Força das provas sociais
- Qualidade dos CTAs
- Tratamento de objeções
```

### Checklist de Revisão da Copy (Humano — 5 min)

- [ ] Headline comunica valor em menos de 3 segundos?
- [ ] Message match com o anúncio que vai trazer tráfego?
- [ ] CTAs são orientados a ação + benefício? (não "Enviar", sim "Quero Meu Orçamento Grátis")
- [ ] Objeções principais foram tratadas no FAQ?
- [ ] Tom de voz combina com o público?
- [ ] Prova social é crível e específica?
- [ ] Não tem links externos que vazam visitantes?

---

## FASE 2: WIREFRAME NO FIGMA — Humano (10 min)

### Critérios de Seleção Rápida

Com a copy pronta, selecionar das 100+ variações no Figma:

1. **Tipo de página** — Serviço local? E-commerce? Captura de lead? VSL?
2. **Número de seções** — Bate com a estrutura da copy gerada?
3. **Elementos necessários** — Tem espaço para vídeo? Carousel? Formulário? Mapa?
4. **Estilo do segmento** — Saúde (clean, confiança), Serviços (resultados, urgência), Produto (visual, desejo)?

### Ação

1. Abrir Figma → Biblioteca de referências
2. Duplicar o wireframe escolhido para novo arquivo: `[Cliente] - Landing Page v1`
3. **Criar 3 frames no mesmo arquivo:**
   - Frame 1: **Mobile 375px** (ESTE É O PRINCIPAL — começar por aqui)
   - Frame 2: **Tablet 768px**
   - Frame 3: **Desktop 1440px**
4. Reorganizar seções para espelhar a estrutura da copy
5. Aplicar as decisões de responsivo da Fase 0.5 (o que muda, some, aparece por device)

---

## FASE 3: DESIGN NO FIGMA — Humano + IA (30 min)

### O que o HUMANO faz:
- Aplicar cores e fontes definidas na Fase 0.5 (tokens visuais)
- Inserir logo
- Inserir fotos reais do cliente/produto (sempre melhor que IA para serviços locais)
- Ajustar hierarquia visual (F-pattern ou Z-pattern)
- Inserir a copy gerada em cada seção
- Garantir contraste mínimo 4.5:1 (texto) e 3:1 (texto grande)
- **Completar os 3 frames** (mobile → tablet → desktop) seguindo a tabela de comportamento da Fase 0.5
- Verificar que NENHUM texto fica cortado/overflow no frame mobile

### O que a IA faz (via Claude Code + Figma MCP):

```
# Ler e analisar o design atual
Acesse o design no Figma via MCP: [URL_DO_FIGMA]

Analise e sugira melhorias em:
1. Hierarquia visual (H1 > H2 > body está claro?)
2. Contraste de cores (acessibilidade WCAG AA)
3. Posicionamento dos CTAs (visíveis sem scroll?)
4. Espaçamento e respiração entre seções
5. Consistência tipográfica
6. Mobile readability (fontes ≥ 16px)
```

### Para gerar imagens (se necessário):

**Prompt base para Midjourney/DALL-E:**
```
[TIPO DE IMAGEM] for a [SEGMENTO] landing page.
Style: [clean/modern/warm/professional].
Color palette: [CORES DO BRIEF].
[DESCRIÇÃO ESPECÍFICA DO QUE PRECISA].
No text. High quality. Web-optimized aspect ratio [16:9 / 3:2 / 1:1].
```

### Gate de Aprovação (NÃO PULAR — evita retrabalho)

- [ ] **3 frames completos** no Figma (mobile 375, tablet 768, desktop 1440)
- [ ] Copy inserida e revisada em TODOS os frames
- [ ] Elementos responsivos conferidos (o que some, muda, reordena)
- [ ] Contraste de cores verificado (webaim.org/resources/contrastchecker)
- [ ] Imagens hero com crop correto para cada breakpoint
- [ ] CTAs visíveis sem scroll em todos os devices
- [ ] Se cliente externo: **aprovação escrita** antes de codar (print/email serve)
- [ ] Decisões da Fase 0.5 estão refletidas no design

---

## FASE 4: FIGMA → CÓDIGO — IA (20 min)

### Prompt Master para Claude Code

> **IMPORTANTE:** Anexar o arquivo `decisoes.md` (Fase 0.5 preenchida) junto com este prompt.
> Isso garante que o código já sai com responsivo, cores, fontes, performance e tracking corretos.

```
Use o Figma MCP para ler o design em [URL_DO_FIGMA].
Leia também o arquivo decisoes.md com todas as especificações técnicas.

Converta para um projeto completo seguindo TODAS as decisões documentadas.

## Stack
- React 18+ com TypeScript strict
- TailwindCSS (config com as cores/fontes definidas em decisoes.md)
- Vite como bundler
- Sem dependências desnecessárias

## Estrutura
src/
  components/
    Hero.tsx
    Problem.tsx
    Solution.tsx
    Benefits.tsx
    HowItWorks.tsx
    Testimonials.tsx
    About.tsx
    Pricing.tsx (se aplicável)
    FAQ.tsx
    FinalCTA.tsx
    WhatsAppButton.tsx
    CookieConsent.tsx
  App.tsx
  main.tsx
  index.css
public/
  images/ (otimizadas)
index.html

## Requisitos Técnicos
- Mobile-first, totalmente responsivo
- Semantic HTML (H1 único, H2 por seção, H3 subtítulos)
- Imagens: lazy loading, WebP, alt text descritivo
- Botões/links: min 48x48px tap target
- Fonts: min 16px body
- PageSpeed target: 95+ mobile
- Sem JS desnecessário (sem animações pesadas)

## SEO
- Title tag: [TÍTULO] (máx 60 chars)
- Meta description: [DESCRIÇÃO] (máx 160 chars)
- Open Graph tags (title, description, image, url)
- Schema markup JSON-LD (LocalBusiness ou Product conforme caso)
- Canonical URL
- Lang="pt-BR"

## Tracking
- Google Tag Manager container: [GTM-XXXXX]
- Data layer events para:
  - cta_click (cada CTA)
  - form_submit
  - whatsapp_click
  - scroll_depth (25%, 50%, 75%, 100%)
- NÃO incluir GA4/Pixel direto (vai pelo GTM)

## LGPD
- Cookie consent banner (bloqueia cookies não-essenciais até aceitar)
- Botões "Aceitar" e "Recusar" com mesmo destaque
- Link para política de privacidade
- Sem cookies pré-carregados antes do consentimento

## CTA WhatsApp
- Botão flutuante canto inferior direito
- Número: [NÚMERO]
- Mensagem pré-preenchida: "Olá! Vi o site e gostaria de saber mais sobre [SERVIÇO]"
- Evento GTM no clique

## Extras
- Favicon
- robots.txt (allow all)
- sitemap.xml básico

Gerar o projeto completo, pronto para npm run build.
```

### Revisão Humana do Código (15 min)

**Funcional:**
- [ ] `npm run dev` — funciona sem erros no console?
- [ ] Todos os CTAs funcionam (WhatsApp abre, formulário envia)?
- [ ] Copy está 100% correta (sem truncamento, sem placeholder)?
- [ ] Cookie consent aparece e bloqueia cookies antes do aceite?
- [ ] Tab navigation funciona nos elementos interativos?
- [ ] Formulário valida, submete, e redireciona para /obrigado?

**Responsivo — testar nos 4 breakpoints (DevTools → device toolbar):**
- [ ] **Mobile 375px** (iPhone SE) — hero legível? CTA visível? Nada overflow?
- [ ] **Mobile 390px** (iPhone 14) — mesmo check
- [ ] **Tablet 768px** (iPad) — colunas redistribuem? Imagens ajustam?
- [ ] **Desktop 1440px** — layout usa o espaço? Não fica "espremido" nem "esticado"?
- [ ] **Extra: 320px** (menor mobile) — nada quebra? (teste de stress)

**Performance rápida:**
- [ ] Lighthouse no DevTools → Score mobile > 90?
- [ ] Hero image carrega em < 2s?
- [ ] Não tem layout shift visível ao carregar (CLS)?

**Pixel-perfect com Figma:**
- [ ] Espaçamentos seguem o design?
- [ ] Fontes e sizes batem com a Fase 0.5?
- [ ] Cores corretas (comparar hex)?

---

## FASE 5: PRE-LAUNCH CHECKLIST

### Conteúdo
- [ ] Todo placeholder/lorem ipsum removido
- [ ] Headline comunica valor em < 3 segundos
- [ ] Sem links externos que vazam visitantes
- [ ] Navegação removida ou mínima (landing page = foco único)

### Técnico
- [ ] SSL ativo (HTTPS via certbot)
- [ ] Favicon presente
- [ ] OG tags configuradas (testar em developers.facebook.com/tools/debug)
- [ ] Canonical URL configurada
- [ ] robots.txt não bloqueia a página
- [ ] sitemap.xml gerado

### Performance (Core Web Vitals)
- [ ] LCP (Largest Contentful Paint) ≤ 2.5s
- [ ] INP (Interaction to Next Paint) < 200ms
- [ ] CLS (Cumulative Layout Shift) < 0.1
- [ ] PageSpeed mobile ≥ 90 (ideal 95+)
- [ ] Peso total da página < 1.5MB
- [ ] Imagens em WebP/AVIF, comprimidas
- [ ] CSS/JS minificados
- [ ] Gzip/Brotli habilitado no nginx

### Formulário (se aplicável)
- [ ] Submissão funciona
- [ ] Dados chegam no destino (email, CRM, planilha)
- [ ] Página de obrigado/confirmação carrega
- [ ] Mensagem de erro clara se falhar
- [ ] Campos mínimos (cada campo extra reduz conversão)

### Analytics & Tracking
- [ ] GTM instalado e em modo Preview sem erros
- [ ] GA4 recebendo pageview (verificar em Realtime)
- [ ] Evento de conversão configurado e marcado como Key Event
- [ ] Google Ads conversion tag (se usa Google Ads)
- [ ] Meta Pixel + Conversions API (se usa Meta Ads)
- [ ] Eventos de CTA click, form_submit, whatsapp_click disparando
- [ ] UTM parameters sendo capturados nos form submissions
- [ ] Teste real: submeter lead fake e verificar todo o fluxo

### LGPD
- [ ] Cookie consent banner aparece antes de qualquer cookie não-essencial
- [ ] Banner em português
- [ ] Botões Aceitar/Recusar com destaque igual
- [ ] Cookies bloqueados até consentimento
- [ ] Política de privacidade linkada e acessível
- [ ] Opt-in explícito para marketing (não pré-marcado)

### Acessibilidade (mínimo WCAG 2.1 AA)
- [ ] Contraste ≥ 4.5:1 texto normal, ≥ 3:1 texto grande
- [ ] Alt text em todas as imagens
- [ ] Navegação por teclado funciona
- [ ] Focus indicators visíveis
- [ ] Labels nos inputs de formulário
- [ ] Font size mínimo 16px body

### Verificação Final
- [ ] Abrir em janela anônima
- [ ] Testar em dispositivo móvel real
- [ ] Submeter lead de teste pelo fluxo completo
- [ ] Verificar conversão no GA4 DebugView
- [ ] Screenshot/backup antes de publicar

---

## FASE 6: DEPLOY NA VPS (5 min)

### Comandos

```bash
# Build do projeto
cd /path/to/projeto-cliente
npm run build

# Deploy para VPS
rsync -avz --delete dist/ claude-server:/var/www/[cliente-slug]/

# No VPS: configurar nginx (primeira vez)
ssh claude-server
```

### Nginx config template:

```nginx
server {
    listen 80;
    server_name [dominio.com.br] www.[dominio.com.br];
    root /var/www/[cliente-slug];
    index index.html;

    # Gzip
    gzip on;
    gzip_types text/plain text/css application/json application/javascript text/xml;

    # Cache de assets
    location ~* \.(js|css|png|jpg|jpeg|gif|ico|svg|webp|avif|woff2)$ {
        expires 1y;
        add_header Cache-Control "public, immutable";
    }

    # SPA fallback
    location / {
        try_files $uri $uri/ /index.html;
    }

    # Security headers
    add_header X-Frame-Options "SAMEORIGIN" always;
    add_header X-Content-Type-Options "nosniff" always;
    add_header Referrer-Policy "strict-origin-when-cross-origin" always;
}
```

```bash
# SSL
sudo certbot --nginx -d [dominio.com.br] -d www.[dominio.com.br]

# Testar
sudo nginx -t && sudo systemctl reload nginx
```

### Script automatizado (para futuros deploys):

```bash
#!/bin/bash
# deploy-landing.sh [cliente-slug]
CLIENT=$1
npm run build
rsync -avz --delete dist/ claude-server:/var/www/$CLIENT/
echo "Deploy completo: https://$CLIENT.nucip.com.br"
```

---

## FASE 7: VARIAÇÕES E OTIMIZAÇÃO (Contínuo)

### Gerar Variações Rapidamente (15 min cada)

**Prompt para variação de copy:**
```
Leia o componente Hero.tsx atual.

Gere 3 variações mantendo o mesmo design:
A) Headline focada em DOR (medo de perder/consequência negativa)
B) Headline focada em GANHO (desejo/resultado positivo)
C) Headline focada em PROVA SOCIAL (números/resultado de outros)

Salvar como Hero-A.tsx, Hero-B.tsx, Hero-C.tsx
Incluir lógica de A/B test no App.tsx que:
- Distribui 33/33/33 aleatoriamente
- Salva variante no localStorage (visitante sempre vê a mesma)
- Dispara evento GTM: ab_test_variant com valor A/B/C
```

### A/B Test Simples (sem ferramentas pagas)

```typescript
// utils/abtest.ts
export function getVariant(testName: string, variants: string[]): string {
  const key = `ab_${testName}`;
  const stored = localStorage.getItem(key);
  if (stored && variants.includes(stored)) return stored;

  const variant = variants[Math.floor(Math.random() * variants.length)];
  localStorage.setItem(key, variant);

  // Evento GTM
  window.dataLayer?.push({
    event: 'ab_test_variant',
    test_name: testName,
    variant: variant
  });

  return variant;
}
```

### Metodologia de Otimização (NÃO testar aleatoriamente)

**Framework ICE para priorizar testes:**

| Teste | Impact (1-10) | Confidence (1-10) | Ease (1-10) | Score |
|-------|------|------|------|-------|
| Nova headline | ? | ? | ? | ? |
| CTA diferente | ? | ? | ? | ? |
| Prova social acima da dobra | ? | ? | ? | ? |

**Prioridade de testes (do mais impactante para menos):**
1. Headlines e proposta de valor
2. Texto e posição do CTA
3. Número de campos do formulário
4. Tipo e posição de prova social
5. Ordem das seções
6. Hero image/vídeo
7. Apresentação de preço/oferta

**Requisitos mínimos para resultado confiável:**
- 1.000+ visitantes por variante
- 100+ conversões por variante (ideal)
- Mínimo 2 semanas de teste
- 95% de confiança estatística antes de declarar vencedor

### Ritmo Mensal de Otimização

**Semana 1: Medir & Diagnosticar**
- [ ] Puxar dados de conversão do GA4
- [ ] Revisar heatmaps no Clarity
- [ ] Identificar top 3 pontos de fricção

**Semana 2: Formular Hipótese**
- [ ] "Se mudarmos [X], [métrica Y] vai melhorar porque [Z]"
- [ ] Pontuar com ICE
- [ ] Selecionar teste #1

**Semana 3-4: Testar**
- [ ] Lançar variação
- [ ] NÃO parar o teste antes da significância estatística

**Fim do mês: Implementar & Documentar**
- [ ] Implementar variante vencedora
- [ ] Documentar: o que testou, resultado, lift de conversão
- [ ] Alimentar próximo ciclo

### Prompt para Análise de Resultados

```
Analise os dados de conversão deste A/B test:

Variante A (original): [X] visitas, [Y] conversões ([Z]%)
Variante B: [X] visitas, [Y] conversões ([Z]%)
Variante C: [X] visitas, [Y] conversões ([Z]%)

Período: [DATA] a [DATA]
Fonte de tráfego: [GOOGLE ADS / META / ORGÂNICO]

1. Qual variante venceu e com qual confiança estatística?
2. Por que provavelmente venceu? (analisar o que mudou)
3. Sugira 3 novas hipóteses de teste baseadas neste resultado
4. Calcule o impacto financeiro: se mantiver o vencedor,
   quanto a mais em conversões por mês?
```

---

## Métricas-Chave para Acompanhar

| Métrica | O que mede | Target |
|---------|-----------|--------|
| Taxa de conversão | Conversões / Visitantes | 3-5% (lead), 1-3% (venda) |
| Bounce rate | Saem sem interagir | < 50% |
| Tempo na página | Engajamento com conteúdo | > 1 min |
| Scroll depth | % que chega ao CTA final | > 60% ao CTA principal |
| Form start vs complete | Fricção no formulário | Ratio > 70% |
| CPA | Custo por conversão (ads) | Depende do ticket |
| Mobile vs Desktop conv. | Gap de experiência | Desktop ~2x mobile é normal |
| PageSpeed mobile | Performance técnica | 90+ |

---

## O Que É Humano vs IA — Resumo Final

| Etapa | IA faz | Humano faz |
|-------|--------|-----------|
| Brief | Template padronizado | Preencher com dados reais do cliente |
| Copy | Gera 100% do draft | Escolher versão, ajustar voz e hooks emocionais |
| Wireframe | — | Selecionar referência certa (olho treinado) |
| Design | Sugere melhorias, gera imagens | Aplicar identidade, validar hierarquia |
| Código | Gera 95% do projeto | Review de responsivo, funcionalidade, QA |
| Pre-launch | Checklist automatizável | Verificação final em dispositivo real |
| Deploy | Script automatizado | Config inicial do domínio |
| Variações | Gera N versões | Formular hipótese, decidir o que testar |
| Otimização | Gera análise de dados | Interpretar, decidir próximo passo |

---

## Ferramentas Complementares (se necessário no futuro)

| Ferramenta | Quando usar | Preço |
|-----------|-------------|-------|
| Microsoft Clarity | Heatmaps + session replay (GRÁTIS) | $0 |
| Midjourney | Hero images e visuais de campanha | $10/mês |
| AdCreative.ai | Criativos de ads em volume | $29/mês |
| Surfer SEO | Otimização de conteúdo SEO | $89/mês |
| Anyword | Copy com score preditivo de conversão | $49/mês |
| Make.com | Automação lead → CRM → notificação | $9/mês |

---

## Decisões Tomadas Nesta Sessão

1. **Figma → Código direto** (não usar Elementor/WordPress) — PageSpeed superior, controle total
2. **VPS própria** (não usar Vercel/Netlify) — já temos, custo zero
3. **React/Tailwind/Vite** — stack que já dominamos
4. **Sem ferramentas de landing page pagas** (Unbounce, Leadpages) — o pipeline nosso entrega o mesmo com mais controle
5. **A/B test caseiro** — suficiente para o volume de tráfego dos clientes
6. **Microsoft Clarity** como ferramenta de heatmap — grátis e suficiente
7. **LGPD compliance** integrado desde o código — não deixar para depois
