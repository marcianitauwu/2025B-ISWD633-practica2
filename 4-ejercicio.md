## Esquema para el ejercicio
![Imagen](esquema-4-ejercicio.PNG)

### Crear la red
# COMPLETAR
```
docker network create net-wp
```
### Crear el contenedor mysql a partir de la imagen mysql:8, configurar las variables de entorno necesarias
# COMPLETAR
```
docker run -d --name mysql-contenedor --network net-wp -e MYSQL_ROOT_PASSWORD=admin -e MYSQL_DATABASE=dbwp -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin mysql:8
```
### Crear el contenedor wordpress a partir de la imagen: wordpress, configurar las variables de entorno necesarias
# COMPLETAR
```
docker run -d --name wordpress-contenedor --network net-wp -p 8000:80 -e WORDPRESS_DB_HOST=mysql-contenedor:3306 -e WORDPRESS_DB_USER=admin -e WORDPRESS_DB_PASSWORD=admin -e WORDPRESS_DB_NAME=dbwp wordpress
```
Ingresar desde el navegador al wordpress y finalizar la configuración de instalación.
# COLOCAR UNA CAPTURA DE LA CONFIGURACIÓN

<img width="2449" height="1409" alt="image" src="https://github.com/user-attachments/assets/9fc9b750-5f9d-43d2-bca6-18056801bf14" />

Desde el panel de admin: cambiar el tema y crear una nueva publicación.
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress
# COLOCAR UNA CAPTURA DEL SITO EN DONDE SEA VISIBLE LA PUBLICACIÓN.
<img width="2411" height="1198" alt="image" src="https://github.com/user-attachments/assets/09f47a9f-a54d-44bb-8d9c-084afa46c46e" />

### Eliminar el contenedor wordpress
# COMPLETAR
```
docker rm -f wordpress-contenedor
```
### Crear nuevamente el contenedor wordpress
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress

<img width="2337" height="979" alt="image" src="https://github.com/user-attachments/assets/06164027-1227-45de-9f6c-abf1563da762" />

### ¿Qué ha sucedido, qué puede observar?
# COMPLETAR

Aunque el contenedor de WordPress fue eliminado y luego recreado, el sitio web volvió a cargar correctamente gracias a que la base de datos MySQL seguía activa y contenía la información principal del sitio. Sin embargo, se observa que el tema personalizado y la imagen de la publicación ya no están presentes.
