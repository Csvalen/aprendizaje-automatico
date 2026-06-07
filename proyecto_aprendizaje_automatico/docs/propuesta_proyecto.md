# Propuesta de Proyecto de Aprendizaje Automático

## Predicción del consumo mensual de gas envasado en Tierra del Fuego a partir de variables climáticas y temporales

## 1. Contexto y relevancia del problema

El presente proyecto propone desarrollar un modelo de Aprendizaje Automático orientado al análisis y predicción del consumo mensual de gas envasado en la provincia de Tierra del Fuego, utilizando variables climáticas, meteorológicas y temporales obtenidas de fuentes oficiales.

La provincia presenta características climáticas particulares en comparación con otras regiones del país, destacándose por sus bajas temperaturas y una marcada estacionalidad durante los meses invernales. Estas condiciones generan un impacto directo sobre el consumo mensual de gas, especialmente en hogares que utilizan gas envasado como fuente de calefacción y uso doméstico.

A diferencia de otros proyectos desarrollados sobre datasets genéricos o internacionales, esta propuesta busca trabajar con información local y contextualizada en la realidad energética y climática de Tierra del Fuego, integrando datos provinciales de consumo de gas envasado con registros meteorológicos de ciudades como Río Grande y Ushuaia.

Desde el punto de vista del Aprendizaje Automático, el análisis del comportamiento energético en función de variables climáticas representa una problemática interesante debido a la relación existente entre las condiciones meteorológicas y la demanda energética.

Además de aplicar técnicas vistas durante la cursada, el proyecto busca desarrollar un análisis regional utilizando datos reales provenientes de fuentes oficiales y públicas.

## 2. Objetivo general

Desarrollar un modelo de Aprendizaje Automático capaz de predecir el consumo mensual de gas envasado en Tierra del Fuego a partir de variables climáticas, temporales y de cantidad de usuarios empadronados.

## 3. Objetivos específicos

* Obtener y consolidar datasets climáticos y energéticos provenientes de fuentes oficiales.
* Realizar tareas de limpieza y preprocesamiento de datos.
* Analizar la relación entre variables meteorológicas y el consumo mensual de gas envasado.
* Aplicar análisis exploratorio de datos (EDA) para identificar patrones y tendencias.
* Seleccionar variables relevantes para el entrenamiento del modelo.
* Entrenar y comparar distintos modelos de regresión.
* Evaluar el desempeño de los modelos mediante métricas apropiadas.
* Interpretar los resultados obtenidos.

## 4. Tipo de problema

Se trata de un problema de aprendizaje supervisado de regresión, ya que el objetivo es predecir un valor numérico continuo correspondiente al consumo mensual de gas envasado.

La variable objetivo será el nivel de consumo mensual registrado para determinados períodos de tiempo.

## 5. Variable objetivo

La variable objetivo del proyecto será el consumo mensual de gas envasado expresado en kilogramos (kg).

El modelo intentará estimar el nivel de consumo mensual utilizando información climática, temporal y variables relacionadas con la cantidad de usuarios registrados.

## 6. Variables predictoras propuestas

Las principales variables predictoras consideradas serán:

* Cantidad de usuarios empadronados
* Temperatura mínima
* Temperatura máxima
* Temperatura media
* Precipitaciones
* Días con nieve
* Mes del año / estacionalidad
* Año

Estas variables fueron seleccionadas debido a su posible relación con la demanda de gas envasado, especialmente durante períodos invernales característicos de la región patagónica.

## 7. Modelos a utilizar

Inicialmente se propone trabajar con modelos de regresión vistos durante la cursada, entre ellos:

* Regresión Lineal
* Árbol de Decisión
* Random Forest Regressor

Como posible extensión del proyecto y de manera opcional, podría evaluarse el uso de Gradient Boosting Regressor para comparar desempeño y resultados predictivos.

## 8. Fuentes de datos

Los datasets serán obtenidos principalmente a partir de fuentes oficiales y públicas:

* Instituto Provincial de Análisis e Investigación, Estadística y Censos (IPIEC)
* Registros meteorológicos provinciales
* Datos estadísticos vinculados al consumo de gas envasado
* Datos climáticos históricos de Río Grande y Ushuaia

Los datos serán trabajados en formato CSV y XLSX para facilitar su procesamiento mediante Python y bibliotecas de análisis de datos.

## 9. Metodología propuesta (pipeline de trabajo)

1. Recolección y consolidación de datasets.
2. Limpieza y preprocesamiento de datos.
3. Integración de datasets climáticos y energéticos.
4. Análisis exploratorio de datos (EDA).
5. Visualización de patrones y tendencias.
6. Selección de variables relevantes.
7. División de datos en entrenamiento y prueba.
8. Entrenamiento de modelos predictivos.
9. Evaluación mediante métricas de regresión.
10. Comparación de resultados e interpretación final.

## 10. Métricas de evaluación

Para evaluar el desempeño de los modelos se utilizarán métricas de regresión como:

* MAE (Mean Absolute Error)
* MSE (Mean Squared Error)
* RMSE (Root Mean Squared Error)
* Coeficiente R²

## 11. Resultado esperado

Se espera obtener un modelo capaz de identificar patrones entre las condiciones climáticas y el consumo mensual de gas envasado en Tierra del Fuego, permitiendo analizar cómo diferentes variables meteorológicas pueden influir en la demanda de consumo de gas envasado.

Además, se espera generar visualizaciones y conclusiones que permitan comprender mejor el comportamiento energético frente a cambios estacionales y climáticos propios de la región.

## 12. Valor agregado del proyecto

Como extensión del proyecto, se propone analizar el impacto de eventos climáticos extremos como olas de frío, temperaturas muy bajas o nevadas intensas sobre el consumo mensual de gas envasado.

Esto permitiría incorporar una perspectiva regional y aplicada a problemáticas reales de la provincia.

Asimismo, el proyecto busca trabajar con información pública provincial y construir un dataset integrado orientado específicamente al entrenamiento de modelos de Machine Learning.

## 13. Cierre personal

Elegí esta temática porque considero que combina una problemática real de Tierra del Fuego con técnicas de Aprendizaje Automático aplicadas al análisis predictivo.

Además de trabajar con datos locales y oficiales, el proyecto permitirá aplicar distintas etapas del proceso de Machine Learning vistas durante la cursada, incluyendo análisis exploratorio de datos, preprocesamiento, integración de datasets, entrenamiento y evaluación de modelos predictivos.

Finalmente, considero interesante analizar cómo las condiciones climáticas características de la provincia pueden influir en el comportamiento energético y cómo el uso de modelos predictivos puede ayudar a comprender mejor estos patrones.
