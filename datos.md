---
title: "Proyecto 3 - Predicción del Bajo Peso al Nacer"
output: html_document
---

## 📁 Estructura del Proyecto

El proyecto se divide en dos scripts principales:

- **`Analisis_Exploratorio.Rmd`**: Contiene el análisis exploratorio de los datos, incluyendo limpieza, resumen de variables, y visualización de patrones relevantes relacionados con el peso al nacer.
- **`Script_Modelos.Rmd`**: Incluye el desarrollo y ejecución de modelos estadísticos, como regresión lineal múltiple, para predecir el bajo peso al nacer.

## 🧾 Dataset

Los datos utilizados provienen del archivo `Nacimientos_Data_Final.RData`, el cual se carga bajo el nombre de objeto `dataset_final`.

## 🎯 Variable Respuesta

La variable respuesta elegida para el análisis es:

```r
respuesta <- "peso_total_g"
