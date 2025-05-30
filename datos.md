

# Proyecto_3_Script_Final.Rmd - Modelado del Peso al Nacer



## 📁 Script y Datos

Este script (`Proyecto_3_Script_Final.Rmd`) contiene la implementación de los algoritmos de modelado estadístico para predecir el **peso al nacer** de los recién nacidos.

Los datos se encuentran en el archivo `Nacimientos_Data_Final.RData`, el cual puede ser cargado con:

```r
load("Nacimientos_Data_Final.RData")
````

Esto genera el objeto `dataset_final` que contiene todas las observaciones a analizar.

---

## 🎯 Variable Respuesta

La variable seleccionada como **respuesta** del modelo es:

```r
respuesta <- "peso_total_g"
```

Corresponde al **peso total del bebé al nacer en gramos**, y es una variable numérica continua.

---

## 📋 Variables Predictoras

Las variables predictoras utilizadas en los modelos están definidas en el vector `variables_oficiales`:

```r
variables_oficiales <- c(
  "Depreg", "Mupreg", "Mesreg", "Añoreg", "Depocu", "Mupocu",
  "Libras", "Onzas", "Diaocu", "Mesocu", "Añoocu", "Sexo", "Tipar", "Edadp",
  "Deprep", "Muprep", "Escivp", "Depnap", "Mupnap", "Naciop", "Ocupap",
  "Edadm", "Deprem", "Muprem", "Escivm", "Depnam", "Mupnam", "Naciom", "Ocupam",
  "Escolap", "Escolam", "Paisrep", "Paisrem", "Paisnacp", "Paisnacm", "Asisrec",
  "Sitioocu", "TipoIns", "ViaPar", "PuebloPP", "PuebloPM", "Tohite", "Tohinm",
  "Tohivi", "grupetma", "Gretnp", "Gretnm", "Ciuopad", "Ciuomad", "Munpnam",
  "archivo", "anio"
)
```

---

## 🧾 Descripción y tipo de cada variable

| **Variable** | **Descripción**                                               | **Tipo de variable**     |
| ------------ | ------------------------------------------------------------- | ------------------------ |
| Depreg       | Código del departamento donde se registró el nacimiento       | Categórica nominal       |
| Mupreg       | Código del municipio donde se registró el nacimiento          | Categórica nominal       |
| Mesreg       | Mes de registro del nacimiento                                | Identificador temporal   |
| Añoreg       | Año de registro del nacimiento                                | Identificador temporal   |
| Depocu       | Código del departamento donde ocurrió el nacimiento           | Categórica nominal       |
| Mupocu       | Código del municipio donde ocurrió el nacimiento              | Categórica nominal       |
| Libras       | Peso del bebé al nacer en libras                              | Numérica discreta        |
| Onzas        | Peso del bebé al nacer en onzas                               | Numérica discreta        |
| Diaocu       | Día en que ocurrió el nacimiento                              | Identificador temporal   |
| Mesocu       | Mes en que ocurrió el nacimiento                              | Identificador temporal   |
| Añoocu       | Año en que ocurrió el nacimiento                              | Identificador temporal   |
| Sexo         | Sexo del bebé (1 = Hombre, 2 = Mujer)                         | Categórica nominal       |
| Tipar        | Tipo de parto (1 = Vaginal, 2 = Cesárea, etc.)                | Categórica nominal       |
| Edadp        | Edad del padre en años                                        | Numérica discreta        |
| Deprep       | Departamento de residencia del padre                          | Categórica nominal       |
| Muprep       | Municipio de residencia del padre                             | Categórica nominal       |
| Escivp       | Estado civil del padre                                        | Categórica nominal       |
| Depnap       | Departamento de nacimiento del padre                          | Categórica nominal       |
| Mupnap       | Municipio de nacimiento del padre                             | Categórica nominal       |
| Naciop       | Nacionalidad del padre (código)                               | Categórica nominal       |
| Ocupap       | Ocupación del padre (según clasificación nacional)            | Categórica nominal       |
| Edadm        | Edad de la madre en años                                      | Numérica discreta        |
| Deprem       | Departamento de residencia de la madre                        | Categórica nominal       |
| Muprem       | Municipio de residencia de la madre                           | Categórica nominal       |
| Escivm       | Estado civil de la madre                                      | Categórica nominal       |
| Depnam       | Departamento de nacimiento de la madre                        | Categórica nominal       |
| Mupnam       | Municipio de nacimiento de la madre                           | Categórica nominal       |
| Naciom       | Nacionalidad de la madre (código)                             | Categórica nominal       |
| Ocupam       | Ocupación de la madre                                         | Categórica nominal       |
| Escolap      | Nivel educativo alcanzado por el padre                        | Categórica ordinal       |
| Escolam      | Nivel educativo alcanzado por la madre                        | Categórica ordinal       |
| Paisrep      | País de residencia del padre                                  | Categórica nominal       |
| Paisrem      | País de residencia de la madre                                | Categórica nominal       |
| Paisnacp     | País de nacimiento del padre                                  | Categórica nominal       |
| Paisnacm     | País de nacimiento de la madre                                | Categórica nominal       |
| Asisrec      | Si hubo asistencia médica en el nacimiento                    | Categórica nominal       |
| Sitioocu     | Lugar donde ocurrió el nacimiento (hospital, casa, etc.)      | Categórica nominal       |
| TipoIns      | Tipo de institución que atendió el parto (si aplica)          | Categórica nominal       |
| ViaPar       | Vía del parto (puede estar duplicada en algunos registros)    | Categórica nominal       |
| PuebloPP     | Pertenencia étnica del padre (pueblo indígena, mestizo, etc.) | Categórica nominal       |
| PuebloPM     | Pertenencia étnica de la madre                                | Categórica nominal       |
| Tohite       | Total de hijos tenidos                                        | Numérica discreta        |
| Tohinm       | Total de hijos nacidos muertos                                | Numérica discreta        |
| Tohivi       | Total de hijos vivos                                          | Numérica discreta        |
| grupetma     | Clasificación del grupo étnico de la madre (código)           | Categórica nominal       |
| Gretnp       | Grupo étnico del padre                                        | Categórica nominal       |
| Gretnm       | Grupo étnico de la madre                                      | Categórica nominal       |
| Ciuopad      | Ciudad de nacimiento del padre (algunos años)                 | Categórica nominal       |
| Ciuomad      | Ciudad de nacimiento de la madre (algunos años)               | Categórica nominal       |
| Munpnam      | Municipio de nacimiento de la madre (alternativa a munnam)    | Categórica nominal       |
| archivo      | Nombre del archivo del cual se extrajo el dato                | Identificador de archivo |
| anio         | Año correspondiente al archivo (2009–2022)                    | Identificador de archivo |

---

## 📁 Scripts utilizados

El proyecto se divide en dos scripts principales:

- **`Analisis_Exploratorio.Rmd`**: Contiene el análisis exploratorio de los datos, incluyendo limpieza, resumen de variables, y visualización de patrones relevantes relacionados con el peso al nacer.
- **`Script_Modelos.Rmd`**: Incluye el desarrollo y ejecución de modelos estadísticos, como regresión lineal múltiple, para predecir el bajo peso al nacer.
