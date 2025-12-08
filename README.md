#  Predicción de Metabolitos en Bioprocesos con Espectroscopía Raman

Este repositorio contiene un flujo de trabajo en **Jupyter Notebook** para el análisis y modelado de datos espectrales Raman. El objetivo principal es predecir la concentración de metabolitos críticos (**Glucosa**, **Acetato de Sodio** y **Sulfato de Magnesio**) en cultivos celulares, utilizando datos provenientes de múltiples espectrómetros.

El proyecto aborda el desafío de la variabilidad instrumental mediante la comparación de modelos lineales (**PLS**) y no lineales (**XGBoost**), optimizados para generalizar a través de diferentes dispositivos.

## Contenido del Repositorio

* **`borrar.ipynb`**: El cuaderno principal que contiene todo el pipeline: carga de datos, preprocesamiento, entrenamiento de modelos, validación y visualización. *(Nota: Se recomienda renombrar este archivo a algo más descriptivo como `analisis_espectral.ipynb`)*.
* **Archivos de datos (`.csv`)**: (Estos archivos deben estar en la ruta especificada en el notebook):
    * `anton_532.csv`, `anton_785.csv`
    * `kaiser.csv`
    * `metrohm.csv`
    * `mettler_toledo.csv`
    * `tec5.csv`, `timegate.csv`, `tornado.csv`

## Requisitos Previos

Para ejecutar este cuaderno, necesitas un entorno de Python 3 con las siguientes librerías instaladas:

```bash
pip install pandas numpy matplotlib scikit-learn xgboost scipy
