# Parâmetros de reconciliação

Estes são os parâmetros padrão. Podem ser alterados pelo utilizador nas instruções da tarefa.

| Parâmetro | Valor padrão |
|---|---:|
| Tolerância de diferença de data para matching automático | ±3 dias |
| Tolerância monetária | 0,01 € |
| Máximo de movimentos numa correspondência agregada automática | 3 |
| Correspondência exata de montante | obrigatória para RECONCILIADO, salvo agrupamentos |
| Referência idêntica | evidência forte |
| Descrição semelhante | evidência complementar, nunca suficiente isoladamente |

## Princípios

1. O montante deve ser comparado depois de normalizado o sinal.
2. A diferença de datas é calculada em dias de calendário.
3. Descrições são normalizadas para comparação, mas a descrição original é sempre preservada.
4. Referências/documentos têm maior peso do que texto genérico.
5. Uma correspondência 1:N ou N:1 é permitida apenas quando a soma dos montantes coincide dentro da tolerância.
6. Correspondências agregadas com múltiplas combinações plausíveis devem ser marcadas `REVER`.
7. Não efetuar matching automático N:N.
