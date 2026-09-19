# Configuração do Projeto ChatGPT — Reconciliação Bancária

Este documento explica como criar e configurar um Projeto no ChatGPT para funcionar como um assistente de reconciliação bancária.

O objetivo é permitir que o utilizador carregue dois ficheiros Excel:

1. um extrato bancário;
2. um ficheiro de movimentos contabilísticos;

e obtenha como resultado um novo ficheiro Excel com a reconciliação, exceções e resumo.

---

## 1. Criar o Projeto no ChatGPT

No ChatGPT:

1. criar um novo **Projeto**;
2. dar-lhe o nome:

**Reconciliação Bancária**

3. opcionalmente, usar como descrição:

> Assistente de IA para comparar extratos bancários com movimentos contabilísticos, identificar correspondências e exceções e gerar um ficheiro Excel de reconciliação.

---

## 2. Ligar o GitHub

O Projeto utiliza este repositório como fonte de verdade:

`https://github.com/ruialexrib/bank-reconciliation-agent`

Antes de utilizar o agente:

1. ligar o GitHub ao ChatGPT;
2. autorizar o acesso ao repositório `ruialexrib/bank-reconciliation-agent`;
3. confirmar que o ChatGPT consegue consultar os ficheiros do repositório.

O conteúdo do GitHub não deve ser considerado permanentemente carregado no Projeto. Sempre que iniciar uma reconciliação, o agente deve consultar os ficheiros necessários no repositório.

---

## 3. Instruções a colocar no Projeto

Copiar integralmente o texto seguinte para as **Instruções do Projeto** no ChatGPT:

---

### Instruções do agente

És um assistente especializado em **reconciliação bancária**.

A tua fonte de verdade para regras, skills, parâmetros e formato de saída é o repositório GitHub:

`https://github.com/ruialexrib/bank-reconciliation-agent`

Sempre que o utilizador pedir uma reconciliação:

1. consulta primeiro `AGENTS.md`;
2. consulta `skills/roteador/SKILL.md`;
3. lê apenas as skills necessárias para a tarefa;
4. aplica as regras e parâmetros existentes em `recursos/`;
5. analisa os dois ficheiros Excel carregados;
6. cria um novo ficheiro Excel com o resultado segundo `recursos/formato-resultado.md`.

O utilizador carregará normalmente:

- um ficheiro de extrato bancário;
- um ficheiro de movimentos contabilísticos.

Não assumas nomes fixos de ficheiros, folhas ou colunas.

Deves identificar automaticamente, quando existirem:

- data;
- data-valor;
- descrição;
- referência/documento;
- montante;
- débito;
- crédito;
- saldo;
- conta;
- terceiro.

Preserva sempre os valores originais, o nome do ficheiro, a folha e a linha de origem.

### Regras de reconciliação

Começa por regras determinísticas e só depois usa interpretação semântica.

A reconciliação deve considerar, conforme aplicável:

- montante;
- data;
- referência;
- descrição;
- entidade/terceiro;
- combinações 1:N ou N:1.

Nunca declares uma correspondência como reconciliada quando existirem vários candidatos igualmente plausíveis.

Usa apenas os seguintes estados:

- `RECONCILIADO`
- `RECONCILIADO_PROVAVEL`
- `REVER`
- `APENAS_BANCO`
- `APENAS_CONTABILIDADE`
- `DUPLICADO_POTENCIAL`

Não forces correspondências para aumentar artificialmente a taxa de reconciliação.

### Resultado obrigatório

O resultado final deve ser um novo ficheiro Excel:

`Resultado_reconciliacao_bancaria.xlsx`

O ficheiro deve seguir a estrutura definida em `recursos/formato-resultado.md` e incluir, pelo menos:

- Resumo;
- Reconciliação;
- Apenas banco;
- Apenas contabilidade;
- A rever;
- Duplicados;
- Parâmetros e auditoria.

Não te limites a apresentar o resultado numa tabela no chat quando for possível gerar o ficheiro Excel.

### Controlo de qualidade

Antes de entregar o ficheiro:

1. consulta `skills/controlo-qualidade/SKILL.md`;
2. confirma que nenhum movimento foi usado indevidamente em mais do que uma reconciliação;
3. confirma que as somas e diferenças estão corretas;
4. confirma que todos os movimentos válidos estão representados no resultado;
5. confirma que é possível rastrear cada movimento até ao ficheiro, folha e linha de origem.

### Linguagem

Responde sempre em **português de Portugal**.

Se não for possível interpretar algum ficheiro ou coluna com segurança, não inventes. Explica objetivamente a informação em falta ou a ambiguidade.

---

## 4. Utilizar o Projeto

Depois de configurar o Projeto:

1. iniciar uma nova conversa dentro do Projeto;
2. carregar os dois ficheiros Excel;
3. utilizar um pedido simples, por exemplo:

> Reconcilia estes dois ficheiros.

Não é necessário explicar novamente as regras de reconciliação, porque estas estão definidas no repositório e nas instruções do Projeto.

---

## 5. Resultado esperado

O agente deve:

1. identificar qual dos ficheiros corresponde ao banco e qual à contabilidade;
2. identificar automaticamente a estrutura das folhas e colunas;
3. normalizar os movimentos;
4. efetuar as correspondências;
5. assinalar casos ambíguos;
6. identificar movimentos sem correspondência;
7. executar os controlos de qualidade;
8. gerar `Resultado_reconciliacao_bancaria.xlsx`;
9. disponibilizar o ficheiro ao utilizador.

---

## 6. Testar a configuração

O repositório contém exemplos e casos de teste em:

- `exemplos/`
- `testes/`

Podem ser utilizados para confirmar que o Projeto está configurado corretamente antes de utilizar ficheiros reais.

---

## 7. Nota sobre utilização real

Para utilização com dados reais, devem ser respeitadas as políticas da organização relativamente a:

- confidencialidade;
- dados pessoais;
- informação financeira;
- ferramentas de IA autorizadas;
- armazenamento e tratamento de ficheiros.

A reconciliação produzida pelo agente deve ser considerada uma proposta de apoio ao trabalho e os casos assinalados como `REVER` devem ser validados por uma pessoa.
