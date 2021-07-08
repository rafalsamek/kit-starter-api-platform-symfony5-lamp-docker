# kit-starter-api-platform-symfony5-lamp-docker
API Platform and Symfony 5.2.9 on LAMP and Docker starter application

## Installation guide
1. Clone the starter application
```
git clone https://github.com/rafalsamek/kit-starter-api-platform-symfony5-lamp-docker.git
```
2. Go to the project root directory
```
cd kit-starter-api-platform-symfony5-lamp-docker
```
3. Install vendors
```
composer install
```
4. Launch docker
```
docker-compose up --force-recreate --build -d
```
5. Setup database in .env file
```
DATABASE_URL="mysql://root:root@mysql:3306/main"
```
6. Go to the php-apache container
```
docker ps
docker exec -it kit-starter-api-platform-symfony5-lamp-docker_php-apache_1 bash
```
7. Create database
```
./bin/console doctrine:database:create
```
## Create API entity and make migration (from php-apache container see 6.)
1. Make entity
```
./bin/console make:entity
```
2. Make migration
```
./bin/console make:migration
```
3. Migrate migrations
```
./bin/console doctrine:migrations:migrate
```
