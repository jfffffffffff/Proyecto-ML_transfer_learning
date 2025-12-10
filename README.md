# Predicción de Metabolitos en Bioprocesos con Espectroscopía Raman

Este repositorio contiene un flujo de trabajo en **Jupyter Notebook** para el análisis y modelado de datos espectrales Raman. El objetivo principal es predecir la concentración de metabolitos críticos (**Glucosa**, **Acetato de Sodio** y **Sulfato de Magnesio**) en cultivos celulares, utilizando datos provenientes de múltiples espectrómetros.

El proyecto aborda el desafío de la variabilidad instrumental mediante la comparación de modelos lineales (**PLS**) y no lineales (**XGBoost**), optimizados para generalizar a través de diferentes dispositivos.

## Contenido del Repositorio

* **`Proyecto_Ml_transfer_script.ipynb`**: El cuaderno principal que contiene todo el pipeline: carga de datos, preprocesamiento, entrenamiento de modelos, validación y visualización.
* **Archivos de datos (`.csv`)**: (Estos archivos deben estar en la ruta especificada en el notebook):
    * `anton_532.csv`, `anton_785.csv`
    * `kaiser.csv`
    * `metrohm.csv`
    * `mettler_toledo.csv`
    * `tec5.csv`, `timegate.csv`, `tornado.csv`

## Diagrama de bloques: assets/Diagrama de bloques.png 
```mermaid
graph LR
    %% Nodos y Estilos
    A[<b>INPUT</b><br/>Espectros Raman<br/>8 Disp + Transfer]
    B[<b>PRE-PROCESAMIENTO</b><br/>1. Intersección<br/>2. Interpolación<br/>3. Max-Norm]
    C[<b>VALIDACIÓN</b><br/>Predefined Split]
    D[<b>PLS Reg</b><br/>Grid: n_comp]
    E[<b>XGBoost</b><br/>Grid: params]
    F[<b>ENSAMBLE</b><br/>Blending 50/50]
    G[<b>POST-PROC</b><br/>Clips < 0<br/>Outliers]
    H((<b>OUTPUT FINAL</b><br/>Glucosa<br/>Acetato Na<br/>Sulfato Mg))

    %% Conexiones
    A --> B
    B --> C
    C --> D
    C --> E
    D --> F
    E --> F
    F --> G
    G --> H

    %% Estilos opcionales para parecerse a tu imagen (Azul y blanco)
    classDef blue fill:#1f55a8,stroke:#1f55a8,color:white;
    classDef white fill:white,stroke:#1f55a8,color:#1f55a8,stroke-width:2px;
    
    class B,F blue;
    class A,C,D,E,G,H white;
## Requisitos Previos

Para ejecutar este cuaderno, necesitas un entorno de Python 3 con las siguientes librerías instaladas:


```bash
pip install pandas numpy matplotlib scikit-learn xgboost scipy 
```


El enlace de kaggle para obtener los datos usados es: https://www.kaggle.com/competitions/dig-4-bio-raman-transfer-learning-challenge/data

## Metodología

El flujo de trabajo se divide en las siguientes etapas:

### 1️. Ingesta de Datos
- Carga y consolidación de datos espectrales de **8 dispositivos diferentes**.
- Alineación de longitudes de onda y variables objetivo.

### 2️. Preprocesamiento
- Limpieza de datos (manejo de **saturación** y **valores nulos**).
- División de datos utilizando **PredefinedSplit** para asegurar una validación cruzada robusta y evitar *data leakage* entre entrenamiento y prueba.

### 3. Modelado

#### PLS (Partial Least Squares)
- Utilizado como línea base (*baseline*) por su alta interpretabilidad en quimiometría.

#### XGBoost (eXtreme Gradient Boosting)
- Implementado para capturar **no linealidades complejas** introducidas por la heterogeneidad instrumental.

### 4.vOptimización
- Ajuste de hiperparámetros mediante **GridSearchCV**:
  - `n_components` para PLS.
  - `learning_rate`, `max_depth`, `n_estimators` para XGBoost.

### 5. Evaluación
- Comparación basada en métricas de error (**MSE**, **RMSE**) y correlación (**R²**).

### Interpretación
- Visualización de los **coeficientes de regresión PLS** para identificar las bandas espectrales más influyentes.

---

## 6. Resultados Esperados

El cuaderno genera:

- Tablas comparativas de desempeño (**R²**, **RMSE**) para cada metabolito.
- Gráficos de dispersión (**Predicho vs. Real**) para evaluar la calidad del ajuste.
- Gráficos de **Coeficientes de Regresión PLS** (*multi-plot*), mostrando las longitudes de onda críticas para:
  - **Glucosa**
  - **Acetato de Sodio**
  - **Sulfato de Magnesio (MgSO₄)**

---

## Instrucciones de Uso

1. Clona este repositorio o descarga el archivo `.ipynb`.
2. Asegúrate de tener los archivos `.csv` de los datos espectrales en la misma carpeta o configura correctamente la ruta.
3. Abre el cuaderno:

```bash
jupyter notebook Proyecto_Ml_transfer_script.ipynb
```
##Autoría y Créditos

Este trabajo fue desarrollado como parte de una investigación en la asignatura de ML

Autores: Jhon Eduardo Meneses Viecco - Juan Márquez Chamorro
