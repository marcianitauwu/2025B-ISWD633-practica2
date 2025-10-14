### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:15-alpine3.21
# COMPLETAR
```
docker run -d --name contenedor-postgres -e POSTGRES_PASSWORD=samira postgres:15-alpine3.21
```
### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4

# COMPLETAR
```
docker run -d --name pgAdminContenedor -e PGADMIN_DEFAULT_EMAIL=admin@mail.com -e PGADMIN_DEFAULT_PASSWORD=admin -p 8080:80 dpage/pgadmin4
```
La figura presenta el esquema creado en donde los puertos son:
- a: (8080)
- b: (5432)
- c: (80)

![Imagen](esquema-2-ejercicio.PNG)

## Desde el cliente
### Acceder desde el cliente al servidor postgres creado.
# COMPLETAR CON UNA CAPTURA DEL LOGIN
<img width="2437" height="1218" alt="image" src="https://github.com/user-attachments/assets/c4f60a76-21b9-4333-a04a-a9713190c60f" />

### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.

<img width="2452" height="1118" alt="image" src="https://github.com/user-attachments/assets/8d1a0785-4b61-4a42-b256-446131b4a476" />

Importante, que esten dentro de la misma red.
```
docker network create postgresNet

docker network connect postgresNet contenedor-postgres

docker network connect postgresNet pgAdminContenedor
```

Crear base de datos
```
CREATE DATABASE info;
```
Crear la tabla personas
```
CREATE TABLE personas (
  id SERIAL PRIMARY KEY,
  nombre VARCHAR(100)
);
```
Insetar registros
```
INSERT INTO personas (nombre) VALUES ('Samira');
INSERT INTO personas (nombre) VALUES ('Fernanda');
```
<img width="988" height="1139" alt="image" src="https://github.com/user-attachments/assets/ff6d4021-0d48-401e-9315-6b54890b68cd" />


## Desde el servidor postgresl
### Acceder al servidor
### Conectarse a la base de datos info
# COMPLETAR
```
docker exec -it contenedor-postgres psql -U postgres
```
Se debe poner \c info para entrar a la base de datos "info"

### Realizar un select * from personas
# AGREGAR UNA CAPTURA DE PANTALLA DEL RESULTADO
<img width="495" height="191" alt="image" src="https://github.com/user-attachments/assets/e0f650c6-05b1-4cdc-9fa3-1485a39ef360" />

