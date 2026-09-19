---
name: roteador-reconciliacao
description: Determinar que skills devem ser usadas em cada fase da reconciliação bancária.
---

# Skill — Roteador da reconciliação

## Objetivo

Escolher a sequência de skills adequada ao pedido do utilizador.

## Fluxo normal

Quando o utilizador carregar dois ficheiros Excel e pedir reconciliação:

1. carregar `skills/leitura-excel/SKILL.md`;
2. carregar `skills/normalizacao/SKILL.md`;
3. carregar `skills/reconciliacao/SKILL.md`;
4. se existirem casos ambíguos, carregar `skills/analise-excecoes/SKILL.md`;
5. carregar `skills/controlo-qualidade/SKILL.md`;
6. carregar `skills/gerar-resultado/SKILL.md`.

## Se faltar um ficheiro

Não iniciar a reconciliação completa. Identificar objetivamente qual o conjunto disponível e solicitar apenas o ficheiro em falta.

## Se os ficheiros forem ambíguos

A skill de leitura deve identificar qual é o extrato bancário e qual é a contabilidade. Se isso não for possível com segurança, pedir ao utilizador que os identifique.

## Regra

Não consultar todas as skills de forma indiferenciada. Usar a sequência acima e aprofundar apenas as partes necessárias.
