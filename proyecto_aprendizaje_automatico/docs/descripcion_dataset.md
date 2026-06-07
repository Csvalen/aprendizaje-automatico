# Entrega 2 – Descripción del Dataset y Origen de los Datos

## Proyecto

**Predicción del consumo mensual de gas envasado en Tierra del Fuego a partir de variables climáticas**

**Alumna:** Sara Valenzuela

---

## 1. Introducción

El presente informe corresponde a la segunda entrega del proyecto de Aprendizaje Automático. En esta etapa se describe el origen de los datos utilizados, las características de los datasets seleccionados, las variables consideradas para el análisis y el proceso de preprocesamiento realizado para construir el conjunto de datos que será empleado en las etapas posteriores del proyecto.

El objetivo general consiste en analizar la relación existente entre las condiciones climáticas y el consumo mensual de gas envasado en la Provincia de Tierra del Fuego mediante técnicas de aprendizaje supervisado.

Para ello se utilizaron dos fuentes de información oficiales:

* Dataset energético vinculado al consumo de gas envasado.
* Dataset climático con información meteorológica de las ciudades de Río Grande y Ushuaia.

---

## 2. Objetivo del Proyecto

El proyecto tiene como finalidad desarrollar un modelo predictivo capaz de estimar el consumo mensual de gas envasado a partir de variables climáticas, temporales y de demanda.

La hipótesis de trabajo plantea que variables como temperatura, precipitaciones, días con nieve y cantidad de usuarios pueden influir significativamente sobre el comportamiento del consumo energético.

Por este motivo se construyó una base de datos integrada que permita estudiar dichas relaciones y posteriormente entrenar modelos de regresión supervisada.

---

## 3. Origen de los Datos

Los datos utilizados fueron obtenidos del Instituto Provincial de Análisis e Investigación, Estadística y Censos de Tierra del Fuego (IPIEC), organismo oficial encargado de la producción y difusión de información estadística provincial.

### Fuente oficial

https://ipiec.tierradelfuego.gob.ar/

### Conjuntos de datos utilizados

* Consumo de gas envasado.
* Cantidad de usuarios.
* Temperaturas máximas medias.
* Temperaturas mínimas medias.
* Temperaturas medias.
* Precipitaciones mensuales.
* Días con nieve.
* Información meteorológica de Río Grande.
* Información meteorológica de Ushuaia.

La utilización de fuentes oficiales permite garantizar la calidad, confiabilidad y trazabilidad de la información empleada en el proyecto.

---

## 4. Descripción del Dataset Energético

### 4.1 Descripción

El dataset energético contiene información mensual relacionada con el consumo de gas envasado expresado en kilogramos y la cantidad de usuarios registrados para cada período.

Inicialmente la información se encontraba distribuida en hojas de cálculo independientes y organizada en formato matricial, por lo que fue necesario transformarla a una estructura tabular adecuada para su posterior procesamiento.

### 4.2 Dimensiones

| Característica    | Valor     |
| ----------------- | --------- |
| Registros         | 144       |
| Variables         | 4         |
| Período utilizado | 2014–2025 |
| Frecuencia        | Mensual   |

### 4.3 Variables

| Variable          | Descripción                                             |
| ----------------- | ------------------------------------------------------- |
| mes               | Mes correspondiente al registro                         |
| año               | Año correspondiente al registro                         |
| consumo_gas_kg    | Consumo mensual de gas envasado expresado en kilogramos |
| cantidad_usuarios | Cantidad de usuarios registrados para el período        |

La variable objetivo principal del proyecto corresponde a **consumo_gas_kg**.

Por otra parte, la variable **cantidad_usuarios** fue incorporada como predictor debido a que el consumo total observado puede verse influenciado por la cantidad de usuarios registrados en cada período.

---

## 5. Descripción del Dataset Climático

### 5.1 Descripción

El dataset climático contiene información meteorológica mensual correspondiente a las ciudades de Río Grande y Ushuaia.

Las variables seleccionadas representan factores ambientales potencialmente relacionados con el comportamiento del consumo de gas envasado.

### 5.2 Dimensiones

| Característica | Valor   |
| -------------- | ------- |
| Registros      | 204     |
| Variables      | 12      |
| Frecuencia     | Mensual |

### 5.3 Variables del Dataset Climático

| Variable          | Descripción                                    |
| ----------------- | ---------------------------------------------- |
| temp_max_rg       | Temperatura máxima media mensual de Río Grande |
| temp_min_rg       | Temperatura mínima media mensual de Río Grande |
| temp_media_rg     | Temperatura media mensual de Río Grande        |
| precipitacion_rg  | Precipitación mensual acumulada de Río Grande  |
| nieve_rg          | Días con nieve registrados en Río Grande       |
| temp_max_ush      | Temperatura máxima media mensual de Ushuaia    |
| temp_min_ush      | Temperatura mínima media mensual de Ushuaia    |
| temp_media_ush    | Temperatura media mensual de Ushuaia           |
| precipitacion_ush | Precipitación mensual acumulada de Ushuaia     |
| nieve_ush         | Días con nieve registrados en Ushuaia          |
| mes               | Mes correspondiente al registro                |
| año               | Año correspondiente al registro                |

Estas variables fueron seleccionadas debido a que las condiciones meteorológicas pueden influir sobre la demanda de gas utilizada para calefacción y otros usos asociados a bajas temperaturas.

---

## 6. Selección del Período de Trabajo

Aunque el dataset climático contiene información adicional, se decidió trabajar exclusivamente con el período comprendido entre enero de 2014 y diciembre de 2025.

Esta decisión metodológica responde a que dicho intervalo constituye la ventana temporal común utilizada para integrar la información energética y climática.

Asimismo, la utilización de una ventana temporal consistente facilita la comparación entre períodos y mejora la calidad de los análisis exploratorios y modelos predictivos que serán desarrollados en etapas posteriores.

---

## 7. Preprocesamiento de los Datos

El proceso de preparación de datos se desarrolló utilizando Python y Google Colab mediante la librería Pandas.

Las principales tareas realizadas fueron:

### 7.1 Transformación de estructuras

* Lectura de archivos Excel.
* Selección de hojas específicas.
* Conversión de tablas matriciales a formato tabular.
* Renombrado de columnas.

### 7.2 Limpieza de datos

* Eliminación de filas vacías.
* Normalización de nombres de meses.
* Conversión de tipos de datos.
* Revisión de registros inconsistentes.

### 7.3 Corrección temporal

En el dataset climático el valor del año aparecía únicamente al inicio de determinados bloques anuales.

Para evitar registros sin identificación temporal se aplicó una propagación hacia adelante del año utilizando la técnica Forward Fill (`ffill()`), permitiendo asociar correctamente cada mes con su año correspondiente.

### 7.4 Resumen del preprocesamiento realizado hasta ahora

| Etapa               | Acción realizada                                                                                                                                                     |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Transformación      | Conversión de tablas matriciales a formato tabular                                                                                                                   |
| Limpieza            | Eliminación de filas vacías                                                                                                                                          |
| Normalización       | Corrección de nombres de columnas y meses                                                                                                                            |
| Conversión          | Ajuste de tipos de datos                                                                                                                                             |
| Corrección temporal | Aplicación de Forward Fill (`ffill()`)                                                                                                                               |
| Imputación          | Recuperación de variables climáticas de Ushuaia para 2024 mediante la API Open-Meteo e imputación de la variable `nieve_ush` utilizando la mediana histórica mensual |
| Integración         | Unión de datasets mediante mes y año                                                                                                                                 |

Las tareas de preprocesamiento permitieron obtener una estructura homogénea y consistente para ambas fuentes de datos, facilitando posteriormente la integración de la información.

---

## 8. Tratamiento de Valores Faltantes

### 8.1 Valores faltantes puntuales

Durante el proceso de exploración y limpieza de los datos se identificaron valores faltantes en algunas variables específicas del dataset integrado.

En las variables energéticas (`consumo_gas_kg` y `cantidad_usuarios`) se aplicó una estrategia de imputación basada en el promedio histórico correspondiente al mismo mes. Esta metodología permite conservar la estacionalidad característica de la serie temporal y minimizar el impacto de los valores faltantes sobre el comportamiento general de los datos.

Asimismo, se detectó un valor faltante puntual en la variable `temp_min_rg`. Debido a que se trataba de una observación aislada, el dato fue recuperado mediante información meteorológica histórica obtenida de fuentes climáticas externas, evitando la necesidad de estimarlo mediante técnicas de imputación.

La utilización de estas estrategias permitió preservar la coherencia temporal del dataset y garantizar la disponibilidad de información para todas las observaciones utilizadas en el proyecto.

### 8.2 Variable días con nieve

Las variables asociadas a días con nieve contenían registros representados mediante los símbolos "-" y "--". Luego de revisar la estructura del dataset y la documentación disponible, dichos valores fueron interpretados como ausencia de eventos de nieve durante el período correspondiente y reemplazados por el valor 0.

Esta decisión se fundamenta en que la variable representa una cantidad discreta de días con nieve registrados por mes, por lo que la ausencia del fenómeno climático resulta equivalente a un valor nulo de ocurrencia y no a un dato faltante.

De esta manera se preserva la interpretación física de la variable y se evita la generación innecesaria de valores faltantes dentro del dataset.

---

## 9. Recuperación de Información Climática de Ushuaia para 2024

Durante la etapa de preprocesamiento se detectó que las variables meteorológicas correspondientes a la ciudad de Ushuaia presentaban ausencia de información para los doce meses del año 2024.

### Variables afectadas

* temp_max_ush
* temp_min_ush
* temp_media_ush
* precipitacion_ush
* nieve_ush

Para las variables de temperatura y precipitación se recuperó información meteorológica histórica mediante la utilización de la API Open-Meteo, permitiendo incorporar registros consistentes para todo el período anual.

En el caso de la variable `nieve_ush`, debido a la ausencia total de información para el año 2024, se aplicó una imputación basada en la mediana histórica mensual calculada a partir de los registros disponibles de años anteriores.

La elección de la mediana se fundamenta en que la variable representa una cantidad discreta de días con nieve por mes. A diferencia de la media aritmética, la mediana es menos sensible a valores atípicos y distribuciones asimétricas, características frecuentes en variables climáticas.

Además, permite obtener valores enteros más representativos del comportamiento histórico mensual sin que eventos excepcionales de nevadas intensas distorsionen la estimación.

Por este motivo, la mediana fue considerada una medida más adecuada para la imputación de los valores faltantes correspondientes al año 2024, preservando la coherencia estadística y la interpretación física de la variable.

---

## 10. Integración de los Datasets

Una vez completadas las tareas de limpieza y preparación, ambos conjuntos de datos fueron integrados utilizando las variables:

* mes
* año

como claves de unión.

El dataset climático original contiene 204 registros, mientras que el dataset energético contiene 144 registros.

Debido a que la integración se realizó conservando únicamente los períodos coincidentes entre ambos conjuntos de datos, el dataset final quedó compuesto por 144 observaciones.

Esta decisión garantiza que cada registro utilizado para el entrenamiento de modelos disponga simultáneamente de información energética y climática correspondiente al mismo período temporal.

De esta forma se evita la generación de observaciones incompletas que podrían afectar la calidad del análisis y del entrenamiento de los modelos predictivos.

---

## 11. Dataset Final Generado

### 11.1 Dimensiones

| Dataset         | Registros | Variables |
| --------------- | --------- | --------- |
| Energético      | 144       | 4         |
| Climático       | 204       | 12        |
| Final Integrado | 144       | 14        |

### 11.2 Variables finales

| Variable          | Rol dentro del modelo |
| ----------------- | --------------------- |
| consumo_gas_kg    | Variable objetivo     |
| cantidad_usuarios | Predictora de demanda |
| mes               | Predictora temporal   |
| año               | Predictora temporal   |
| temp_max_rg       | Predictora climática  |
| temp_min_rg       | Predictora climática  |
| temp_media_rg     | Predictora climática  |
| precipitacion_rg  | Predictora climática  |
| nieve_rg          | Predictora climática  |
| temp_max_ush      | Predictora climática  |
| temp_min_ush      | Predictora climática  |
| temp_media_ush    | Predictora climática  |
| precipitacion_ush | Predictora climática  |
| nieve_ush         | Predictora climática  |

La construcción de este dataset integrado constituye el resultado principal de la presente etapa del proyecto y representa la base de trabajo para las siguientes fases de análisis y modelado.

---

## 12. Archivos Generados para el Proyecto

Como resultado del proceso de preparación e integración de datos, se generaron distintos archivos que serán incorporados al repositorio GitHub correspondiente al proyecto.

Los elementos que formarán parte del repositorio son los siguientes:

* Dataset energético original.
* Dataset climático original.
* Dataset final integrado en formato CSV.
* Dataset final integrado en formato XLSX.
* Notebook de Google Colab con el proceso completo de transformación y preparación de datos.
* Informe técnico correspondiente a la Entrega 2.

La conservación de estos archivos permite garantizar la reproducibilidad del proceso realizado y facilita futuras tareas de auditoría, revisión o actualización de la información.

Asimismo, la disponibilidad de los datasets originales permite mantener la trazabilidad de las transformaciones efectuadas durante el preprocesamiento.

---

## 13. Conclusión

A partir de información oficial proveniente del Instituto Provincial de Análisis e Investigación, Estadística y Censos (IPIEC), se construyó un dataset integrado orientado al estudio del consumo mensual de gas envasado en la Provincia de Tierra del Fuego.

El proceso desarrollado incluyó tareas de extracción, transformación, limpieza, normalización e integración de datos provenientes de diferentes fuentes, obteniéndose finalmente una base consolidada compuesta por 144 observaciones mensuales y 14 variables.

Asimismo, se documentaron las decisiones metodológicas adoptadas durante el preprocesamiento, incluyendo el tratamiento de valores faltantes, la corrección temporal mediante Forward Fill, la interpretación de registros asociados a nieve y la identificación de limitaciones presentes en la fuente original de datos.

Particularmente, durante el proceso de preparación de los datos se identificó la ausencia de información meteorológica correspondiente a la ciudad de Ushuaia durante el año 2024. Esta situación fue resuelta mediante la recuperación de datos climáticos históricos para las variables de temperatura y precipitación, complementada con técnicas de imputación basadas en estadísticas históricas para la variable días con nieve.

Las tareas de extracción, transformación, limpieza, normalización, recuperación e imputación permitieron obtener finalmente un dataset integrado compuesto por 144 observaciones mensuales y 14 variables, sin presencia de valores faltantes.

Asimismo, las decisiones de recuperación e imputación fueron aplicadas de forma diferenciada según la naturaleza de cada variable, priorizando la coherencia temporal y la interpretación física de los datos. Esto permitió obtener una base de datos consistente y adecuada para el desarrollo de modelos predictivos supervisados.

El dataset final obtenido constituye una representación consistente de la información energética y climática disponible para el período comprendido entre 2014 y 2025, proporcionando una base sólida para las etapas posteriores de análisis exploratorio, selección de variables y entrenamiento de modelos predictivos de Aprendizaje Automático.
