A instalação do XAMPP no Windows é uma maneira prática e eficiente de configurar um ambiente de desenvolvimento local, incluindo o servidor Apache, o banco de dados MySQL (agora MariaDB), e outras ferramentas úteis. Aqui está um passo a passo detalhado para instalar o XAMPP e configurar o MySQL no Windows:

### Passo 1: Download do XAMPP

1. **Acesse o Site Oficial**:
   - Vá até o site oficial do XAMPP: [https://www.apachefriends.org/index.html](https://www.apachefriends.org/index.html)

2. **Baixe o Instalador**:
   - Clique no botão "Download" e selecione a versão adequada para o seu sistema operacional (Windows). Geralmente, você pode baixar a versão mais recente disponível.

### Passo 2: Instalando o XAMPP

1. **Execute o Instalador**:
   - Após o download, execute o arquivo do instalador do XAMPP (`xampp-windows-x64-7.4.13-0-VC15-installer.exe` ou similar).

2. **Aceite o Controle de Conta de Usuário (UAC)**:
   - Se aparecer uma mensagem do Controle de Conta de Usuário (UAC), clique em "Sim" para permitir que o instalador faça alterações no seu dispositivo.

3. **Escolha os Componentes**:
   - Na tela de seleção de componentes, você pode escolher quais componentes deseja instalar. Por padrão, todos os componentes necessários, incluindo o Apache, MySQL (MariaDB), PHP, e phpMyAdmin, estarão selecionados. Deixe os padrões selecionados e clique em "Next".

4. **Escolha a Pasta de Instalação**:
   - Escolha o diretório onde deseja instalar o XAMPP. O diretório padrão é `C:\xampp`. Clique em "Next" para continuar.

5. **Linguagem de Instalação**:
   - Escolha o idioma da instalação (Inglês ou Alemão) e clique em "Next".

6. **Iniciar a Instalação**:
   - Clique em "Next" para iniciar o processo de instalação. Aguarde enquanto o XAMPP é instalado no seu sistema.

7. **Concluir a Instalação**:
   - Após a conclusão da instalação, marque a opção para iniciar o painel de controle do XAMPP e clique em "Finish".

### Passo 3: Configurando e Iniciando os Serviços do XAMPP

1. **Iniciar o Painel de Controle do XAMPP**:
   - O painel de controle do XAMPP será aberto automaticamente. Caso contrário, você pode iniciá-lo manualmente através do menu Iniciar ou do atalho na área de trabalho.

2. **Iniciar o Apache e MySQL**:
   - No painel de controle do XAMPP, clique nos botões "Start" ao lado de "Apache" e "MySQL". Isso iniciará os serviços necessários.
   - Os status dos serviços devem mudar para "Running".

### Passo 4: Verificando a Instalação

1. **Acesse o Painel de Controle do XAMPP**:
   - Abra um navegador web e digite `http://localhost` na barra de endereços. Isso abrirá a página inicial do XAMPP, indicando que o servidor Apache está funcionando corretamente.

2. **Acesse o phpMyAdmin**:
   - Na página inicial do XAMPP, clique em "phpMyAdmin" no menu de navegação superior, ou digite `http://localhost/phpmyadmin` diretamente no navegador.
   - Isso abrirá a interface do phpMyAdmin, onde você pode gerenciar seu banco de dados MySQL (MariaDB).

### Passo 5: Configurando o MySQL

1. **Configurações Iniciais do phpMyAdmin**:
   - No phpMyAdmin, você pode criar novos bancos de dados, tabelas, usuários e realizar consultas SQL.

2. **Criando um Novo Banco de Dados**:
   - Clique em "Databases" no menu superior.
   - Digite um nome para o novo banco de dados e clique em "Create".

3. **Criando um Novo Usuário**:
   - Clique em "User accounts" no menu superior.
   - Clique em "Add user account".
   - Preencha os detalhes do usuário e defina as permissões necessárias.
   - Clique em "Go" para criar o usuário.

### Conclusão

Seguindo esses passos, você terá o XAMPP instalado e configurado no seu sistema Windows, com o servidor Apache e o banco de dados MySQL (MariaDB) prontos para uso. O XAMPP facilita a configuração de um ambiente de desenvolvimento local completo, permitindo que você comece a desenvolver e testar suas aplicações web rapidamente.
