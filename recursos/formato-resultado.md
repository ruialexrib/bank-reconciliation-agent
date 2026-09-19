# Formato obrigatório do ficheiro de resultado

Nome sugerido:

`Resultado_reconciliacao_bancaria.xlsx`

## Folha 1 — Resumo

Incluir:
- total de movimentos bancários;
- total de movimentos contabilísticos;
- número e valor de `RECONCILIADO`;
- número e valor de `RECONCILIADO_PROVAVEL`;
- número de casos `REVER`;
- número/valor `APENAS_BANCO`;
- número/valor `APENAS_CONTABILIDADE`;
- duplicados potenciais;
- data/hora da análise;
- parâmetros utilizados.

## Folha 2 — Reconciliação

Uma linha por relação de matching.

Colunas mínimas:
- ID reconciliação;
- estado;
- confiança;
- IDs banco;
- IDs contabilidade;
- data banco;
- data contabilidade;
- diferença em dias;
- valor banco;
- valor contabilidade;
- diferença de valor;
- descrição banco;
- descrição contabilidade;
- referência banco;
- referência contabilidade;
- regra aplicada;
- justificação;
- origem banco;
- origem contabilidade.

## Folha 3 — Apenas banco

Todos os movimentos bancários não reconciliados, preservando os campos originais e acrescentando:
- ID interno;
- motivo;
- candidatos considerados, se existirem.

## Folha 4 — Apenas contabilidade

Todos os movimentos contabilísticos não reconciliados, preservando os campos originais e acrescentando:
- ID interno;
- motivo;
- candidatos considerados, se existirem.

## Folha 5 — A rever

Casos `REVER` e `RECONCILIADO_PROVAVEL`.

Incluir todos os candidatos relevantes para permitir validação humana.

## Folha 6 — Duplicados

Duplicados potenciais encontrados no banco ou na contabilidade.

## Folha 7 — Parâmetros e auditoria

Incluir:
- tolerâncias aplicadas;
- regras usadas;
- ficheiros de origem;
- folhas processadas;
- mapeamento de colunas detetado;
- avisos de qualidade dos dados;
- contagem de linhas ignoradas e respetivo motivo.

## Formatação

- Usar filtros nas tabelas.
- Congelar cabeçalhos.
- Formatar datas como datas reais.
- Formatar valores como moeda.
- Usar formatação condicional simples para destacar estados.
- Não eliminar nem substituir os ficheiros de origem.
