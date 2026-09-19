---
name: analise-excecoes
description: Analisar movimentos ambíguos, concorrentes, agregados ou potencialmente duplicados.
---

# Skill — Análise de exceções

## Objetivo

Tratar apenas os casos que não ficaram resolvidos pelas regras fortes.

## Casos típicos

- dois movimentos contabilísticos com o mesmo valor e datas próximas;
- duas operações bancárias idênticas;
- descrição bancária abreviada;
- pagamento agregado de várias faturas;
- um movimento contabilístico liquidado por várias operações bancárias;
- possível duplicação;
- diferença temporal superior ao padrão;
- pequena diferença monetária que excede a tolerância.

## Procedimento

1. reunir todos os candidatos;
2. comparar montante, data, referência e descrição;
3. avaliar se existe um candidato claramente dominante;
4. se houver concorrência material, marcar `REVER`;
5. apresentar no Excel final os candidatos considerados.

## Linguagem

A justificação deve ser factual:
- “mesmo valor e referência semelhante; diferença de 1 dia”;
- “existem dois candidatos com o mesmo valor”;
- “soma de três movimentos contabilísticos coincide com o movimento bancário”.

Evitar frases vagas como “parece correto” sem explicar porquê.
