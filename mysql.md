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