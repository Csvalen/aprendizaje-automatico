# Predicción del Consumo Mensual de Gas Envasado en Tierra del Fuego a partir de Variables Climáticas y Temporales

## 1. Introducción

El consumo energético constituye un componente fundamental para el desarrollo económico y social de una región. En provincias con características climáticas extremas, como Tierra del Fuego, las condiciones meteorológicas influyen directamente sobre la demanda de energía, particularmente durante los meses invernales, cuando las bajas temperaturas incrementan la necesidad de calefacción en hogares y establecimientos.

Dentro de las distintas fuentes energéticas utilizadas en la provincia, el gas envasado representa un recurso de gran importancia para numerosos usuarios. Por este motivo, resulta relevante comprender los factores que influyen sobre su consumo y desarrollar herramientas que permitan anticipar su comportamiento futuro mediante el análisis de datos históricos.

En este contexto, el presente proyecto aplica técnicas de Aprendizaje Automático con el objetivo de analizar y predecir el consumo mensual de gas envasado en la Provincia de Tierra del Fuego a partir de variables climáticas, temporales y operativas.

Para ello se integraron datos energéticos y meteorológicos provenientes de fuentes oficiales, construyendo un dataset consolidado que permitió realizar análisis exploratorios, identificar patrones relevantes y entrenar distintos modelos predictivos supervisados.

La propuesta busca aportar una aproximación basada en datos reales de la provincia, permitiendo estudiar cómo factores como la temperatura, las precipitaciones, la ocurrencia de nieve, la evolución temporal y la cantidad de usuarios registrados pueden influir sobre la demanda energética.

Asimismo, el proyecto permite aplicar de manera práctica las diferentes etapas del proceso de Machine Learning desarrolladas durante la cursada, incluyendo la recolección y preparación de datos, el análisis exploratorio, el entrenamiento de modelos predictivos, la evaluación mediante métricas de regresión y la interpretación de resultados.

---

# 2. Objetivos

## 2.1 Objetivo General

Desarrollar un modelo de Aprendizaje Automático capaz de predecir el consumo mensual de gas envasado en la Provincia de Tierra del Fuego a partir de variables climáticas, temporales y de cantidad de usuarios registrados.

## 2.2 Objetivos Específicos

* Obtener y consolidar datasets energéticos y climáticos provenientes de fuentes oficiales.
* Realizar tareas de limpieza, transformación y preprocesamiento de datos.
* Integrar información meteorológica y energética en un único conjunto de datos.
* Analizar la relación existente entre las variables climáticas y el consumo de gas envasado.
* Aplicar técnicas de análisis exploratorio de datos (EDA) para identificar patrones y tendencias.
* Seleccionar variables relevantes para el entrenamiento de modelos predictivos.
* Entrenar y comparar distintos modelos de regresión supervisada.
* Evaluar el desempeño de los modelos mediante métricas apropiadas.
* Interpretar los resultados obtenidos y seleccionar el modelo con mejor capacidad predictiva.

---

# 3. Descripción de los Datos

## 3.1 Origen de la Información

Los datos utilizados en el presente proyecto fueron obtenidos principalmente del Instituto Provincial de Análisis e Investigación, Estadística y Censos (IPIEC) de Tierra del Fuego, organismo oficial responsable de la producción y difusión de información estadística provincial.

### Fuente oficial

https://ipiec.tierradelfuego.gob.ar/

Para el desarrollo del proyecto se trabajó con dos fuentes principales de información:

* Un dataset energético relacionado con el consumo mensual de gas envasado y la cantidad de usuarios registrados.
* Un dataset climático con información meteorológica mensual correspondiente a las ciudades de Río Grande y Ushuaia.

Posteriormente, ambos conjuntos de datos fueron integrados para construir una base consolidada orientada al entrenamiento y evaluación de modelos predictivos de Aprendizaje Automático.

---

## 3.2 Dataset Energético

El dataset energético contiene información mensual relacionada con el consumo de gas envasado y la cantidad de usuarios registrados en la Provincia de Tierra del Fuego.

Los datos corresponden al período comprendido entre enero de 2014 y diciembre de 2025, con frecuencia mensual. Inicialmente, la información se encontraba distribuida en hojas de cálculo con una estructura matricial, por lo que fue necesario realizar tareas de transformación para convertirla a un formato tabular adecuado para su procesamiento mediante Python.

### Características del dataset energético

| Característica | Valor     |
| -------------- | --------- |
| Registros      | 144       |
| Variables      | 4         |
| Período        | 2014–2025 |
| Frecuencia     | Mensual   |

### Variables del dataset

* `mes`: mes correspondiente al registro.
* `año`: año correspondiente al registro.
* `consumo_gas_kg`: consumo mensual de gas envasado expresado en kilogramos.
* `cantidad_usuarios`: cantidad de usuarios registrados para cada período.

Dentro de estas variables, `consumo_gas_kg` fue definida como la variable objetivo del proyecto, mientras que `cantidad_usuarios` fue incorporada como variable predictora debido a su posible influencia sobre la demanda total observada.

---

## 3.3 Dataset Climático

El dataset climático contiene información meteorológica mensual correspondiente a las ciudades de Río Grande y Ushuaia.

Este conjunto de datos incluye variables asociadas a temperatura máxima, temperatura mínima, temperatura media, precipitaciones y días con nieve. Debido a que las condiciones climáticas pueden influir directamente sobre la demanda energética, estas variables fueron consideradas relevantes para el desarrollo del modelo predictivo.

La fuente original contenía información climática correspondiente al período comprendido entre los años 2009 y 2025. Sin embargo, para el presente proyecto se decidió trabajar únicamente con el período 2014–2025, ya que este intervalo coincidía con la disponibilidad temporal del dataset energético.

Esta decisión permitió integrar ambas fuentes de información de manera consistente, evitando la incorporación de períodos sin correspondencia entre las variables energéticas y climáticas.

### Características del dataset climático

| Característica    | Valor     |
| ----------------- | --------- |
| Registros         | 204       |
| Variables         | 12        |
| Período original  | 2009–2025 |
| Período utilizado | 2014–2025 |
| Frecuencia        | Mensual   |

### Variables climáticas consideradas

* Temperatura máxima media mensual.
* Temperatura mínima media mensual.
* Temperatura media mensual.
* Precipitación mensual acumulada.
* Días con nieve registrados por mes.
* Mes y año correspondientes a cada observación.

Estas variables fueron seleccionadas debido a su potencial capacidad para explicar variaciones en el consumo de gas envasado, particularmente durante los períodos de bajas temperaturas característicos de la región.

---

## 3.4 Dataset Final Integrado

Una vez completadas las tareas de limpieza, transformación, normalización e integración de ambas fuentes, se obtuvo un dataset consolidado que fue utilizado para el análisis exploratorio de datos y el entrenamiento de los modelos predictivos.

La integración se realizó utilizando las variables `mes` y `año` como claves de unión, conservando únicamente los períodos coincidentes entre ambos conjuntos de datos.

### Características del dataset final

| Característica            | Valor          |
| ------------------------- | -------------- |
| Registros                 | 144            |
| Variables                 | 14             |
| Período                   | 2014–2025      |
| Frecuencia                | Mensual        |
| Variable objetivo         | consumo_gas_kg |
| Valores faltantes finales | 0              |

### Variables del dataset final

* consumo_gas_kg
* cantidad_usuarios
* temp_max_rg
* temp_min_rg
* temp_media_rg
* precipitacion_rg
* nieve_rg
* temp_max_ush
* temp_min_ush
* temp_media_ush
* precipitacion_ush
* nieve_ush
* año
* mes

Estas variables integran información energética, climática y temporal correspondiente a la Provincia de Tierra del Fuego, permitiendo analizar conjuntamente la evolución del consumo de gas envasado y las condiciones meteorológicas observadas durante cada período.

La construcción de este dataset integrado constituyó una etapa fundamental del proyecto, ya que proporcionó la base de información necesaria para desarrollar las etapas posteriores de análisis exploratorio, ingeniería de características, modelado predictivo y evaluación de resultados.
# 4. Preprocesamiento de Datos

La calidad de los datos constituye un aspecto fundamental dentro de cualquier proyecto de Aprendizaje Automático. Antes de entrenar los modelos predictivos fue necesario realizar diversas tareas de preparación, limpieza y transformación con el objetivo de garantizar la consistencia, integridad y confiabilidad del conjunto de datos utilizado.

Estas tareas permitieron obtener un dataset consolidado, libre de inconsistencias y adecuado para las etapas posteriores de análisis exploratorio y modelado predictivo.

---

## 4.1 Integración de Fuentes de Datos

Inicialmente se trabajó con dos conjuntos de datos independientes:

* Un dataset energético con información de consumo mensual de gas envasado y cantidad de usuarios registrados.
* Un dataset climático con variables meteorológicas correspondientes a las ciudades de Río Grande y Ushuaia.

Con el objetivo de analizar conjuntamente ambas fuentes de información, se realizó un proceso de integración utilizando las variables temporales `mes` y `año` como claves de unión.

Este procedimiento permitió relacionar el consumo energético observado en cada período con las condiciones climáticas registradas durante el mismo intervalo temporal.

Como resultado, se obtuvo un dataset único que integró información energética, climática y temporal en una misma estructura de datos.

---

## 4.2 Limpieza y Transformación de Datos

Una vez integradas las fuentes de información, se llevaron a cabo distintas tareas de limpieza y transformación orientadas a mejorar la calidad de los datos y garantizar su correcta utilización durante el análisis.

### Principales actividades realizadas

* Corrección y estandarización de nombres de variables.
* Conversión de variables numéricas almacenadas inicialmente como texto.
* Eliminación de caracteres especiales y espacios innecesarios.
* Verificación de registros duplicados.
* Revisión de inconsistencias temporales.
* Validación de tipos de datos.
* Normalización de formatos para facilitar el procesamiento posterior mediante Python.

Estas tareas permitieron construir un conjunto de datos consistente y preparado para las etapas posteriores del proyecto.

---

## 4.3 Tratamiento de Valores Faltantes

Durante la exploración inicial de los datos se identificaron valores faltantes principalmente en variables climáticas correspondientes a la ciudad de Ushuaia durante el año 2024.

Con el objetivo de preservar la continuidad temporal de la serie y evitar la pérdida de observaciones, se recurrió a información histórica obtenida mediante la API Open-Meteo. A partir de esta fuente se recuperaron registros correspondientes a variables de temperatura y precipitación para los períodos faltantes.

En el caso particular de la variable asociada a los días con nieve, no fue posible obtener información completa y consistente para todos los períodos requeridos. Por este motivo se aplicó una estrategia de imputación basada en la mediana histórica mensual de cada período correspondiente.

La utilización de la mediana permitió reducir la influencia de posibles valores atípicos y conservar patrones estacionales característicos de la variable, evitando introducir distorsiones significativas en el conjunto de datos.

Estas técnicas de imputación permitieron obtener un dataset completo y consistente para el entrenamiento de los modelos predictivos, eliminando la presencia de valores faltantes en la versión final utilizada durante el proyecto.

---

## 4.4 Selección de Variables

Una vez finalizadas las tareas de limpieza e integración, se definieron las variables que formarían parte del dataset utilizado para las etapas posteriores de análisis exploratorio y modelado predictivo.

Las variables seleccionadas incluyen información climática, temporal y operativa, considerando aquellas con potencial capacidad explicativa sobre el comportamiento del consumo mensual de gas envasado.

Asimismo, se definió como variable objetivo del proyecto el consumo mensual de gas envasado expresado en kilogramos (`consumo_gas_kg`), mientras que el resto de las variables fueron consideradas potenciales predictores para el entrenamiento de los modelos supervisados.

---

## 4.5 Codificación de Variables Temporales

Además de las variables originales presentes en el dataset integrado, se incorporaron variables derivadas destinadas a representar adecuadamente la naturaleza cíclica del tiempo.

La variable `mes` fue transformada mediante funciones trigonométricas seno y coseno, generando las variables:

* `mes_sin`
* `mes_cos`

Esta técnica permite representar la estacionalidad anual preservando la continuidad temporal existente entre los distintos meses del año.

La utilización de una representación cíclica evita que el modelo interprete incorrectamente que diciembre y enero constituyen períodos temporalmente distantes, cuando en realidad corresponden a meses consecutivos dentro del mismo ciclo anual.

La incorporación de estas variables permitió capturar de manera más precisa los patrones estacionales presentes en el consumo de gas envasado, aportando información relevante para el entrenamiento de los modelos predictivos.

---

# 5. Análisis Exploratorio de Datos (EDA)

El Análisis Exploratorio de Datos (EDA) constituye una etapa fundamental dentro de cualquier proyecto de Aprendizaje Automático, ya que permite comprender la estructura de la información disponible, identificar patrones relevantes, detectar posibles anomalías y evaluar la relación existente entre las variables predictoras y la variable objetivo.

En este proyecto, el EDA tuvo como finalidad analizar el comportamiento histórico del consumo mensual de gas envasado, estudiar su relación con las variables climáticas y temporales, e identificar factores que pudieran contribuir al desarrollo de modelos predictivos capaces de estimar la demanda energética provincial.

Para ello se utilizaron técnicas de estadística descriptiva y visualización de datos mediante las bibliotecas Pandas, Matplotlib y Seaborn en Python.

---

## 5.1 Distribución del Consumo de Gas

Como primera etapa del análisis exploratorio se analizó la distribución de la variable objetivo (`consumo_gas_kg`) mediante estadísticas descriptivas básicas y visualizaciones gráficas.

Las estadísticas descriptivas permitieron obtener una primera caracterización cuantitativa de los datos, analizando aspectos como la variabilidad general del consumo y el rango de valores observados durante el período de estudio.

Posteriormente se utilizaron histogramas y diagramas de caja (boxplots) para complementar el análisis.

El histograma permitió visualizar la distribución de los valores de consumo, identificar la concentración de observaciones en distintos rangos y evaluar la variabilidad existente entre los diferentes períodos analizados.

Por su parte, el boxplot fue empleado para analizar la dispersión de los datos y detectar posibles valores extremos. A través de esta visualización se identificaron registros con consumos superiores al promedio, asociados principalmente a períodos invernales caracterizados por bajas temperaturas y una mayor demanda de calefacción.

Los resultados mostraron una variabilidad considerable en el consumo mensual de gas, reflejando la influencia de factores climáticos y estacionales sobre la demanda energética provincial.

Asimismo, los valores extremos observados fueron considerados consistentes con el contexto climático de Tierra del Fuego y no fueron tratados como errores de medición.

Este análisis permitió verificar que la variable objetivo presenta una dispersión adecuada para el desarrollo de modelos de regresión orientados a explicar y predecir su comportamiento.

### Figura 1. Distribución del consumo mensual de gas envasado (Histograma)

```markdown
![Distribución del consumo de gas](images/histograma_consumo.png)
```

### Figura 2. Distribución del consumo mensual de gas envasado (Boxplot)

```markdown
![Boxplot consumo de gas](images/boxplot_consumo.png)
```
## 5.2 Análisis de Correlación

Con el objetivo de identificar relaciones entre las variables numéricas del dataset, se calculó una matriz de correlación y se representó gráficamente mediante un mapa de calor (*heatmap*).

La matriz de correlación constituye una herramienta exploratoria que permite evaluar la intensidad y dirección de las relaciones lineales existentes entre las variables, facilitando la identificación de posibles predictores relevantes para el modelado.

Los resultados evidenciaron asociaciones importantes entre el consumo de gas y diversas variables climáticas, particularmente aquellas relacionadas con la temperatura mínima, temperatura media y temperatura máxima registradas en Río Grande y Ushuaia.

Asimismo, se observaron correlaciones elevadas entre algunas variables meteorológicas, comportamiento esperable debido a la naturaleza física de las mediciones climáticas.

Las variables temporales también mostraron capacidad explicativa, sugiriendo la existencia de patrones estacionales y tendencias históricas en la evolución del consumo energético.

En conjunto, este análisis permitió confirmar que las variables seleccionadas contienen información relevante para la construcción de modelos predictivos y justificó su utilización en las etapas posteriores del proyecto.

### Figura 3. Matriz de correlación entre las variables del dataset

```markdown
![Matriz de correlación](images/heatmap_correlacion.png)
```

---

## 5.3 Relación entre Consumo y Temperatura

Con el propósito de analizar visualmente la relación entre las variables térmicas y el consumo de gas envasado, se construyeron gráficos de dispersión entre la variable objetivo y distintas medidas de temperatura.

Los gráficos de dispersión permiten identificar tendencias, relaciones lineales y posibles comportamientos atípicos, proporcionando una primera aproximación visual al vínculo existente entre las variables analizadas.

Los resultados mostraron una tendencia consistente entre las temperaturas y el consumo mensual de gas, observándose que los períodos caracterizados por temperaturas más bajas suelen asociarse con niveles de consumo superiores.

Este comportamiento resulta coherente con las condiciones climáticas de la provincia, donde la necesidad de calefacción aumenta considerablemente durante los meses más fríos del año.

La relación observada permitió confirmar que las variables térmicas constituyen algunos de los predictores más relevantes para explicar la demanda energética y justificó su incorporación dentro de los modelos de Aprendizaje Automático desarrollados.

### Figura 4. Relación entre consumo mensual de gas y temperatura media de Río Grande

```markdown
![Consumo vs Temperatura Río Grande](images/scatter_temp_rg.png)
```

### Figura 5. Relación entre consumo mensual de gas y temperatura media de Ushuaia

```markdown
![Consumo vs Temperatura Ushuaia](images/scatter_temp_ush.png)
```

---

## 5.4 Evolución Histórica del Consumo de Gas

Con el objetivo de analizar la evolución temporal del consumo de gas envasado en la Provincia de Tierra del Fuego, se construyó un gráfico de series temporales considerando los valores anuales registrados durante el período 2014–2025.

La visualización permitió identificar una tendencia creciente del consumo entre los años 2014 y 2022, período en el cual la demanda energética mostró un incremento sostenido.

Este comportamiento puede asociarse al crecimiento de la cantidad de usuarios beneficiarios del programa de gas envasado y a factores climáticos característicos de la región.

A partir de 2023 se observa una disminución gradual del consumo total, manteniéndose sin embargo en valores superiores a los registrados durante los primeros años analizados.

Esta reducción podría estar relacionada con variaciones en la cantidad de usuarios, cambios en las condiciones climáticas o modificaciones en los patrones de consumo energético.

En términos generales, la evolución histórica evidencia la existencia de tendencias temporales relevantes que justifican la incorporación de variables cronológicas dentro de los modelos predictivos desarrollados en el presente trabajo.

### Figura 6. Evolución histórica del consumo mensual de gas envasado (2014–2025)

```markdown
![Serie temporal consumo de gas](images/serie_temporal_consumo.png)
```

---

## 5.5 Principales Hallazgos del Análisis Exploratorio

A partir del análisis exploratorio realizado se identificaron los siguientes hallazgos relevantes:

* Existe una relación significativa entre las condiciones climáticas y el consumo mensual de gas envasado.
* Las variables asociadas a la temperatura presentan una capacidad explicativa superior respecto a otras variables meteorológicas.
* El consumo energético presenta patrones estacionales claramente definidos.
* La evolución temporal del consumo evidencia tendencias históricas identificables.
* Las variables climáticas, temporales y operativas seleccionadas contienen información suficiente para el desarrollo de modelos predictivos de regresión.

En consecuencia, los resultados obtenidos durante el análisis exploratorio respaldan la utilización de técnicas de Aprendizaje Automático para modelar y predecir el comportamiento futuro del consumo mensual de gas envasado en la Provincia de Tierra del Fuego.

---

# 6. Modelado Predictivo

Una vez finalizadas las etapas de integración, limpieza, transformación y análisis exploratorio de los datos, se procedió al desarrollo de modelos de Aprendizaje Automático supervisado orientados a la predicción del consumo mensual de gas envasado en la Provincia de Tierra del Fuego.

El objetivo principal de esta etapa fue construir un modelo capaz de estimar el consumo futuro de gas a partir de variables climáticas, temporales y operativas, evaluando posteriormente su capacidad predictiva mediante métricas cuantitativas y análisis visuales.

Para ello se implementaron distintos algoritmos de regresión utilizando la biblioteca **Scikit-Learn** de Python.

Los modelos fueron entrenados utilizando información histórica y posteriormente evaluados sobre observaciones no utilizadas durante el proceso de aprendizaje, con el fin de medir su capacidad de generalización.
## 6.1 División del Conjunto de Datos

Dado que el problema abordado posee una naturaleza temporal, la partición del dataset se realizó respetando el orden cronológico de las observaciones.

Inicialmente, los registros fueron ordenados por año y mes. Posteriormente, el conjunto de datos fue dividido en dos subconjuntos:

### Conjunto de entrenamiento

* Período: 2014–2023

### Conjunto de prueba

* Período: 2024–2025

Esta estrategia permitió simular un escenario real de predicción, donde el modelo aprende a partir de información histórica y posteriormente realiza estimaciones sobre períodos futuros no observados durante el entrenamiento.

A diferencia de una partición aleatoria tradicional, este enfoque evita la fuga de información temporal (*data leakage*), garantizando una evaluación más realista del desempeño predictivo del modelo.

---

## 6.2 Variables Utilizadas

El conjunto de variables predictoras fue construido a partir del dataset final integrado descrito anteriormente.

Dicho conjunto incorpora información climática, temporal y operativa correspondiente a la Provincia de Tierra del Fuego, permitiendo representar tanto las condiciones meteorológicas como los patrones históricos asociados al consumo energético.

Adicionalmente, durante la etapa de ingeniería de características se incorporaron las variables derivadas:

* `mes_sin`
* `mes_cos`

Estas variables fueron construidas a partir de la variable `mes` mediante una transformación trigonométrica.

Esta técnica permite representar adecuadamente la naturaleza cíclica del calendario, evitando discontinuidades artificiales entre diciembre y enero y facilitando la captura de patrones estacionales presentes en el consumo de gas envasado.

La variable objetivo seleccionada fue:

```text
consumo_gas_kg
```

Mientras que el resto de las variables fueron utilizadas como predictoras durante el entrenamiento y evaluación de los modelos de Aprendizaje Automático.

La inclusión de variables climáticas permitió representar las condiciones meteorológicas de las ciudades de Río Grande y Ushuaia, mientras que las variables temporales y operativas aportaron información complementaria relacionada con la evolución histórica de la demanda energética y la cantidad de usuarios registrados.

---

## 6.3 Regresión Lineal Múltiple

La Regresión Lineal Múltiple fue uno de los modelos supervisados evaluados durante el desarrollo del proyecto y resultó ser el algoritmo con mejor desempeño sobre el conjunto de prueba.

Este algoritmo modela la relación existente entre una variable objetivo y múltiples variables predictoras mediante una combinación lineal de sus efectos.

Su objetivo consiste en estimar el valor de la variable dependiente minimizando el error entre las observaciones reales y las predicciones generadas.

La elección de este modelo estuvo fundamentada tanto en las características del problema como en los resultados obtenidos durante el análisis exploratorio de datos.

Las correlaciones observadas entre el consumo de gas y diversas variables climáticas sugerían la existencia de relaciones aproximadamente lineales que podían ser aprovechadas por este algoritmo.

Además, la Regresión Lineal Múltiple presenta ventajas importantes para este tipo de problemas, entre ellas:

* Simplicidad de implementación.
* Facilidad de interpretación.
* Capacidad para identificar la contribución relativa de cada variable predictora.

La implementación fue realizada utilizando la biblioteca **Scikit-Learn** de Python mediante la clase `LinearRegression`.

Previamente al entrenamiento, las variables predictoras fueron escaladas utilizando `StandardScaler` con el objetivo de estandarizar sus magnitudes y evitar que diferencias de escala influyeran en el proceso de aprendizaje.

Una vez completado el entrenamiento utilizando los registros correspondientes al período 2014–2023, el modelo fue evaluado sobre el conjunto de prueba compuesto por observaciones de los años 2024 y 2025.

### Métricas de evaluación utilizadas

* Error Absoluto Medio (MAE).
* Error Cuadrático Medio (MSE).
* Raíz del Error Cuadrático Medio (RMSE).
* Coeficiente de Determinación (R²).

### Resultados obtenidos

| Métrica | Valor                 |
| ------- | --------------------- |
| MAE     | 192.844,84 kg         |
| MSE     | 60.691.581.612,93 kg² |
| RMSE    | 246.356,61 kg         |
| R²      | 0,85                  |

Los resultados obtenidos indican un desempeño satisfactorio del modelo sobre el conjunto de prueba.

El Error Absoluto Medio (MAE) muestra que, en promedio, las predicciones difieren de los valores reales en aproximadamente **192.845 kg de gas**.

Por su parte, el Error Cuadrático Medio (MSE) y la Raíz del Error Cuadrático Medio (RMSE) evidencian que el modelo mantiene una capacidad adecuada para controlar errores de mayor magnitud, conservando un nivel de precisión consistente en las estimaciones realizadas.

El valor de **R² = 0,85** indica que aproximadamente el **85 % de la variabilidad observada** en el consumo mensual de gas envasado puede ser explicada por las variables incorporadas al modelo.

Este resultado evidencia una capacidad predictiva elevada considerando la complejidad del fenómeno analizado y la influencia de factores externos que no forman parte del conjunto de datos utilizado.

---

### 6.3.1 Comparación entre Valores Reales y Predichos

Además de las métricas numéricas, se realizó una evaluación visual del desempeño del modelo mediante un gráfico de dispersión que compara los valores reales observados en el conjunto de prueba con los valores predichos por la Regresión Lineal Múltiple.

Este tipo de visualización permite analizar la capacidad del modelo para reproducir el comportamiento real de la variable objetivo.

En una situación ideal, todas las observaciones deberían ubicarse sobre la línea diagonal de referencia, indicando una coincidencia perfecta entre los valores observados y las predicciones generadas.

Los resultados obtenidos muestran una relación positiva consistente entre los valores reales y los valores predichos.

La mayoría de las observaciones se distribuyen próximas a la línea de referencia, evidenciando que el modelo logró capturar adecuadamente la tendencia general del consumo mensual de gas envasado.

### Figura 7. Comparación entre valores reales y predichos

```markdown
![Valores reales vs predichos](images/real_vs_predicho.png)
```
### 6.3.2 Análisis de Residuos

Con el objetivo de complementar la evaluación del modelo, se realizó un análisis de residuos. Los residuos representan la diferencia entre los valores reales observados y las predicciones generadas por el algoritmo.

El estudio de los residuos constituye una herramienta fundamental para evaluar la calidad del ajuste de un modelo de regresión, ya que permite identificar posibles patrones sistemáticos de error, problemas de sesgo o comportamientos no capturados por el modelo.

En el gráfico de residuos se observa una distribución general alrededor de la línea horizontal ubicada en cero. Este comportamiento sugiere que la Regresión Lineal Múltiple no presenta una tendencia sistemática a sobreestimar o subestimar el consumo mensual de gas.

Asimismo, se identifican algunos residuos de magnitud considerable correspondientes a determinadas observaciones del conjunto de prueba. Estos errores puntuales indican que existen períodos específicos donde el comportamiento real del consumo difiere de las predicciones realizadas por el modelo.

Sin embargo, la ausencia de patrones claramente definidos en la distribución de los residuos constituye un indicador favorable, ya que sugiere que el modelo logra capturar adecuadamente la tendencia principal de los datos sin presentar problemas evidentes de ajuste.

Los resultados obtenidos permiten concluir que los errores observados son compatibles con la complejidad inherente al fenómeno estudiado y no comprometen la capacidad predictiva general del modelo.

### Figura 8. Análisis de residuos de la Regresión Lineal Múltiple

```markdown id="r81m4j"
![Análisis de residuos](images/residuos_regresion.png)
```

---

### 6.3.3 Importancia de Variables

Una de las principales ventajas de la Regresión Lineal Múltiple es su capacidad para interpretar la contribución relativa de cada variable predictora sobre la variable objetivo.

Con el propósito de identificar los factores con mayor influencia sobre las predicciones, se analizaron los coeficientes obtenidos por el modelo una vez finalizado el entrenamiento.

Para facilitar su interpretación, se utilizaron los valores absolutos de dichos coeficientes como medida de importancia relativa.

Los resultados mostraron que las variables con mayor influencia sobre el consumo mensual de gas envasado fueron:

* Temperatura mínima de Río Grande (`temp_min_rg`).
* Cantidad de usuarios registrados (`cantidad_usuarios`).
* Año.
* `mes_cos`.
* Temperatura máxima de Ushuaia (`temp_max_ush`).

La elevada importancia observada en la temperatura mínima de Río Grande resulta coherente con las características climáticas de la provincia.

A medida que disminuyen las temperaturas mínimas, aumenta la necesidad de calefacción, generando una mayor demanda de gas envasado.

Por otra parte, la relevancia de la variable `cantidad_usuarios` confirma que la cantidad de beneficiarios del programa constituye un factor directamente relacionado con el nivel de consumo registrado.

Asimismo, la importancia de las variables temporales evidencia la existencia de patrones estacionales y tendencias históricas que influyen significativamente sobre el comportamiento del consumo energético.

Estos resultados no solo aportan evidencia sobre la capacidad predictiva del modelo, sino que también permiten comprender cuáles son los factores más relevantes para explicar las variaciones observadas en la demanda mensual de gas envasado.

### Figura 9. Importancia relativa de las variables predictoras

```markdown id="lj3zrv"
![Importancia de variables](images/importancia_variables.png)
```

---

### 6.3.4 Interpretación General del Desempeño

La Regresión Lineal Múltiple presentó el mejor desempeño entre todos los algoritmos evaluados durante el proyecto.

El valor de **R² = 0,85** indica que el modelo logra explicar aproximadamente el **85 % de la variabilidad observada** en el consumo mensual de gas envasado, lo que representa un nivel de ajuste elevado para un problema influenciado por múltiples factores climáticos, temporales y operativos.

La combinación de las métricas obtenidas, el análisis de valores reales versus predichos, la distribución de residuos y la coherencia observada en la importancia de variables permite concluir que el modelo logró capturar adecuadamente las relaciones principales presentes en los datos.

Además de su buen desempeño predictivo, la Regresión Lineal Múltiple presenta una ventaja adicional vinculada a su interpretabilidad.

A diferencia de modelos más complejos, permite comprender cómo influyen las distintas variables sobre las predicciones realizadas, aportando información útil para el análisis y la toma de decisiones.

Por estos motivos, la Regresión Lineal Múltiple fue considerada el modelo más adecuado para la resolución del problema planteado.

---

### 6.3.5 Fortalezas y Limitaciones del Modelo

#### Fortalezas

* Buena capacidad predictiva.
* Facilidad de interpretación.
* Simplicidad de implementación.
* Coherencia con los patrones observados durante el análisis exploratorio.
* Identificación clara de variables relevantes para explicar el consumo.

#### Limitaciones

* Asume relaciones lineales entre variables predictoras y variable objetivo.
* Existen factores externos no incorporados al dataset.
* El comportamiento del consumo energético puede verse afectado por variables económicas, tarifarias o sociales no consideradas en el modelo.

Por esta razón, los resultados obtenidos deben interpretarse como estimaciones fundamentadas en la información disponible y no como representaciones exactas del comportamiento futuro del sistema energético provincial.

---

## 6.4 Modelos Alternativos y Comparación de Resultados

Con el objetivo de evaluar distintas estrategias de aprendizaje supervisado para problemas de regresión, además de la Regresión Lineal Múltiple se implementaron los algoritmos:

* Árbol de Decisión.
* Random Forest Regressor.

El Árbol de Decisión permitió modelar relaciones no lineales entre las variables predictoras y la variable objetivo mediante particiones sucesivas de los datos.

Por su parte, Random Forest utilizó un conjunto de árboles de decisión combinados con el propósito de mejorar la capacidad de generalización del modelo.

Una vez finalizado el entrenamiento, se comparó el desempeño de los tres algoritmos utilizando las métricas MAE, RMSE y R² sobre el conjunto de prueba.

| Modelo                    |   MAE (kg) |  RMSE (kg) |   R² |
| ------------------------- | ---------: | ---------: | ---: |
| Regresión Lineal Múltiple | 192.844,84 | 246.356,61 | 0,85 |
| Árbol de Decisión         | 199.675,30 | 250.714,38 | 0,84 |
| Random Forest             | 254.952,84 | 346.167,22 | 0,70 |

Los resultados obtenidos muestran que la Regresión Lineal Múltiple presentó el mejor desempeño general, alcanzando el mayor valor de R² y los menores errores de predicción.

Si bien el Árbol de Decisión obtuvo resultados cercanos, la Regresión Lineal logró una capacidad explicativa ligeramente superior.

En contraste, Random Forest presentó un desempeño considerablemente inferior sobre el conjunto de prueba.

En función de estos resultados, la Regresión Lineal Múltiple fue seleccionada como modelo principal para la resolución del problema planteado.
# 7. Conclusiones

## 7.1 Conclusiones Generales

El presente proyecto permitió desarrollar un modelo predictivo orientado a estimar el consumo mensual de gas envasado en la Provincia de Tierra del Fuego a partir de variables climáticas, temporales y operativas.

A lo largo del trabajo se llevó a cabo un proceso completo de Ciencia de Datos que incluyó la recopilación e integración de múltiples fuentes de información, la preparación y limpieza de los datos, el análisis exploratorio, la construcción de variables y la implementación de distintos modelos de Aprendizaje Automático supervisado.

Los resultados obtenidos durante el análisis exploratorio permitieron identificar patrones consistentes entre las condiciones climáticas y el consumo energético. Particularmente, las variables asociadas a la temperatura mostraron una relación significativa con el comportamiento de la demanda de gas envasado, resultado coherente con las características climáticas de la región.

Posteriormente, se evaluaron distintos algoritmos de regresión con el propósito de identificar la alternativa más adecuada para resolver el problema planteado.

La comparación de resultados evidenció que la **Regresión Lineal Múltiple** presentó el mejor desempeño general, alcanzando una elevada capacidad explicativa y menores errores de predicción respecto de los demás modelos evaluados.

El análisis de métricas, gráficos de predicción, residuos e importancia de variables permitió verificar que el modelo logró capturar adecuadamente las relaciones principales presentes en los datos.

Asimismo, la interpretación de los coeficientes permitió identificar a la temperatura mínima de Río Grande, la cantidad de usuarios y las variables temporales como algunos de los factores más influyentes sobre el consumo mensual de gas envasado.

En consecuencia, puede concluirse que las variables incorporadas al modelo aportan información relevante para explicar el comportamiento histórico del consumo energético provincial y que la metodología desarrollada constituye una herramienta válida para generar estimaciones futuras basadas en información climática y temporal.

---

## 7.2 Limitaciones del Proyecto

A pesar de los resultados satisfactorios obtenidos, es importante reconocer algunas limitaciones presentes en el desarrollo del proyecto.

En primer lugar, el conjunto de datos utilizado posee una cantidad relativamente reducida de observaciones mensuales, lo que limita la capacidad de los modelos para capturar comportamientos más complejos o eventos poco frecuentes.

Asimismo, existen factores potencialmente relevantes para explicar el consumo energético que no fueron incorporados al análisis, tales como:

* Variaciones tarifarias.
* Indicadores económicos.
* Cambios demográficos.
* Políticas públicas.
* Modificaciones en los hábitos de consumo de los usuarios.

Otra limitación está asociada a la disponibilidad de información climática histórica, particularmente en aquellos períodos donde fue necesario aplicar técnicas de imputación para completar registros faltantes.

Por estas razones, los resultados obtenidos deben interpretarse como estimaciones fundamentadas en la información disponible y no como representaciones exactas del comportamiento futuro del sistema energético provincial.

---

## 7.3 Líneas Futuras de Trabajo

Como posibles líneas de mejora para futuras investigaciones, se propone ampliar el conjunto de variables utilizadas incorporando información económica, demográfica y energética adicional que permita enriquecer el proceso de modelado.

También podría resultar de interés evaluar algoritmos más avanzados de aprendizaje supervisado, tales como:

* Gradient Boosting.
* XGBoost.
* LightGBM.

El objetivo sería analizar si estos algoritmos logran capturar patrones adicionales presentes en los datos y mejorar la capacidad predictiva del modelo.

Otra posible mejora consiste en ampliar la serie temporal utilizada mediante la incorporación de nuevos registros históricos, permitiendo incrementar la cantidad de observaciones disponibles para el entrenamiento y evaluación de los modelos.

Finalmente, se recomienda actualizar periódicamente el modelo a medida que se disponga de nueva información, favoreciendo su adaptación a cambios futuros en las condiciones climáticas, energéticas y sociales de la provincia.

---

# 8. Bibliografía

* Instituto Provincial de Análisis e Investigación, Estadística y Censos (IPIEC). Datos estadísticos provinciales de consumo energético y variables climáticas de la Provincia de Tierra del Fuego. Disponible en: https://ipiec.tierradelfuego.gob.ar/

* Open-Meteo. Historical Weather API. Datos meteorológicos históricos utilizados para la imputación de valores faltantes. Disponible en: https://open-meteo.com/

* Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., et al. (2011). *Scikit-Learn: Machine Learning in Python*. Journal of Machine Learning Research, 12, 2825–2830.

* McKinney, W. (2022). *Python for Data Analysis* (3rd ed.). O'Reilly Media.

* Harris, C. R., Millman, K. J., van der Walt, S. J., et al. (2020). *Array Programming with NumPy*. Nature, 585, 357–362.

* Hunter, J. D. (2007). *Matplotlib: A 2D Graphics Environment*. Computing in Science & Engineering, 9(3), 90–95.

* Waskom, M. (2024). *Seaborn: Statistical Data Visualization*. Disponible en: https://seaborn.pydata.org/

* Python Software Foundation. *Python Language Reference*. Disponible en: https://www.python.org/

* Pandas Development Team. *Pandas Documentation*. Disponible en: https://pandas.pydata.org/

* Scikit-Learn Developers. *Scikit-Learn Documentation*. Disponible en: https://scikit-learn.org/
