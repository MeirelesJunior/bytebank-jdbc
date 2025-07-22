# Projeto: Sistema Bancário com JDBC

Este projeto consiste em uma aplicação Java que simula operações bancárias utilizando JDBC para persistência de dados em um banco MySQL. O objetivo principal foi aplicar boas práticas de programação e organização de código, como separação de responsabilidades com DAOs, uso de pool de conexões com HikariCP e commit semântico no controle de versões.

## 📚 Tecnologias Utilizadas

- Java 17
- JDBC (Java Database Connectivity)
- MySQL
- HikariCP (Pool de Conexões)
- IntelliJ IDEA
- Git e GitHub

## 📂 Estrutura do Projeto

- `ConnectionFactory`: Classe responsável por criar conexões com o banco de dados.
- `ContaService`: Contém a lógica de regras de negócio, chamando métodos DAO.
- `ContaDAO`: Responsável pelas operações diretas com o banco (CRUD).
- `Main`: Ponto de entrada para testes das funcionalidades.

## ✅ Funcionalidades Implementadas

- Criar conta com dados do cliente
- Listar contas
- Buscar conta por número
- Sacar e depositar com atualização de saldo
- Exclusão lógica de conta (não deleta do banco, apenas marca como inativa)

## ⚙️ Regras de Negócio

- O saldo é iniciado com R$ 0,00 ao abrir a conta
- Não é possível excluir fisicamente uma conta (aplicada exclusão lógica)
- Utilização de `setAutoCommit(false)` para melhor controle de transações

## 💡 Boas Práticas Aplicadas

- Separação de responsabilidades (Service e DAO)
- Pool de conexões com HikariCP
- Commit semântico
- Uso de `PreparedStatement` para evitar SQL Injection
- Controle de transações com `try-with-resources` e `finally`

## 💾 Exemplo de Query Utilizada

```sql
SELECT * FROM conta WHERE numero = ?;
UPDATE conta SET saldo = saldo - ? WHERE numero = ?;
DELETE FROM conta WHERE numero = ?; -- Apenas em exclusão lógica
```

## 🚀 Como Executar

1. Configure seu banco de dados MySQL com a tabela `conta`
2. Altere as configurações de conexão no `ConnectionFactory`
3. Rode a classe `Main` ou crie seus próprios testes

## 🧠 Aprendizados

Durante o desenvolvimento, foram praticados conceitos como:
- Conexão manual com JDBC
- Refatoração para uso de HikariCP
- Separação de responsabilidades com DAO
- Criação de commits claros e profissionais
- Leitura e escrita no banco com segurança

## 🔗 Histórico de Commits Relevantes

- `feat: cria estrutura inicial do projeto JDBC`
- `feat: implementa ConnectionFactory e conexão manual`
- `refactor: extrai lógica de ContaService para ContaDAO`
- `feat: implementa métodos de listar e buscar contas`
- `refactor: substitui ConnectionFactory por HikariDataSource`
- `feat: adiciona funcionalidades de saque e depósito`
- `feat: implementa exclusão lógica e finaliza regras do sistema`
- `chore: finaliza funcionalidades com saque, depósito, exclusão lógica e estrutura JDBC`

---

Desenvolvido por Jorge Meireles 🚀