\# Implementación de WordPress con Docker Compose y Jenkins



\## Descripción del proyecto



Este proyecto implementa un ambiente completo de WordPress utilizando Docker Compose, integrando una aplicación WordPress con una base de datos MySQL. El ambiente utiliza una red personalizada, volúmenes persistentes, variables de entorno mediante un archivo `.env` y una configuración automatizada de despliegue mediante Jenkins.



El objetivo principal es crear un entorno reproducible, versionado mediante Git y con capacidad de redepliegue automático utilizando un Pipeline de Jenkins.



\## Tecnologías utilizadas



\* Docker

\* Docker Compose

\* WordPress

\* MySQL 8.0

\* Jenkins

\* Git

\* GitHub



\## Organización de archivos



La estructura principal del proyecto es:



```text

wordpress-docker/

│

├── docker-compose.yml

├── .env

├── Jenkinsfile

└── README.md

```



\### Descripción de archivos



\### docker-compose.yml



Contiene la configuración de los servicios Docker:



\* Servicio de WordPress.

\* Servicio de MySQL.

\* Red personalizada.

\* Volúmenes persistentes.

\* Puertos de comunicación.

\* Políticas de reinicio.

\* Variables de entorno.



\### .env



Archivo utilizado para almacenar variables de configuración del ambiente:



\* Nombre de la base de datos.

\* Usuario de la base de datos.

\* Contraseñas.

\* Configuración de WordPress.

\* Parámetros utilizados por Docker Compose.



\### Jenkinsfile



Archivo que contiene el Pipeline utilizado para automatizar el despliegue del ambiente.



Las etapas implementadas son:



1\. Checkout desde Git.

2\. Detener el ambiente actual utilizando Docker Compose.

3\. Levantar nuevamente los servicios mediante Docker Compose.

4\. Verificar los contenedores activos.



\### README.md



Documento de descripción y uso del proyecto.



\# Implementación con Docker Compose



\## Levantar el ambiente



Para iniciar los servicios ejecutar:



```bash

docker compose up -d

```



Este comando crea y ejecuta:



\* Contenedor de WordPress.

\* Contenedor de MySQL.

\* Red personalizada.

\* Volúmenes necesarios.





\## Verificar contenedores activos



Para comprobar que los servicios están funcionando:



```bash

docker ps

```



Se deben visualizar los contenedores:



\* `wordpress-app`

\* `wordpress-db`



\## Verificar redes Docker



Para comprobar la red creada:



```bash

docker network ls

```



La red permite la comunicación entre WordPress y MySQL.



\## Verificar volúmenes Docker



Para comprobar los volúmenes persistentes:



```bash

docker volume ls

```



Los volúmenes permiten conservar la información aunque los contenedores sean eliminados.



\# Validación de comunicación entre servicios



WordPress y MySQL se encuentran conectados mediante la red personalizada definida en Docker Compose.



Para verificar la configuración de los contenedores se puede utilizar:



```bash

docker inspect wordpress-app

```



y:



```bash

docker inspect wordpress-db

```



Dentro de la información mostrada se valida que ambos contenedores pertenecen a la misma red Docker.



\# Control de versiones con Git



El proyecto fue versionado utilizando Git y almacenado en GitHub.



Comandos utilizados:



Inicializar repositorio:



```bash

git init

```



Agregar archivos:



```bash

git add .

```



Crear commits:



```bash

git commit -m "Mensaje del commit"

```



Subir cambios al repositorio remoto:



```bash

git push

```



El proyecto cuenta con commits descriptivos para registrar los cambios realizados durante la implementación.



\# Automatización con Jenkins



Jenkins se utiliza para automatizar el despliegue del ambiente Docker.



El Pipeline definido en el archivo `Jenkinsfile` contiene las siguientes etapas:



\## 1. Checkout desde Git



Jenkins obtiene la versión más reciente del proyecto desde el repositorio GitHub.



\## 2. Detener ambiente actual



Ejecuta:



```bash

docker compose down

```



Además elimina contenedores anteriores para permitir un nuevo despliegue.



\## 3. Levantar ambiente nuevamente



Ejecuta:



```bash

docker compose up -d

```



Este proceso crea y ejecuta nuevamente los servicios definidos en Docker Compose.



\## 4. Verificar despliegue



Ejecuta:



```bash

docker ps

```



para comprobar que los contenedores estén activos correctamente.





\# Acceso a WordPress



Después de levantar el ambiente, el asistente inicial de instalación de WordPress está disponible en:



```text

http://localhost:8080

```



Desde esta dirección se puede completar la configuración inicial del sitio.



\# Servicios desplegados



\## WordPress



Contenedor encargado de ejecutar la aplicación web.



Nombre del contenedor:



```text

wordpress-app

```



Puerto utilizado:



```text

8080

```



\## MySQL



Contenedor encargado de almacenar la información de WordPress.



Nombre del contenedor:



```text

wordpress-db

```



Puerto interno:



```text

3306

```



\## Jenkins



Servicio utilizado para automatizar el despliegue mediante Pipeline.



Puerto de acceso:



```text

http://localhost:8081

```



\# Resultado esperado



Al finalizar la implementación se obtiene:



\* Ambiente WordPress funcional.

\* Base de datos MySQL conectada.

\* Persistencia mediante volúmenes Docker.

\* Comunicación mediante red personalizada.

\* Proyecto versionado en GitHub.

\* Despliegue automatizado mediante Jenkins.

\* Pipeline ejecutado correctamente.



