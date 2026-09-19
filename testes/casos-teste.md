# Casos de teste

## Teste 1 — Correspondência exata
Mesmo valor, referência e data.
Esperado: `RECONCILIADO`.

## Teste 2 — Diferença de data
Mesmo valor/referência, diferença de 2 dias.
Esperado: `RECONCILIADO`.

## Teste 3 — Candidatos duplicados
Um movimento bancário e dois movimentos contabilísticos com mesmo valor/data e sem referência distintiva.
Esperado: `REVER`.

## Teste 4 — Movimento só no banco
Sem candidato contabilístico.
Esperado: `APENAS_BANCO`.

## Teste 5 — Movimento só na contabilidade
Sem candidato bancário.
Esperado: `APENAS_CONTABILIDADE`.

## Teste 6 — Agregação
Um movimento bancário de -300 € e dois movimentos contabilísticos de -100 € e -200 €, com referências/descrições compatíveis.
Esperado: `RECONCILIADO_PROVAVEL` ou `REVER`, consoante a unicidade dos candidatos.

## Teste 7 — Saldo bancário
Linha identificada como saldo inicial/final.
Esperado: ignorar como movimento e registar a exclusão na auditoria.

## Teste 8 — Valor igual, descrição incompatível
Mesmo valor, mas entidades/referências incompatíveis.
Esperado: não reconciliar automaticamente.

## Teste 9 — Duplicado potencial
Dois movimentos idênticos no mesmo ficheiro de origem.
Esperado: `DUPLICADO_POTENCIAL`.

## Teste 10 — Integridade final
Todos os movimentos válidos devem aparecer uma única vez na cobertura final, sem reutilização indevida.
