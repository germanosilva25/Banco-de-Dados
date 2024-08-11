No SQL, uma **view** (ou "visão") é uma tabela virtual que representa o resultado de uma consulta. Ela não armazena dados por si só, mas sim a consulta SQL que define como os dados são apresentados. Views são úteis para simplificar consultas complexas, restringir o acesso a dados sensíveis e criar abstrações lógicas no banco de dados.

### Tipos de Views

Existem diferentes tipos de views, cada uma com características e funcionalidades específicas:

1. **Simple View (View Simples)**
2. **Complex View (View Complexa)**
3. **Materialized View (View Materializada)**

#### 1. Simple View (View Simples)

Uma **Simple View** é criada a partir de uma única tabela e não contém funções agregadas ou subconsultas. Geralmente, ela é usada para simplificar o acesso a dados específicos de uma tabela.

**Exemplo:**
Vamos criar uma simple view para mostrar apenas os nomes e os e-mails dos clientes:

```sql
CREATE VIEW view_clientes AS
SELECT nome, email
FROM clientes;
```

Agora, sempre que você quiser acessar os nomes e e-mails dos clientes, basta consultar a `view_clientes`:

```sql
SELECT * FROM view_clientes;
```

**Explicação**: 
- A `view_clientes` mostra os dados de `nome` e `email` diretamente da tabela `clientes`.

#### 2. Complex View (View Complexa)

Uma **Complex View** é criada a partir de uma ou mais tabelas e pode incluir funções agregadas, subconsultas, junções (joins) e outras operações SQL complexas.

**Exemplo:**
Vamos criar uma complex view que mostra o total de vendas por cliente:

```sql
CREATE VIEW view_vendas_clientes AS
SELECT c.nome, SUM(v.valor) AS total_vendas
FROM clientes c
JOIN vendas v ON c.id_cliente = v.id_cliente
GROUP BY c.nome;
```

Agora, você pode consultar o total de vendas por cliente:

```sql
SELECT * FROM view_vendas_clientes;
```

**Explicação**:
- A `view_vendas_clientes` combina dados das tabelas `clientes` e `vendas`, agregando o total de vendas por cliente.

#### 3. Materialized View (View Materializada)

Uma **Materialized View** armazena fisicamente o resultado da consulta em disco, ao contrário das views simples e complexas, que são calculadas sob demanda. As materialized views são usadas para melhorar o desempenho, especialmente em consultas complexas ou em ambientes com grandes volumes de dados.

**Exemplo:**
Vamos criar uma materialized view que armazena o total de vendas por mês:

```sql
CREATE MATERIALIZED VIEW view_vendas_mensais AS
SELECT EXTRACT(MONTH FROM data_venda) AS mes, SUM(valor) AS total_vendas
FROM vendas
GROUP BY EXTRACT(MONTH FROM data_venda);
```

Para acessar os dados armazenados na materialized view:

```sql
SELECT * FROM view_vendas_mensais;
```

**Explicação**:
- A `view_vendas_mensais` armazena o total de vendas por mês em disco, permitindo acesso rápido aos dados.
- A materialized view precisa ser atualizada manualmente ou em intervalos regulares para refletir os dados mais recentes, diferentemente das views simples e complexas que sempre mostram os dados atuais.

### Atualizando Materialized Views

Materialized views podem não refletir automaticamente as mudanças nos dados subjacentes. Para garantir que os dados estejam atualizados, você pode usar o comando `REFRESH MATERIALIZED VIEW`:

```sql
REFRESH MATERIALIZED VIEW view_vendas_mensais;
```

### Vantagens e Desvantagens das Views

#### Vantagens:

- **Simplificação**: Views podem simplificar consultas complexas, tornando-as mais fáceis de entender e manter.
- **Segurança**: Podem ser usadas para restringir o acesso a dados sensíveis, mostrando apenas as colunas necessárias.
- **Consistência**: As views garantem que a mesma lógica de consulta seja aplicada consistentemente em todo o sistema.

#### Desvantagens:

- **Desempenho**: Views complexas podem impactar o desempenho, especialmente se envolverem junções ou agregações complexas.
- **Atualizações**: Atualizar dados através de uma view pode ser complicado, especialmente em views complexas. Nem todas as views permitem operações de `INSERT`, `UPDATE` ou `DELETE`.
- **Manutenção**: Mudanças na estrutura das tabelas subjacentes podem exigir modificações nas views associadas.

### Exemplo Completo de Uso de Views

Suponha que você tenha as seguintes tabelas: `clientes`, `vendas`, e `produtos`. 

#### Criando a Tabela de Exemplo

```sql
CREATE TABLE clientes (
    id_cliente SERIAL PRIMARY KEY,
    nome VARCHAR(100),
    email VARCHAR(100)
);

CREATE TABLE vendas (
    id_venda SERIAL PRIMARY KEY,
    id_cliente INT,
    id_produto INT,
    valor DECIMAL(10,2),
    data_venda DATE,
    FOREIGN KEY (id_cliente) REFERENCES clientes(id_cliente)
);

CREATE TABLE produtos (
    id_produto SERIAL PRIMARY KEY,
    nome_produto VARCHAR(100),
    preco DECIMAL(10,2)
);
```

#### Criando uma Simple View

```sql
CREATE VIEW view_dados_clientes AS
SELECT nome, email FROM clientes;
```

#### Criando uma Complex View

```sql
CREATE VIEW view_resumo_vendas AS
SELECT c.nome, p.nome_produto, SUM(v.valor) AS total_gasto
FROM vendas v
JOIN clientes c ON v.id_cliente = c.id_cliente
JOIN produtos p ON v.id_produto = p.id_produto
GROUP BY c.nome, p.nome_produto;
```

#### Criando uma Materialized View

```sql
CREATE MATERIALIZED VIEW view_total_vendas_por_mes AS
SELECT EXTRACT(MONTH FROM data_venda) AS mes, SUM(valor) AS total_vendas
FROM vendas
GROUP BY EXTRACT(MONTH FROM data_venda);
```

### Consultando as Views

- **Simple View**: `SELECT * FROM view_dados_clientes;`
- **Complex View**: `SELECT * FROM view_resumo_vendas;`
- **Materialized View**: `SELECT * FROM view_total_vendas_por_mes;`

### Conclusão

Views são uma ferramenta poderosa no SQL que permite criar tabelas virtuais para simplificar consultas, melhorar a segurança e criar abstrações. Dependendo das necessidades, você pode usar simple views, complex views, ou materialized views para otimizar o acesso aos dados e melhorar o desempenho das suas consultas.