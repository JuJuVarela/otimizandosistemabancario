# Sistema Bancário Simplificado (Otimizado)

Este repositório contém um arquivo Python (`desafio_otimizando.py`) que implementa um **sistema bancário simples** com operações de depósito, saque, extrato, criação de usuário e criação/listagem de contas. O código é estruturado de forma modular, utilizando **funções** para cada operação, o que facilita a organização e manutenção.

---

## Visão Geral do Sistema

O sistema simula funcionalidades básicas de uma conta bancária:

1.  **Usuários (Clientes):** Podem ser criados com informações como CPF, nome, data de nascimento e endereço.
2.  **Contas Correntes:** Associadas a um único usuário (titular), possuem um número de agência fixo (`0001`) e um número sequencial.
3.  **Operações:**
    * **Depósito (`d`):** Aumenta o saldo.
    * **Saque (`s`):** Diminui o saldo, respeitando um limite diário de valor (`R$ 500.00`) e um limite de quantidade de saques por dia (`3`).
    * **Extrato (`e`):** Mostra o saldo atual e o histórico de transações.
4.  **Estruturas de Dados:** Listas e dicionários são usados para armazenar usuários e contas.

---

## Estrutura do Código e Funções

O código é dividido em funções para organizar as responsabilidades.

### 1. Funções de Interface e Menu

| Função | Descrição |
| :--- | :--- |
| `menu()` | Exibe o menu principal de opções e captura a escolha do usuário. |

### 2. Funções de Operações Financeiras

| Função | Parâmetros | Descrição |
| :--- | :--- | :--- |
| `depositar(saldo, valor, extrato, /)` | **Posicionais (`/`):** `saldo`, `valor`, `extrato`. | Realiza um depósito. Adiciona o `valor` ao `saldo` e registra a transação no `extrato`. |
| `sacar(*, saldo, valor, extrato, limite, numero_saques, limite_saques)` | **Nomeados (`*`):** Todos. | Realiza um saque. Verifica se o `valor` não excede o `saldo`, o `limite` por saque e o `limite_saques` diário. Atualiza `saldo` e `extrato`. |
| `exibir_extrato(saldo, /, *, extrato)` | **Posicional (`/`):** `saldo`. **Nomeado (`*`):** `extrato`. | Imprime o histórico de movimentações (`extrato`) e o `saldo` atual. |

> **Observação sobre Parâmetros:** As funções financeiras utilizam *keyword-only* (`*`) e *positional-only* (`/`) arguments para impor um formato de chamada específico, garantindo clareza na manipulação de dados.

### 3. Funções de Usuário e Conta

| Função | Parâmetros | Descrição |
| :--- | :--- | :--- |
| `criar_usuario(usuarios)` | `usuarios` | Solicita dados e cadastra um novo usuário na lista `usuarios`, verificando se o **CPF** já existe. |
| `filtrar_usuario(cpf, usuarios)` | `cpf`, `usuarios` | Busca um usuário na lista `usuarios` com base no `cpf` informado. Retorna o objeto usuário ou `None`. |
| `criar_conta(agencia, numero_conta, usuarios)` | `agencia`, `numero_conta`, `usuarios` | Cria uma nova conta, solicitando o CPF para vincular a um usuário existente (utiliza `filtrar_usuario`). Retorna um dicionário com os dados da conta. |
| `listar_contas(contas)` | `contas` | Percorre a lista de `contas` e imprime os detalhes de cada uma (Agência, C/C, Titular). |

### 4. Função Principal

| Função | Descrição |
| :--- | :--- |
| `main()` | É o ponto de entrada e o *loop* principal do sistema. Inicializa as variáveis de estado (`saldo`, `extrato`, `usuarios`, `contas`, etc.) e gerencia as chamadas às funções de acordo com a opção escolhida no `menu()`. |

---

## Execução

Para rodar o programa, basta executar o arquivo Python:

```bash
python desafio_otimizando.py
