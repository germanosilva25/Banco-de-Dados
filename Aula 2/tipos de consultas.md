SQL (Structured Query Language) é uma linguagem usada para gerenciar e manipular bancos de dados relacionais. Dentro do SQL, há diferentes subgrupos de comandos categorizados como DML, DDL, DCL e TCL. Cada uma dessas categorias serve a propósitos específicos na interação com o banco de dados. Aqui está uma explicação detalhada:

### 1. **DML (Data Manipulation Language) - Linguagem de Manipulação de Dados**
   - **Objetivo**: Manipulação dos dados dentro das tabelas.
   - **Principais Comandos**:
     - **`SELECT`**: Recupera dados de uma ou mais tabelas.
     - **`INSERT`**: Insere novos registros em uma tabela.
     - **`UPDATE`**: Atualiza registros existentes em uma tabela.
     - **`DELETE`**: Remove registros de uma tabela.
   - **Exemplo**:
     ```sql
     INSERT INTO clientes (nome, idade) VALUES ('João', 25);
     ```

### 2. **DDL (Data Definition Language) - Linguagem de Definição de Dados**
   - **Objetivo**: Definição e modificação da estrutura dos objetos de banco de dados, como tabelas, índices, e esquemas.
   - **Principais Comandos**:
     - **`CREATE`**: Cria novos objetos de banco de dados, como tabelas, índices, ou visões.
     - **`ALTER`**: Modifica a estrutura de objetos existentes, como adicionar ou remover colunas em uma tabela.
     - **`DROP`**: Remove objetos de banco de dados, como tabelas ou visões.
     - **`TRUNCATE`**: Remove todos os registros de uma tabela, mas mantém a estrutura da tabela.
   - **Exemplo**:
     ```sql
     CREATE TABLE produtos (
         id INT PRIMARY KEY,
         nome VARCHAR(50),
         preco DECIMAL(10, 2)
     );
     ```

### 3. **DCL (Data Control Language) - Linguagem de Controle de Dados**
   - **Objetivo**: Controle de permissões e acesso aos dados.
   - **Principais Comandos**:
     - **`GRANT`**: Concede permissões a usuários ou grupos para realizar ações no banco de dados.
     - **`REVOKE`**: Remove permissões previamente concedidas.
   - **Exemplo**:
     ```sql
     GRANT SELECT, INSERT ON produtos TO usuario1;
     ```

### 4. **TCL (Transaction Control Language) - Linguagem de Controle de Transações**
   - **Objetivo**: Gerenciamento de transações dentro do banco de dados, garantindo que operações múltiplas possam ser tratadas como uma unidade única de trabalho.
   - **Principais Comandos**:
     - **`COMMIT`**: Finaliza uma transação, salvando todas as mudanças feitas no banco de dados.
     - **`ROLLBACK`**: Reverte as mudanças feitas durante uma transação, retornando o banco de dados ao estado anterior.
     - **`SAVEPOINT`**: Define um ponto dentro de uma transação ao qual pode ser feito um rollback parcial.
     - **`SET TRANSACTION`**: Define as características de uma transação, como o nível de isolamento.
   - **Exemplo**:
     ```sql
     BEGIN TRANSACTION;
     INSERT INTO vendas (produto_id, quantidade) VALUES (1, 10);
     COMMIT;
     ```

### Resumo:
- **DML** é usado para **manipular dados**.
- **DDL** é usado para **definir a estrutura** do banco de dados.
- **DCL** é usado para **controlar o acesso** aos dados.
- **TCL** é usado para **gerenciar transações**.

Cada um desses conjuntos de comandos desempenha um papel vital na administração e operação de bancos de dados relacionais.