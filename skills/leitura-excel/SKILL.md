---
name: leitura-excel
description: Identificar estrutura, folhas e colunas relevantes nos ficheiros bancário e contabilístico.
---

# Skill — Leitura dos ficheiros Excel

## Objetivo

Interpretar os dois ficheiros sem assumir um layout pré-definido.

## Procedimento

Para cada ficheiro:

1. listar folhas;
2. identificar regiões tabulares;
3. localizar a linha de cabeçalhos;
4. mapear semanticamente as colunas;
5. identificar linhas de dados;
6. excluir linhas de total, saldo, subtotais, títulos e vazios;
7. preservar folha e número de linha de origem.

## Mapeamento esperado

### Banco
Procurar equivalentes de:
- data;
- data-valor;
- descrição;
- referência;
- débito;
- crédito;
- montante;
- saldo.

### Contabilidade
Procurar equivalentes de:
- data;
- data de documento;
- documento;
- descrição;
- conta;
- terceiro;
- débito;
- crédito;
- montante.

## Regras

- Não escolher uma coluna apenas pela posição.
- Usar cabeçalho, tipo dos valores e padrão dos dados.
- Se houver duas colunas candidatas, registar a ambiguidade.
- O saldo bancário não é um movimento.
- Preservar os valores originais antes de normalizar.
