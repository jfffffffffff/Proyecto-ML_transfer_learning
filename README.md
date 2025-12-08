# Proyecto-ML_transfer_learning

Predicción de Metabolitos en Bioprocesos con Espectroscopía Raman
Este repositorio contiene un flujo de trabajo en Jupyter Notebook para el análisis y modelado de datos espectrales Raman. El objetivo principal es predecir la concentración de metabolitos críticos (Glucosa, Acetato de Sodio y Sulfato de Magnesio) en cultivos celulares, utilizando datos provenientes de múltiples espectrómetros.
El proyecto aborda el desafío de la variabilidad instrumental mediante la comparación de modelos lineales (PLS) y no lineales (XGBoost), optimizados para generalizar a través de diferentes dispositivos. 
Contenido del Repositorio
borrar.ipynb: El cuaderno principal que contiene todo el pipeline: carga de datos, preprocesamiento, entrenamiento de modelos, validación y visualización.
Archivos de datos (.csv): (Estos archivos deben estar en la ruta especificada en el notebook):
* anton_532.csv, anton_785.csv
* kaiser.csv
* metrohm.csv
* mettler_toledo.csv
* tec5.csv,
* timegate.csv, tornado.csv
* Requisitos Previos
* Para ejecutar este cuaderno, necesitas un entorno de Python 3 con las siguientes librerías instaladas:
* Bashpip install pandas numpy matplotlib scikit-learn xgboost scipy
Metodología:
El flujo de trabajo se divide en las siguientes etapas:Ingesta de Datos:
Carga y consolidación de datos espectrales de 8 dispositivos diferentes, alineando las longitudes de onda y las variables objetivo.
Preprocesamiento:Limpieza de datos (manejo de saturación y valores nulos).División de datos utilizando PredefinedSplit para asegurar una validación cruzada robusta sin fuga de datos entre entrenamiento y prueba.Modelado:PLS (Partial Least Squares): Utilizado como línea base (baseline) por su interpretabilidad en quimiometría.XGBoost (eXtreme Gradient Boosting): Implementado para capturar no linealidades complejas introducidas por la heterogeneidad de los instrumentos.Optimización: Ajuste de hiperparámetros (n_components para PLS; learning_rate, max_depth, n_estimators para XGBoost) mediante GridSearchCV.Evaluación: Comparación basada en métricas de error (MSE) y correlación ($R^2$).Interpretación: Visualización de los coeficientes de regresión PLS para identificar las bandas espectrales más influyentes. Resultados EsperadosEl cuaderno genera:Tablas comparativas del desempeño ($R^2$, RMSE) para cada metabolito.Gráficos de dispersión (Predicho vs. Real) para evaluar la calidad del ajuste.Un gráfico de Coeficientes de Regresión PLS (multi-plot) que muestra qué longitudes de onda son críticas para la predicción de cada variable (Glucosa, Acetato, MgSO4). Instrucciones de UsoClona este repositorio o descarga el archivo .ipynb.Asegúrate de tener los archivos .csv de los datos espectrales.Abre el cuaderno:Bashjupyter notebook borrar.ipynb
Importante: Verifica la celda de carga de datos. Si tus archivos no están en /content/ (ruta por defecto de Google Colab), actualiza la lista file_paths con la ubicación correcta en tu máquina local.Ejecuta todas las celdas secuencialmente. Autoría y CréditosEste trabajo fue desarrollado como parte de una investigación sobre la transferencia de modelos en bioprocesos.Autores: Jhon Eduardo Meneses - Juan Márquez Este proyecto utiliza datos del desafío Dig4Bio Raman Transfer Learning.
Datos usados para el proyecto:
https://www.kaggle.com/competitions/dig-4-bio-raman-transfer-learning-challenge/data
