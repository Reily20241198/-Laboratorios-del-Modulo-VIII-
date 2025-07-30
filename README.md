# -Laboratorios-del-Modulo-VIII-
Práctica 1: Instalación y configuración de Docker (1 Punto)
1. INSTALACIÓN DE DOCKER EN EL SERVIDOR
----------------------------------------
# Actualizamos el sistema e instalamos Docker
sudo dnf update -y
sudo dnf install -y docker

# Habilitamos e iniciamos el servicio de Docker
sudo systemctl enable --now docker

# Verificamos que Docker esté corriendo
sudo systemctl status docker

------------------------------------------------------------
2. DESCARGA DE IMAGEN DE NGINX DESDE DOCKERHUB
------------------------------------------------------------
# Descargar la imagen oficial de nginx desde Docker Hub
sudo docker pull nginx

------------------------------------------------------------
3. CREACIÓN DE UN CONTENEDOR NGINX CON PUERTO REDIRECCIONADO Y VOLUMEN PERSISTENTE
-----------------------------------------------------------------------------------
# Crear una carpeta local para el contenido web (página HTML)
mkdir -p /home/website

# Crear el contenedor mapeando:
# - el puerto 8888 del host al puerto 80 del contenedor
# - el volumen /home/website del host a /usr/share/nginx/html/ en el contenedor
sudo docker run -d --name web_nginx -p 8888:80 -v /home/website:/usr/share/nginx/html nginx

------------------------------------------------------------
4. CREACIÓN Y COPIA DE LA PÁGINA HTML AL VOLUMEN PERSISTENTE
------------------------------------------------------------
# Crear un archivo HTML sencillo
echo "<!DOCTYPE html>
<html>
<head>
  <title>Mi Página</title>
</head>
<body>
  <h1>Nombre: Reily Castillo Del Rosario</h1>
  <h2>Matrícula: 20241198</h2>
</body>
</html>" > /home/website/index.html

------------------------------------------------------------
5. VERIFICACIÓN EN EL NAVEGADOR
------------------------------------------------------------
# Abrir el navegador y acceder a:
http://127.0.0.1:8888

# Esto mostrará la página HTML servida por NGINX desde el contenedor.
v
