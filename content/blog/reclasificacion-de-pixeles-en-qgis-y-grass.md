+++
author = "@yoltoltohua"
title = "Reclasificación de pixeles en #QGIS y #GRASS"
date = "2017-11-22"
description = ""
tags = [""]
categories = ["Tutoriales"]
images  = ["/images/1.png"]
type = "post"
+++

## En este tutorial reclasificaremos pixeles de un archivo Raster.

## PASO 1. Carga tu archivo raster en QGIS.

La cobertura de suelo es tomada del sitio de la [Comisión para la Cooperación Ambiental](http://www.cec.org/es/herramientas-y-recursos/archivos-cartogr%C3%A1ficos/cobertura-del-suelo-2010-landsat-30m).

La tabla de datos tiene los siguientes valores:

1 Bosque de coníferas templado o subpolar 2 Bosque de coníferas (taiga) subpolar 3 Bosque de latifoliadas perennifolio tropical o subtropical 4 Bosque de latifoliadas caducifolio tropical o subtropical 5 Bosque de latifoliadas caducifolio templado o subpolar 6 Bosque mixto 7 Matorral tropical o subtropical 8 Matorral templado o subpolar 9 Pastizal tropical o subtropical 10 Pastizal templado o subpolar 11 Matorral con líquenes y musgos subpolar o polar 12 Pastizal con líquenes y musgos subpolar o polar 13 Suelo desnudo con líquenes y musgos subpolar o polar 14 Humedal 15 Suelo agrícola 16 Suelo desnudo 17 Asentamiento humano 18 Cuerpo de agua 19 Nieve y hielo

##### ![1](/images/1.png)Figura 1. Cobertura de suelo con la [simbología en QGIS ](https://github.com/qgismexico/simbologias)de la Comisión para la Cooperación Ambiental.

## Paso 2. Haz el archivo de reclasificación de pixeles.

Las categorías manejadas por el modelo [MM5 Modeling System Version](http://www2.mmm.ucar.edu/mm5/documents/MM5_tut_Web_notes/TERRAIN/terrain.htm) son los siguientes:

 



**Landuse**

**Integer**

**Identification**

**Landuse**

**Description**

1

Urban land

2

Agriculture

3

Range-grassland

4

Deciduous forest

5

Coniferous forest

6

Mixed forest and

wet land

7

Water

8

Marsh or wet land

9

Desert

10

Tundra

11

Permanent ice

12

Tropical or sub

tropical forest

13

Savannah

##### Tabla 1. 13 Categorías  (PSU/NCAR) de uso de suelo.

Una propuesta de correspondencia sería la siguiente:

0 = NULL 1 2 = 5 Coniferous forest 3 = 12 Tropical or subtropical forest 4 5 = 4 Deciduous forest 6 = 6 Mixed forest and wet land 7 8 = 13 Savannah 9 10 = 3 Range-grassland 11 thru 13 = 10 Tundra 14 = 8 Marsh or wet land 15 = 2 Agriculture 16 = 9 Desert 17 = 1 Urban land 18 = 7 Water 19 = 11 Permanent ice

Estos valores se guardan en un archivo de texto para su posterior lectura (archivo con la reclasificación). Puedes descargarlo [aquí](https://github.com/qgismexico/simbologias/blob/master/landusereclass.txt).

## Paso 3. Utiliza la herramienta de reclasificación de raster.

Esta herramienta se encuentra en la caja de herramientas (r.reclass)

![2](/images/2.png)

##### Figura 2. Caja de herramientas.

Indica el nombre de la capa raster y el archivo de reclasificación:

![5](/images/5.png)

##### Figura 3. Herramienta GRASS r.reclass

![4](/images/4.png)

##### Figura 4. Resultado de la reclasificación de pixeles.

## Paso 4. Toma una rica taza de café.

Gracias- Tlazohkamati.

**@qgismx**
