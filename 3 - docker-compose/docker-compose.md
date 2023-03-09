# _Docker-Compose_

## 3.1 Instalação do Docker-compose
Com o docker ativo podemos instalar o docker-compose:
```
sudo apt install docker-compose
```

Agora é possível criar nosso arquivo YML de docker-compose.
```
vim docker-compose.yml
```

-----

## 3.2 docker-compose.yml
Agora vamos usar nosso arquivo para escrever nosso código.
#### OBS: É possível encontrar a documentação das imagens no Dockerhub 
```
version: '3.1'
services:
  db:
    image: mysql:latest
    restart: always
    ports:
      - '6556:3306'
    expose:
      - '3306'
    environment:
      MYSQL_DATABASE: mysql_db
      MYSQL_ROOT_PASSWORD: senha
    volumes:
      - ~/mysql_data:/var/lib/mysql
  wordpress:
    image: wordpress
    restart: always
    ports:
      - '8084:80'
    expose:
      -  '80'
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: root
      WORDPRESS_DB_PASSWORD: senha
      WORDPRESS_DB_NAME: mysql_db
    volumes:
      - ~/site:/var/www/html
  adminer:
    image: adminer
    restart: always
    ports:
      - '8085:8080'
    expose:
      - '8080'
```

Antes de executar devemos criar as pastas de volumes que foram apontadas dentro do código. Neste caso:
```
mkdir site; mkdir mysql_data
```

Pronto agora é possível executar nosso arquivo compose, o terminal irá travar quando finalizada a execução:
```
docker-compose up
```

------

## 3.3 redirecionamento de portas
Observe que as portas utilizadas diferem das portas padrão. Isso foi feito para evitar conflitos de porta, mas é possível alterá-las para qualquer valor livre.

Para acessar as aplicações no navegador, é necessário criar uma nova regra de redirecionamento de portas. A regra deve ser criada da seguinte forma:
<div>
<img src="..\portas.png"/>  
</div>

-----

### Pronto! Agora todas as aplicações já estão rodando dentro de um container docker.