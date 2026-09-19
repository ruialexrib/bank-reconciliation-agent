---
name: normalizacao-movimentos
description: Normalizar datas, montantes, referências e descrições sem perder os valores originais.
---

# Skill — Normalização

## Objetivo

Criar uma representação comparável dos movimentos do banco e da contabilidade.

## Datas

- Converter datas válidas para um formato de data real.
- Manter a data original.
- Não inventar datas quando a célula estiver vazia ou for inválida.

## Montantes

Representar internamente:
- entradas no banco como positivas;
- saídas no banco como negativas.

Adaptar a contabilidade ao mesmo sentido económico para permitir comparação.

Se existirem colunas Débito e Crédito separadas, derivar um montante normalizado sem eliminar as colunas originais.

## Descrições

Criar uma versão normalizada para comparação:
- remover espaços redundantes;
- uniformizar maiúsculas/minúsculas;
- normalizar caracteres de pontuação quando não sejam significativos;
- manter números/referências relevantes;
- reconhecer abreviaturas comuns sem alterar o original.

## Referências

- remover apenas formatação irrelevante;
- não eliminar dígitos;
- preservar zeros significativos quando possam fazer parte de um identificador;
- manter a referência original.

## Identificadores

Atribuir um ID interno único a cada movimento:
- `B000001`, `B000002`... para banco;
- `C000001`, `C000002`... para contabilidade.
