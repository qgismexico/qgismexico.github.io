+++
author = "@yoltotolhua"
title = "Animación en QGIS con el plugin MMQGIS"
date = "2017-05-08"
description = ""
tags = ["plugins"]
categories = ["Plugins"]
images  = ["/images/mmqgis.png"]
type = "post"
+++


El sábado 29 de Abril de 2017 se celebró el Festival Latinoamericano de Instalación de Software Libre ([FLISOL](https://flisol.info/FLISOL2017/Mexico/Ciudad_de_Mexico)) en el Rancho Electrónico. La comunidad QGIS México asistió con la siguiente presentación llamada "Animación de Mapas (Mediante QGIS), explorando la carta Hidrográfica de México".

En general, la platica se centro en el uso del mapa, como un insumo de información geográfica, parte fundamental de una Sistema de Información Geográfica \[[Tomlinson, 2008](http://downloads2.esri.com/ESRIpress/images/147/think3_ch1_SP.pdf)\].

![sig](/images/sig.jpg)

En el ámbito de software de código abierto existe el Movimiento [OSGEO](http://www.osgeo.org/) que tiene como objetivo "Apoyar y promover el desarrollo colaborativo de tecnologías y datos geoespaciales abiertos". Las categorías en que se subdividen las herramientas son:

Bibliotecas Geoespaciales Aplicaciones de escritorio WebMapping (server/client) Catálogos de metadatos geoespaciales Distribuciones

Especificamente, [QGIS](https://es.wikipedia.org/wiki/QGIS), es un software desarrollado por Gary Sherman en el año 2002, OSGEO lo adopto como proyecto en el año 2009 y la primera versión está disponible en el año 2009.

![qgis-icon_anita02](/images/qgis-icon_anita02.png)

La [carta hidrográfica de México](http://www.davidrumsey.com/luna/servlet/s/2s5o6d), realizada en el año 1885 por el Geográfo mexicano [Antonio García Cubas](https://es.wikipedia.org/wiki/Antonio_Garc%C3%ADa_Cubas), plasma de manera artística e ingenieril la longitud de los principales ríos,  así como las delimitación de cuencas hidrográficas en México. La mencionada carta fue obtenida de la Colección de [David Rumsey](http://www.davidrumsey.com/), que se encuentra fisicamente en la Biblioteca de la Universidad de Standford. A su vez, se recomienda explorar la Colección Dígital de la [Mapoteca de Manuel Orozco y Berra](http://w2.siap.sagarpa.gob.mx/mapoteca/) administrada por la SAGARPA a través del SIAP.

### Proceso de animación.

El primer paso consiste en la georreferenciación del mapa descargado de la colección dígital, esto por medio de la herramienta [georeference](http://www.qgistutorials.com/en/docs/georeferencing_basics.html). Los principales puntos de control son la ubicación de las ciudades como México, Monterrey, entre otras.

El segundo paso es empezar la digitalización de los ríos, para ello creamos una capa vectorial de líneas vacia, empezamos el modo de edición y "dibujamos" la trayectoria de los ríos, los corrientes principales y sus corrientes tributarias. Terminamos la edición.

![q0](/images/q0.jpg)

Con el plugin [MMQGIS](http://michaelminn.com/linux/mmqgis/), con el cual además de animaciones  de renglones, columnas de los atributos de una capa es posible otro tipo de operaciones. Seleccionamos la capa creada (ríos); timing "Different Line Speeds Animated Over Full Duration"; Duration de 50 frames y el directorio de salida.

Finalmente con el programa GIMP, realizamos la animación en un formato GIF, el resultado es el siguiente:

![animacionLerma](/images/animacionlerma.gif)

La animación se realiza sobre la Cuenca del Río Lerma, sabemos que los estudiosos en materia hidrológica, tendrán comentarios respecto de la velocidad y duración de la trayectoria, aunque esto es un ejercicio lúdico con fines de divulgación que permita el conocimiento de la importancia ambiental del agua. Por ello, recomendamos el libro "[Aguas con el Agua](https://www.imta.gob.mx/aguas-con-el-agua-disponible)" de Rius, quien de una forma divertida aborda este tema.

[![rius](/images/rius.jpeg)](https://www.imta.gob.mx/aguas-con-el-agua-disponible)

Agradecemos a [Rancho Electrónico](http://ranchoelectronico.org/) y a la comunidad QGISMéxico

Tlazohkamati

@yoltotolhua
