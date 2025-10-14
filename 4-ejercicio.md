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

<img width="1903" height="1514" alt="image" src="https://github.com/user-attachments/assets/f2bd1a56-c8df-4285-8e46-dece99a8f583" />


Desde el panel de admin: cambiar el tema y crear una nueva publicación.
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress
# COLOCAR UNA CAPTURA DEL SITO EN DONDE SEA VISIBLE LA PUBLICACIÓN.
<img width="2949" height="2089" alt="image" src="https://github.com/user-attachments/assets/d369b78d-2d3f-45ec-b40e-d96bb3dad60f" />

### Eliminar el contenedor wordpress
# COMPLETAR
```
docker rm -f wordpress-contenedor
```
### Crear nuevamente el contenedor wordpress
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress

<img width="2805" height="856" alt="image" src="https://github.com/user-attachments/assets/1fa97708-df24-4740-9c3f-d6a1ca0e5438" />


### ¿Qué ha sucedido, qué puede observar?
# COMPLETAR

Aunque el contenedor de WordPress fue eliminado y luego recreado, el sitio web volvió a cargar correctamente gracias a que la base de datos MySQL seguía activa y contenía la información principal del sitio. Sin embargo, se observa que el tema personalizado y la imagen de la publicación ya no están presentes.
