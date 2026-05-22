# Clasificación de personajes de Los Simpsons con CNN

Este proyecto implementa una Red Neuronal Convolucional, o CNN, para clasificar imágenes de personajes de la serie *Los Simpsons*.

El objetivo principal fue construir, comparar y evaluar distintos modelos convolucionales, seleccionando una arquitectura final capaz de obtener buen rendimiento y generalizar correctamente frente a imágenes no vistas.

---

## Objetivo del proyecto

Implementar un modelo de Deep Learning utilizando TensorFlow/Keras para clasificar imágenes de personajes de *Los Simpsons*, evaluando distintas arquitecturas, funciones de activación, optimizadores y técnicas para reducir el sobreajuste.

---

## Dataset

El dataset utilizado contiene imágenes de personajes de *Los Simpsons*, organizadas por clases. Cada clase representa un personaje distinto.

El conjunto de datos fue trabajado mediante:

- Carga de imágenes desde carpetas.
- Redimensionamiento de imágenes a 64x64 píxeles.
- Normalización de valores de píxeles entre 0 y 1.
- Separación en entrenamiento, validación y prueba.

> Nota: El dataset no se incluye directamente en este repositorio debido a su tamaño. Para ejecutar el notebook, las carpetas del dataset deben estar disponibles en el entorno de trabajo.

---

## Flujo del proyecto

El desarrollo se realizó en las siguientes etapas:

1. Carga de librerías y dataset.
2. Exploración inicial de las imágenes.
3. Preprocesamiento y normalización.
4. Comparación de configuraciones para construir el mejor modelo base.
5. Análisis de sobreajuste del modelo base.
6. Aplicación de técnicas de regularización.
7. Selección del modelo final.
8. Evaluación con métricas finales.
9. Matriz de confusión.
10. Visualización de predicciones correctas e incorrectas.

---

## Experimentación realizada

Para construir el mejor modelo base se probaron distintas configuraciones:

- Profundidad de la arquitectura.
- Funciones de activación: ReLU, tanh y ELU.
- Optimizadores: Adam, RMSprop y SGD Momentum.
- Función de pérdida para clasificación multiclase.

A partir de los experimentos, se seleccionó una arquitectura profunda con padding, activación ReLU, optimizador Adam y función de pérdida `sparse_categorical_crossentropy`.

---

## Técnicas aplicadas para reducir sobreajuste

Luego de detectar sobreajuste en el modelo base, se aplicaron técnicas como:

- Dropout.
- Batch Normalization.
- Data Augmentation.

El modelo final seleccionado fue una CNN profunda personalizada de estilo VGG-like, con padding, Dropout y Data Augmentation.

---

## Arquitectura del modelo final

El modelo final corresponde a una CNN profunda personalizada de estilo VGG-like.

Se considera VGG-like porque utiliza:

- Bloques secuenciales de convoluciones 3x3.
- Aumento progresivo de filtros.
- Capas MaxPooling2D para reducir dimensionalidad.
- Capas densas para la clasificación final.
- Activación Softmax en la capa de salida.

No corresponde directamente a ResNet, ya que no utiliza conexiones residuales, ni a Inception, ya que no utiliza ramas paralelas de convolución.

---

## Hiperparámetros principales

| Parámetro | Valor |
|---|---|
| Tamaño de imagen | 64x64 |
| Canales | 3 |
| Función de activación | ReLU |
| Optimizador | Adam |
| Learning rate | 0.001 |
| Función de pérdida | sparse_categorical_crossentropy |
| Batch size | 64 |
| Épocas | 50 |
| Regularización | Dropout 0.5 |
| Aumento de datos | RandomFlip, RandomRotation, RandomZoom, RandomTranslation |

---

## Resultados finales

El modelo final obtuvo un rendimiento alto en el conjunto de prueba:

| Métrica | Resultado |
|---|---:|
| Accuracy | 97.53% |
| Precision Macro | 97.63% |
| Recall Macro | 97.53% |
| F1-score Macro | 97.54% |

El modelo clasificó correctamente 868 imágenes de un total de 890.

---

## Análisis de resultados

La matriz de confusión mostró que la mayoría de las predicciones correctas se concentran en la diagonal principal, lo que indica un buen desempeño por clase.

Los errores fueron bajos y aislados, principalmente entre personajes con similitudes visuales, fondos complejos o posturas parecidas.

El uso de Data Augmentation ayudó a mejorar la generalización del modelo, reduciendo la diferencia entre entrenamiento y validación.

---

## Tecnologías utilizadas

- Python
- Google Colab
- TensorFlow / Keras
- OpenCV
- NumPy
- Pandas
- Matplotlib
- Scikit-learn

---

## Conclusión

Este proyecto demuestra el uso de Redes Neuronales Convolucionales para resolver un problema de clasificación de imágenes multiclase.

El proceso no se limitó a entrenar un modelo, sino que incluyó comparación de arquitecturas, selección de hiperparámetros, diagnóstico de sobreajuste, aplicación de técnicas de regularización y evaluación final mediante métricas y visualizaciones.

El resultado final fue una CNN profunda personalizada con buen rendimiento y capacidad de generalización sobre imágenes no vistas.
