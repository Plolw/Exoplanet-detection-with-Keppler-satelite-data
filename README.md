# Detección de Exoplanetas con Machine Learning 🪐

> **Lee el informe completo con toda la formulación matemática y metodológica en:** [`project_report.pdf`](project_report.pdf)

## Objetivo del Proyecto
Este proyecto desarrolla y evalúa modelos de aprendizaje automático (Machine Learning) para clasificar señales captadas por el telescopio espacial Kepler de la NASA. El objetivo principal es determinar, basándose exclusivamente en los parámetros observados, si un cuerpo espacial detectado corresponde a un exoplaneta confirmado (`CONFIRMED`) o a un falso positivo (`FALSE POSITIVE`).

## Conjunto de Datos
* **Origen:** Los datos se obtuvieron del "Kepler Exoplanet Search Results" gestionado por el NASA Exoplanet Archive.
* **Filtrado:** Se descartaron todas las instancias etiquetadas como `CANDIDATE` (señales aún no confirmadas oficialmente) para entrenar el modelo exclusivamente con datos resueltos.
* **Tamaño:** Tras eliminar los valores faltantes y aplicar el filtrado, el conjunto de datos de trabajo consta de 7015 observaciones.

## Metodología
* **Preprocesamiento:** Se aplicaron transformaciones logarítmicas a variables con sesgos severos (como el radio planetario, el período orbital y la profundidad del tránsito) y se estandarizaron las escalas numéricas utilizando `StandardScaler` para evitar distorsiones en el entrenamiento.
* **Modelos Evaluados:** Se implementaron tres algoritmos distintos: K-Nearest Neighbors (K-NN), Random Forest y Máquinas de Soporte Vectorial (SVM).
* **Validación:** El rendimiento se midió con métricas como Exactitud, F1-Score, MCC y AUC, validadas a través de un riguroso *K-fold Cross Validation* de 10 particiones.

## Resultados Principales
* **Rendimiento General:** Todos los algoritmos analizados demostraron una capacidad predictiva excepcional, con una exactitud (accuracy) media superior al 98,5%.
* **Selección del Modelo Óptimo:** Tras evaluar la significación estadística entre los modelos (pruebas de Shapiro-Wilk y Wilcoxon), se determinó que no había diferencias estadísticamente significativas en exactitud. Se seleccionó el **Random Forest (con 100 estimadores y profundidad máxima de 30)** como el modelo definitivo por alcanzar el Área Bajo la Curva (AUC) más alta (0.9987) y por su mayor interpretabilidad física.
* **Importancia de las Variables:** Según el modelo Random Forest, las variables predictivas más determinantes son los indicadores de falsos positivos (especialmente `koi_fpflag_nt`) y el radio estimado del planeta (`koi_prad`). Por el contrario, las características de la estrella anfitriona mostraron una influencia menor en la decisión final de clasificación.

## Autores
Proyecto realizado en la Universitat Autònoma de Barcelona (UAB) por:
* Pol ORTIZ
* Rubén SORIA
* Pau VERDEJO