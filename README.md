<div align="center">

# Bank Reconciliation Agent

### Agente de IA para reconciliação bancária assistida no ChatGPT

[![ChatGPT](https://img.shields.io/badge/ChatGPT-Projeto-10A37F?logo=openai&logoColor=white)](https://chatgpt.com/)
[![Excel](https://img.shields.io/badge/Excel-Reconcilia%C3%A7%C3%A3o-217346?logo=microsoftexcel&logoColor=white)](#resultado)
[![IA](https://img.shields.io/badge/IA-Assisted-6C63FF)](#princ%C3%ADpio-essencial)
[![Validação](https://img.shields.io/badge/Valida%C3%A7%C3%A3o-Humana-2563EB)](#princ%C3%ADpio-essencial)

**Reconciliação bancária · Excel · Correspondência de movimentos · Exceções · Auditoria · Human-in-the-loop**

Desenvolvido por [Rui Ribeiro](https://github.com/ruialexrib)

</div>

---

## Sobre

Este repositório contém as instruções, recursos, skills, exemplos e testes necessários para configurar um **Projeto no ChatGPT** orientado à reconciliação bancária.

O objetivo é carregar dois ficheiros — um extrato bancário e um ficheiro de movimentos contabilísticos — e obter um novo ficheiro Excel com o resultado estruturado da reconciliação.

O projeto foi concebido para demonstração e apoio ao trabalho. Não altera sistemas contabilísticos nem efetua registos automáticos.

> A IA apoia a identificação de correspondências e exceções, mas os casos ambíguos devem permanecer identificados para validação humana.

---

## Objetivo

O agente procura transformar dois conjuntos de movimentos financeiros num resultado de reconciliação rastreável e auditável.

O processo inclui:

- leitura e interpretação dos ficheiros de origem;
- normalização de datas, montantes, referências e descrições;
- aplicação de regras de correspondência;
- análise de ambiguidades e exceções;
- validação da consistência do resultado;
- geração de um novo ficheiro Excel;
- preservação da rastreabilidade até às linhas originais.

---

## Fluxo

```text
Extrato bancário.xlsx
        +
Movimentos contabilísticos.xlsx
        │
        ▼
Identificar estrutura dos ficheiros
        │
        ▼
Normalizar datas, montantes,
referências e descrições
        │
        ▼
Aplicar regras de correspondência
        │
        ▼
Analisar ambiguidades e exceções
        │
        ▼
Validar resultado
        │
        ▼
Gerar Resultado_reconciliacao_bancaria.xlsx
```

---

## Resultado

O ficheiro produzido pelo agente deve separar claramente os diferentes estados da reconciliação.

| Área | Finalidade |
| --- | --- |
| Resumo | Síntese dos resultados da reconciliação |
| Reconciliados | Correspondências consideradas suficientemente robustas |
| Prováveis / a rever | Correspondências plausíveis que exigem validação |
| Apenas banco | Movimentos sem correspondência contabilística |
| Apenas contabilidade | Movimentos sem correspondência bancária |
| Duplicados potenciais | Situações que podem representar duplicação |
| Parâmetros e auditoria | Critérios utilizados e informação de rastreabilidade |

---

## Estrutura do repositório

```text
AGENTS.md                          Regras centrais do agente
INSTRUCOES_PROJETO_CHATGPT.md     Texto a usar nas instruções do Projeto ChatGPT

recursos/
├── regras-reconciliacao.md        Regras funcionais
├── formato-ficheiros.md           Como interpretar os dois ficheiros
├── formato-resultado.md           Estrutura do Excel final
└── parametros.md                  Tolerâncias e critérios configuráveis

skills/
├── roteador/SKILL.md              Decide que skills devem ser consultadas
├── leitura-excel/SKILL.md         Interpreta os ficheiros carregados
├── normalizacao/SKILL.md          Normaliza os movimentos
├── reconciliacao/SKILL.md         Executa a correspondência
├── analise-excecoes/SKILL.md      Analisa casos ambíguos
├── gerar-resultado/SKILL.md       Cria o novo ficheiro Excel
└── controlo-qualidade/SKILL.md    Verifica o resultado final

prompts/
└── reconciliar.md                 Prompt de utilização

exemplos/
├── extrato-bancario-exemplo.csv
├── movimentos-contabilidade-exemplo.csv
└── resultado-esperado.md

testes/
└── casos-teste.md
```

---

## Skills do agente

Cada skill tem uma responsabilidade específica dentro do processo de reconciliação.

| Skill | Responsabilidade |
| --- | --- |
| `roteador` | Determinar as skills necessárias para o pedido |
| `leitura-excel` | Interpretar os ficheiros carregados |
| `normalizacao` | Uniformizar os dados antes da comparação |
| `reconciliacao` | Aplicar as regras de correspondência |
| `analise-excecoes` | Tratar casos ambíguos e exceções |
| `gerar-resultado` | Produzir o ficheiro Excel final |
| `controlo-qualidade` | Validar a consistência e rastreabilidade do resultado |

---

## Configuração no ChatGPT

1. Criar um novo Projeto no ChatGPT.
2. Ligar o GitHub ao ChatGPT e autorizar o acesso ao repositório `ruialexrib/bank-reconciliation-agent`.
3. Copiar para as instruções do Projeto o conteúdo de `INSTRUCOES_PROJETO_CHATGPT.md`.
4. Carregar os dois ficheiros a reconciliar:
   - extrato bancário;
   - movimentos contabilísticos.
5. Pedir: **“Reconcilia estes dois ficheiros.”**
6. O resultado esperado é um novo ficheiro Excel, e não apenas uma resposta em texto.

O acesso ao GitHub é feito a pedido; o repositório não é automaticamente indexado apenas por o URL constar nas instruções.

---

## Princípio essencial

A IA pode ajudar a identificar correspondências e exceções, mas **não deve forçar uma reconciliação quando existem alternativas plausíveis**.

Quando a evidência é insuficiente ou existem múltiplas correspondências possíveis, o movimento deve permanecer classificado para revisão humana.

Este princípio procura garantir:

- transparência;
- rastreabilidade;
- auditabilidade;
- separação entre correspondências robustas e hipóteses;
- controlo humano sobre decisões ambíguas.

---

## Documentação principal

| Documento | Finalidade |
| --- | --- |
| [`AGENTS.md`](AGENTS.md) | Regras centrais e orientação do agente |
| [`INSTRUCOES_PROJETO_CHATGPT.md`](INSTRUCOES_PROJETO_CHATGPT.md) | Instruções para configurar o Projeto no ChatGPT |
| [`recursos/regras-reconciliacao.md`](recursos/regras-reconciliacao.md) | Regras funcionais da reconciliação |
| [`recursos/formato-ficheiros.md`](recursos/formato-ficheiros.md) | Estrutura e interpretação dos ficheiros |
| [`recursos/formato-resultado.md`](recursos/formato-resultado.md) | Estrutura do Excel final |
| [`recursos/parametros.md`](recursos/parametros.md) | Tolerâncias e critérios configuráveis |
| [`prompts/reconciliar.md`](prompts/reconciliar.md) | Prompt principal de utilização |
| [`testes/casos-teste.md`](testes/casos-teste.md) | Casos de teste do agente |
