### Apostila de Banco de Dados MySQL

---

## Fundamentos Básicos

### Evolução Histórica de Banco de Dados
A evolução dos bancos de dados pode ser dividida em várias fases:
1. **Arquivos em Papel**: Armazenamento manual de dados.
2. **Sistemas de Arquivos**: Uso de arquivos digitais para armazenamento de dados.
3. **Bancos de Dados Hierárquicos**: Estrutura de dados em forma de árvore.
4. **Bancos de Dados em Rede**: Modelos mais flexíveis, permitindo relações mais complexas.
5. **Bancos de Dados Relacionais**: Baseados no modelo de tabelas, propostos por Edgar F. Codd.
6. **Bancos de Dados Orientados a Objetos**: Integração de conceitos de POO.
7. **Bancos de Dados NoSQL**: Projetados para lidar com grandes volumes de dados não estruturados e semi-estruturados.

### Conceito de Banco de Dados e Sistema Gerenciador de Banco de Dados (SGBD)
- **Banco de Dados**: Conjunto organizado de dados armazenados e acessíveis eletronicamente.
- **SGBD**: Software que permite a criação, manipulação e administração de bancos de dados. Exemplos incluem MySQL, PostgreSQL, Oracle, SQL Server.

### Arquitetura Cliente-Servidor
- **Cliente**: Envia solicitações de dados ao servidor.
- **Servidor**: Processa as solicitações e envia as respostas de volta ao cliente.
- **Comunicação**: Realizada através de protocolos como TCP/IP.

---

## Modelo Entidade-Relacionamento

### Entidade
- **Entidade**: Objeto ou coisa no mundo real que é distinguível dos outros objetos.
- **Exemplo**: Aluno, Curso, Professor.

### Atributos
- **Atributo**: Propriedade ou característica de uma entidade.
- **Exemplo**: Nome, Idade, Matrícula.

### Relacionamentos
- **Relacionamento**: Associação entre duas ou mais entidades.
- **Exemplo**: Um aluno se matricula em um curso.

### Generalização
- **Generalização**: Processo de abstrair características comuns de várias entidades para criar uma entidade geral.
- **Exemplo**: Pessoa (generalização de Aluno e Professor).

### Diagrama Entidade-Relacionamento (DER)
- **DER**: Representação gráfica das entidades, atributos e relacionamentos de um banco de dados.
- **Componentes do DER**: Entidades (retângulos), atributos (elipses), relacionamentos (losangos), linhas conectando os componentes.

---

## Modelo Relacional

### Conceitos
- **Relações**: Tabelas no modelo relacional.
- **Atributos**: Colunas das tabelas.
- **Tuplas**: Linhas das tabelas.
- **Chave Primária**: Identificador único para cada tupla.
- **Chave Estrangeira**: Atributo que cria uma relação entre duas tabelas.

### Restrições de Integridade
- **Integridade de Entidade**: Nenhuma tupla pode ter um valor nulo em uma chave primária.
- **Integridade Referencial**: Valores de chave estrangeira devem corresponder a valores de chave primária em outra tabela.

---

## Linguagem de Definição e Manipulação de Dados

### Comandos DDL (Data Definition Language)
Utilizados para definir e gerenciar estruturas de banco de dados.
- **CREATE**: Cria novas tabelas, esquemas, índices.
  ```sql
  CREATE TABLE Alunos (
      id INT AUTO_INCREMENT,
      nome VARCHAR(100),
      idade INT,
      PRIMARY KEY (id)
  );
  ```
- **ALTER**: Modifica estruturas existentes.
  ```sql
  ALTER TABLE Alunos ADD email VARCHAR(100);
  ```
- **DROP**: Remove estruturas do banco de dados.
  ```sql
  DROP TABLE Alunos;
  ```

### Comandos DML (Data Manipulation Language)
Utilizados para manipular os dados no banco de dados.
- **INSERT**: Insere novas tuplas.
  ```sql
  INSERT INTO Alunos (nome, idade) VALUES ('João', 22);
  ```
- **SELECT**: Consulta dados.
  ```sql
  SELECT * FROM Alunos;
  ```
- **UPDATE**: Atualiza dados existentes.
  ```sql
  UPDATE Alunos SET idade = 23 WHERE nome = 'João';
  ```
- **DELETE**: Exclui dados.
  ```sql
  DELETE FROM Alunos WHERE nome = 'João';
  ```

### Consultas Básicas
- **Selecionar todos os dados de uma tabela**:
  ```sql
  SELECT * FROM Alunos;
  ```
- **Selecionar dados específicos com condição**:
  ```sql
  SELECT nome FROM Alunos WHERE idade > 20;
  ```

### Consultas Avançadas
- **Join entre tabelas**:
  ```sql
  SELECT Alunos.nome, Cursos.nome
  FROM Alunos
  JOIN Matriculas ON Alunos.id = Matriculas.aluno_id
  JOIN Cursos ON Matriculas.curso_id = Cursos.id;
  ```
- **Subconsultas**:
  ```sql
  SELECT nome FROM Alunos WHERE idade = (SELECT MAX(idade) FROM Alunos);
  ```

---

## Introdução a Banco de Dados NoSQL
- **Conceito**: Bancos de dados NoSQL são projetados para armazenar e gerenciar grandes volumes de dados não estruturados ou semi-estruturados.
- **Tipos de Bancos de Dados NoSQL**:
  - **Documentos**: MongoDB, CouchDB.
  - **Colunas**: Cassandra, HBase.
  - **Chave-Valor**: Redis, DynamoDB.
  - **Grafos**: Neo4j, OrientDB.
- **Características**:
  - **Escalabilidade Horizontal**: Adição de mais servidores para aumentar a capacidade.
  - **Flexibilidade de Esquema**: Suporte a dados semi-estruturados.
  - **Desempenho em Altas Cargas**: Alta performance em operações de leitura e escrita.

---

### Conclusão
Compreender os fundamentos de banco de dados, tanto relacionais quanto NoSQL, é essencial para gerenciar e utilizar eficientemente grandes volumes de dados. A prática com comandos SQL e a modelagem de dados são habilidades cruciais para qualquer profissional de TI.


### Criação de Aplicativo com Expo
- **Criando aplicativo**:
  ```javascript
  npx create-expo-app MOBI-Rio
  ```