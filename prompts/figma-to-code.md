# Prompt: Figma para Codigo

> Testado com: Claude Code (Figma MCP), Cursor
> Qualidade media: 8.5/10 (responsivo sai bem, precisa ajustar detalhes visuais)

## Pre-requisitos

- Design pronto no Figma com 3 frames (mobile/tablet/desktop)
- Arquivo `decisoes.md` preenchido
- URL do Figma ou acesso via MCP

## Prompt

```
Use o Figma MCP para ler o design em [URL_DO_FIGMA].
Leia tambem o arquivo decisoes.md com todas as especificacoes tecnicas.

Converta para um projeto completo seguindo TODAS as decisoes documentadas.

## Stack
- React 18+ com TypeScript strict
- TailwindCSS (config com as cores/fontes definidas em decisoes.md)
- Vite como bundler
- Sem dependencias desnecessarias

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
    Pricing.tsx (se aplicavel)
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

## Requisitos Tecnicos
- Mobile-first, totalmente responsivo
- Semantic HTML (H1 unico, H2 por secao, H3 subtitulos)
- Imagens: lazy loading, WebP, alt text descritivo
- Botoes/links: min 48x48px tap target
- Fonts: min 16px body
- PageSpeed target: 95+ mobile
- Sem JS desnecessario

## SEO
- Title tag: [TITULO] (max 60 chars)
- Meta description: [DESCRICAO] (max 160 chars)
- Open Graph tags (title, description, image, url)
- Schema markup JSON-LD (conforme decisoes.md)
- Canonical URL
- Lang="pt-BR"

## Tracking
- Google Tag Manager container: [GTM-XXXXX]
- Data layer events para:
  - cta_click (cada CTA)
  - form_submit
  - whatsapp_click
  - scroll_depth (25%, 50%, 75%, 100%)
- NAO incluir GA4/Pixel direto (vai pelo GTM)

## LGPD
- Cookie consent banner (bloqueia cookies nao-essenciais ate aceitar)
- Botoes "Aceitar" e "Recusar" com mesmo destaque
- Link para politica de privacidade
- Sem cookies pre-carregados antes do consentimento

## CTA WhatsApp
- Botao flutuante canto inferior direito
- Numero: [NUMERO]
- Mensagem pre-preenchida: "Ola! Vi o site e gostaria de saber mais sobre [SERVICO]"
- Evento GTM no clique

## Extras
- Favicon
- robots.txt
- sitemap.xml basico

Gerar o projeto completo, pronto para npm run build.
```

## Variacao: Sem Figma MCP

Se nao tiver Figma MCP, use screenshot do design:

```
Veja o screenshot anexo do design da landing page.
Recrie fielmente em React + TailwindCSS + Vite.
[... mesmo prompt acima sem a linha do Figma MCP ...]
```

## Revisao (Humano)

- [ ] `npm run dev` sem erros
- [ ] Mobile 375px ok
- [ ] Mobile 390px ok
- [ ] Tablet 768px ok
- [ ] Desktop 1440px ok
- [ ] 320px stress test
- [ ] CTAs funcionam
- [ ] Copy 100% correta
- [ ] Cookie consent funciona
- [ ] Lighthouse > 90
