📚 README: Tarea de Limpieza y Preprocesamiento de Datos (Data Wrangling Challenge)
Este repositorio contiene la solución para una tarea de limpieza y preprocesamiento de datos, simulando el ciclo completo de creación, suciedad, limpieza y análisis de un conjunto de datos.

La tarea se realizó en dos roles: Data Creator (creador de datos sucios en un dataset de Viviendas) y Data Cleaner (limpiador y analista de datos de Videojuegos).

🚀 Estructura del Repositorio
El repositorio sigue la estructura de entrega requerida:
.
├── datacleaner/
│   ├── clean_dataset.csv           # ⬅️ Dataset de Videojuegos limpiado por el estudiante
│   ├── cleaner.ipynb               # ⬅️ Notebook con los pasos de limpieza y análisis de Videojuegos
│   └── recieved_dirty_dataset.csv  # ⬅️ Dataset sucio de Videojuegos recibido del compañero
└── datacreator/
    ├── dirty_dataset.csv           # ⬅️ Dataset sucio de Viviendas creado por el estudiante
    ├── enshitificator.ipynb        # ⬅️ Notebook explicando cómo se introdujeron los 10 errores en Viviendas
    └── source_clean_dataset.csv    # ⬅️ Dataset original de Viviendas de partida

    I. Rol: Data Creator (Creación de Dataset Sucio)
Dataset Original: Base de datos de Ventas de Viviendas (Housing Data). Dataset Modificado: Muestra aleatoria modificada con 10 tipos de errores.

🎯 Lista de Errores Introducidos (Dataset de Viviendas)
Se introdujeron los siguientes 10 tipos de errores en el dataset de Viviendas (datacreator/enshitificator.ipynb):
Datos Faltantes: Valores np.nan, 'Unknown', "" y 'N/A' en columnas como price, sqft_living, bathrooms y bedrooms.
Filas Duplicadas: Se añadieron duplicados exactos (20% del dataset base).
Outliers Extremos: Valores ilógicos como un precio de 1 billón y superficies de 1 millón de pies cuadrados. También se introdujeron años fuera de rango (2050, 1700) en yr_built.
Inconsistencias de Formato/Unidad: Conversión del 1% de los valores de price a string con el símbolo $ (ej: "$369900.0").
Errores Tipográficos: Reemplazo de la categoría de condición '4' por la palabra mal escrita 'Fouur'.
Categorías Extranormales: Inserción de valores de ruido como 'ZOMBIE' y 'ERROR_MAP' en la columna condition.
Tipo de Dato Incorrecto: Conversión del año de construcción (yr_built) a string añadiendo texto (ej: '1992 Built').
Problemas de Codificación: Inserción de caracteres acentuados (ó, é, ñ) y prefijos de error en columnas de texto.
Encabezados Incorrectos: Inconsistencias de formato y puntuación en los nombres de columna (ej: ID_REGISTRO_X, BATH).
Símbolos de Puntuación Extra: Inserción del sufijo ' EUR' al 15% de la columna price, mezclando divisas.


    II. Rol: Data Cleaner (Limpieza y Análisis)
Dataset Recibido: datacleaner/recieved_dirty_dataset.csv (Dataset de Ventas de Videojuegos). Dataset Final Limpio: 202 filas.
Error Corregido,Columna(s),Técnica Aplicada
Encabezados,Múltiples,"Estandarización de Rank_, Name_, platform!!!!!!!!!!! a Rank, Name, Platform."
Tipo de Dato/Formato,Rank,"Eliminación de sufijos ordinales ('st', 'nd', 'rd', 'th') y conversión a tipo Int64."
Símbolos Extra,EU_Sales,Eliminación del símbolo de moneda ¥ y conversión de la columna a float.
Inconsistencia Unidad,EU_Sales,Detección de valores multiplicados por 1000 (Outliers > 35.0) y corrección mediante división por 1000.
Outliers Extremos,"GlobalSales, NASales","Reemplazo de valores de error (9999.0, 5000.0) por la mediana de la columna."
Outliers IQR,"NASales, EUSales, etc.","Se aplicó la imputación IQR (reemplazo por mediana) en las ventas, estabilizando la distribución."
Errores Tipográficos,Genre,Consolidación y corrección de la falta de ortografía 'Sprots' a 'Sports'.
Datos Faltantes,Publisher,"Imputación de NaN, 'N/A', y """" con la categoría 'Unknown'."
Datos Faltantes,Year,Imputación de NaN y 'Unknown' con la moda del año.
Duplicados,Todas,"Eliminación de duplicados exactos y duplicados por clave (Name, Platform)."

🛠️ Tareas de Limpieza Realizadas (Videojuegos)
El proceso de limpieza fue exhaustivo para corregir todos los errores conocidos:
