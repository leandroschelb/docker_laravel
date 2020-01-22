# Docker Laravel

Este é um projeto pessoal para criar um ambiente de desenvolvimento laravel docker. Sinta-se livre para utilizar como bem entender.

## Instalação

 - #### va para a pasta do seu projeto laravel
     - `cd ~/<nome_do_projeto>`

 - #### clone o projeto do docker-laravel
     - `git clone https://github.com/leandroschelb/docker_laravel.git`
     
 - #### remova README para evitar sobreescrita
     - `rm docker_laravel/README.md`

 - #### mova os arquivos do docker para a pasta root do seu projeto
     - `mv docker_laravel/* .`

 - #### delete a pasta do docker_laravel
     - `rm -rf docker_laravel`

 - #### troque o nome dos containers
    - `troque o nome dos containers para por exemplo: app_nome_do_projeto`

 - #### certifique-se de criar um volume novo para o banco de dados
    - `troque o nome do volume para por exemplo: db_data1`

 - #### adicione as seguintes linhas em seu .gitignore
     - `docker-compose.yml`
     - `Dockerfile`
     - `mysql/`
     - `nginx/`
     - `php/`

 - #### rode o composer install
     - `docker run --rm -v $(pwd):/app composer install`

 - #### torna o usuario o proprietario da pasta do projeto
     - `sudo chown -R $USER:$USER ~/<nome_do_projeto>`

 - #### configuração do banco de dados
     - `certificar-se que em seu arquivo .env do seu projeto`
     - `DB_HOST = nome_do_container_mysql`
     
 - #### suba os containers
     - `docker-compose up -d`

 - #### Abre terminal no container php
     - `docker exec -it nome_do_container_php bash`
     
 - #### Gere a key
     - `php artisan key:generate`
     
 - #### Se a aplicação tiver jwt
     - `php artisan jwt:secret`
     
 - #### limpa cache antigo
     - `php artisan config:clear`
     - `php artisan config:cache`
     
 - #### saia do container anterior e entre no banco de dados
     - `docker exec -it nome_container_db bash`    
     
 - #### logue como root senha default: minha_senha_root_mysql
     - `mysql -u root -p`
     
 - #### crie um usuario pra você
     - `GRANT ALL ON laravel.* TO 'seu_nome'@'%' IDENTIFIED BY 'sua_senha';`
     
     

 - #### adicione o seguinte alias em seu ~/.bashrc (evita o docker criar arquivos como root)
     -  `alias docker-compose-up-d="CURRENT_UID=$(id -u):$(id -g) docker-compose up -d"`
     -  execute o docker-compose como `docker-compose-up-d` tudo junto.


## Possíveis problemas

 - #### The stream or file "/var/www/mydomain.com/storage/logs/laravel.log" could not be opened: failed to open stream: Permission denied
    -  Execute os seguintes comandos no seu container PHP na pasta var/www:
    - `chgrp -R www-data storage bootstrap/cache`
    - `chmod -R ug+rwx storage bootstrap/cache`

