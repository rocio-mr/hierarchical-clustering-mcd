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

Para la exploración inicial se puede utilizar el dataset completo mediante:

```python
dataset = fetch_20newsgroups(
    subset='all',
    remove=('headers', 'footers', 'quotes')
)
```

La opción `remove` permite excluir determinadas partes de los mensajes que pueden introducir información adicional no relacionada directamente con el contenido textual.

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

Las categorías abarcan diferentes áreas, principalmente:

* 💻 Computación y tecnología
* 🚗 Automóviles y motocicletas
* ⚾ Deportes
* 🔬 Ciencia
* 🛒 Compra y venta
* ⛪ Religión
* 🗣️ Temas sociales y políticos

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
🔢 Representación numérica 
      │
      ▼
📊 Reducción de dimensionalidad
      │
      ▼
🌳 Clustering jerárquico
```

---

## 👩‍💻 Autora

**Milesa Rocio Maquera Ramos**



---

