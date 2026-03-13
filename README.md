# 🩺 Predicción de Diabetes - Clasificación Binaria

## 📖 Descripción del Proyecto
Este repositorio contiene el desarrollo de la Práctica 1 para la asignatura *Sistemas Inteligentes para la Gestión en la Empresa* de la Universidad de Granada. El objetivo principal es implementar un flujo completo de Ciencia de Datos: desde el **pre-procesamiento y limpieza de datos** hasta la construcción y optimización de modelos de **Machine Learning para clasificación binaria**. 

El reto consiste en predecir si un paciente padece diabetes basándose en una serie de indicadores clínicos y de estilo de vida.

## 📊 Sobre los Datos
Se ha utilizado una versión modificada del «Diabetes Health Indicators Dataset» original de Kaggle.
* **Volumen de datos:** 60.796 observaciones (pacientes).
* **Estructura:** 1 variable objetivo (`Diabetes_binary`) y 21 características predictoras.
* **Naturaleza de los datos:** Combinación de variables binarias (respuestas de encuestas codificadas como 0/1) y numéricas continuas (como la Edad o el Índice de Masa Corporal. Los valores desconocidos o perdidos venían codificados con el valor centinela `-999`.

## ⚙️ Flujo de Trabajo (Pipeline)
El proyecto está estructurado de manera modular siguiendo un enfoque científico:

1. **Pre-procesamiento:**
   * Sustitución de valores anómalos (`-999`) e imputación de nulos utilizando la mediana poblacional para mantener la robustez estadística.
   * Normalización (Min-Max Scaler) de variables numéricas para unificar la escala computacional.
   * División estratificada en conjuntos de Entrenamiento, Validación y Test.

2. **Ingeniería de Características (Feature Selection):**
   * [cite_Se aplicó eliminación basada en la importancia de variables (usando un modelo Random Forest base).
   * Se logró reducir el ruido del dataset, pasando de 21 variables a las 11 más críticas (como *HighBP*, *BMI*, *GenHlth*), mejorando la eficiencia del modelo sin pérdida de precisión.

3. **Modelado y Ajuste Fino:**
   * Se evaluaron y compararon dos algoritmos avanzados: **Random Forest** y **HistGradientBoosting**.
   * Se utilizó Validación Cruzada Estratificada (*Stratified K-Fold*) para asegurar la estabilidad del entrenamiento.
   * Optimización hiperparamétrica final mediante `GridSearchCV`.

## 🏆 Resultados Destacados
El modelo definitivo (Gradient Boosting) alcanzó un **Accuracy del 74.47%** sobre el conjunto de Test (datos nunca antes vistos por el algoritmo). 

A través del análisis de resultados se extrajo una conclusión clave: la estabilización del rendimiento en torno al ~74.5% revela el **Error de Bayes** del conjunto de datos. Existe un solapamiento clínico natural (pacientes con presión alta y colesterol que aún no son diabéticos) que establece un techo predictivo matemático para las variables disponibles.

## 🛠️ Stack Tecnológico
* **Lenguaje:** Python 3 
* **Manejo de Datos:** `pandas`, `numpy`
* **Visualización:** `matplotlib`, `seaborn`
* **Machine Learning:** `scikit-learn`

## 🚀 Cómo reproducir este proyecto
El código ha sido diseñado para ser fácilmente reproducible. Se recomienda abrir el cuaderno en un entorno como **Google Colab** o ejecutar el script localmente tras instalar las dependencias básicas de Scikit-Learn y Pandas.
