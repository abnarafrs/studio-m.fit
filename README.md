# Studio M.fit - Sistema de Gestão

## 📌 Sobre o projeto
Sistema interno sendo desenvolvido para o **Studio M.fit**, com o objetivo de auxiliar no controle de alunos e na contabilidade do estúdio.

O sistema irá permitir:

- Cadastro de alunos
- Registro de pagamentos de mensalidade
- Controle de entradas e saídas financeiras
- Identificação automática de alunos inadimplentes
- Visualização de saldo financeiro

---

# ⚙️ Funcionalidades

## 👤 Gestão de alunos
- Cadastro de alunos
- Editar informações
- Visualizar status de pagamento

## 💰 Controle financeiro
- Registrar entradas (mensalidades)
- Registrar saídas (despesas)
- Visualizar histórico financeiro

## 📊 Dashboard
- Saldo atual
- Total de entradas
- Total de saídas
- Total de alunos
- Total de alunos inadimplentes

---

# 👤 Fluxo de cadastro de aluno

```mermaid
flowchart TD
A[Usuário acessa página Alunos] --> B[Clica em cadastrar aluno]
B --> C[Preenche os dados]
C --> D[Salvar aluno]
D --> E[Aluno aparece na lista]
```
# 🧠 Estados do pagamento do aluno

```mermaid
stateDiagram-v2
[*] --> SemPagamento

SemPagamento --> EmDia : Pagamento registrado
EmDia --> EmDia : Novo Pagamento
EmDia --> Atrasado : Prazo maior de 30 dias
Atrasado --> EmDia : Pagamento realizado
Atrasado --> Inativo : Aluno cancelado
```

# 🗂️ Modelo de dados do sistema

```mermaid
erDiagram

ALUNO {
  int id
  string nome
  string telefone
  string plano
  date dataInicio
}

PAGAMENTO {
  int id
  int alunoid
  float valor
  date dataPagemento
}

MOVIMENTACAO {
  int id
  string tipo
  float valor
  date data
}

ALUNO ||--o{ PAGAMENTO : faz
PAGAMENTO ||--|| MOVIMENTACAO : gera
```
