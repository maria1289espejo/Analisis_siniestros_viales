<h1 align="center">Proyecto de Análisis de Siniestros Viales</h1>

![Accidente_vial](C:/Users/57315/Documentos/Phyton_Henry/proyecto_data/imagenes/accident-1497295_1280.jpg)

## Descripción

Este proyecto tiene como objetivo utilizar técnicas de análisis de datos para abordar el problema de los siniestros viales en la ciudad de Buenos Aires, Argentina, una de las principales causas de muertes violentas en el país.

### Contexto

En Argentina, alrededor de 11 personas por día mueren en accidentes de tránsito, lo que posiciona a los siniestros viales como la principal causa de muerte violenta. Según informes del Sistema Nacional de Información Criminal, entre 2018 y 2022 se registraron 19,630 muertes en siniestros viales en todo el país..

### Objetivo

El objetivo principal de este proyecto es brindar información útil que permita a las autoridades locales tomar medidas efectivas para reducir la cantidad de víctimas mortales en accidentes de tránsito. Se busca identificar patrones, tendencias y factores de riesgo asociados con los siniestros viales utilizando análisis de datos. Además, se definirán tres Key Performance Indicators (KPI) para medir el impacto de las medidas tomadas en la reducción de fallecidos.

## Tecnologias Usadas

La transformación, limpieza y EDA fueron realizados con Python 3.10.4 en Visual Studio Code 1.86.0. Las librerás utilizadas en cada etapa fueron las siguientes:

- pandas: Lectura de archivos en formato .xlsx y manipulación de dataframe
- numpy: Manipulación de dataframe
- seaborn: Creación de gráficos
- matplotlib.pyplot: Creación de gráficos
- datetime: Manipulación de datos de fecha y hora

El dashboard fue realizado con Power BI 2.124.2028.0

## EDA

Se realizó una exploración inicial de los archivos para identificar la cantidad de filas y columnas, el tipo de datos y la presencia de valores faltantes, nulos, duplicados y únicos. Se llevaron a cabo acciones de limpieza de datos, incluida la corrección, imputación o eliminación de valores inconsistentes, como imputación por moda y reemplazo por cero, entre otras. Posteriormente, se procedió al análisis descriptivo, donde se examinaron las distribuciones y comportamientos de las variables mediante estadísticas resumidas, visualizaciones gráficas y análisis correspondientes. Se generaron archivos con los dataframe limpios en formato .csv para su posterior uso en otras tecnologías. Puede ver esta información de manera detallada en el archivo  [EDA.ipynb](https://github.com/maria1289espejo/Analisis_siniestros_viales/blob/main/EDA.ipynb).

## Dashboard

Se cargaron los dos dataframe limpios en formato .csv, seguidamente se realizó revisión y transformación de los datos, ya que durante el proceso de carga, algunas columnas no quedaron con el formato correspondiente al tipo de datos, y se agregaron algunas filas con datos que no estaban en los archivos .csv. En el modelo los archivos quedaron cargados com las tablas Hechos y victimas.

Luego se creo una tabla llamada Calendario por medio de DAX, con columnas las columnas `Fecha`, `Año`, `Mes` y `dia_semana`. Las formulas DAX utilizadas fueron las siguientes:

`Calendario = CALENDAR(DATE(2016, 1, 1), DATE(2021, 12, 31))`\
`Año = YEAR(Calendario[Fecha])`\
`Mes = MONTH(Calendario[Fecha])`\
`día_semana = FORMAT(Calendario[Fecha], "DDDD")`\

### Relaciones

Una vez creada la tabla Calendario, en la pestaña modelo, se crearon relaciones entre la columna `Fecha` de la tabla Calendario y las columnas `FECHA` de las tablas Hechos y Victimas.

Después se creo la tabla ID_hechos como una tabla puente, con los valores únicos de las columnas `ID` de la tabla Hechos y `ID_hecho`de la tabla Victimas, ya que no se podia relacionar estas dos tablas directamente, porque ambas presentaban valores repetidos en esa columna: la formula DAX utilizada fue:

`ID_hechos = DISTINCT(UNION(VALUES(Hechos[ID]), VALUES(Victimas[ID_hechos])))`\

### Visualizaciones

Recuento de victimas respecto al tiempo...

## Análisis y conclusiones

## Estado del proyecto

En proceso

## Referencias

- **Argentina
sociodemográfica: Composición de la población.** [https://static.ign.gob.ar/anida/fasciculos/fasc_composicion_poblacion.pdf](https://static.ign.gob.ar/anida/fasciculos/fasc_composicion_poblacion.pdf) [19-02-2024]

## Contacto

[Linkedink](https://www.linkedin.com/in/alejandra-monroy-e/)

[Correo](mailto:maria1289espejo@gmail.com)
