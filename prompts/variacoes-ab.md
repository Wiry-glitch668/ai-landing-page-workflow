# Prompt: Gerar Variacoes para A/B Test

> Testado com: Claude Code, Cursor
> Uso: Gerar variacoes rapidas para testar conversao

## Prompt: Variacoes de Hero

```
Leia o componente Hero.tsx atual.

Gere 3 variacoes mantendo o mesmo design:
A) Headline focada em DOR (medo de perder/consequencia negativa)
B) Headline focada em GANHO (desejo/resultado positivo)
C) Headline focada em PROVA SOCIAL (numeros/resultado de outros)

Salvar como Hero-A.tsx, Hero-B.tsx, Hero-C.tsx

Incluir logica de A/B test no App.tsx que:
- Distribui 33/33/33 aleatoriamente
- Salva variante no localStorage (visitante sempre ve a mesma)
- Dispara evento GTM: ab_test_variant com valor A/B/C
```

## Codigo de A/B Test (pronto para usar)

```typescript
// utils/abtest.ts
export function getVariant(testName: string, variants: string[]): string {
  const key = `ab_${testName}`;
  const stored = localStorage.getItem(key);
  if (stored && variants.includes(stored)) return stored;

  const variant = variants[Math.floor(Math.random() * variants.length)];
  localStorage.setItem(key, variant);

  window.dataLayer?.push({
    event: 'ab_test_variant',
    test_name: testName,
    variant: variant
  });

  return variant;
}
```

## Prompt: Analise de Resultados

```
Analise os dados de conversao deste A/B test:

Variante A (original): [X] visitas, [Y] conversoes ([Z]%)
Variante B: [X] visitas, [Y] conversoes ([Z]%)
Variante C: [X] visitas, [Y] conversoes ([Z]%)

Periodo: [DATA] a [DATA]
Fonte de trafego: [GOOGLE ADS / META / ORGANICO]

1. Qual variante venceu e com qual confianca estatistica?
2. Por que provavelmente venceu?
3. Sugira 3 novas hipoteses de teste baseadas neste resultado
4. Calcule o impacto financeiro mensal se mantiver o vencedor
```

## Requisitos Minimos para Resultado Confiavel

- 1.000+ visitantes por variante
- 100+ conversoes por variante (ideal)
- Minimo 2 semanas de teste
- 95% de confianca estatistica
