
# Proyecto Final: Clasificación de Sentimientos en Reseñas de Concesionarias

Este proyecto tiene como objetivo entrenar y evaluar modelos de aprendizaje automático para la clasificación de sentimientos a partir de reseñas de concesionarias de autos en Argentina. El dataset utilizado fue generado de forma sintética con fines educativos y simula reseñas reales escritas en español.

---

## 1. Descripción del Dataset

- **Nombre**: `reseñas_concesionarias_argentina.csv`
- **Registros**: 45.000 reseñas
- **Características**: Texto libre (reseña), calificación (1 a 5 estrellas), y sentimiento (etiquetado binario: positivo/negativo)
- **Observación**: Dataset completamente sintético, creado para propósitos didácticos. No representa opiniones reales.

---

## 2. Preprocesamiento de Texto

Se aplican las siguientes etapas:

- Limpieza del texto (minúsculas, sin signos, sin números, sin espacios innecesarios)
- Tokenización con `nltk`
- Lematización y remoción de stopwords con `spaCy`
- Filtrado por frecuencia (palabras con muy baja o muy alta frecuencia eliminadas)
- Reconstrucción del texto final (`review_final`) y cálculo de su longitud

---

## 3. Análisis Exploratorio

- Distribución de calificaciones relativamente uniforme
- Predominio de sentimiento negativo en el dataset (60%)
- Las reseñas procesadas tienen entre 1 y 4 palabras
- Nubes de palabras revelan patrones claros por grupo (positivas, neutras y negativas)

---

## 4. División de Datos

- Se realiza una división estratificada 80/20 (entrenamiento/prueba)
- Se verifica que la distribución de clases se mantenga tras la partición
  - Entrenamiento: 60.3% negativo / 39.7% positivo
  - Prueba: 59.3% negativo / 40.7% positivo

---

## 5. Modelado

### Modelo 1: CountVectorizer + Regresión Logística
- Vectorización: BoW con n-gramas de 1 a 4
- Accuracy: **0.8987**
- Buen desempeño general, especialmente en clases negativas
- Recall perfecto para negativos, menor para positivos

### Modelo 2: TF-IDF + Regresión Logística
- Vectorización: TF-IDF con n-gramas de 1 a 4
- Accuracy: **0.8987** (idéntico al modelo 1)
- Métricas muy similares. No se observan mejoras significativas

---

## 6. Evaluación Cualitativa

Se prueban frases nuevas con ambos modelos:

- El modelo responde correctamente ante ejemplos con polaridad clara
- Ambos modelos tienden a clasificar como negativas las frases con matices ambiguos o juicios mixtos
- TF-IDF muestra buen desempeño pero no supera al modelo basado en BoW

---

## 7. Conclusiones

- Ambos modelos presentan un rendimiento sólido con una accuracy cercana al 90%
- Se confirma que incluso con reseñas sintéticas y breves, es posible entrenar clasificadores eficaces
- El modelo basado en BoW resulta competitivo frente a TF-IDF, probablemente por la simplicidad del corpus
- Se recomienda mejorar el balance de clases y enriquecer los textos para proyectos futuros

---
 
**Formato**: Notebook en Python (.ipynb), compatible con Google Colab y Jupyter
