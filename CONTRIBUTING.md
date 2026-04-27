# Contribuindo

Obrigado por querer melhorar este workflow! Contribuicoes de todos os niveis sao bem-vindas.

## Como Contribuir

### 1. Reportar Problemas ou Sugerir Melhorias

Abra uma [Issue](../../issues) usando um dos templates:
- **Sugestao de melhoria** — para propor mudancas no workflow
- **Novo prompt** — para compartilhar um prompt que funciona bem
- **Bug no workflow** — quando algo nao funciona como documentado
- **Exemplo real** — para compartilhar como voce usou o workflow

### 2. Contribuir com Codigo/Conteudo

1. Fork o repositorio
2. Crie uma branch: `git checkout -b melhoria/descricao-curta`
3. Faca suas alteracoes
4. Commit: `git commit -m "feat: descricao da melhoria"`
5. Push: `git push origin melhoria/descricao-curta`
6. Abra um Pull Request

### 3. Tipos de Contribuicao

| Tipo | Onde | Descricao |
|------|------|-----------|
| **Melhoria no workflow** | `workflow/` | Ajustar etapas, adicionar checks, otimizar processo |
| **Novo prompt** | `prompts/` | Prompts testados para outras IAs ou casos de uso |
| **Template** | `templates/` | Briefs, checklists, decisoes para nichos especificos |
| **Exemplo** | `examples/` | Brief preenchido + resultado real (anonimizado) |
| **Traducao** | `docs/` | Traduzir workflow para ingles ou outros idiomas |
| **Integracao** | `integrations/` | Adaptar workflow para Webflow, WordPress, Next.js, etc. |

## Convencoes

### Commits

Usamos [Conventional Commits](https://www.conventionalcommits.org/):

```
feat: adiciona prompt para copy de e-commerce
fix: corrige checklist de pre-launch (faltava OG image)
docs: traduz secao de CRO para ingles
chore: reorganiza pasta de templates
```

### Idioma

- Conteudo principal: **Portugues (BR)**
- Traducao ingles: bem-vinda em `docs/en/`
- Commits e PRs: portugues ou ingles

### Qualidade

Antes de submeter, verifique:
- [ ] Links internos funcionam
- [ ] Markdown renderiza corretamente
- [ ] Prompts foram testados (mencionar qual IA usou)
- [ ] Sem informacoes sensiveis (tokens, senhas, dados de clientes reais)

## Estrutura do Projeto

```
ai-landing-page-workflow/
├── README.md              ← Visao geral e guia rapido
├── CONTRIBUTING.md         ← Voce esta aqui
├── LICENSE                 ← MIT
├── docs/
│   └── workflow-completo-pt.md  ← Documento unico completo
├── workflow/               ← Cada fase em detalhe
│   ├── 00-brief/
│   ├── 01-micro-decisions/
│   ├── 02-copy/
│   ├── 03-wireframe/
│   ├── 04-design/
│   ├── 05-code/
│   ├── 06-pre-launch/
│   ├── 07-deploy/
│   └── 08-optimization/
├── templates/              ← Templates prontos para copiar e usar
│   ├── brief.md
│   ├── decisoes.md
│   └── checklist-pre-launch.md
├── prompts/                ← Prompts otimizados por fase
│   ├── copy-vendas.md
│   ├── figma-to-code.md
│   ├── variacoes-ab.md
│   └── analise-resultados.md
├── examples/               ← Exemplos reais (anonimizados)
└── .github/                ← Templates de Issue e PR
```

## Codigo de Conduta

- Seja respeitoso e construtivo
- Foque em melhorar o workflow, nao em criticar ferramentas
- Compartilhe resultados reais sempre que possivel
- Credite fontes quando usar material de terceiros

## Duvidas?

Abra uma Issue com a tag `question` ou inicie uma Discussion.
