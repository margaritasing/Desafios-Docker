### Crea el contenedor de Nginx con el siguiente comando:
docker run -d -p 9999:80 --name bootcamp-web nginx
.- Este comando creará un contenedor de Nginx con el nombre "bootcamp-web" y expondrá el puerto 80 del contenedor en el puerto 9999 de tu máquina local (-p 9999:80).

### Copia el contenido de la carpeta web en la ruta que sirve el servidor web en el contenedor de Nginx. Para hacer esto, primero debes obtener el ID del contenedor de Nginx:
docker ps
.- Este comando mostrará una lista de todos los contenedores en ejecución en tu sistema. Busca el contenedor "bootcamp-web" y toma nota de su ID.

### Luego, copia el contenido de la carpeta "web" al contenedor con el siguiente comando:
docker cp web/. <CONTAINER_ID>:/usr/share/nginx/html
docker cp web/.c220b921c9e6:/usr/share/nginx/html
.- Reemplaza <CONTAINER_ID> con el ID del contenedor de Nginx que tomaste nota antes.

### Ejecuta dentro del contenedor la acción ls, para comprobar que los archivos se han copiado correctamente. Para hacer esto, primero debes ingresar al contenedor de Nginx:
docker exec -it bootcamp-web /bin/bash
.- Este comando te llevará a una terminal interactiva dentro del contenedor. Desde aquí, puedes ejecutar el comando "ls" para verificar que los archivos se han copiado correctamente:

ls /usr/share/nginx/html

.- Este comando mostrará una lista de todos los archivos y carpetas en la ruta del servidor web. Si ves los archivos que esperas, entonces todo se ha copiado correctamente.

### Hacer que el servidor web sea accesible desde el puerto 9999 de tu máquina local. Este paso ya lo hicimos en el primer comando que ejecutamos para crear el contenedor, pero si necesitas cambiar el puerto, puedes detener el contenedor con docker stop bootcamp-web y luego crear el contenedor nuevamente con el puerto deseado.

.- ¡Listo! Ahora puedes acceder al servidor web de Nginx desde tu navegador web en http://localhost:9999.