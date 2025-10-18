# Mi aprendizaje
- Crear redes personalizadas en Docker para conectar contenedores de forma controlada, usando *docker network create*.
- Comprendí cómo configurar contenedores con variables de entorno, lo cual fue clave para que WordPress pudiera conectarse correctamente a MySQL. Usar parámetros como *MYSQL_DATABASE*, *MYSQL_USER* y *WORDPRESS_DB_HOST* me enseñó que la configuración inicial de cada servicio depende directamente de estos valores.
- Los contenedores pueden pertenecer a más de una red, lo que permite que actúen como puentes entre servicios, con *docker network connect*.
- Observé que al eliminar y recrear un contenedor, los datos pueden conservarse o perderse dependiendo de dónde estén guardados. En el caso de WordPress, la publicación seguía visible porque estaba almacenada en MySQL, pero el tema y las imágenes se perdieron porque estaban en el contenedor de WordPress.


# Docker Secrets
Docker Secrets es una funcionalidad diseñada para proteger información sensible como contraseñas, claves SSH, certificados, etc., especialmente en entornos de producción con Docker Swarm.
Características clave:
- Los secretos se almacenan cifrados en reposo y en tránsito
- Solo los servicios que los necesitan pueden acceder a ellos
- Se definen con docker secret create y se asignan a servicios con --secret
- No se exponen en variables de entorno ni en archivos visibles
Por ejemplo, en lugar de usar -e MYSQL_PASSWORD=admin, podrías usar:
```
docker secret create mysql_pass secret.txt
```

1. Crear el secreto
```
echo "valor_confidencial" > secreto.txt
docker secret create nombre_secreto secreto.txt
```

2. Usar el secreto en un servicio
```
docker service create \
  --name servicio-ejemplo \
  --secret nombre_secreto \
  imagen:tag
```
Dentro del contenedor, el secreto estará disponible como un archivo en:
```
/run/secrets/nombre_secreto
```

Docker Secrets es una herramienta esencial para la gestión segura de credenciales y datos sensibles en aplicaciones modernas basadas en contenedores. Su uso es altamente recomendado en entornos productivos, donde la seguridad y el control de acceso son prioritarios.
