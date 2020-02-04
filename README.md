# docker-compose

File: .env
- NGINX_HOST=localhost
- MYSQL_DATABASE=laravel
- MYSQL_USER=secret
- MYSQL_PASSWORD=secret
- MYSQL_ROOT_PASSWORD=secret
- MYSQL_ALLOW_EMPTY_PASSWORD=yes
- NGROK_REGION=eu

Folder: db
- Can include a dump.sql file which will be imported when docker-compose up -d

Folder: db -> persist
- It keeps the database so that if docker-compose build the database will not be lost

Folder: www
- Where the project is.
