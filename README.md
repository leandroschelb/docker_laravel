# Docker Laravel

Este é um projeto pessoal para criar um ambiente de desenvolvimento laravel docker. Sinta-se livre para utilizar como bem entender.

## Instalação

 - #### va para a pasta do seu projeto laravel
    cd ~/<nome_do_projeto>

 - #### clone o projeto do docker-laravel
    git clone https://github.com/leandroschelb/docker_laravel.git

 - #### mova os arquivos do docker para a pasta root do seu projeto
    mv docker_laravel/* .

 - #### delete a pasta do docker_laravel
    rm -rf docker_laravel

 - #### adicione as seguintes linhas em seu .gitignore
    docker-compose.yml
    Dockerfile
    mysql/
    nginx/
    php/

 - #### rode o composer install
    docker run --rm -v $(pwd):/app composer install

 - #### torna o usuario o proprietario da pasta do projeto
    sudo chown -R $USER:$USER ~/<nome_do_projeto>

 - #### suba os containers
    docker-compose up -d


 - #### configuração do banco de dados
    certificar-se que em seu arquivo .env do seu container php
    DB_HOST = nome_do_container_mysql

 - #### caso o projeto não possua jwt não utilizar os comandos que iniciam com php
    docker-compose exec app php artisan key:generate
    php artisan jwt:secret
    php artisan config:clear
    php artisan config:cache
    docker-compose exec app php artisan config:cache

    docker-compose exec db bash
    mysql -u root -p
    GRANT ALL ON laravel.* TO 'leandro'@'%' IDENTIFIED BY 'toor';