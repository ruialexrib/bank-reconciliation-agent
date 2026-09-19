---
name: reconciliacao-bancaria
description: Aplicar regras determinísticas e semânticas para reconciliar movimentos bancários e contabilísticos.
---

# Skill — Reconciliação bancária

## Objetivo

Produzir correspondências auditáveis entre movimentos do banco e da contabilidade.

## Ordem obrigatória

### 1. Matching exato forte
Procurar primeiro:
- valor coincidente;
- referência coincidente;
- data dentro da tolerância;
- candidato único.

### 2. Matching por valor + descrição
Para movimentos ainda não resolvidos:
- valor coincidente;
- data compatível;
- descrição/entidade fortemente relacionada;
- candidato único.

### 3. Matching provável
Para casos com:
- valor coincidente;
- referência parcial ou ausente;
- descrição semanticamente compatível;
- pequena diferença temporal.

Marcar como `RECONCILIADO_PROVAVEL`, não como reconciliação definitiva.

### 4. Matching agregado
Procurar 1:N e N:1 dentro do limite configurado.
A soma tem de coincidir dentro da tolerância.

### 5. Exceções
Encaminhar casos concorrentes ou pouco claros para `skills/analise-excecoes/SKILL.md`.

## Regra de unicidade

Um movimento não pode ser usado em duas reconciliações diferentes, salvo quando o próprio modelo de dados representar explicitamente uma repartição e esta estiver documentada.

## Explicabilidade

Cada correspondência deve guardar:
- IDs;
- regra;
- diferenças;
- evidência;
- estado;
- confiança;
- justificação curta.

## Proibição

Nunca aumentar a taxa de reconciliação à custa de correspondências especulativas.
