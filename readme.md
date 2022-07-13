# Reto-de-Krowdy:Deployment

# Dockerizacion de Mysql

### Comandos

Creamos un directorio llamado d2, ingresamos y creamos un archivo Dockerfile con vim

```bash
mkdir d2
cd d2
vim Dockerfile
```

Dentro de este Dockerfile agregamos:

```bash
FROM mysql
MAINTAINER sb@mail.com

ENV MYSQL_ROOT_PASSWORD=12345678
ENV MYSQL_DATABASE=devdb
ENV MYSQL_MYSQL_USER=dev1
ENV MYSQL_PASSWORD=dev1A1

EXPOSE 3306
```

Guardamos y cerramos vim con los siguientes comandos:

```bash
:w
:q
```

Construimos la imagen a partir del Dockerfile

```bash
sudo docker build -t shirleyaguilar/database-mysql-1.0 .
```

Hacemos login al docker hub publico

```bash
sudo docker login -u shirleyaguilar
```

Subimos la imagen al repositorio en el hub publico:

```bash
sudo docker push shirleyaguilar/database-mysql-1.0:latest
```

### Repositorio

```bash
https://hub.docker.com/r/shirleyaguilar/database-mysql-1.0
```

### Capturas

![Untitled](Reto-de-Krowdy%20Deployment%20735c94ce7fc54d9ea8491f851e9a8cb9/Untitled.png)

![Untitled](Reto-de-Krowdy%20Deployment%20735c94ce7fc54d9ea8491f851e9a8cb9/Untitled%201.png)

![Untitled](Reto-de-Krowdy%20Deployment%20735c94ce7fc54d9ea8491f851e9a8cb9/Untitled%202.png)

### Corriendo la imagen mysql de Docker

```bash
sudo docker run --detach --name=mysqlinstance --publish 6603:3306 mysqlinstance:0.1
```

Nos conectamos desde Dbeaver (db client) para validar la conexion

![Untitled](Reto-de-Krowdy%20Deployment%20735c94ce7fc54d9ea8491f851e9a8cb9/Untitled%203.png)

![Untitled](Reto-de-Krowdy%20Deployment%20735c94ce7fc54d9ea8491f851e9a8cb9/Untitled%204.png)

# Dockerizacion de aplicación Nodejs

 Creamos un dockerfile para la aplicacion

```bash
FROM node:10-alpine
WORKDIR /var/www
COPY package.json .
RUN npm install
COPY . .
EXPOSE 8077
CMD ["node", "index.js"]
```

Construimos la imagen de docker basado en el dockerfile

```bash
sudo docker build -t shirleyaguilar/backend-nodejs-1.0 .
```

Hacemos el push de la imagen al repo

```bash
sudo docker push shirleyaguilar/backend-nodejs-1.0:latest
```

Repo:

```bash
https://hub.docker.com/r/shirleyaguilar/backend-nodejs-1.0
```

![Untitled](Reto-de-Krowdy%20Deployment%20735c94ce7fc54d9ea8491f851e9a8cb9/Untitled%205.png)

# Corriendo las dos imagenes

![Untitled](Reto-de-Krowdy%20Deployment%20735c94ce7fc54d9ea8491f851e9a8cb9/Untitled%206.png)

La inserción funciona correctamente:

![Untitled](Reto-de-Krowdy%20Deployment%20735c94ce7fc54d9ea8491f851e9a8cb9/Untitled%207.png)