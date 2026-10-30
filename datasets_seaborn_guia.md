# Datasets de Seaborn: identificación, tipos y descarga

Los **datasets de Seaborn** son conjuntos de datos que se utilizan para aprender, practicar y desarrollar proyectos de análisis de datos, estadística, visualización y Machine Learning con Python.

Una ventaja de Seaborn es que incluye varios conjuntos de datos de ejemplo que puedes cargar directamente desde Python, sin tener que descargar manualmente archivos CSV.

## 1. ¿Qué es un dataset de Seaborn?

Un *dataset* es un conjunto de datos organizado en filas y columnas, normalmente representado mediante un DataFrame de Pandas.

Por ejemplo, un dataset puede contener información sobre:

- Pasajeros del Titanic.
- Propinas en restaurantes.
- Especies de pingüinos.
- Flores y sus características.
- Automóviles y consumo de combustible.
- Temperaturas y condiciones climáticas.

## 2. ¿Cómo saber qué datasets tiene Seaborn?

Primero debes instalar Seaborn.

Abre la terminal de VS Code y ejecuta:

```bash
pip install seaborn pandas matplotlib
```

Después, crea un archivo llamado:

```text
dataset_seaborn.py
```

Escribe el siguiente código:

```python
import seaborn as sns

# Mostrar los datasets disponibles
print(sns.get_dataset_names())
```

La función:

```python
sns.get_dataset_names()
```

Permite consultar los nombres de los datasets que Seaborn tiene registrados en su catálogo.

**Importante:** los nombres disponibles pueden variar según la versión y el acceso a los recursos externos.

## 3. ¿Los datasets vienen incluidos o se descargan?

Esta es una distinción importante: **Seaborn incluye las funciones para acceder a los datasets, pero los archivos de datos de ejemplo normalmente se descargan desde Internet.**

El funcionamiento es el siguiente:

1. Instalas Seaborn en Python.
2. Utilizas `sns.load_dataset()`.
3. Seaborn busca el archivo CSV en su repositorio de datos.
4. Si no existe una copia local, lo descarga.
5. Guarda una copia en la caché de tu computadora.
6. Lo carga como un DataFrame de Pandas.

Por lo tanto, la primera descarga requiere conexión a Internet. Si el dataset ya está almacenado en caché, puedes volver a utilizarlo sin descargarlo nuevamente.

## 4. ¿Cómo cargar un dataset?

Ejemplo utilizando el dataset Titanic:

```python
import seaborn as sns
import pandas as pd

# Cargar dataset
titanic = sns.load_dataset('titanic')

# Mostrar las primeras 5 filas
print(titanic.head())

# Mostrar dimensiones
print(titanic.shape)

# Mostrar nombres de columnas
print(titanic.columns)

# Mostrar información general
print(titanic.info())
```

El resultado se almacena en una variable llamada `titanic`, que es un DataFrame de Pandas.

## 5. ¿Qué tipos de datasets existen en Seaborn?

Los datasets contienen diferentes tipos de información. Esta tabla presenta algunos de los más útiles para comenzar a estudiar análisis de datos y Machine Learning.

| Dataset | Información que contiene | Aplicación |
|---|---|---|
| `titanic` | Pasajeros del Titanic | Clasificación |
| `iris` | Características de flores | Clasificación |
| `penguins` | Características de pingüinos | Clasificación |
| `tips` | Propinas en restaurantes | Regresión y análisis |
| `diamonds` | Características y precios de diamantes | Regresión |
| `flights` | Pasajeros de aerolíneas por mes | Series temporales |
| `mpg` | Consumo de combustible de automóviles | Regresión |
| `planets` | Información sobre planetas | Análisis exploratorio |
| `car_crashes` | Accidentes automovilísticos | Análisis estadístico |
| `fmri` | Señales de resonancia magnética funcional | Análisis de señales |

## 6. ¿De qué tipo son sus columnas?

Los datasets pueden contener distintos tipos de variables:

| Tipo de dato | Descripción | Ejemplo |
|---|---|---|
| `int64` | Números enteros | Edad: 25 |
| `float64` | Números decimales | Peso: 65.5 |
| `object` | Texto o categorías | Sexo: masculino |
| `category` | Datos categóricos | Clase: primera |
| `bool` | Valores verdadero o falso | Superviviente: True |
| `datetime64` | Fechas y horas | 2026-10-30 |

Para conocer los tipos de datos de cualquier dataset, utiliza:

```python
print(titanic.dtypes)
```

Para conocer su estructura completa:

```python
print(titanic.info())
```

**Nota:** los tipos concretos dependen del dataset y de cómo Pandas interprete sus columnas.

## 7. ¿Cómo descargar los datasets en formato CSV?

Existen dos maneras.

### Opción A. Descargar directamente desde GitHub

Seaborn mantiene un repositorio público con los archivos CSV:

**Repositorio oficial de datasets de Seaborn:**  
https://github.com/mwaskom/seaborn-data

Pasos:

1. Abre el repositorio.
2. Busca el dataset que necesitas, por ejemplo `titanic.csv`.
3. Abre el archivo.
4. Selecciona la opción **Raw**.
5. Guarda el archivo en tu computadora.

### Opción B. Descargar mediante Python

Puedes descargar un dataset y guardarlo en tu propia carpeta de trabajo:

```python
import seaborn as sns

# Cargar dataset desde Seaborn
titanic = sns.load_dataset('titanic')

# Guardar en formato CSV
titanic.to_csv('titanic.csv', index=False)

print("Dataset descargado correctamente")
```

El archivo `titanic.csv` quedará guardado en el directorio de trabajo actual de Python.

## 8. Ejemplo práctico: identificar un dataset

Este ejemplo te permitirá conocer las características de cualquier dataset de Seaborn.

```python
import seaborn as sns
import pandas as pd

# Cargar dataset
df = sns.load_dataset('penguins')

# Mostrar primeras filas
print("PRIMERAS FILAS")
print(df.head())

# Número de filas y columnas
print("DIMENSIONES")
print(df.shape)

# Nombres de columnas
print("COLUMNAS")
print(df.columns)

# Tipos de datos
print("TIPOS DE DATOS")
print(df.dtypes)

# Información general
print("INFORMACIÓN GENERAL")
print(df.info())

# Valores faltantes
print("VALORES FALTANTES")
print(df.isnull().sum())
```

Este ejercicio es útil para que los estudiantes aprendan a identificar la estructura de los datos antes de desarrollar un modelo de Machine Learning.

## 9. ¿Qué datasets recomiendo para aprender Machine Learning?

### 1. Titanic

**Nivel:** Principiante

- Predecir si un pasajero sobrevivió.
- Variables: edad, sexo, clase y tarifa.
- Tipo de aprendizaje: supervisado, clasificación.

### 2. Iris

**Nivel:** Principiante

- Clasificar especies de flores.
- Variables: longitud y anchura de pétalos y sépalos.
- Tipo de aprendizaje: supervisado, clasificación.

### 3. Penguins

**Nivel:** Principiante

- Identificar especies de pingüinos.
- Variables: peso, longitud del pico y aletas.
- Tipo de aprendizaje: supervisado, clasificación.

### 4. Diamonds

**Nivel:** Intermedio

- Predecir el precio de un diamante.
- Variables: quilates, corte, color y claridad.
- Tipo de aprendizaje: supervisado, regresión.

### 5. MPG

**Nivel:** Intermedio

- Predecir el consumo de combustible.
- Variables: cilindros, potencia, peso y aceleración.
- Tipo de aprendizaje: supervisado, regresión.

## 10. Resumen de comandos importantes

| Comando | ¿Para qué sirve? |
|---|---|
| `sns.get_dataset_names()` | Consultar datasets disponibles. |
| `sns.load_dataset('titanic')` | Cargar un dataset. |
| `df.head()` | Mostrar primeras filas. |
| `df.tail()` | Mostrar últimas filas. |
| `df.shape` | Obtener filas y columnas. |
| `df.columns` | Consultar nombres de columnas. |
| `df.dtypes` | Consultar tipos de datos. |
| `df.info()` | Consultar información general. |
| `df.describe()` | Obtener estadísticas descriptivas. |
| `df.isnull().sum()` | Contar valores faltantes. |
| `df.to_csv()` | Guardar los datos en CSV. |

## Documentación oficial para consultar

- [get_dataset_names()](https://seaborn.pydata.org/generated/seaborn.get_dataset_names.html)
- [load_dataset()](https://seaborn.pydata.org/generated/seaborn.load_dataset.html)
- [Estructuras de datos en Seaborn](https://seaborn.pydata.org/tutorial/data_structure.html)

## Recomendación didáctica

Comienza con `iris`, `titanic` y `penguins`. Son excelentes para enseñar carga de datos, limpieza, identificación de variables, estadísticas descriptivas, gráficas y posteriormente clasificación mediante Scikit-learn.
