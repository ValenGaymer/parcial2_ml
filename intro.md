# Evaluación

La presente evaluación debe ser entregada usando solamente un link de página web de GitHub, creado mediante Jupyter Book. Cada figura, tabla y resultado debe ser interpretado. Los resultados y visualizaciones que no cuenten con su respectivo análisis serán evaluados con la nota más baja.

## Ejercicio 1: Análisis Exploratorio de Datos

### Análisis Exploratorio de Datos

Dado los siguientes conjuntos de datos: **Default Probability Prediction** y **Wind Speed**, realizar un análisis exploratorio de datos el cual incluya lo siguiente:

1. **Descripción de tipos de variables**, reducción de nombres extensos en columnas, calcular número de observaciones, media, desviación estándar, mínimo, máximo, cuartiles, realizar conteo de datos faltantes y su porcentaje, histograma o diagrama de barras para la variable respuesta e independientes según corresponda. Seleccionar un mínimo de 10 variables independientes para este análisis.

2. **Análisis de simetría**, datos atípicos y dispersión, etc., por medio de **boxplot()**.

3. **Análisis bivariado**: Trazado de **scatterplot()** y **regplot()** para un mínimo de 10 pares de variables explicativas. En cada figura agregar un análisis y descripción.

4. Según corresponda, realizar **imputación de datos faltantes** por medio de **Imputación Iterativa Múltiple**.

5. Realizar reducción de dimensionalidad por medio de **eliminación de columnas altamente correlacionadas** usando **Variance Inflation Factor (VIF)**. Para esto se recomienda usar la librería `variance_inflation_factor()`. Un **VIF ≥ 10** indica alta multicolinealidad entre la correspondiente variable independiente y las demás variables.

   - **Recomendación**: Eliminar una columna a la vez, aquella con el máximo **VIF ≥ 10**. Luego, para el nuevo DataFrame, calcular nuevamente VIF e identificar nuevas columnas con VIF ≥ 10, y así sucesivamente hasta obtener solo valores de VIF < 10.

6. Según corresponda, variables categóricas deben previamente codificarse usando, por ejemplo, **OneHotEncoder()**. Se pueden mantener las variables categóricas antes de la codificación previa al entrenamiento del modelo y reducir multicolinealidad usando la prueba **chi2_contingency()**.

   - Como Científico de Datos, queda a su juicio la decisión sobre qué variables independientes deberían ser eliminadas. Justifique en cada caso su respuesta.

   - Puede proponer una metodología alternativa de reducción de dimensionalidad que considere más pertinente. En cada caso, justifique su respuesta.

   - Puede evitar eliminar variables en el dataset **Wind Speed**, debido a la baja cantidad de características.

### Research

Escriba un informe de no más de dos páginas (seleccione algún formato de entrega: Látex, JBook, Word) con las siguientes secciones: resumen, descripción de metodología y librería Python. 

El ejercicio de investigación se enfocará en estudiar las siguientes técnicas para balanceo de clases y **hiperparametrización**:

- **ADASYN (Adaptive Synthetic Sampling)**
- **Bayesian optimization**


## Ejercicio 2. Modelos de Clasificación. 
Considere el conjunto de datos Default Probability Prediction. Implemente la versión de clasificación para cada uno de los modelos estudiados en clases, y prediga la variable respuesta, probabilidad para la variable target (default probability). Construir una tabla de error que contenga las métricas usuales de clasificación: precision, recall, f1-score, AUC. Además, agregue matrices de confusión (ver confusion_matrix) y curvas ROC (ver plot_roc). Inicialmente realice un balanceo de clases usando ADASYN (Adaptive Synthetic Sampling), luego compare los resultados predictivos con o sin balanceo ADASYN. Posteriormente, realice hiperparametrización usando BayesianOptimization, GridSearchCV, y Pipeline para evaluar cada modelo, compare los resultados en términos de tiempo de computo. Verifique que la validación cruzada seleccionada es la adecuada, y justifíquelo. Utilice la métrica M = 0.5 · (G + D), para seleccionar el mejor modelo de clasificación (maximizar M) (ver sección Default Probability Prediction). Los resultados deben estar registrados en una tabla de error (ver Tabla 1) que resuma cada score obtenido por modelo implementado.

## Ejercicio 3. Modelos de Regresión
Considere el conjunto de datos **Wind Speed**. Implemente la versión de regresión de cada uno de los modelos estudiados en clases, para predecir la **velocidad del viento horaria** (**VENTO, VELOCIDADE HORARIA (m/s)**) en el conjunto de datos suministrado.

1. Construir una tabla de error con las métricas usuales de regresión, **MAPE**, **RMSE**, **R²** (ver **Table 2**).

2. Además, agregue pruebas de independencia y normalidad para los residuos: **Ljung-Box p-value** y **Jarque-Bera p-value**.

3. Realice **particiones de entrenamiento, validación y prueba**, con base en lo descrito en la **Figura 2**. Estas particiones siguen la tendencia de la velocidad del viento.

4. Realice una figura donde represente la velocidad del viento y su predicción.

5. Utilice las métricas **MAPE**, **RMSE**, **R²** en la fase de validación para seleccionar el mejor modelo de regresión, e identifique cuál es la métrica más adecuada.

6. Use también en la selección de los mejores hiperparámetros del mejor modelo **BayesianOptimization**. El pliegue de validación en cada partición debe estar siempre ubicado en el porcentaje final de cada partición, debido a que el tiempo es fundamental en dichas predicciones. No tiene sentido predecir el pasado conocido con el futuro.

7. Entre los periodos diarios **T = 7, 14, 21, 28**, indique cuál corresponde a la mejor ventana de predicción para el entrenamiento.

8. Nótese que **TimeSeriesSplit** no aplica en este problema, y por lo tanto no debe usarla debido a que dichos pliegues no corresponden con los solicitados en este ejercicio.

9. Defina una función para construir los pliegues para este ejercicio.

