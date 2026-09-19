# Agente de Reconciliação Bancária com ChatGPT

Este repositório contém as instruções, recursos, skills, exemplos e testes necessários para configurar um **Projeto no ChatGPT** orientado à reconciliação bancária.

O objetivo é simples:

> carregar dois ficheiros Excel — um extrato bancário e um ficheiro de movimentos contabilísticos — e obter um novo ficheiro Excel com o resultado da reconciliação.

O projeto foi pensado para demonstração e apoio ao trabalho. Não altera sistemas contabilísticos nem efetua registos automáticos.

## Fluxo

```text
Extrato bancário.xlsx
        +
Movimentos contabilísticos.xlsx
        ↓
Identificar estrutura dos ficheiros
        ↓
Normalizar datas, montantes, referências e descrições
        ↓
Aplicar regras de correspondência
        ↓
Analisar ambiguidades
        ↓
Validar resultado
        ↓
Gerar Resultado_reconciliacao.xlsx
```

## Estrutura do repositório

```text
AGENTS.md                         Regras centrais do agente
INSTRUCOES_PROJETO_CHATGPT.md     Texto a usar nas instruções do Projeto ChatGPT

resources/
  regras-reconciliacao.md         Regras funcionais
  formato-ficheiros.md            Como interpretar os dois ficheiros
  formato-resultado.md            Estrutura do Excel final
  parametros.md                   Tolerâncias e critérios configuráveis

skills/
  roteador/SKILL.md               Decide que skills devem ser consultadas
  leitura-excel/SKILL.md          Interpreta os ficheiros carregados
  normalizacao/SKILL.md           Normaliza os movimentos
  reconciliacao/SKILL.md          Executa o matching
  analise-excecoes/SKILL.md       Analisa casos ambíguos
  gerar-resultado/SKILL.md        Cria o novo ficheiro Excel
  controlo-qualidade/SKILL.md     Verifica o resultado final

prompts/
  reconciliar.md                  Prompt de utilização

examples/
  extrato-bancario-exemplo.csv
  movimentos-contabilidade-exemplo.csv
  resultado-esperado.md

tests/
  casos-teste.md
```

## Configuração no ChatGPT

1. Criar um novo Projeto no ChatGPT.
2. Copiar para as instruções do Projeto o conteúdo de `INSTRUCOES_PROJETO_CHATGPT.md`.
3. Garantir que o Projeto pode consultar este repositório público:
   `https://github.com/ruialexrib/ncrf-accounting-agent`
4. Carregar dois ficheiros Excel:
   - extrato bancário;
   - movimentos contabilísticos.
5. Pedir: **“Reconcilia estes dois ficheiros.”**
6. O resultado esperado é um novo ficheiro Excel, não apenas uma resposta em texto.

## Princípio essencial

A IA pode ajudar a identificar correspondências e exceções, mas **não deve forçar uma reconciliação quando existem alternativas plausíveis**. Os casos ambíguos devem ficar marcados para validação humana.
