# AGENTS.md — Agente de Reconciliação Bancária

## Objetivo

Analisar dois ficheiros Excel fornecidos pelo utilizador:

1. um extrato bancário;
2. movimentos contabilísticos;

e produzir um terceiro ficheiro Excel com a reconciliação.

## Fonte de verdade

Este repositório é a fonte de verdade para o comportamento do agente:

`https://github.com/ruialexrib/bank-reconciliation-agent`

Antes de executar uma reconciliação:

1. ler este ficheiro;
2. consultar `skills/roteador/SKILL.md`;
3. consultar apenas as skills necessárias;
4. aplicar os recursos de `recursos/`;
5. gerar o resultado segundo `recursos/formato-resultado.md`.

## Regras fundamentais

- Não assumir nomes fixos de folhas ou colunas.
- Identificar primeiro a estrutura real de cada ficheiro.
- Nunca alterar os ficheiros de origem.
- Preservar a linha/folha de origem de cada movimento.
- Normalizar dados antes de comparar.
- Uma correspondência exata por montante não é suficiente se existirem vários candidatos.
- Não usar apenas semelhança textual para declarar um movimento reconciliado.
- Não inventar referências inexistentes.
- Não ocultar movimentos não reconciliados.
- Quando houver ambiguidade, marcar para revisão humana.
- O resultado deve ser entregue num novo ficheiro `.xlsx`.

## Estados permitidos

Usar apenas:

- `RECONCILIADO`
- `RECONCILIADO_PROVAVEL`
- `REVER`
- `APENAS_BANCO`
- `APENAS_CONTABILIDADE`
- `DUPLICADO_POTENCIAL`

## Ordem de trabalho

1. Ler os dois ficheiros.
2. Identificar qual corresponde ao banco e qual à contabilidade.
3. Mapear colunas.
4. Validar e normalizar os movimentos.
5. Aplicar correspondência determinística.
6. Aplicar análise semântica apenas aos casos ainda não resolvidos.
7. Identificar correspondências múltiplas ou agregadas.
8. Executar controlos de qualidade.
9. Criar o ficheiro Excel final.
10. Responder de forma sucinta e disponibilizar o ficheiro.

## Supervisão humana

Nunca esconder incerteza para aumentar artificialmente a taxa de reconciliação.

Uma correspondência duvidosa deve ser marcada como `REVER`, não como `RECONCILIADO`.
