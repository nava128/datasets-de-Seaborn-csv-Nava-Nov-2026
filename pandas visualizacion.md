¡Excelente evolución del curso! Para trabajar todo esto de forma profesional y ordenada en **VS Code**, lo primero es organizar nuestro proyecto con una estructura clara de carpetas y archivos.

---

### 1. Estructura de Carpetas y Archivos en VS Code

Crea una carpeta principal llamada `curso_data_science` y dentro organiza los archivos por módulos:

```text
curso_data_science/
│
├── datos/                      # Carpeta para archivos de entrada/salida
│   └── ventas_raw.csv          # Datos sin procesar (ejemplo)
│
├── modulo2_datos/
│   ├── 07_tipos_de_datos.py     # Lección 7: NumPy arrays y tipos
│   ├── 08_almacenar_datos.py    # Lección 8: Cargar y guardar con Pandas
│   └── 09_10_preprocesamiento.py# Lecciones 9 y 10: Limpieza de datos
│
└── modulo3_tecnicas/
    ├── 11_analisis_descriptivo.py# Lección 11: Estadísticas y Matplotlib
    ├── 12_analisis_explicativo.py# Lección 12: Correlaciones y causalidad
    ├── 13_analisis_predictivo.py # Lección 13: Regresión/Predicción rápida
    └── 14_analisis_prescriptivo.py# Lección 14: Simulación de escenarios/optimización

```

> **Tip para VS Code:** Abre VS Code, presiona `Ctrl + Shift + N` (o `Cmd + O` en Mac) y abre la carpeta `curso_data_science`. Puedes ejecutar cada script haciendo clic en el botón de reproducción ▶️ arriba a la derecha o usando la terminal integrada con `python modulo2_datos/07_tipos_de_datos.py`.

---

### MÓDULO 2: LOS DATOS

#### Lección 7: Tipos de Datos (Con NumPy y Pandas)

*Archivo: `modulo2_datos/07_tipos_de_datos.py*`

```python
import numpy as np
import pandas as pd

# NumPy maneja arreglos numéricos optimizados (float, int, bool)
edades = np.array([25, 30, 35, 40], dtype=np.int32)
precios = np.array([19.99, 29.50, 49.99, 9.99], dtype=np.float64)

# Pandas nos permite combinar múltiples tipos de datos en un DataFrame
df_tipos = pd.DataFrame(
    {
        "ID": np.arange(1, 5),  # Numérico entero
        "Edad": edades,  # Numérico entero
        "Precio": precios,  # Numérico flotante
        "Cliente_VIP": [True, False, True, False],  # Booleano
        "Categoria": [
            "Alta",
            "Media",
            "Alta",
            "Baja",
        ],  # Categórico (Texto / String)
    }
)

# Inspeccionamos los tipos de datos en cada columna
print("--- Tipos de datos de cada columna ---")
print(df_tipos.dtypes)

```

---

#### Lección 8: Formas de Almacenar Datos

*Archivo: `modulo2_datos/08_almacenar_datos.py*`

```python
import pandas as pd

# 1. Crear datos en memoria
datos = {
    "Producto": ["Laptop", "Mouse", "Teclado"],
    "Stock": [15, 120, 45],
    "Precio": [850.0, 25.5, 45.0],
}
df = pd.DataFrame(datos)

# 2. Guardar datos localmente en formato CSV
df.to_csv("datos/inventario.csv", index=False)
print("¡Archivo 'inventario.csv' guardado correctamente en la carpeta datos/!")

# 3. Cargar datos almacenados desde el disco
df_cargado = pd.read_csv("datos/inventario.csv")
print("\n--- Datos cargados desde el archivo CSV ---")
print(df_cargado)

```

---

#### Lecciones 9 y 10: Pre-procesamiento de Datos (Teoría y Ejemplo Práctico)

*Archivo: `modulo2_datos/09_10_preprocesamiento.py*`

```python
import numpy as np
import pandas as pd

# Ejemplo práctico: Crear un DataFrame con errores comunes (Valores nulos y duplicados)
raw_data = {
    "Cliente": ["Ana", "Luis", "Carlos", "Luis", "Sofia"],
    "Edad": [28, np.nan, 34, np.nan, 22],  # np.nan representa un valor nulo
    "Gasto": [150.0, 200.0, np.nan, 200.0, 95.0],
}
df = pd.DataFrame(raw_data)

print("--- DATOS ORIGINALES CON ERRORES ---")
print(df)

# PASO 1: Eliminar filas duplicadas
df_limpio = df.drop_duplicates()

# PASO 2: Tratar valores nulos (Imputación: rellenar Edad con el promedio y Gasto con 0)
df_limpio["Edad"] = df_limpio["Edad"].fillna(df_limpio["Edad"].mean())
df_limpio["Gasto"] = df_limpio["Gasto"].fillna(0)

# PASO 3: Convertir tipos de datos (Edad a entero)
df_limpio["Edad"] = df_limpio["Edad"].astype(int)

print("\n--- DATOS PRE-PROCESADOS Y LIMPIOS ---")
print(df_limpio)

```

---

### MÓDULO 3: LAS TÉCNICAS

#### Lección 11: Análisis Descriptivo y Exploratorio (EDA)

*Archivo: `modulo3_tecnicas/11_analisis_descriptivo.py*`

```python
import matplotlib.pyplot as plt
import pandas as pd

# Datos de ventas semanales
datos = {
    "Dia": ["Lun", "Mar", "Mie", "Jue", "Vie", "Sab", "Dom"],
    "Ventas": [120, 150, 170, 160, 240, 310, 280],
}
df = pd.DataFrame(datos)

# Análisis Estadístico Descriptivo
print("--- RESUMEN ESTADÍSTICO ---")
print(df["Ventas"].describe())  # Media, mediana, desviación estándar, min, max

# Análisis Exploratorio Visual (Matplotlib)
plt.figure(figsize=(8, 4))
plt.plot(
    df["Dia"],
    df["Ventas"],
    marker="o",
    color="b",
    linestyle="-",
    label="Ventas ($)",
)
plt.title("Análisis Exploratorio: Tendencia de Ventas Semanales")
plt.xlabel("Día de la semana")
plt.ylabel("Ventas totales ($)")
plt.grid(True, linestyle="--", alpha=0.6)
plt.legend()
plt.tight_layout()
plt.show()

```

---

#### Lección 12: Análisis Explicativo (Buscando el "Por Qué")

*Archivo: `modulo3_tecnicas/12_analisis_explicativo.py*`

```python
import matplotlib.pyplot as plt
import pandas as pd

# Evaluar la relación entre Inversión en Publicidad y Ventas
df = pd.DataFrame(
    {
        "Inversion_Publicidad": [100, 200, 300, 400, 500, 600],
        "Ventas": [1200, 1800, 2600, 3100, 3900, 4400],
    }
)

# Calcular el coeficiente de correlación (Explicación cuantitativa)
correlacion = df["Inversion_Publicidad"].corr(df["Ventas"])
print(f"Coeficiente de correlación de Pearson: {correlacion:.2f}")

# Gráfica de dispersión para explicar la relación causa-efecto
plt.figure(figsize=(7, 4))
plt.scatter(
    df["Inversion_Publicidad"], df["Ventas"], color="green", s=80, alpha=0.8
)
plt.title(
    f"Análisis Explicativo: Impacto del Marketing (Correlación: {correlacion:.2f})"
)
plt.xlabel("Inversión en Publicidad ($)")
plt.ylabel("Ventas Obtenidas ($)")
plt.grid(True)
plt.tight_layout()
plt.show()

```

---

#### Lección 13: Análisis Predictivo (Estimación Futura)

*Archivo: `modulo3_tecnicas/13_analisis_predictivo.py*`

```python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Datos históricos de ventas
meses = np.array([1, 2, 3, 4, 5])
ventas = np.array([100, 150, 200, 240, 300])

# Ajuste de línea de tendencia simple (Modelo predictivo lineal: y = mx + b)
linea_tendencia = np.polyfit(meses, ventas, 1)
modelo_predictivo = np.poly1d(linea_tendencia)

# Predicción para los meses 6 y 7
meses_futuros = np.array([6, 7])
ventas_predichas = modelo_predictivo(meses_futuros)

print(f"Predicción Mes 6: ${ventas_predichas[0]:.2f}")
print(f"Predicción Mes 7: ${ventas_predichas[1]:.2f}")

# Visualización del modelo
plt.figure(figsize=(8, 4))
plt.scatter(meses, ventas, color="black", label="Datos Históricos")
plt.plot(
    np.append(meses, meses_futuros),
    modelo_predictivo(np.append(meses, meses_futuros)),
    "r--",
    label="Modelo Predictivo",
)
plt.scatter(
    meses_futuros,
    ventas_predichas,
    color="red",
    s=100,
    zorder=5,
    label="Predicciones",
)
plt.title("Análisis Predictivo: Proyección de Ventas Futuras")
plt.xlabel("Mes")
plt.ylabel("Ventas ($)")
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()

```

---

#### Lección 14: Análisis Prescriptivo (Toma de Decisiones / Recomendación)

*Archivo: `modulo3_tecnicas/14_analisis_prescriptivo.py*`

```python
import matplotlib.pyplot as plt
import pandas as pd

# Escenarios posibles para decidir la mejor estrategia de inventario
escenarios = pd.DataFrame(
    {
        "Estrategia": [
            "Sin Descuento",
            "Descuento 10%",
            "Descuento 20%",
            "Promoción 2x1",
        ],
        "Ventas_Estimadas_Unidades": [100, 150, 220, 300],
        "Ganancia_Neta_Estimada": [5000, 6000, 6600, 4500],
    }
)

# Prescripción: Encontrar automáticamente la opción óptima para maximizar ganancia
mejor_opcion = escenarios.loc[escenarios["Ganancia_Neta_Estimada"].idxmax()]

print("--- RECOMENDACIÓN PRESCRIPTIVA ---")
print(
    f"Estrategia sugerida: '{mejor_opcion['Estrategia']}' maximiza el beneficio con ${mejor_opcion['Ganancia_Neta_Estimada']}"
)

# Graficar la comparación de escenarios prescriptivos
plt.figure(figsize=(8, 4))
barras = plt.bar(
    escenarios["Estrategia"],
    escenarios["Ganancia_Neta_Estimada"],
    color=["gray", "gray", "green", "gray"],
)
plt.title(
    "Análisis Prescriptivo: Comparativa de Ganancia Neta por Estrategia"
)
plt.ylabel("Ganancia Neta ($)")
plt.axhline(
    mejor_opcion["Ganancia_Neta_Estimada"],
    color="green",
    linestyle=":",
    label="Óptimo recomendado",
)
plt.legend()
plt.tight_layout()
plt.show()

```

---
