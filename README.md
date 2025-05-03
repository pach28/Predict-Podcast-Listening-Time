# Predict Podcast Listening Time | Kaggle Competition Analysis

[![Kaggle](https://kaggle.com/static/images/site-logo.svg)](https://www.kaggle.com/competitions/predict-podcast-listening-time)

Este repositorio contiene el análisis y los notebooks desarrollados para mi participación en la competencia "[Predict Podcast Listening Time](https://www.kaggle.com/competitions/predict-podcast-listening-time)" en Kaggle. El objetivo de la competencia fue predecir la duración de la escucha de podcasts por parte de los usuarios.

## Objetivo de la Competencia

El desafío principal consistió en construir un modelo de regresión capaz de predecir la cantidad de segundos que un usuario escuchará un episodio de podcast específico. Esto implicó el análisis de las interacciones entre usuarios, podcasts y episodios, el manejo de valores faltantes (NaNs) y la construcción de modelos predictivos precisos.

## Notebooks Incluidos

Este repositorio incluye los siguientes notebooks, que exploran diferentes estrategias para el tratamiento de datos y el modelado:

1.  **`NaN_Imputation_RF_y_Modelado_por_Combinacion PPLT.ipynb`**: https://colab.research.google.com/drive/1BS11xiWF_sbTMTZxo4o1n62QOZ_e6tNi?usp=sharing
    * **Análisis de Relaciones con la Variable Objetivo:** Se exploran las relaciones entre las diferentes características y la variable objetivo (listening time) para comprender mejor su influencia.
    * **Imputación de NaNs con Random Forest:** Dada la presencia de valores faltantes, se opta por utilizar modelos de Random Forest para imputar los NaNs, buscando una imputación más informada que la simple media o mediana.
    * **Análisis de Combinaciones de Episodio y Título:** Se identifica un gran número de combinaciones únicas de episodio y título de podcast (aproximadamente 4800). Se analiza el comportamiento de la variable objetivo para cada una de estas combinaciones.
    * **Modelado Específico por Combinación:** Dada la posible variabilidad en los patrones de escucha entre diferentes podcasts y episodios, se decide construir modelos predictivos específicos para cada combinación única de episodio y título.

2.  **`NaN_Test_Imputation_Promedio_y_Ensemble_por_Combinacion PPLT.ipynb`**: https://colab.research.google.com/drive/1O40jMHbXq3QxThI7w8QQN05Vr1iw6lV0?usp=sharing
    * **Descarte de NaNs en Train y Centrado en Test:** Se observa que la gran cantidad de datos en el conjunto de entrenamiento permite, en este caso, despreciar las filas con NaNs sin una pérdida significativa de información para el modelado. La atención se centra en el tratamiento de los NaNs en el conjunto de prueba.
    * **Ajuste de Outliers en Train y Test:** Se realiza un análisis y ajuste de los valores atípicos (outliers) en ambos conjuntos de datos (entrenamiento y prueba) para reducir su impacto negativo en el entrenamiento de los modelos.
    * **Imputación de NaNs en Test por Promedio de Combinación:** Los valores faltantes en el conjunto de prueba se imputan utilizando el promedio de la variable objetivo (listening time) para cada combinación única de título y episodio presente en el conjunto de entrenamiento.
    * **Comparación y Selección de Modelos por Combinación:** Se entrenan y comparan cuatro modelos de regresión diferentes para cada combinación única de título y episodio. Se guarda el modelo con mejor rendimiento para cada combinación.
    * **Aplicación del Mejor Modelo en Test:** Finalmente, se aplica el modelo previamente seleccionado como el mejor para cada combinación específica para realizar las predicciones en el conjunto de prueba. Esta estrategia busca optimizar las predicciones individualmente para cada patrón de escucha.

**Nota sobre la visualización en GitHub: Este notebook puede mostrar el error 'Invalid Notebook' debido al uso de elementos interactivos (widgets) durante el análisis en Colab. GitHub no renderiza estos elementos de forma nativa. El código y los resultados estáticos son visibles, pero la interactividad se experimenta mejor al ejecutar el notebook en un entorno Jupyter o Colab.
