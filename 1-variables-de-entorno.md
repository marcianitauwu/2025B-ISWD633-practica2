# Variables de Entorno
### ¿Qué son las variables de entorno?
# COMPLETAR
Las variables de entorno son pares clave-valor que el sistema operativo y las aplicaciones utilizan para configurar su comportamiento sin necesidad de modificar el código fuente.

### Para crear un contenedor con variables de entorno

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

# COMPLETAR
```
docker run -d --name variablesEntorno-nginx -e username=samira -e role=admin nginx:alpine
```

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR

<img width="1274" height="400" alt="image" src="https://github.com/user-attachments/assets/6506e1d7-a9a6-4d17-a2d5-1e8a526723d7" />

### Crear un contenedor con la imagen de mysql, mapear todos los puertos

# COMPLETAR
```
docker run -d --name srv-mysql -P mysql
```
### ¿El contenedor se está ejecutando?
# COMPLETAR
```
docker ps
```
Podemos ver que no se está ejecutando el contenedor srv-mysql.
### Identificar el problema
# COMPLETAR
```
docker logs srv-mysql
```
<img width="1197" height="424" alt="image" src="https://github.com/user-attachments/assets/89e68103-d814-4a36-92e4-bca2f572cf0d" />

### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.
  
### Crear un contenedor con mysql, mapear todos los puertos y configurar las variables de entorno mediante un archivo
# COMPLETAR
```
docker run -d --name contenedor-mysql -P -e MYSQL_ROOT_PASSWORD=samira mysql
```
# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR 
```
docker exec contenedor-mysql env
```

<img width="1065" height="295" alt="image" src="https://github.com/user-attachments/assets/c772dbe4-4bbc-441f-a05d-ae1dbc060cb3" />

### ¿Qué bases de datos existen en el contenedor creado?
# COMPLETAR
```
docker exec -it contenedor-mysql mysql -u root -p
```
<img width="1193" height="787" alt="image" src="https://github.com/user-attachments/assets/f907ed85-62b4-408d-b2ae-17cd0ef515f0" />

- information_schema
- mysql
- performance_schema
- sys
