+++
author = "@yoltoltohua"
title = "Instalación de Orfeo Toolbox para QGIS"
date = "2016-11-06"
description = ""
tags = [""]
categories = ["Tutoriales"]
images  = ["/images/osgeo4w9.png"]
type = "post"
+++

## ¿Qué es Orfeo Toolbox?

[Orfeo Toolbox (OTB)](https://www.orfeo-toolbox.org/) es un proyecto de software de código abierto dedicado a la teledetección. Puede procesar imágenes ópticas multiespectrales de alta resolución o SAR y cuenta con herramientas para ortorectificar, fusionar, segmentar, filtrar y clasificar imágenes. Principalmente está orientado al uso de imágenes Pleiades pero podemos usarlo con cualquier imagen satelital (o aérea).

OTB cuenta con un interfaz gráfico llamado Monteverdi pero sus herramientas pueden ser utilizadas desde QGIS, Python, la linea de comando o a través de una potente API en C++.

El proyecto está siendo desarrollado por el **CNES** (Centro Nacional de Estudios Espaciales, Francia), la empresa **CS Systemes d’Information **y la comunidad de usuarios de OTB.

## ¿Cómo lo instalamos?

En Windows, es muy sencillo, para simplificar la tarea vamos a utilizar OSGeo4W, del cual ya hemos hablado en otra entrada del blog.

Para comenzar corremos OSGeo4w y seleccionamos _Advanced style_. Vamos a hacer click en siguiente hasta que lleguemos al menú de selección de paquetes.

![osgeo4w9](/images/osgeo4w9.png)

Una vez en el menú de selección de paquetes, escribimos OTB en la caja de _Search_, para que nos filtre los paquetes de OTB. Como vemos aparecen los paquetes otb-Monteverdi (el interfaz gráfico), otb-bin (las herramientas de la linea de comandos necesarias para corrrer el programa) y otb-python, la api de Python para OTB.

![instalacion_otb_1](/images/instalacion_otb_13.png)

Haciendo click en la palabra _Skip _aparecerá el número de la versión que vamos a instalar. En este caso la 5.0.0., aunque desde la página web de OTB podemos descargar la 5.6.1.

![instalacion_otb_2](/images/instalacion_otb_2.png)

Para finalizar hacemos click en siguiente y esperamos hasta que se descarguen e instalen los paquetes.Ahora que está instalado solo tenemos que asegurarnos de que el proveedor esté activado en el las opciones del menú Procesos de QGIS.

![instalacion_otb_3](/images/instalacion_otb_3.png)

![instalacion_otb_4](/images/instalacion_otb_4.png)

Una vez activado el proveedor ya podremos utilizar las herramientas de OTB desde la caja de herramientas de proceso de QGIS.

![instalacion_otb_6](/images/instalacion_otb_6.png)

A continuación puedes ver una imagen del interfaz gráfico de OTB, Monteverdi. Espero te haya resultado de interés la entrada y volvamos a vernos pronto.![instalacion_otb_5.png](/images/instalacion_otb_5.png)
