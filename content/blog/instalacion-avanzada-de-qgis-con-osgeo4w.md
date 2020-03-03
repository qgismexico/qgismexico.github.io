+++
author = "@yoltoltohua"
title = "Instalación Avanzada de QGIS con OSGeo4W"
date = "2016-10-10"
description = ""
tags = [""]
categories = ["Tutoriales"]
images  = ["/images/banner-2.jpg"]
type = "post"
+++

## Instalando por primera vez

Bienvenidos al primer tutorial del blog del grupo de usuarios de QGIS México, hoy vamos a ver como instalar QGIS en modo avanzado usando una pequeña aplicación, _**OSGeo4W**_, creada por la [Open Source Geospatial Foundation](http://www.osgeo.org/content/foundation/about.html) (OSGeo). Está fundación sin ánimo de lucro nació con el objetivo de promover el software libre geoespacial siendo una organización con una filosofía abierta y una comunidad de programación colaborativa que se dedica a incubar y organizar diversos proyectos de software geoespacial.

Dada la frecuencia con la que actualiza QGIS muchas veces es mejor utilizar [Osgeo4w](https://trac.osgeo.org/osgeo4w/) para instalar y actualizar QGIS que la versiones 'standalone' que podemos obtener desde la página de [QGIS](http://qgis.org). ¿Qué es **OSGeo4W**? Es un sistema de distribución de software geoespacial de código abierto para sistemas operativos Windows de 32 y 64 bits. Incluye programas como GRASS, UDig, GDAL, QGIS, Orfeo Toolbox, Mapserver, etc.

Antes de empezar la instalación, si tenemos una versión previa de QGIS es bueno desinstalarla para evitar que pueda haber algún conflicto con la nueva versión que vamos a instalar. Toda nuestra configuración se almacena en la carpeta C:\\Users\\nombre\_de\_usuario\\.qgis2. Está carpeta se encuentra oculta así que para encontrarla tal vez tengamos que permitir que Windows nos deje ver las carpetas ocultas. Otra recomendación es usar un nombre de usuario que no contenga ni acentos ni espacios en blanco ya que esto en ocasiones puede resultar un problema para algunos programas.

Después debemos descargar **OSGeo4W** y para ello necesitamos la versión acorde al sistema operativo que tengamos, [32](http://download.osgeo.org/osgeo4w/osgeo4w-setup-x86.exe) o [64](http://download.osgeo.org/osgeo4w/osgeo4w-setup-x86_64.exe) bits. Una vez descargado lo corremos y nos mostrará la primera pantalla (Figura 1).

\[caption id="attachment\_87" align="aligncenter" width="602"\]![osgeo4w1](/images/osgeo4w1.png) Tipo de Instalación\[/caption\]

Aquí debemos seleccionar la primera opción Express Desktop Install - Instalación Express para Escritorio y después hacer click en Siguiente lo que nos llevará a la siguiente pantalla.

\[caption id="attachment\_88" align="aligncenter" width="602"\]![osgeo4w2](/images/osgeo4w2.png) Seleccionar paquetes\[/caption\]

En ella podemos ver que se han marcado los componentes mínimos para la instalación de QGIS: QGIS, GDAL y GRASS GIS. Dejamos las opciones por defecto y damos click en Siguiente. Esto nos instalará la versión más actual de QGIS (a la fecha 2.16.3). Si queremos instalar la versión LTR (long term release - versión de larga duración) tendremos que hacerlo desde la opción _Advanced Install_ y seleccionar el paquete para su instalación, lo veremos más adelante.

\[caption id="attachment\_89" align="aligncenter" width="602"\]![osgeo4w3](/images/osgeo4w3.png) Fuente de la instalación\[/caption\]

Esta pantalla nos permite seleccionar si queremos instalar desde Internet (Install from Internet) o si queremos descargar sin instalar o instalar desde un directorio local. Marcamos _Install from Internet_ y hacemos click en Siguiente.

\[caption id="attachment\_90" align="aligncenter" width="602"\]![osgeo4w4](/images/osgeo4w4.png) Directorio de instalación\[/caption\]

En esta pantalla le vamos a indicar dónde queremos instalar OSGeo4W y todos sus componentes. Les recomiendo seleccionar un directorio que esté en C:\\ o en alguna carpeta como C:\\Archivos de Programa. Nunca en su directorio de Mis Documentos. Una vez hayamos seleccionado la carpeta de instalación hacemos click en Siguiente.

\[caption id="attachment\_91" align="aligncenter" width="602"\]![osgeo4w5](/images/osgeo4w5.png) Directorio de descarga\[/caption\]

En esta pantalla se nos pregunta donde queremos que se almacén los archivos descargados antes de instalarlos, en este caso he seleccionado la carpeta de Descargas de mi sistema aunque podemos usar cualquier carpeta que nos convenga. Muchas veces es bueno no borrar esta carpeta para en caso de algo falle y queramos volver a instalar algo podamos usar los archivos previamente descargados. De nuevo hacemos click en Siguiente.

![osgeo4w6](/images/osgeo4w6.png)

Dejamos por defecto (a no ser que estemos detrás de un proxy) y hacemos click en Siguiente.

![osgeo4w7](/images/osgeo4w7.png)

Para finalizar, dejamos la opción por defecto y hacemos click en Siguiente. En este momento empezará la descarga e instalación de todo el software que hemos seleccionado QGIS, GDAL y GRASS.

![osgeo4w8](/images/osgeo4w8.png)

Cuando termine la instalación tendremos QGIS funcionando al 100%.

## Actualización

En el caso de que queramos actualizar a una nueva versión de QGIS habiendo ya hecho la instalación con QGIS debemos hacer el siguiente proceso. Corremos OSGeo4W o buscamos 'Setup' en el menú de Inicio de Windows y lo corremos.![osgeo4w9](/images/osgeo4w9.png)

Nos aparecerá la ventana de instalación que ya conocemos pero en este caso seleccionamos 'Advanced Install' y hacemos click en Siguiente.

![osgeo4w10](/images/osgeo4w10.png)

Esto nos llevará al menú de Paquetes de OSGeo4W donde podemos explorar los paquetes que se van a instalar durante la actualización. No hace falta que hagamos nada. Simplemente hacemos click en Siguiente y vamos aceptando todas las ventanas como hicimos durante el proces de instalación. OSGeo4W detectará qué versiones han cambiado y las actulizará por nosotros sin que tengamos que hacer nada más.

## Instalación de la versión LTR

La versión LTR es la recomendada para entornos de producción ya que se actualiza una vez al año, no contiene los últimos avances de la versión normal de QGIS pero es mucho más estable, recibiendo actualizaciones menores y correcciones de bugs durante todo su periodo de vida.

Para instalar la versión LTR tenemos que entrar en la opción _Advanced Install_ y seleccionar el paquete LTR. Para ello primero marcamos el modo avanzado y hacemos click en Siguiente.

El siguiente paso consiste en seleccionar el paquete qgis-ltr. Para ello como podemos ver en la imagen hemos introducido en la ventana de Search la palabra qgis lo que nos muestra todos los paquetes relacionados con el termino. Ahora solo tenemos que marca el paquete para instalación, para ello hacemos click en _**Skip **_hasta que nos aparezca la versión del paquete qgis-ltr que queremos instalar. Para finalizar simplemente hacemos click en siguiente y OSGeo4W se encargará de seleccionar el resto de paquetes que necesitamos para terminar la instalación. El resto del proceso ya es el habitual haciendo click en Siguiente hasta que comience la instalación.

![osgeo4w13](/images/osgeo4w13.png)

Esperamos os haya resultado de interés el tutorial y deseando verlos en el próximo tutorial del grupo de usuarios QGIS México.

Feliz SIG a Todos!
