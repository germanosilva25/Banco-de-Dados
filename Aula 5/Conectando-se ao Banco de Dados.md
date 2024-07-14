Para criar um arquivo de configuração de conexão com um banco de dados MySQL usando PHP 8, você precisará definir as informações de conexão, como host, nome de usuário, senha e nome do banco de dados. Aqui está um exemplo simples de como você pode configurar isso:

1. **Criando o arquivo de configuração (`config.php`)**:

```php
<?php

// Configurações de conexão com o banco de dados MySQL
$host = 'localhost'; // Host do MySQL (geralmente 'localhost' para ambiente local)
$username = 'seu_usuario_mysql'; // Nome de usuário do MySQL
$password = 'sua_senha_mysql'; // Senha do MySQL
$database = 'nome_do_banco_de_dados'; // Nome do banco de dados a ser usado

// Tentativa de conexão
try {
    $pdo = new PDO("mysql:host=$host;dbname=$database", $username, $password);
    // Configurações adicionais
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION); // Ativar modo de exceções
    $pdo->setAttribute(PDO::ATTR_DEFAULT_FETCH_MODE, PDO::FETCH_ASSOC); // Modo de retorno de dados por padrão
    // Outras configurações, se necessário
} catch (PDOException $e) {
    die("Erro ao conectar ao banco de dados: " . $e->getMessage());
}
```

### Explicação:

- **`$host`**: Aqui você deve fornecer o endereço do servidor MySQL. Geralmente, `localhost` é usado quando o MySQL está instalado na mesma máquina que o servidor web.
  
- **`$username`** e **`$password`**: São suas credenciais de acesso ao MySQL.

- **`$database`**: É o nome do banco de dados que você deseja acessar.

- **`try...catch`**: É usado para tentar estabelecer a conexão com o banco de dados MySQL. Se ocorrer algum erro durante a conexão, uma exceção do tipo `PDOException` será lançada e o script exibirá uma mensagem de erro.

- **`PDO`**: É uma classe do PHP que fornece uma interface para trabalhar com bancos de dados. No exemplo, `PDO::setAttribute` é usado para configurar o modo de tratamento de erros (`ERRMODE_EXCEPTION`) e o modo de retorno de dados (`FETCH_ASSOC`).

### Utilizando a conexão:

Depois de incluir o arquivo `config.php` em seus scripts PHP, você pode utilizar a variável `$pdo` para executar consultas SQL e interagir com o banco de dados. Aqui está um exemplo simples de como você pode fazer isso:

```php
<?php

// Inclua o arquivo de configuração
require_once 'config.php';

// Exemplo de consulta SQL
$query = "SELECT * FROM usuarios";
$stmt = $pdo->query($query);

// Exemplo de exibição dos resultados
while ($row = $stmt->fetch()) {
    echo "ID: " . $row['id'] . ", Nome: " . $row['nome'] . "<br>";
}
```

Este exemplo mostra como configurar e utilizar uma conexão com MySQL usando PHP 8, seguindo as melhores práticas de segurança e tratamento de erros. Certifique-se de substituir `seu_usuario_mysql`, `sua_senha_mysql` e `nome_do_banco_de_dados` com suas próprias credenciais e nome do banco de dados MySQL.