# docker-compose

File: .env
- NGINX_HOST=localhost
- MYSQL_DATABASE=laravel
- MYSQL_USER=secret
- MYSQL_PASSWORD=secret
- MYSQL_ROOT_PASSWORD=secret

Folder: db
- Can include a dump.sql file which will be imported when docjer-compose up -d

Folder: db -> persist
- It keeps the database so that if docker-compose build the database will not be lost

Folder: www
- Where the project is.
