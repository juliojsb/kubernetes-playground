# Preparación entorno para Laboratorios de docker

## 1. Creación maquina virtual Ubuntu para instalar docker:

https://www.manusoft.es/linux/configurar-una-maquina-virtual-con-ubuntu-en-virtualbox/

Añadir guest additions:

https://kifarunix.com/install-virtualbox-guest-additions-on-ubuntu-20-04/

## 2. Instalar docker:

https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository

## 3. Comprobar versión de Docker
Podemos comprobar la versión de Docker ejecutando el comando

	$ docker --version

y de esta manera nos aseguraremos de tener una versión compatible de Docker.

O ejecutando los siguientes comando podemos ver aún más detalles sobre la instalación de nuestro docker

	$ sudo docker --version
	Docker version 20.10.21, build baeda1f

	$ sudo docker info
	Client:
	 Context:    default
	 Debug Mode: false
	 Plugins:
	  app: Docker App (Docker Inc., v0.9.1-beta3)
	  buildx: Docker Buildx (Docker Inc., v0.9.1-docker)
	  compose: Docker Compose (Docker Inc., v2.12.2)
	  scan: Docker Scan (Docker Inc., v0.21.0)
	...

## 4. Comprobar instalación de Docker

4.1. En un terminal de la máquina virtual, ejecute los siguientes comandos para comprobar que inicialmente no hay ningún contenedor creado
(la opción -a hace que se muestren también los contenedores detenidos, sin ella se muestran sólo los contenedor que estén en
marcha):

	$ sudo docker ps -a

o también

	$ sudo docker container ls -a

	CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS
	PORTS               NAMES

4.2. Compruebe que inicialmente tampoco hay de ninguna imagen en local:

	$ sudo docker image ls

	REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE

4.3. Docker crea los contenedores a partir de imágenes locales (ya descargadas), pero si al crear el contenedor no se dispone de la imagen local, Docker descarga la imagen de su repositorio público. Ejecutar el siguiente comando para crear un contendor con la aplicación de ejemplo `hello-world`. La imagen de este contenedor se llama `hello-world`:

	$ sudo docker run hello-world

Como no tenemos todavía la imagen en registro local, Docker descarga la imagen, crea el contenedor y lo pone en marcha.
En este caso, la aplicación que contiene el contenedor `hello-world` simplemente escribe un mensaje de salida al arrancar e inmediatamente se detiene el contenedor. La respuesta será similar a esta:

	Unable to find image 'hello-world:latest' locally
	latest: Pulling from library/hello-world
	1b930d010525: Pull complete
	Digest: sha256:4fe721ccc2e8dc7362278a29dc660d833570ec2682f4e4194f4ee23e415e1064
	Status: Download newer image from hello-wolrd:latest

	Hello from Docker!
	This message shows that your installation appears to be working correctly.
	...

4.4. Si listamos ahora las imágenes existentes ...

	$ sudo docker image ls

... se mostrará información de la imagen creada:

	REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
	hello-world         latest              fce209e99eb9        4 weeks ago         1.84 kB

Si listamos ahora los contenedores existentes ...

	$ sudo docker ps -a

... se mostrará información del contenedor creado:

	CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS
	PORTS               NAMES
	614B4c431ffa        hello-world         "/hello"            2 minutes ago       Exited (0) 2 minutes
	ago                 hopeful_elbakyan
