# Crear un servidor de MYSQL mediante Docker

### 1. Descargar la imagen de MYSQL desde Docker Hub

```
docker pull mysql
```

### 2. Verificar y filtrar imágenes de MYSQL desde la lista de imágenes de Docker

```
docker images (listar todos)
docker images | grep mysql (linux/mac) -> filtrar búsqueda
docker images | findStr <NAME-IMAGE> or <ID> (windows) filtrar búsqueda
```

### 3. Eliminar una imagen de Docker

```
docker rmi mysql:8 or docker rmi <ID>
```

### 4. Crear un contenedor con la imagen de MYSQL con un nombre aleatorio
```
docker create mysql:8 (nombre: toma uno aleatorio)
```

### 5. Para eliminar un contenedor
```
docker rm bold_keldysh or docker rm <NAME> | <ID>
docker rm -f bold_keldysh or docker rm <NAME> | <ID> (para eliminar contenedores en ejecución)
```

### 6. Crear un contenedor con la imagen de MYSQL con un nombre propio
```
docker create --name mysqlserver mysql:8
```

### 7. Listar contenedores de Docker
```
docker ps - a (Lista todos los contenedores independientes de su status)
docker ps - a | grep mysqlserver (linux/mac)
docker ps - a | findStr mysqlserver (windows)
docker ps (listo solo los que estén en ejecución)
docker ps | grep mysqlserver (linux/mac)
docker ps | findStr mysqlserver (windows)
```

### 7. Para iniciar o arrancar un contenedor de Docker
```
docker start mysqlserver or docker start <ID>
```

### 8. Para revisar el status actual del contenedor
```
docker logs mysqlserver | <ID>
```

### 9. Para crear y ejecutar un contenedor con variables de entorno, puertos y en modo detached 
```
docker run -d --name mysqlserver -p 3310:3306 -e MYSQL_ROOT_PASSWORD=1234 -e MYSQL_USER=user -e MYSQL_PASSWORD=1234 -e MYSQL_DATABASE=sqldb mysql:8
```

### 10. Para detener un contenedor 
```
docker stop mysqlserver or docker stop <ID> (recomendado: detención controlada de procesos (dormir))
docker kill mysqlserver or docker kill <ID> (no recomendado: mata el proceso padre y los subprocesos sin ninguna espera de la conclusión de sus ejecuciones)
```

### 11. Para poder inspeccionar un contenedor, imágenes y volumenes de Docker
```
docker inspect mysqlserver
docker inspect mysql:8
```

### 12. Para ingresar a la red virtual de Docker desde windows
```
Anotar \\wsl$ desde cualquier path de búsqueda
```

### 13. Para crear un contenedor con un volumen anónimo
```
docker run -d --name mysqlserver -p 3310:3306 -v /var/lib/mysql -e MYSQL_ROOT_PASSWORD=1234 -e MYSQL_USER=user -e MYSQL_PASSWORD=1234 -e MYSQL_DATABASE=sqldb mysql:8
```

### 14. Para listar y filtrar volumenes
```
docker volume ls
docker volume ls | grep <NAME> OR <ID> (linux/mac)
docker volume ls | findStr <NAME> OR <ID> (linux/mac)
```

### 15. Para eliminar un contenedor con un volumen anónimo
```
docker rm -fv mysqlserver or docker rm -fv <ID>
```

### 16. Para eliminar un volumen específico
```
docker volume rm <NAME> OR <ID>
```

### 17. Para eliminar una lista de volumenes huerfanos
```
docker volume prune
```

### 18. Para eliminar un contenedor con un volumen anónimo
```
docker rm -fv mysqlserver or docker rm -fv <ID>
```

### 19. Para crear un contenedor con un volumen de tipo host
```
docker run -d --name mysqlserver -p 3310:3306 -v E:\docker_examples\docker\volumen\mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=1234 -e MYSQL_USER=user -e MYSQL_PASSWORD=1234 -e MYSQL_DATABASE=sqldb mysql:8
```

### 20. Para eliminar un volumen host
```
Se elimina la carpeta de manera manual
rmdir /s /q "C:\ruta\a\la\carpeta" (windows)
rm -rf /ruta/a/la/carpeta (linux/mac)
```

### 21. Para crear un contenedor con un volumen de tipo nombrado
```
docker run -d --name mysqlserver -p 3310:3306 -v vol-mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=1234 -e MYSQL_USER=user -e MYSQL_PASSWORD=1234 -e MYSQL_DATABASE=sqldb mysql:8
```

### 22. Para eliminar un contenedor con un volumen nombrado
```
docker rm -fv mysqlserver or docker rm -fv <ID>
```

### 23. Para crear una red de Docker
```
docker network create net-mysql (opción corta)
docker network create net-mysql -d bridge (opción más larga)
```

### 24. Para listar las redes de Docker
```
docker network ls
```

### 25. Para filtrar el listado de redes de Docker
```
docker network ls | findStr net-mysql (windows)
docker network ls | grep net-mysql (linux/mac)
```

### 26. Para inspeccionar una red de Docker
```
docker network inspect net-mysql
```

### 27. Para eliminar una red de Docker
```
docker network remove net-mysql
```

### 28. Para conectar un contenedor con una red de Docker
```
docker network connect net-mysql mysqlserver
```

### 29. Para desconectar un contenedor de una red de Docker
```
docker network disconnect net-mysql mysqlserver
```

### 30. Para asociar una red en la creación y ejecución de un contenedor
```
docker run -d --name mysqlserver --network net-mysql -p 3310:3306 -v vol-mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=1234 -e MYSQL_USER=user -e MYSQL_PASSWORD=1234 -e MYSQL_DATABASE=sqldb mysql:8
```