# PPS-Unidad1-Actividad1-JulioManuelTatoPulido

Tenemos varios objetivos:

> [Crear un entorno de desarrollo Eclipse con docker](#Eclipse-Docker)

> [Instalar extensiones en un IDE](#Instalar-extensiones)

> [Probar los entornos de Desarrollo](#Prueba-entornos) 
---
## Eclipse Docker

1. Primero creamos las carpetas necesarias y cambiamos el propietario:
~~~
sudo mkdir -p  $HOME/docker/eclipse/datos
sudo chown -R kali:kali eclipse
~~~

2. Configuramos el entorno gráfico:

~~~
export DISPLAY=:0
startxwin -- -listen tcp &
xhost + 
~~~

3. Lanzamos el contenedor:

~~~
sudo docker run -ti --rm \
           --ulimit nofile=8096:8096\
           -e DISPLAY=$DISPLAY \
	       -e artifactory_host='IP:PUERTO'\
		   --name eclipse \
           -v /tmp/.X11-unix:/tmp/.X11-unix \
           -v `pwd`:/workspace \
           -v $HOME/docker/eclipse/datos:/home/developer \
           dockeruc/eclipse
~~~

<div align="center">
  <img src="2.png" width="300">
</div>

## Instalar extensiones

Las dos extensiones que comentaré a continuación han sido instalados en Visual Studio, que va a ser el IDE que vaya a utilizar en estas prácticas.

### Checkstyle

Checkstyle es un plugin que se utiliza para verificar que el código siga un estándar de estilo definido. Es ideal para mantener la coherencia en equipos grandes, revisando el formato y la estructura del código automáticamente.

<div align="center">
  <img src="3.png" width="300">
</div>

### Sonar Lint

SonarLint es un pligun que se utiliza para corregir el código en tiempo real. Detecta errores, vulnerabilidades y problemas de calidad mientras escribes, y funciona con varios lenguajes. Además, ayuda a mejorar la seguridad y limpieza del código desde el principio.

<div align="center">
  <img src="4.png" width="300">
</div>

## Prueba entornos

Para empezar he instalado en Visual Studio la extensión de Python:

<div align="center">
  <img src="7.png" width="300">
</div>

Después he instalado en mi Windows la aplicación de Python 3.11:

<div align="center">
  <img src="8.png" width="300">
</div>

Después, he accedido al repoistorio del profesor, donde nos ha dejado diferentes proyectos de calculadoras, para poder probarlos en nuestro IDE:

<div align="center">
  <img src="5.png" width="300">
</div>

Pudiendo comprobarlo así con la extensión instalado en Visual Studio:

<div align="center">
  <img src="6.png" width="300">
</div>