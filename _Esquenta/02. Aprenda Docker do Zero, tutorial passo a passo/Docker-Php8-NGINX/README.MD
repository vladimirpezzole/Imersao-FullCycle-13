## **02. Aprenda Docker do Zero, tutorial passo a passo**

[>> Video 🎞️](https://youtu.be/8MJWke19g8U)
*************
<hr>

### **Importante!!!** antes de continuar verifique se o **Docker** está instalado corretamente, caso precise instalar siga o tutorial: [**Instalação do Docker e Docker Compose**](Como-Instalar-Docker-e-Docker-Compose.md)

<hr>

**************

### Abaixo um modelo de uso de containers usando **Docker** e **Docker Compose**, que através do manifesto **docker-compose.yml** constrói um ambiente para usou ou laboratório com containers **MariaDB**, **PHP MyAdmin**, **NGINX** + **PHP_PFM**, utilizando arquivo **.env** com lista de variáveis de ambiente.


<hr>

**>> docker-compose.yml**
```yaml
version: '3.9'
services:
    mariadb:
        image: 'mariadb:${MARIADB_VERSION}'
        ports:
            - "${MYSQL_PORT}:3306"
        working_dir: /app
        volumes:
            - ./app/db:/var/lib/mysql
            - ./table.sql:/docker-entrypoint-initdb.d/table.sql
        environment:
            MYSQL_ROOT_PASSWORD: "${MYSQL_ROOT_PASSWORD}"
            MYSQL_DATABASE: "${MYSQL_DATABASE}"
            MYSQL_USER: "${MYSQL_USER}"
            MYSQL_PASSWORD: "${MYSQL_PASSWORD}"

    phpmyadmin:
        image: phpmyadmin/phpmyadmin
        ports:
            - "${PORT_PMA}:80"
        environment:
            PMA_HOST: ${PMA_HOST}
            PMA_PORT: ${PMA_PORT}
            PMA_USER: ${PMA_USER}
            PMA_PASSWORD: ${PMA_PASSWORD}
        depends_on:
            - mariadb

    webserver:
        image: 'nginx:alpine'
        working_dir: /app
        volumes:
            - '.:/app'
            - './phpdocker/nginx/nginx.conf:/etc/nginx/conf.d/default.conf'
        ports:
            - '${PORT_WEB}:80'

    php-fpm:
        build: "${PHP_PFM}"
        working_dir: /app
        volumes:
            - '.:/app'
            - './phpdocker/php-fpm/php-ini-overrides.ini:/etc/php/8.2/fpm/conf.d/99-overrides.ini'

```
**>> .env**
```yaml
PORT_WEB=9010
PORT_PMA=9011
MYSQL_PORT=9012

MARIADB_VERSION=10.6
MYSQL_ROOT_PASSWORD=secret
MYSQL_DATABASE=labphp8-db
MYSQL_USER=labphp8
MYSQL_PASSWORD=secret

PMA_HOST=mariadb
PMA_PORT=3306
PMA_USER=labphp8
PMA_PASSWORD="secret"

PHP_PFM=phpdocker/php-fpm

```
Na pasta **phpdocker** ficam outros arquivos de configuração como **Dockerfile** do **PHP_PFM**
```bash
phpdocker
|  |
|  | --> nginx
|        |--> nginx.conf
|
| --> php-fpm
      |--> Dockerfile
      |--> php-ini-overrides.ini

```

### **Para carregar um arquivo diretamente no banco de dados MariaDB:**
Ex.: 
Arquivo `table.sql` ẽ montado como um volume em:

**docker-compose.yml:**
```yaml
version: '3.9'
services:
    mariadb:
        ....
        volumes:
            - ./app/db:/var/lib/mysql
            - ./table.sql:/docker-entrypoint-initdb.d/table.sql
        .....
```

Quando você executar `docker-compose up`, ele montará o arquivo `table.sql` como um volume e o copiará para o diretório `/docker-entrypoint-initdb.d/` dentro do contêiner MariaDB. O MariaDB executará automaticamente todos os arquivos SQL nesse diretório ao inicializar o banco de dados.

Certifique-se de ter o arquivo `table.sql` no mesmo diretório em que está o arquivo `docker-compose.yml`. Em seguida, você pode executar `docker-compose up` para iniciar o contêiner MariaDB com o arquivo SQL sendo executado automaticamente.


<hr>

*****

### **Para rodar execute:**

`docker compose up -d` 

ou 

`docker-compose up -d ` 

<i>(dependendo da sua versão do **Docker  Compose**)</i>

<hr>

********

*************
### **Comandos Bãsicos de Docker:**

```
docker run (executar novo container)

docker ps (lista todos os containers rodando)

docker ps -a (demonstra todos os containers, até os parados)

docker run ubuntu bash (roda container com Ubuntu e já abre o terminal)

docker run -it ubuntu bash (roda imagem de modo interativo)

crtl + d (sair do contêiner/bash)

docker run nginx (roda imagem do nginx na porta 80 do contêiner, não do computador)

docker run -p 8080:80 nginx (roda a imagem nginx com o contêiner publicado na porta 8080 do computador)

docker exec [nome do container] ls (lista diretórios dentro do container devido ao comando exec)

docker run -p 8080:80 -v [diretório pasta compartilhada] (mesmo derrubando o container, os arquivos de desenvolvimento não são perdidos)

dockerfile (criar sua própria imagem)

docker build -t [usuario]/[imagem]:latest
```