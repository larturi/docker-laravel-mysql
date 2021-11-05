# Laravel & MySQL with Docker

### Se recomienda usar Laravel Sail para nuevos proyectos.
##### En caso de querer Dockerizar un Laravel ya existente, incluir los archivos y seguir los pasos.

<hr/>

Una vez ejecutado, se generan tres contenedores:

App: http://localhost:81/login
PhpMyAdmin: http://localhost:82
MySQL en puerto 3307

<hr/>

## Get Started 🚀

### Configurar variables de entorno en el .env Local:
```bash
APP_DEBUG=true
APP_URL=http://localhost:81
ADMIN_HTTPS=false
```

### Crear un .htaccess con el siguiente codigo y guardar en /public

```bash
<IfModule mod_rewrite.c>
    <IfModule mod_negotiation.c>
        Options -MultiViews -Indexes
    </IfModule>

    RewriteEngine On

    # Handle Authorization Header
    RewriteCond %{HTTP:Authorization} .
    RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]

    # Redirect Trailing Slashes If Not A Folder...
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_URI} (.+)/$
    RewriteRule ^ %1 [L,R=301]

    # Send Requests To Front Controller...
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^ index.php [L]
</IfModule>
```

### Levantar Docker:

```bash
docker-compose up -d
```

### Base de Datos:

- Las credenciales de la BD deben setearse en el .env

<hr/><br/>

### Comandos Utiles Docker:

```bash
# Levantar el entorno
docker-compose up -d

# Bajar el entorno
docker-compose down

# Borrar datos del entorno
docker-compose down -v

# Listar contenedores y buscar el id 
docker ps

# Mas informacion de un contenedor
docker inspect <container-id>
```

### Comandos Utiles Laravel:

```bash
# Ingresar a la bash del contenedor
docker exec -it <container-id> /bin/sh

# Borrar cache
php artisan optimize

# Borrar los archivos de la carpeta
\bootstrap\cache
```

