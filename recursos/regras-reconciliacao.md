# Regras de reconciliação

## 1. Preparação

Criar para cada movimento:
- identificador interno;
- ficheiro de origem;
- folha;
- linha;
- data normalizada;
- montante normalizado;
- descrição original;
- descrição normalizada;
- referência original;
- referência normalizada.

## 2. Ordem de correspondência

Aplicar pela seguinte ordem.

### Regra A — Correspondência forte

Marcar `RECONCILIADO` quando:
- montante coincide dentro da tolerância;
- data está dentro da tolerância;
- referência/documento coincide de forma inequívoca;
- existe apenas um candidato plausível.

### Regra B — Montante + descrição forte

Pode marcar `RECONCILIADO` quando:
- montante coincide;
- data está dentro da tolerância;
- descrição/entidade apresenta correspondência forte e específica;
- não existem candidatos concorrentes plausíveis.

### Regra C — Correspondência provável

Marcar `RECONCILIADO_PROVAVEL` quando:
- montante coincide;
- data está dentro da tolerância ou existe uma explicação temporal plausível;
- referência está ausente ou parcialmente divergente;
- descrição é suficientemente semelhante;
- existe um candidato claramente mais plausível, mas a evidência não permite classificação forte.

### Regra D — Agregação 1:N ou N:1

Procurar combinações até ao limite definido em `recursos/parametros.md`.

Uma combinação pode ser marcada `RECONCILIADO_PROVAVEL` se:
- a soma coincide dentro da tolerância monetária;
- datas são compatíveis;
- descrições/referências suportam a relação;
- não existe outra combinação de plausibilidade semelhante.

Se houver múltiplas combinações possíveis, marcar `REVER`.

### Regra E — Ambiguidade

Marcar `REVER` quando:
- existem dois ou mais candidatos equivalentes;
- o montante coincide mas a relação semântica é fraca;
- existe diferença superior às tolerâncias, mas alguns indícios sugerem relação;
- a agregação é plausível mas não inequívoca.

### Regra F — Sem correspondência

Depois de esgotadas as regras:
- movimento bancário sem candidato: `APENAS_BANCO`;
- movimento contabilístico sem candidato: `APENAS_CONTABILIDADE`.

### Regra G — Duplicados

Marcar `DUPLICADO_POTENCIAL` quando existirem movimentos muito semelhantes no mesmo conjunto de origem e a duplicação puder explicar a reconciliação ou a exceção.

## 3. Informação semântica

A IA pode interpretar abreviaturas e descrições, por exemplo:
- `TRF` ↔ transferência;
- `PGTO` ↔ pagamento;
- nomes abreviados de fornecedores;
- referências incorporadas em textos maiores.

A interpretação semântica **não substitui** a comparação de montantes e a análise de candidatos concorrentes.

## 4. Rastreabilidade

Cada reconciliação deve indicar:
- regra utilizada;
- diferença de dias;
- diferença de valor;
- evidência textual/referência;
- nível de confiança;
- identificadores dos movimentos associados.
