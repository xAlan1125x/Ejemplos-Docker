WordpressDB
--mount source=wordpress-db,target=/var/lib/mysql:
    Crea un Volumen llamado "wordpress-db". Esto sirve para que, si borras el contenedor, tus publicaciones y configuraciones de la base de datos no se pierdan.

-e MYSQL_...:
    Son Variables de Entorno. Aquí se define la contraseña del root, el nombre de la base de datos (wordpress) y el usuario con su clave.

mariadb:10.3.9:
    La imagen oficial de MariaDB que se descargará.

Wordpress
--link wordpress-db:mysql:
    Este es el "puente". Permite que el contenedor de WordPress se comunique con el de la base de datos usando el nombre mysql.

--mount type=bind,source="$(pwd)"/wordpress,target=/var/www/html:
    Esto es un Bind Mount. Sincroniza la carpeta /wordpress de tu computadora actual con la carpeta del servidor dentro del contenedor. Cualquier cambio que hagas en tu PC se verá reflejado al instante.

-p 8080:80:
    Mapea el puerto 8080 de tu PC al 80 del contenedor.

    