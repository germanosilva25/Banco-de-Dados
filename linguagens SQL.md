Vamos explorar em detalhe cada uma das linguagens SQL com exemplos de queries e explicações gráficas:

### 1. **DDL (Data Definition Language) - Linguagem de Definição de Dados**

**Objetivo:** Usada para definir, alterar, e remover a estrutura de objetos no banco de dados, como tabelas, índices, e esquemas.

#### Principais Comandos e Exemplos:

- **`CREATE TABLE`**: Cria uma nova tabela no banco de dados.
  
  ```sql
  CREATE TABLE clientes (
      id_cliente INT PRIMARY KEY,
      nome VARCHAR(100),
      email VARCHAR(100),
      data_registro DATE
  );
  ```
  **Explicação**: Este comando cria uma tabela chamada `clientes` com quatro colunas: `id_cliente`, `nome`, `email`, e `data_registro`.

  **Gráfico**:
  - Imagem mostrando uma tabela vazia chamada `clientes` com as colunas acima.

- **`ALTER TABLE`**: Modifica a estrutura de uma tabela existente.
  
  ```sql
  ALTER TABLE clientes ADD telefone VARCHAR(15);
  ```
  **Explicação**: Este comando adiciona uma nova coluna `telefone` à tabela `clientes`.

  **Gráfico**:
  - Imagem mostrando a tabela `clientes` antes e depois de adicionar a coluna `telefone`.

- **`DROP TABLE`**: Remove uma tabela do banco de dados.
  
  ```sql
  DROP TABLE clientes;
  ```
  **Explicação**: Este comando remove completamente a tabela `clientes` e todos os seus dados.

  **Gráfico**:
  - Imagem mostrando a tabela `clientes` sendo removida.

- **`TRUNCATE TABLE`**: Remove todos os registros de uma tabela, mas mantém a estrutura da tabela intacta.
  
  ```sql
  TRUNCATE TABLE clientes;
  ```
  **Explicação**: Este comando remove todos os dados da tabela `clientes`, mas mantém a tabela e sua estrutura.

  **Gráfico**:
  - Imagem mostrando a tabela `clientes` antes e depois do `TRUNCATE`, onde os dados desaparecem, mas as colunas permanecem.

### 2. **DML (Data Manipulation Language) - Linguagem de Manipulação de Dados**

**Objetivo:** Usada para consultar e modificar os dados armazenados no banco de dados.

#### Principais Comandos e Exemplos:

- **`SELECT`**: Consulta e recupera dados do banco de dados.
  
  ```sql
  SELECT nome, email FROM clientes WHERE data_registro > '2023-01-01';
  ```
  **Explicação**: Este comando seleciona os campos `nome` e `email` de todos os clientes que foram registrados após 1º de janeiro de 2023.

  **Gráfico**:
  - Imagem mostrando uma tabela com os dados filtrados e as colunas `nome` e `email` destacadas.

- **`INSERT`**: Insere novos registros em uma tabela.
  
  ```sql
  INSERT INTO clientes (id_cliente, nome, email, data_registro) VALUES (1, 'João Silva', 'joao@exemplo.com', '2023-06-15');
  ```
  **Explicação**: Este comando insere um novo registro na tabela `clientes` com os valores fornecidos.

  **Gráfico**:
  - Imagem mostrando a tabela `clientes` antes e depois de adicionar a nova linha.

- **`UPDATE`**: Atualiza registros existentes em uma tabela.
  
  ```sql
  UPDATE clientes SET email = 'joao_silva@exemplo.com' WHERE id_cliente = 1;
  ```
  **Explicação**: Este comando atualiza o campo `email` do cliente com `id_cliente` igual a 1.

  **Gráfico**:
  - Imagem mostrando a tabela `clientes` antes e depois da atualização do e-mail.

- **`DELETE`**: Remove registros de uma tabela.
  
  ```sql
  DELETE FROM clientes WHERE id_cliente = 1;
  ```
  **Explicação**: Este comando remove o registro do cliente com `id_cliente` igual a 1.

  **Gráfico**:
  - Imagem mostrando a tabela `clientes` antes e depois da remoção da linha.

### 3. **DCL (Data Control Language) - Linguagem de Controle de Dados**

**Objetivo:** Usada para controlar o acesso aos dados no banco de dados.

#### Principais Comandos e Exemplos:

- **`GRANT`**: Concede permissões a usuários para realizar operações específicas.
  
  ```sql
  GRANT SELECT, INSERT ON clientes TO usuario1;
  ```
  **Explicação**: Este comando concede ao `usuario1` as permissões de `SELECT` e `INSERT` na tabela `clientes`.

  **Gráfico**:
  - Diagrama mostrando o usuário `usuario1` recebendo as permissões.

- **`REVOKE`**: Revoga permissões concedidas anteriormente a usuários.
  
  ```sql
  REVOKE INSERT ON clientes FROM usuario1;
  ```
  **Explicação**: Este comando revoga a permissão de `INSERT` na tabela `clientes` do `usuario1`.

  **Gráfico**:
  - Diagrama mostrando a permissão de `INSERT` sendo removida do `usuario1`.

### 4. **TCL (Transaction Control Language) - Linguagem de Controle de Transações**

**Objetivo:** Usada para gerenciar transações no banco de dados, garantindo que elas sejam executadas de maneira consistente.

#### Principais Comandos e Exemplos:

- **`COMMIT`**: Confirma uma transação, salvando todas as alterações feitas.
  
  ```sql
  BEGIN;
  UPDATE clientes SET email = 'novo_email@exemplo.com' WHERE id_cliente = 1;
  COMMIT;
  ```
  **Explicação**: Este comando inicia uma transação, atualiza o e-mail do cliente com `id_cliente` igual a 1, e depois confirma a transação com `COMMIT`, salvando a alteração.

  **Gráfico**:
  - Diagrama mostrando as alterações sendo salvas permanentemente após o `COMMIT`.

- **`ROLLBACK`**: Reverte uma transação, desfezendo todas as alterações desde o último `COMMIT`.
  
  ```sql
  BEGIN;
  UPDATE clientes SET email = 'email_errado@exemplo.com' WHERE id_cliente = 1;
  ROLLBACK;
  ```
  **Explicação**: Este comando inicia uma transação, faz uma atualização errada e depois reverte a transação com `ROLLBACK`, desfazendo a alteração.

  **Gráfico**:
  - Diagrama mostrando a atualização sendo revertida.

- **`SAVEPOINT`**: Define um ponto de salvamento dentro de uma transação para que uma parte da transação possa ser revertida, sem reverter a transação inteira.
  
  ```sql
  BEGIN;
  UPDATE clientes SET email = 'email_inicial@exemplo.com' WHERE id_cliente = 1;
  SAVEPOINT ponto1;
  UPDATE clientes SET email = 'email_final@exemplo.com' WHERE id_cliente = 1;
  ROLLBACK TO ponto1;
  COMMIT;
  ```
  **Explicação**: Este comando inicia uma transação, atualiza o e-mail, define um ponto de salvamento `ponto1`, faz outra atualização e, em seguida, reverte para `ponto1`, descartando a última atualização.

  **Gráfico**:
  - Diagrama mostrando a transação sendo parcialmente revertida.

### 5. **DQL (Data Query Language) - Linguagem de Consulta de Dados**

**Objetivo:** Usada especificamente para consultar dados no banco de dados.

#### Principais Comandos e Exemplos:

- **`SELECT`**: O principal comando para recuperar dados do banco de dados, com possibilidade de uso de cláusulas como `WHERE`, `GROUP BY`, `ORDER BY`, etc.
  
  ```sql
  SELECT nome, email FROM clientes WHERE uf = 'SP' ORDER BY nome ASC;
  ```
  **Explicação**: Este comando seleciona os campos `nome` e `email` dos clientes que estão no estado de São Paulo (`uf = 'SP'`), ordenados alfabeticamente pelo nome.

  **Gráfico**:
  - Imagem mostrando uma tabela filtrada e ordenada conforme a query.

### Resumo Gráfico Geral:
- Uma representação visual de como cada comando afeta os dados ou a estrutura do banco de dados.
- Tabelas antes e depois de cada operação.
- Diagrama de transações mostrando como `COMMIT`, `ROLLBACK`, e `SAVEPOINT` funcionam em sequência.

Essas linguagens formam a base de como interagir e manipular dados em sistemas de gerenciamento de banco de dados, e entender cada uma delas é fundamental para trabalhar efetivamente com SQL.