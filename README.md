# AI Landing Page Workflow

> Pipeline completo para criar landing pages de alta conversao usando IA como acelerador e humano como estrategista.

**De brief a pagina no ar em ~2.5 horas. Variacoes novas em ~20 minutos.**

---

## O Problema

Criar landing pages de qualidade profissional consome tempo demais. Designers, copywriters, devs, QA — o processo tradicional leva dias ou semanas. Ferramentas como Unbounce e Leadpages simplificam mas limitam o controle e custam caro.

## A Solucao

Um workflow passo-a-passo que combina **IA para producao** e **humano para estrategia**, usando ferramentas que voce ja tem ou que sao gratuitas. Sem vendor lock-in. Codigo seu, hospedagem sua.

## Stack Base

| Necessidade | Ferramenta | Custo |
|-------------|-----------|-------|
| Design + Wireframes | Figma (free tier funciona) | $0-15/mes |
| Codigo | React + TypeScript + TailwindCSS + Vite | $0 |
| IA para codigo | Claude Code / Cursor / Copilot | $10-20/mes |
| IA para copy | Claude / ChatGPT | $0-20/mes |
| Deploy | Qualquer VPS / Vercel / Netlify | $0-10/mes |

> Voce pode adaptar a stack. O workflow funciona com qualquer combinacao de ferramentas.

## O Workflow

```
FASE 0 ─── FASE 0.5 ─── FASE 1 ─── FASE 2 ─── FASE 3 ─── FASE 4 ─── FASE 5 ─── FASE 6 ─── FASE 7
Brief      Decisoes     Copy       Wireframe   Design     Codigo     Pre-launch  Deploy     Otimizar
(5 min)    (10 min)     (15 min)   (10 min)    (30 min)   (20 min)   (15 min)    (5 min)    (continuo)
HUMANO     HUMANO       IA+HUMANO  HUMANO      HUMANO+IA  IA+HUMANO  HUMANO      IA+HUMANO  IA+HUMANO
```

> **A Fase 0.5 e a mais importante.** Cada decisao nao tomada antes = retrabalho depois.

## Guia Rapido

1. **Preencha o brief** → [`templates/brief.md`](templates/brief.md)
2. **Tome as micro-decisoes** → [`templates/decisoes.md`](templates/decisoes.md)
3. **Gere a copy** → [`prompts/copy-vendas.md`](prompts/copy-vendas.md)
4. **Selecione wireframe no Figma** → [`workflow/03-wireframe/`](workflow/03-wireframe/)
5. **Design no Figma (3 frames: mobile/tablet/desktop)** → [`workflow/04-design/`](workflow/04-design/)
6. **Gere o codigo** → [`prompts/figma-to-code.md`](prompts/figma-to-code.md)
7. **Pre-launch checklist** → [`workflow/06-pre-launch/`](workflow/06-pre-launch/)
8. **Deploy** → [`workflow/07-deploy/`](workflow/07-deploy/)
9. **Otimize** → [`workflow/08-optimization/`](workflow/08-optimization/)

## Documentacao Completa

| Doc | Descricao |
|-----|-----------|
| [Workflow Completo (PT-BR)](docs/workflow-completo-pt.md) | Documento unico com todo o pipeline detalhado |
| [Templates](templates/) | Brief, decisoes, checklists prontos para usar |
| [Prompts](prompts/) | Prompts otimizados para cada fase |
| [Exemplos](examples/) | Exemplos reais de briefs e decisoes preenchidos |

## O Que a IA Faz vs O Que o Humano Faz

| Etapa | IA | Humano |
|-------|-----|--------|
| Brief | Template padronizado | Preencher com dados reais |
| Copy | Gera 100% do draft | Escolher versao, ajustar voz |
| Wireframe | — | Selecionar referencia certa |
| Design | Sugere melhorias, gera imagens | Aplicar identidade visual |
| Codigo | Gera 95% do projeto | Review responsivo e QA |
| Pre-launch | Checklist automatizavel | Verificacao em device real |
| Deploy | Script automatizado | Config inicial do dominio |
| Otimizacao | Gera variacoes e analisa dados | Formular hipoteses, decidir |

## Melhores Praticas Cobertas

- **Mobile-first** (83% do trafego pago e mobile)
- **Core Web Vitals** (LCP ≤ 2.5s, INP < 200ms, CLS < 0.1)
- **LGPD** (cookie consent, politica de privacidade)
- **Acessibilidade** (WCAG 2.1 AA minimo)
- **CRO** (sequencia psicologica de conversao, A/B testing)
- **SEO** (Schema markup, Open Graph, semantic HTML)
- **Analytics** (GA4 + GTM + data layer events)
- **Performance** (budget de peso, lazy loading, Gzip/Brotli)

## Contribuindo

Contribuicoes sao muito bem-vindas! Veja [CONTRIBUTING.md](CONTRIBUTING.md) para saber como participar.

### Formas de contribuir

- Sugerir melhorias no workflow
- Adicionar prompts otimizados para outras IAs
- Compartilhar templates de design
- Traduzir para outros idiomas
- Reportar o que funcionou (ou nao) no seu caso
- Adicionar exemplos reais

## Para Quem E Este Projeto

- Gestores de trafego que criam LPs para clientes
- Freelancers de web design
- Agencias digitais pequenas
- Desenvolvedores que querem um processo estruturado
- Qualquer pessoa que cria landing pages regularmente

## Licenca

[MIT](LICENSE) — use, modifique, distribua livremente.

---

Criado por [Nucip](https://nucip.com.br) | Mantido pela comunidade
