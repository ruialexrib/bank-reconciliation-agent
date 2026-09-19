# Interpretação dos ficheiros de entrada

## Princípio

Os ficheiros Excel podem ter estruturas diferentes. Não exigir nomes fixos de folhas ou colunas.

## Ficheiro bancário

Identificar, quando existirem:
- data do movimento;
- data-valor;
- descrição;
- referência;
- débito;
- crédito;
- montante com sinal;
- saldo.

O saldo pode ajudar na validação do ficheiro, mas **não é usado como movimento a reconciliar**.

### Normalização do montante bancário

Representar internamente:
- entradas no banco: valor positivo;
- saídas do banco: valor negativo.

Se existirem colunas Débito e Crédito separadas, convertê-las num único montante normalizado.

## Ficheiro contabilístico

Identificar, quando existirem:
- data;
- data do documento;
- número/referência do documento;
- descrição;
- conta;
- entidade/terceiro;
- débito;
- crédito;
- montante.

O agente deve determinar, a partir da estrutura e contexto, o sinal equivalente ao movimento bancário.

Quando o ficheiro contabilístico apresentar débitos/créditos de várias contas do mesmo lançamento, deve evitar tratar cada linha como pagamento independente sem verificar se existe uma conta de banco/tesouraria ou outra lógica que permita isolar o movimento financeiro.

## Folhas

Se existirem várias folhas:
1. identificar folhas com dados tabulares relevantes;
2. ignorar folhas manifestamente auxiliares, capas ou instruções;
3. registar no resultado a folha e linha de origem.

## Validação inicial

Antes da reconciliação:
- confirmar que as datas são interpretáveis;
- confirmar que os valores são numéricos;
- detetar linhas de totais/subtotais;
- detetar linhas em branco;
- não reconciliar linhas de cabeçalho, saldo inicial/final ou totalizadores.
