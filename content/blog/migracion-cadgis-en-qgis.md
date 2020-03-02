+++
author = "@yoltoltohua"
title = "Migración CAD/GIS en QGIS"
date = "2016-10-24"
description = ""
tags = [""]
categories = ["Tutoriales"]
images  = ["/images/screenshot-from-2016-10-16-16-26-44.png"]
type = "post"
+++

https://www.youtube.com/watch?v=lDS5orJvO4U

Una de las actividades más recurrentes para los que utilizamos SIG es la manipulación de información CAD. Años de uso y mal uso del software y formato estándar de facto, AutoCAD y su DWG, hacen que hoy en día cada que recibimos información en CAD para procesarla en un SIG.nos encontremos con diferentes situaciones, desde una mala referencia, trazos que no corresponden a su capa, escalado del dibujo, información fuera de la extensión del dibujo y un largo etcétera que se repetirá hasta que los usuarios de CAD no aprendan a trabajar correctamente o simplemente dejen de utilizar dicha plataforma.

Para la migración CAD/GIS que mostramos, nos vamos a centrar únicamente en la conversión de geometrías con sus respectivas capas. Para esto vamos a apoyarnos del software CAD de descarga gratuita Draftsight:

[http://www.3ds.com/products-services/draftsight-cad-software/free-download/](http://www.3ds.com/products-services/draftsight-cad-software/free-download/)

La principal razón es simplemente para la conversión DGW a DXF, si contamos con el software AutoCAD, también desde ahí se puede hacer la conversión o con cualquier otro software, lo importante es que la información vectorial se encuentre en DXF ya que es el formato que admite QGIS.

![screenshot-from-2016-10-16-16-16-03](https://qgismx.files.wordpress.com/2016/10/screenshot-from-2016-10-16-16-16-03.png?w=1024)

_Recomendaciones mínimas (ya que estamos en un entorno CAD):_

- _Todas las capas encendidas_
- _Información georreferenciada_
- _Conocer el sistema de coordenadas de referencia_
- _Vectores en sus capas correspondientes_
- _Extensión X Y delimitada_

Una vez que tengamos el archivo DWG abierto en Draftsight y hayamos hecho las recomendaciones mínimas, procedemos a guardarlo como DXF:

![peek-2016-10-16-16-22](/images/peek-2016-10-16-16-22.gif)

![screenshot-from-2016-10-16-16-19-06](https://qgismx.files.wordpress.com/2016/10/screenshot-from-2016-10-16-16-19-06.png?w=1024)![screenshot-from-2016-10-16-16-20-02](https://qgismx.files.wordpress.com/2016/10/screenshot-from-2016-10-16-16-20-02.png?w=1024)

Hecho lo anterios, cerramos Draftsight y abrimos QGIS.

Dentro de QGIS añadimos capa vectorial y filtramos por "AutoCAD DXF":

![screenshot-from-2016-10-16-16-26-44](/images/screenshot-from-2016-10-16-16-26-44.png)

Abrimos el archivo y QGIS nos pedirá el sistema de coordenadas de referencia en el que se encuentra la información, se la asiganmos:

![screenshot-from-2016-10-16-16-27-03](/images/screenshot-from-2016-10-16-16-27-03.png)

Después seleccionamos las entidades que contiene el archivo CAD y que queremos importar a QGIS, por cada entidad QGIS volverá a pedir el sistema de coordenadas de referencia.

![screenshot-from-2016-10-16-16-27-31](/images/screenshot-from-2016-10-16-16-27-31.png)

A continuación, la información vectorial se desplegará dentro de QGIS:

![screenshot-from-2016-10-16-16-31-26](https://qgismx.files.wordpress.com/2016/10/screenshot-from-2016-10-16-16-31-26.png?w=1024)

Por último, "guardamos como" shapefile (o el formato que queramos) cada un de las entidades que sean de nuestro interés:

![peek-2016-10-16-16-36](/images/peek-2016-10-16-16-36.gif)

Dividir por capas nuestra información vectorial.

Para dividir nuestras entidades de líneas y de puntos, con base a un atributo, en este caso verificamos que se encuentre el campo "Layer" en nuestros shapefiles recién exportados:

![screenshot-from-2016-10-20-21-17-53](/images/screenshot-from-2016-10-20-21-17-53.png)

Después de esto y con la herramienta "Split vector layer" dividimos nuestro shapefile en múltiples capas de acuerdo al contenido del campo "Layer":

Menú > Vector > Data Management Tools > Split vector layer

![peek-2016-10-20-21-23](/images/peek-2016-10-20-21-23.gif)

Se genera una capa por cada atributo distinto, cuyo nombre corresponde al nombre de la capa madre, el campo por el que se dividió y el nombre de la capa.

Aquí ya toca, depende de la información con la que estemos trabajando, hacer limpieza de las capas, renombrar las capas, convertir a polígonos, corregir campos, determinar si las capas son puntos, líneas o polígonos, etc.

![screenshot-from-2016-10-20-21-30-47](/images/screenshot-from-2016-10-20-21-30-47.png)

Dudas o comentarios con gusto serán respondidos, saludos.
