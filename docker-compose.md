# Docker Compose Commands

### 1. Para ejecutar un archivo docker-compose.yaml

```
docker-compose up -d
docker compose up -d
```

### 2. Para eliminar lo definido en el docker compose

```
docker compose down
```

### 3. Para poder listar y filtrar servicios levantados por docker compose

```
docker compose ps
docker compose ps | grep mysqlserver (mac/linux)
docker compose ps | findStr mysql-server OR <NAME-CONTAINER> OR <IMAGE> (mac/linux)
```

### 4. Para detener todos los servicios

```
docker-compose stop
```

### 5. Para detener un servicio en especifico

```
docker-compose stop mysql-server
```

### 6. Para levantar todos los servicios detenidos

```
docker-compose start
```

### 7. Para levantar un servicio en especifico

```
docker-compose start mysql-server
```

### 8. Para ejecutar solo ciertos servicios de un total de x

```
docker compose up -d <NAME-SERVICE> <NAME-SERVICE2>.....
```

### 9. Para remover un servicio en ejecución

```
docker-compose rm -s mysql-server (por confirmación)
docker-compose rm -s -f mysql-server-2 (inmediata)
```

### 10. Para poder refrescar las implementaciones o cambios que han sufrido ciertas imagenes

```
docker compose up -d --build 
```

### 11. Para la construcción de imágenes personalizadas

```
Se necesita crear un archivo: Dockerfile
```