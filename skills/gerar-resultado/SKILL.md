---
name: gerar-resultado-excel
description: Criar o ficheiro Excel final da reconciliação com tabelas, filtros, resumo e auditoria.
---

# Skill — Gerar resultado Excel

## Objetivo

Produzir o entregável final:

`Resultado_reconciliacao_bancaria.xlsx`

## Estrutura

Seguir integralmente `resources/formato-resultado.md`.

## Requisitos de qualidade

- criar folhas com nomes claros em português;
- usar tabelas e filtros;
- congelar cabeçalhos;
- datas como datas reais;
- valores como moeda;
- texto legível e colunas com largura adequada;
- incluir formatação condicional moderada por estado;
- incluir uma folha de resumo;
- incluir parâmetros e mapeamento de colunas detetado.

## Dados originais

Não substituir nem apagar os ficheiros carregados.

Quando possível, preservar nos resultados:
- descrição original;
- referência original;
- valor original;
- folha/linha de origem.

## Resposta ao utilizador

Depois de gerar o ficheiro:
1. disponibilizar o ficheiro;
2. indicar numa frase quantos movimentos ficaram reconciliados, a rever e não reconciliados;
3. não reproduzir no chat toda a tabela se o ficheiro já contiver o detalhe.
