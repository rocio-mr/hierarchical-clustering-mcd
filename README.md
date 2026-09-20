# Activity 8 - Hierarchical Clustering and Image Segmentation by Clustering

# 📚 PART 1: Hierarchical Clustering - 20 Newsgroups

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-blue?logo=python" alt="Python">
  <img src="https://img.shields.io/badge/Scikit--learn-Dataset-orange?logo=scikit-learn" alt="Scikit-learn">
  <img src="https://img.shields.io/badge/Clustering-Hierarchical-purple" alt="Clustering">
  <img src="https://img.shields.io/badge/Status-In%20Progress-yellow" alt="Status">
</p>

## 📌 Descripción

Esta primera parte del proyecto utiliza el dataset **20 Newsgroups**, una colección de documentos de texto pertenecientes a diferentes grupos temáticos.

El objetivo inicial es realizar una **exploración y caracterización del dataset**, identificando su estructura, cantidad de documentos, categorías y distribución de datos.

Posteriormente, estos datos serán utilizados para aplicar técnicas de **clustering jerárquico**, buscando identificar agrupaciones de documentos a partir de sus características textuales.

---

## 📊 Dataset: 20 Newsgroups

El dataset utilizado es **20 Newsgroups**, disponible directamente mediante `scikit-learn`. El conjunto contiene aproximadamente **18,846 documentos de texto**, distribuidos en **20 categorías temáticas**.

### 🔢 Características principales

| Característica       | Descripción                                 |
| -------------------- | ------------------------------------------- |
| 📄 Documentos        | 18,846                                      |
| 🏷️ Categorías        | 20                                          |
| 📝 Tipo de datos     | Texto                                       |
| 🎯 Variable objetivo | Categoría temática                          |
| 📚 Naturaleza        | Colección de mensajes de grupos de noticias |
| 🧠 Tipo de problema  | Agrupamiento de documentos                  |
| 🐍 Librería          | Scikit-learn                                |

---

## 🗂️ División del dataset

El dataset original se encuentra dividido en dos conjuntos:

| Conjunto    |   Cantidad |
| ----------- | ---------: |
| 🟦 Training |     11,314 |
| 🟩 Test     |      7,532 |
| **Total**   | **18,846** |

---

## 🏷️ Categorías

El dataset contiene **20 categorías temáticas**:

| Nº | Categoría                  |
| -: | -------------------------- |
|  0 | `alt.atheism`              |
|  1 | `comp.graphics`            |
|  2 | `comp.os.ms-windows.misc`  |
|  3 | `comp.sys.ibm.pc.hardware` |
|  4 | `comp.sys.mac.hardware`    |
|  5 | `comp.windows.x`           |
|  6 | `misc.forsale`             |
|  7 | `rec.autos`                |
|  8 | `rec.motorcycles`          |
|  9 | `rec.sport.baseball`       |
| 10 | `rec.sport.hockey`         |
| 11 | `sci.crypt`                |
| 12 | `sci.electronics`          |
| 13 | `sci.med`                  |
| 14 | `sci.space`                |
| 15 | `soc.religion.christian`   |
| 16 | `talk.politics.guns`       |
| 17 | `talk.politics.mideast`    |
| 18 | `talk.politics.misc`       |
| 19 | `talk.religion.misc`       |

---

## 📐 Características del problema

A diferencia de datasets numéricos tradicionales, **20 Newsgroups está compuesto principalmente por datos textuales**.

Esto significa que los documentos no pueden utilizarse directamente en algoritmos de clustering que requieren una representación numérica.

Por ello, una etapa posterior de esta primera parte del proyecto consistirá en transformar los textos en una representación numérica adecuada.

El flujo general será:

```text
📄 Documentos
      │
      ▼
🧹 Preprocesamiento
      │
      ▼
🔢 Representación numérica con embeddings
      │
      ▼
📊 Reducción de dimensionalidad
      │
      ▼
🌳 Clustering jerárquico
```

---
# 📚 PART 2: Hierarchical Clustering - Mall Customers

## 📌 Descripción del proyecto

Este proyecto tiene como objetivo aplicar técnicas de aprendizaje no supervisado (clustering jerárquico) para identificar grupos de clientes con características y comportamientos similares a partir del dataset Mall Customers.

El análisis busca descubrir segmentos de clientes sin utilizar una variable objetivo previamente definida. Para ello, se aplican diferentes algoritmos de clustering y se comparan sus resultados mediante métricas de evaluación.

## 📂 Dataset

El dataset utilizado es Mall Customers, disponible en Kaggle.

Este conjunto de datos contiene información sobre clientes de un centro comercial y permite analizar diferentes características demográficas y de comportamiento de compra.

## 📋 Variables principales
Variable	Descripción	Tipo
CustomerID	Identificador único del cliente	Numérica
Gender	Género del cliente	Categórica
Age	Edad del cliente	Numérica
Annual Income (k$)	Ingreso anual en miles de dólares	Numérica
Spending Score (1-100)	Puntuación de gasto asignada al cliente	Numérica

---
# 📚 PART 3: Imagen Segmentation using Hierarchical Clustering - BSDS500 (Berkeley Segmentation Dataset and Benckmarks 500)

## 📌 Descripción del proyecto

En este proyecto se desarrolla un método de segmentación de imágenes mediante aprendizaje no supervisado, utilizando técnicas de clustering jerárquico sobre imágenes pertenecientes al dataset BSDS500.

El objetivo es agrupar los píxeles de cada imagen según características visuales similares, permitiendo separar diferentes regiones de la imagen sin utilizar etiquetas durante el proceso de clustering.

A diferencia de un problema de clasificación, donde el modelo aprende a asignar una clase previamente definida, en este proyecto el algoritmo busca descubrir automáticamente grupos de píxeles con características semejantes.

## 📂 Dataset: BSDS500

El Berkeley Segmentation Dataset and Benchmarks 500 (BSDS500) es un dataset utilizado principalmente para investigación en segmentación de imágenes y detección de contornos.

Está compuesto por 500 imágenes naturales, que presentan diferentes escenas, objetos, animales, personas, paisajes y otros elementos visuales.

📊 Distribución del dataset
Conjunto	Número de imágenes	Propósito
🟢 Train	200	Desarrollo de modelos
🟡 Validation	100	Validación y selección de parámetros
🔵 Test	200	Evaluación
📦 Total	500	Dataset completo

Una característica importante del BSDS500 es que las imágenes cuentan con segmentaciones realizadas manualmente por personas, que pueden utilizarse como referencia para evaluar algoritmos automáticos de segmentación.

Por lo tanto, el dataset permite comparar una segmentación generada automáticamente con diferentes interpretaciones humanas de las regiones presentes en una imagen.

## 🔄 Preparación de las imágenes

Para aplicar clustering, cada imagen se transforma desde su representación bidimensional a una matriz donde cada fila corresponde a un píxel.

Una imagen RGB puede representarse como:

Alto × Ancho × 3

y posteriormente transformarse en:

Número de píxeles × 3

De esta manera, cada píxel se convierte en una observación que puede ser agrupada mediante el algoritmo de clustering.

## 🎨 Representación RGB

Cada píxel está compuesto por tres valores:

[R, G, B]

donde:

🔴 R → Red
🟢 G → Green
🔵 B → Blue
## 👩‍💻 Autora

**Milesa Rocio Maquera Ramos**



---

