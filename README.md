# Predicción de Costos de Seguros Médicos (Regresión)

Este es un proyecto de portafolio de Ciencia de Datos que demuestra un modelo de **Regresión** para predecir los costos médicos (variable `charges`) basado en las características del paciente. El proyecto utiliza Python, Scikit-learn y Pandas.

## Contexto y Objetivo
Como médico, entiendo el impacto de los factores de riesgo en la salud. Como científico de datos, mi objetivo era cuantificar ese impacto en términos financieros. Este modelo busca predecir el costo de un seguro médico, una tarea vital para la gestión hospitalaria y las aseguradoras.

## Herramientas Utilizadas
* **Python**
* **Pandas:** Para limpieza y preprocesamiento.
* **Matplotlib / Seaborn:** Para el Análisis Exploratorio de Datos (EDA).
* **NumPy:** Para transformaciones matemáticas (log).
* **Scikit-learn:** Para `StandardScaler`, `train_test_split`, `LinearRegression` y `RandomForestRegressor`.

## Proceso y Hallazgos Clave

### 1. Análisis Exploratorio (EDA)
El análisis inicial de la variable objetivo (`costo_seguro`) mostró un fuerte **sesgo positivo** (cola larga a la derecha). Esto viola los supuestos de muchos modelos de regresión.


### 2. Preprocesamiento
Para corregir el sesgo, apliqué una **transformación logarítmica (`np.log1p`)** a la variable `costo_seguro`, resultando en una distribución mucho más normal. Además, se codificaron las variables categóricas (`fumador`, `sexo`, `region`) usando `map` y `get_dummies`.


### 3. Modelado y Resultados
Se compararon dos modelos. El **Random Forest Regressor** fue el ganador indiscutible, superando ampliamente a la Regresión Lineal.

* **Random Forest (R²): 0.878** (Explica el 87.8% de la varianza)
* **Random Forest (RMSE): $4,356.50** (El error promedio de predicción)

El gráfico de valores reales vs. predichos muestra un excelente ajuste del modelo:


### 4. Conclusión del Modelo
Finalmente, analicé la importancia de las variables (`feature_importances_`) para entender *en qué* se fijó el modelo:



El análisis confirma que **`fumador` (43.6%)**, **`edad` (38.0%)** y **`imc` (10.5%)** son los tres factores decisivos, sumando más del 92% de la importancia predictiva.
