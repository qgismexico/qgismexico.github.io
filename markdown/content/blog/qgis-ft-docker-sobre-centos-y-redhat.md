+++
author = "@yoltoltohua"
title = "QGIS ft Docker sobre CentOS y RedHat"
date = "2019-12-25"
description = ""
tags = [""]
categories = ["Tutoriales"]
images  = ["/images/qgis_docker.png"]
type = "post"
+++

**Ing. Federico Fabián Jiménez Esparza** \[ffabianjimenez@gmail.com\]

QGIS puede ser instalado en varias distribuciones y versiones de Linux, sin embargo, en CentOs y RedHat no es compatible con las últimas versiones de Qgis 3.X en adelante. Dado lo anterior y después de invertir 30 días intentando instalar **Qgis 3.x en Centos/RedHat 7/8**, me he encontrado con un sin fin de dependencias y aplicativos con versiones específicas, las cuales se contraponen unas con otras; decidí que la mejor opción para mi caso, es la instalación de **Docker** con su correspondiente **container** de **QGIS**.

Cabe hacer mención que la instalación de **QGIS** sobre **Ubuntu 18.04** es algo fácil y directo. Si se cuenta con dicho S.O. no es necesario la instalación de Docker, a menos que quieras mantener encapsulado dicho software.

Un **container** a primera vista pareciera ser una **maquina virtual**, sin embargo, no lo es, ya que su objetivo principal es ofrecer micro servicios, por lo que no esperes que QGIS se ejecute como un GUI, sino que su uso será por medio de **CLI**. La intención de esta publicación  no es la instalación, explicación, funcionamiento y configuración de Docker, por lo que si quieres documentarte al respecto, visita la [página oficial](https://www.docker.com/resources/what-container). Aquí solo explicaré de manera general y concisa la instalación y ejecución de Docker; posteriormente descarga y ejecución de QGIS por medio de un container.

#### **Instalación y ejecución de Docker bajo Centos / RedHat**

Comando

Explicación

#yum-utils y device-mapper-persistent-data

Instalación de paquetes necesarios para Docker.

#yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

Se agrega el repositorio para la instalación del Docker.

#yum install docker-ce docker-ce-cli containerd.io

Instalación del Docker

Si en el último comando desplegara un error de Dependency: **container-selinux >= 2:2.74 for package: containerd.io-1.2.6-3.3.el7.x86\_64** se puede hacer lo siguiente:

Bajar el archivo **containerd.io-1.2.6-3.3.el7.x86\_64**  de la siguiente URL [http://mirror.centos.org/centos/7/extras/x86\_64/Packages/](http://mirror.centos.org/centos/7/extras/x86_64/Packages/) e instalarlo con el comando

 **#rpm –ivh containerd.io-1.2.6-3.3.el7.x86\_64 .rpm**

Si tenemos la activación con **RedHat**, activar el repositorio de extras e instalarlo subscription-manager repos --enable=rhel-7-server-extras-rpms

El fingerprint deberá de ser **060a 61c5 1b55 8a7f 742b 77aa c52f eb6b 621e 9f35**

Con lo anterior, ya se tiene instalado la parte de docker, ahora lo que tenemos que hacer es hacer que se levante el servicio de manera automática cada vez que se reinicie el servidor:

Comando

Explicación

#systemctl start docker

Inicio del daemon de Docker

#systemctl stop docker

Parar el daemon de Docker

Con lo anterior, ya estará ejecutando el servicio de Docker sobre nuestro servidor.

#### **Descarga y ejecución de QGIS**

Primeramente, buscaremos las imágenes disponibles que se tienen para **QGIS**, esto será por medio de comando “**Docker search qgis**”

![](/images/image-4.png)

Como se puede observar, existen varias imágenes que se pueden descargar, sin embargo, para este caso, se descargara la denominada “**qgis/qgis**” que es el **oficial**.

#docker pull qgis/qgis

En este paso comenzara a descargarse la imagen correspondiente sobre nuestro servicio de **Docker**. La versión de la imagen “**qgis/qgis**” contiene un **Ubuntu 18.04.3 LTS con QGIS 3.10**

Una vez que ya se ha terminado el proceso de descarga de la imagen de QGIS, hay que levantarla o si se quiere ver así, hay que levantar nuestro micro servicio de QGIS para su acceso mediante el siguiente comando.

#docker run  --rm - qgis/qgis bash

Con lo anterior, pareciera que ya hemos terminado, sin embargo, apenas estamos empezando el arduo camino para la configuración y puesta a punto de QGIS, lo cual depende de que es lo que queramos hacer.

Dado que **Docker** se maneja por medio de micro servicios y no es una máquina virtual, implicara que al momento de bajar este se perderá lo grabado en la imagen, pero podemos hacer que se graben nuestros cambios por medio de comandos de **Docker**.

#### **Ejemplo**

Para explicar esto de una manera más fácil y práctica, supondremos la siguiente situación.

1. Se quiere servidor con **Qgis 3.x**
2. Acceder al **Docker** por medio de **ssh** (No recomendable es un micro servicio)
3. Se requiere un **Tomcat** en dicho servidor y que acceda a **Qgis** antes instalado
4. El acceso del **Tomcat** será por medio de una **intranet**.

El **paso 1**, es lo que hemos hecho anteriormente, por lo que ya está solucionado.

Para el **paso 2**, solo hay que acceder a la imagen mediante el siguiente comando e instalar el servicio de **openssh-server** sobre el **puerto 22**. Para mi caso, ya se tiene instalado el paquete de **openssh-server**

#docker stats

![](/images/image-5.png)

Para el **paso 3**, es muy sencillo, por lo que recomienda que se baje alguna versión de **Java (1.8.0\_65) y Tomcat (apache-tomcat-8.0.23)** de los sitios oficiales, descompactación y configuración de los mismos.

Como se comentó inicialmente, al ser un **micro-servicio**, no se guardan los cambios realizados de manera automática, por lo que desde una terminal del servidor **host** se deberá de teclear un comando como se indica para que guarde los cambios.

#docker commit -m "Instalacion Qgis con Java, Tomcat y OpenSsh" --author "Tu nombre" df7fc65aebbf qgis/qgis:V2

Donde **df7fc65aebbf** es el **ID** de la imagen que está corriendo.

Con lo anterior, se hizo una **copia (versión)** de la imagen de Qgis y con los componentes que se instalaron. Cabe hacer mención que ahora tenemos dos imágenes y que pueden ser tantas como se guste.

![](/images/image-6.png)

Para el **paso 4**. debemos de tener en cuenta de que, al ser un micro servicio, este no debería de contar con una **IP** propia externa (aunque si la tiene, pero es interna), y que su acceso es por la **IP** del **hosting**, es decir, del servidor en cual se instalado el **Docker**, entonces lo que se hará en este paso es el redireccionamiento de puertos. Como se puede ver en la siguiente imagen, la **IP** del **container** es **172.17.0.1.**

![](/images/image-7.png)

Entonces, para hacer el re direccionamiento debemos indicarle a Docker que deberá de tener disponible los **puertos 8080 (Tomcat)** y **22 (Ssh)** al momento de que este levanta, por lo que debemos de bajar la **imagen** del Docker y levantarla de la siguiente manera:

#docker run --hostname serqgis  --rm -it  -p 8080:22 qgis/qgis:v2  bash

Creación de una regla de iptables para el redireccionamiento del servidor.

iptables -t nat -A DOCKER -p tcp --dport 8081 -j DNAT --to-destination 172.17.0.2:8080

iptables -t nat -A DOCKER -p tcp --dport 8082 -j DNAT --to-destination 172.17.0.2:22

Suponiendo que la **IP** de nuestro hosting es **10.108.10.120**, entonces si queremos acceder al **Tomcat** instalado en el **container** se haría con la **URL** [http://10.108.10.120:8081](http://10.108.10.120:8081) y para el acceso via **ssh** seria con

 $ssh [root@10.108.10.120](mailto:root@10.108.10.120) -p 8082

> _La comunidad QGISMexico agradece la colaboración del_
>
> **_Qgisero Ing. Federico Fabián Jiménez Esparza por la redacción de este tutorial._**

🌎🐧🌎🐧🌎
