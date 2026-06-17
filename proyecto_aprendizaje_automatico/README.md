# Predicción del Consumo Mensual de Gas Envasado en Tierra del Fuego

## Descripción del Proyecto

Este proyecto tiene como objetivo desarrollar un modelo de Aprendizaje Automático capaz de predecir el consumo mensual de gas envasado en la provincia de Tierra del Fuego a partir de variables climáticas, meteorológicas y temporales.

La propuesta busca analizar la relación existente entre las condiciones ambientales y la demanda energética utilizando datos oficiales provenientes de organismos públicos y registros climáticos históricos de las ciudades de Río Grande y Ushuaia.

## Objetivo General

Desarrollar un modelo predictivo que permita estimar el consumo mensual de gas envasado utilizando información climática y temporal.

## Objetivos Específicos

* Obtener y consolidar datasets energéticos y climáticos.
* Realizar tareas de limpieza y preprocesamiento de datos.
* Integrar diferentes fuentes de información.
* Aplicar análisis exploratorio de datos (EDA).
* Seleccionar variables relevantes para el modelado.
* Entrenar y comparar distintos modelos de regresión.
* Evaluar el desempeño de los modelos mediante métricas apropiadas.
* Interpretar los resultados obtenidos.

## Variable Objetivo

* consumo_gas_kg

## Variables Predictoras

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
* mes
* anio

## Estructura del Proyecto

```text
proyecto_aprendizaje_automatico/
│
├── data/          # Datos originales y procesados
├── docs/          # Documentación del proyecto
├── notebooks/     # Notebooks de análisis y modelado
├── references/    # Material de referencia y fuentes
├── reports/       # Informes y resultados
└── README.md
```

## Fuentes de Datos

* Instituto Provincial de Análisis e Investigación, Estadística y Censos (IPIEC)
* Open-Meteo (recuperación de información climática faltante)

## Modelos Evaluados

* Regresión Lineal
* Árbol de Decisión para Regresión
* Random Forest Regressor

## Métricas de Evaluación

* MAE (Mean Absolute Error)
* MSE (Mean Squared Error)
* RMSE (Root Mean Squared Error)
* Coeficiente de Determinación (R²)

## Herramientas Utilizadas

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn
* Google Colab
* Open-Meteo

## Autora

Sara Valenzuela

Tecnicatura Superior en Ciencia de Datos e Inteligencia Artificial

Centro Politécnico Superior Malvinas Argentinas


