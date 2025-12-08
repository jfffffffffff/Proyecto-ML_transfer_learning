# Proyecto-ML_transfer_learning

Predicción de Metabolitos con Espectroscopía Raman (PLS vs XGBoost)
Este notebook implementa un flujo de trabajo para predecir concentraciones de Glucosa, Acetato y Sulfato de Magnesio unificando datos de 8 espectrómetros diferentes.
📋 Requisitos
Ejecuta esto en tu terminal o celda de instalación:Bashpip install pandas numpy matplotlib scikit-learn xgboost scipy
🚀 Instrucciones RápidasArchivos: 
Necesitas el notebook borrar.ipynb y los 8 CSVs de datos (anton_532.csv, kaiser.csv, tornado.csv, etc.).
Rutas: Si no usas Google Colab, cambia las rutas de los archivos en la segunda celda (file_paths) a tu carpeta local.
Ejecución: Corre todas las celdas ("Run All"). El código se encarga de limpiar, entrenar y validar automáticamente.
📊 Resultados que obtendrásComparativa: 
Tabla de rendimiento ($R^2$ y Error) entre PLS y XGBoost.
Gráficas de Predicción: Dispersión de valores Reales vs. Predichos.
Importancia de Variables: Gráfico de coeficientes que muestra qué longitudes de onda usa el modelo para detectar cada sustancia.
