#  Simple Attendance Management System - Docker Deployment

Este proyecto es un sistema de gestión de asistencia desplegado con **Docker** y compuesto por los siguientes servicios:
- **MySQL**: Base de datos que almacena la información del sistema.
- **PHP-FPM**: Servidor de aplicaciones PHP que ejecuta la lógica del sistema.
- **NGINX**: Servidor web que actúa como proxy inverso y sirve el frontend.

---

## 📂 **Estructura del Proyecto**
```
📁 Deployment_web/
 ├── 📂 mysql/                # Archivos de inicialización para MySQL
 │   └── script.sql           # Script de base de datos
 ├── 📂 php/                  # Código de la aplicación PHP
 │   ├── index.php            # Página principal
 │   ├── db-connect.php       # Conexión a la base de datos
 │   ├── classes/             # Clases PHP para la lógica del sistema
 │   ├── assets/              # Archivos estáticos (CSS, JS)
 ├── 📂 nginx/                # Configuración de Nginx
 │   ├── nginx.conf           # Archivo de configuración
 │   ├── Dockerfile           # Imagen personalizada de Nginx
 ├── 🐳 docker-compose.yaml   # Definición de servicios Docker
 ├── 📄 README.md             # Documentación del proyecto
```

---

##  **Requisitos Previos**
Antes de iniciar el proyecto, asegúrate de tener instalados:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

---

##  **Instalación y Uso**

### ** 1️-Clonar el Repositorio**
```bash
git clone https://github.com/Vikolow/Deployment_web.git
cd Deployment_web
```

### ** 2️-Configurar la Base de Datos**
El sistema usa MySQL, y los datos de acceso están predefinidos en `docker-compose.yaml`:
```yaml
MYSQL_ROOT_PASSWORD: 1234
MYSQL_DATABASE: simple_attendance_db
MYSQL_USER: root
MYSQL_PASSWORD: 1234
```
Si necesitas cambiar las credenciales, edítalas en `docker-compose.yaml`.

---

### ** 3️-Construir y Levantar los Contenedores**
Ejecuta el siguiente comando para descargar las imágenes y construir los servicios:
```bash
docker-compose up -d --build
```
Esto iniciará:
- **MySQL** en `localhost:3306`
- **PHP-FPM** conectado con MySQL
- **NGINX** sirviendo la aplicación en `http://localhost`

Para ver los contenedores en ejecución:
```bash
docker ps
```

---

## 4- **Administración de Contenedores**
Si necesitas detener los servicios:
```bash
docker-compose down
```

Si quieres limpiar los volúmenes y eliminar la caché:
```bash
docker-compose down -v
```

Para reconstruir la aplicación:
```bash
docker-compose up -d --build
```

---

##  **Notas Adicionales**
- Si `mysql` no inicia correctamente, revisa los logs:
  ```bash
  docker logs mysql-db
  ```
- Para acceder a MySQL dentro del contenedor:
  ```bash
  docker exec -it mysql-db mysql -uroot -p
  ```
- Si necesitas depurar la aplicación, revisa los logs de PHP:
  ```bash
  docker logs php-app
  ```
- 
---



