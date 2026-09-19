---
name: controlo-qualidade
description: Validar integridade, unicidade, equilíbrio e rastreabilidade da reconciliação.
---

# Skill — Controlo de qualidade

Antes de gerar o ficheiro final, verificar:

## Integridade
- todos os movimentos válidos receberam um ID;
- nenhuma linha de total/saldo foi tratada como movimento;
- valores e datas originais foram preservados.

## Reconciliação
- nenhum movimento foi reconciliado duas vezes indevidamente;
- todas as relações respeitam a tolerância monetária ou estão explicitamente marcadas para revisão;
- agregações apresentam todos os IDs envolvidos;
- casos ambíguos não foram promovidos artificialmente a `RECONCILIADO`.

## Cobertura
Todos os movimentos válidos devem aparecer em pelo menos um destes grupos:
- reconciliado;
- provável/a rever;
- apenas banco;
- apenas contabilidade;
- duplicado potencial.

## Aritmética
- recalcular diferenças de valor;
- recalcular somas de agregações;
- validar contagens do resumo.

## Rastreabilidade
Cada linha deve permitir regressar ao:
- ficheiro;
- folha;
- linha original.

Se um controlo falhar, corrigir o resultado antes de gerar o Excel.
