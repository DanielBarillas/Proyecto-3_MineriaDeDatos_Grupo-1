# 📊 Avances 1: Análisis Exploratorio de Datos de Nacimientos en Guatemala (2009–2022)

## 🏫 Universidad del Valle de Guatemala - Campus Central  
**Facultad:** Ingeniería  
**Departamento:** Ciencias de la Computación  
**Curso:** Minería de Datos (CC3074) - Sección 10  
**Semestre:** II – 2025  
**Proyecto:** Proyecto #3  
**Entrega:** Entrega 1 – Análisis Exploratorio  

---

## 👥 Integrantes del Grupo #1  
- **Pablo Daniel Barillas Moreno** - *Carné No. 22193*  
- **Mathew Cordero Aquino** - *Carné No. 22982*  

---

## 📌 Descripción del Proyecto  

En este proyecto se trabajó con los conjuntos de datos de **nacimientos en Guatemala** publicados por el **INE** desde **2009 hasta 2022**, en formato `.sav` (SPSS). El objetivo fue realizar un **análisis exploratorio detallado** para formular preguntas de investigación y detectar patrones relevantes.

---

## 🔎 Actividades Realizadas  

### 1. Exploración de Datos  
- Se describieron las variables y observaciones presentes en todos los años.
- Se identificaron valores extremos (como `Edadp = 1000`) y se eliminaron.
- Se aplicaron filtros para limpiar los datos fuera de rangos esperados.

### 2. Resumen Estadístico  
- Se analizó la distribución de las variables numéricas: `Edadp`, `Libras` y `Onzas`.
- Se verificó la normalidad con histogramas.
- Se generaron tablas de frecuencia para variables categóricas (`Sexo`, `Tipar`, etc.).

### 3. Cruce de Variables  
- Se analizaron relaciones como `Edadp` vs `Tipar`, y `Sexo` vs `peso al nacer`.
- Se utilizaron gráficos de cajas (boxplots) para visualizar diferencias entre grupos.

### 4. Gráficos Exploratorios  
- Se produjeron histogramas, diagramas de caja, y gráficos de dispersión.
- Se ajustaron escalas para visualizar mejor los datos sin valores atípicos.

### 5. Clustering  
- (Pendiente de incluir...)

---

## 📦 Limpieza y Transformación de Datos  
- Estandarización de variables y tipos (`factor`, `numeric`).
- Conversión de etiquetas codificadas en SPSS (`haven_labelled`) a factores en R.
- Se excluyeron registros con pesos inválidos o edades irreales.
- Se aplicaron etiquetas descriptivas al tipo de parto (`Tipar`).

---

## 🛠 Herramientas Utilizadas  

- **Lenguaje:** R  
- **Entorno:** RStudio  
- **Librerías:** `haven`, `dplyr`, `ggplot2`, `purrr`  
- **Formato de datos:** `.sav` (SPSS)  
- **Control de versiones:** GitHub  

---

## 📢 Hallazgos Destacados hasta los avances 

✔️ La edad de los padres al momento del nacimiento tiene su moda entre 25 y 30 años.  
✔️ El peso al nacer muestra distribuciones normales, con la mayoría entre 6 y 7 libras.  
✔️ Se encontró una fuerte prevalencia del parto vaginal sobre otros tipos.  
✔️ La asistencia médica (`Asisrec`) varía según el municipio y departamento.  
✔️ Se identificaron valores codificados como 999 y 1000 que fueron limpiados.  
✔️ Se logró automatizar el análisis año por año sin sobrecargar la memoria.

---

## 📄 Entregables  

- 📝 **Informe:** Vínculo de GitHub con historial de cambios  
- 💻 **Script R:** Archivo `.R` con todo el análisis exploratorio automatizado  
- 🔗 **Repositorio GitHub:** Contiene el código fuente, este README y visualizaciones

---

