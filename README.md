# Anotações de Desenvolvimento

## SSH
<details>
  <summary>Clique para expandir</summary>
  
  - **Gerar chave SSH:**
  ```bash
    ssh-keygen
  ```

  - **Buscando chave privada:**
  ```bash
    cat ~/.ssh/id_rsa
  ```

  - **Buscando chave pública:**
  ```bash
    cat ~/.ssh/id_rsa.pub
  ```
</details>

## WSL e Docker

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

</details>


## Linux

<details>
<summary>Clique para expandir</summary>

- **Substituir linhas com o primeiro parâmetro para as do segundo parâmetro:**
  ```bash
  sed -i 's/utf8mb4_0900_ai_ci/utf8mb4_unicode_ci/g' seu_arquivo_dump.sql
  ```

- **Definir permissões e alterar o proprietário do diretório:**
  ```bash
  sudo chmod -R 775 /home/julio/projects/atlas-goinfra
  sudo chown -R $USER:$USER /home/julio/projects/atlas-goinfra
  ```

- **Este código verifica a integridade do instalador do Composer ao comparar seu hash oficial com o hash local:**
  ```bash
  HASH=$(curl -sS https://composer.github.io/installer.sig)
  php -r "if (hash_file('SHA384', 'composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
  ```

- **Este código deleta todas as branchs localmente, com exeção de stage e main:**
  ```bash
  git branch | grep -ve " main$\| stage$" | sed 's/^[ *]*//' | xargs git branch -D
  ```


</details>


## Laravel

<details>
<summary>Clique para expandir</summary>

- **Criar um ambiente Laravel:**
  ```bash
  curl -s "https://laravel.build/laravel-10-teste?with=mysql,redis,mailpit" | bash
  ```

- **Controllers de utilização Única**
  ```bash
  sail artisan make:controller CheckoutController --invokable
  ```

- **Utilizando resources**
  ```bash
  sail artisan make:controller PostController --resource --model=Post
  ```

<details>
<summary>Utilizando um apelido para "./vendor/bin/sail"</summary>
  
  - **Abra o arquivo de configuração:**
    ```bash
      vim ~/.bashrc
    ```
  - **Cole o comando abaixo no final do arquivo:**
      ```bash
      alias sail='[ -f sail ] && bash sail || ./vendor/bin/sail'
      ```
  - **Feche o Arquivo de configuração:**
      ```bash
      source ~/.bashrc
      ```
</details>

  <details>
  <summary>Tinker</summary>

    - **Buscando valores com a Model:**
      ```bash
      App\Models\Fornecedor::all()->toArray();
      ```

    - **Buscando valores com "DB":**
      ```bash
      DB::table('fornecedores')->get();
      ```

    - **Buscando Colunas:**
      ```bash
      Schema::getColumnListing('contrato_trechos_geo_view');
      ```

    - **Truncando tabela*:*
      ```bash
      App\Models\Fornecedor::truncate();
      ```
  </details>

    <details>
  <summary>Commit</summary>
    - **Rodando comando que está no Lint:**
      ```Lint
      npm run lint -- --fix
      ```
  </details>
</details>



