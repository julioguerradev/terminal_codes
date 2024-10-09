# Anotações de Desenvolvimento

## SSH
<details>
  <summary>Clique para expandir</summary>
  - **Gerar chave SSH:**
  ```bash
    ssh-keygen
  ```
</details>

## Iniciando o Docker

<details>
<summary>Clique para expandir</summary>

- **Iniciar serviço Docker:**
  ```bash
  sudo service docker start
  ```

- **Lista de distribuições no WSL:**
  ```bash
  wsl --list --verbose
  ```

- **Definir versão padrão do WSL:**
  ```bash
  wsl --set-version Ubuntu-20.04 2
  ```

- **Desinstalar distribuição:**
  ```bash
  wsl --unregister Ubuntu-24.04
  ```

- **Configurações do WSL:**
  Ao iniciar o WSL, edite o arquivo de configuração:
  ```bash
  sudo vim /etc/wsl.conf
  ```

- **Iniciar ambiente Docker com docker-compose:**
  ```bash
  docker-compose up -d
  ```

</details>

## PHP e Composer

<details>
<summary>Clique para expandir</summary>

- **Instalar PHP CLI, Unzip e Curl:**
  ```bash
  sudo apt install php-cli unzip curl
  ```

- **Baixar o Composer:**
  ```bash
  curl -sS https://getcomposer.org/installer -o composer-setup.php
  ```

- **Instalar o Composer:**
  ```bash
  sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
  ```

- **Criar um ambiente Laravel:**
  ```bash
  curl -s "https://laravel.build/laravel-10-teste?with=mysql,redis,mailpit" | bash
  ```

- **Verificar versões possíveis do PHP:**
  ```bash
  sudo update-alternatives --config php
  ```

</details>

## MySQL

<details>
<summary>Clique para expandir</summary>

- **Iniciar MySQL:**
  ```bash
  sudo service mysql start
  sudo mysql -u root -p
  ```

- **Redefinir privilégios de um usuário:**
  ```sql
  ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';
  FLUSH PRIVILEGES;
  ```

- **Verificar a porta do MySQL:**
  ```bash
  cat /etc/mysql/mysql.conf.d/mysqld.cnf | grep port
  ```

- **Verificar conexão do MySQL:**
  ```bash
  sudo service mysql status
  ```

- **Instalar PHP para MySQL:**
  ```bash
  sudo apt install php8.2-mysql
  ```

- **Usando a porta 3306:**
  ```bash
  sudo ss -tuln | grep 3306
  sudo lsof -i :80
  ```

</details>

## Servidor Apache

<details>
<summary>Clique para expandir</summary>

- **Identificar status e parar servidor Apache:**
  ```bash
  sudo systemctl status apache2
  sudo systemctl stop apache2
  ```

- **Verificar o hash do instalador do Composer:**
  ```bash
  HASH=$(curl -sS https://composer.github.io/installer.sig)
  php -r "if (hash_file('SHA384', 'composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
  ```

</details>

## Banco de Dados

<details>
<summary>Clique para expandir</summary>

- **Criar usuário no banco de dados:**
  ```sql
  CREATE USER 'sail'@'%' IDENTIFIED BY 'password';
  GRANT ALL PRIVILEGES ON *.* TO 'sail'@'%';
  FLUSH PRIVILEGES;
  ```

- **Definir permissões e alterar o proprietário do diretório:**
  ```bash
  sudo chmod -R 775 /home/julio/projects/atlas-goinfra
  sudo chown -R $USER:$USER /home/julio/projects/atlas-goinfra
  ```

</details>
