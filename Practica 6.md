# Práctica #6  Creación de un entorno WordPress con Docker Compose

## 1. Título

**Práctica No 6: Instalación de WordPress, MySQL y phpMyAdmin mediante el uso de Docker Compose**

## 2. Tiempo de duración

La duración estimada para esta práctica es de aproximadamente 1 hora.

## 3. Fundamentos

En esta práctica, se aplicarán los conocimientos sobre Docker y Docker Compose para definir y levantar un entorno completo de WordPress, incluyendo su base de datos MySQL y la herramienta de administración phpMyAdmin. Docker Compose simplifica la gestión de múltiples contenedores como una sola aplicación, utilizando un archivo `docker-compose.yml` para definir los servicios, las redes, los volúmenes y sus configuraciones.


## 4. Conocimientos previos

Docker es una plataforma que permite empaquetar aplicaciones y sus dependencias en contenedores, proporcionando un entorno aislado y consistente para su ejecución, como lo afirma **(Docker Documentation, 2025)**. La configuración de estos contenedores, especialmente cuando se gestionan múltiples servicios, se facilita mediante archivos YAML (`.yml`), un formato de serialización de datos legible por humanos que define la estructura y configuración de la aplicación según **(Docker Documentation, 2025)**.

En esta práctica, se utilizarán tres servicios principales. WordPress es un sistema de gestión de contenidos (CMS) de código abierto, ampliamente utilizado para la creación y administración de sitios web, que requiere una base de datos para almacenar su información según **(McGrath, 2018)**. MySQL es un sistema de gestión de bases de datos relacional (RDBMS) de código abierto, fundamental para el funcionamiento de WordPress, que permite organizar y acceder a los datos del sitio web afirma **(Davis, 2015**). Para la administración visual y sencilla de las bases de datos MySQL, se utiliza **phpMyAdmin**, una herramienta web escrita en PHP que ofrece una interfaz gráfica para la gestión de bases de datos, según lo afirmado por **(Wikimedia Foundation, 2022)**.

## 5. Objetivos a alcanzar

En la práctica se lograrán los siguientes objetivos:
- **Construir un archivo `docker-compose.yml` utilizando el formato YAML.**
- **Estructurar 3 servicios dentro del archivo `docker-compose.yml`: `wordpress`, `mysql` y `phpmyadmin`.**
- **Definir una red Docker dentro del archivo `docker-compose.yml` para la comunicación entre los servicios.**
- **Definir un volumen Docker dentro del archivo `docker-compose.yml` para la persistencia de los datos de MySQL y WordPress.**

## 6. Equipo necesario

- Computador con sistema operativo **MacOS 13.7.1** (o similar con Docker instalado).
- **Docker Desktop** instalado y en ejecución.
- Terminal de MacOS
- Editor de texto para crear y modificar el archivo `docker-compose.yml`.
- Conexión a Internet (para descargar las imágenes de Docker si no están disponibles localmente).

## 7. Material de apoyo

- Documentación oficial de Docker 
- Ejemplos de archivos `docker-compose.yml` para WordPress y MySQL.
- Video y material de Apoyo en el EVA

## 8. Procedimiento

**Paso 1**: Crear un directorio **service**  e ingresar dentro del mismo para la ejecución de los contenedores

Figura 1. **"Comando mkdir y cd "**.



**Paso 2:** Crear el archivo `docker-compose.yml` utilizando un editor de texto , **vi** en este caso, para crear y modificarlo.

Figura 2. **"Comando vi "**.



**Paso 3:** Definir el servicio `mysql`, esto incluye especificar la imagen , las variables de entorno necesarias para la configuración (contraseñas, nombre de la base de datos, usuario), la definición de un volumen para la persistencia de los datos y la asignación a una red.

Figura 3. **"Configuración de MYSQL "**.



**Paso 4:** Definir el servicio `wordpress`, esto incluye especificar la imagen, la dependencia del servicio `mysql`, la exposición del puerto 80 del contenedor al puerto 8080 del host, las variables de entorno para la conexión a la base de datos y la definición de un volumen para los archivos de WordPress y la asignación a la misma red.

Figura 3. **"Configuración de WordPress "**.



**Paso 4:** Definir el servicio `phpmyadmin`, esto incluye la imagen, la exposición del puerto 80 del contenedor al puerto 8081 del host , las variables de entorno para la conexión a MySQL y la asignación a la red.

Figura 4. **"Configuración de phpMyAdmin "**.



**Paso 5:** Definir la red `red-leo`de tipo `bridge` para permitir la comunicación entre los contenedores.

Figura 5. **"Configuración de la red "**.


**Paso 6:** Definir el volumen `mysql_data` para la persistencia de los datos de MySQL 

Figura 6. **"Configuración del volumen "**.


**Paso 7:** Levantar el entorno con Docker Compose, guardando el archivo `docker-compose.yml` y ejecutando el siguiente comando para iniciar los contenedores:

Figura 7. **"Comando  docker-compose up -d "**.


**Paso 8:** Verificar  la creación de los contenedores y el acceso una vez que los contenedores estén en funcionamiento, verificando su estado con el comando `docker-compose ps`.

Figura 8. **"Comando  docker-compose  ls"**.



## 9. Resultados esperados

La práctica permitió crear y gestionar contenedores Docker para WordPress, MySQL y phpMyAdmin, y aprender a conectar estos contenedores entre sí mediante una red personalizada en Docker. Después de completar todos los pasos, se logró configurar un entorno funcional de WordPress con su base de datos, utilizando un archivo `docker-compose.yml` que definió los tres servicios. Este archivo permitió automatizar la creación y configuración de los contenedores, estableciendo correctamente los volúmenes para la persistencia de datos y las redes para la comunicación entre los contenedores.

Una vez que los contenedores estuvieron en funcionamiento, se pudo acceder al panel de administración de WordPress a través de `http://localhost:8080` para realizar la instalación y configuración inicial del sitio.

Además, al acceder a phpMyAdmin mediante `http://localhost:8081`, fue posible visualizar y administrar la base de datos de WordPress de forma sencilla y gráfica, facilitando la gestión de tablas, usuarios y datos relacionados al sitio web.

La creación de una red personalizada en Docker, especificada en el archivo `docker-compose.yml`, garantizó una comunicación eficiente y segura entre los contenedores de WordPress, MySQL y phpMyAdmin.

## 10. Bibliografía

Davis, P. (2015). _MySQL: The comprehensive guide to building, programming, and administering MySQL databases_. O'Reilly Media.

Docker Documentation. (2025). _Docker: Documentation_. Recuperado de [https://docs.docker.com](https://docs.docker.com)

McGrath, M. (2018). _WordPress for dummies_. Wiley.

Wikimedia Foundation. (2022). _phpMyAdmin_. Recuperado de [https://www.phpmyadmin.net/](https://www.phpmyadmin.net/)
 