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
### 🔬 Metodología aplicada


Para facilitar el procesamiento y mantener una representación equilibrada de las categorías, se seleccionó una muestra estratificada de **200 documentos**, tomando 10 documentos de cada una de las 20 categorías.

Los documentos fueron preprocesados y posteriormente transformados en vectores mediante el modelo **`all-MiniLM-L6-v2`**, obteniendo embeddings de 384 dimensiones.

Posteriormente, se aplicó **PCA conservando el 90% de la varianza**, con el objetivo de reducir la dimensionalidad antes de calcular las distancias.

Finalmente, se aplicó clustering jerárquico utilizando tres métodos de enlace:

- 🔗 **Single Linkage**
- 🔗 **Complete Linkage**
- 🔗 **Average Linkage**

La distancia utilizada fue la **distancia coseno**, adecuada para comparar representaciones vectoriales de texto.


## 🔎 Hallazgos

Los resultados alcanzados al probar con cada método de enlace fueron los siguientes: En cuanto al comportamiento de **Single Linkage** estuvo condicionado por el efecto de chaining, lo cual indica que este método provoca que documentos que son relativamente diferentes terminen conectados a tráves de una secuencia de documentos intermedios. Mientras que el **Complete Linkage** produjo agrupamientos que fueron más compactos, esto se debe a que considera las distancias entre los elementos más alejados de cada grupo. Por último, **Average Linkage** presentó un comportamiento intermedio al considerar la distancia promedio entre los elementos que conforman los grupos. Así se concluye que el método que presentó el mejor desempeño fue de Average ya que obtuvo un ARI de 0.2957 y un V-measure de 0.6179. 
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

## 🔬 Metodología aplicada

Para realizar la segmentación se utilizaron las variables numéricas:

- **Age**
- **Annual Income (k$)**
- **Spending Score (1-100)**

La variable `CustomerID` no fue utilizada debido a que únicamente funciona como identificador y no aporta información relevante para la segmentación.

Tampoco se utilizó `Gender` en el clustering, ya que el objetivo fue realizar la segmentación a partir de las características numéricas relacionadas con la edad, los ingresos y el comportamiento de gasto.

Antes de aplicar el clustering, las variables fueron estandarizadas mediante `StandardScaler` para evitar que una variable con una escala mayor domine el cálculo de las distancias.

Se utilizó **distancia euclidiana** y se compararon tres métodos de enlace:

- 🔗 **Single Linkage**
- 🔗 **Complete Linkage**
- 🔗 **Average Linkage**

Finalmente, se generaron **5 clusters** para analizar los diferentes segmentos de clientes.

---

## 🌳 Análisis de los dendrogramas

Los dendrogramas permitieron observar cómo los clientes se van agrupando progresivamente a diferentes niveles de distancia.

El corte utilizado permitió obtener cinco grupos, facilitando la interpretación de diferentes perfiles de clientes.

Los tres métodos de enlace produjeron estructuras diferentes debido a la forma en que calculan la distancia entre grupos.

---

## 👥 Perfil de los segmentos

Para interpretar los clusters se calculó el promedio de:

- Edad
- Ingreso anual
- Spending Score

Esto permitió identificar las principales características de cada segmento.

Por ejemplo, los grupos pueden diferenciarse entre clientes con:

- 💰 Ingresos altos y alto nivel de gasto.
- 💰 Ingresos altos y bajo nivel de gasto.
- 🛍️ Ingresos bajos y alto nivel de gasto.
- 🛍️ Ingresos bajos y bajo nivel de gasto.
- 👤 Perfiles intermedios según edad, ingresos y gasto.

> Los perfiles concretos dependen de los resultados obtenidos por cada método de enlace.

---

## 🔎 Hallazgos

El análisis demostró que la elección del método de enlace es fundamental ya que modifica la forma en la que se construyen los segmentos. En primer lugar el, **Single Linkage** puede generar agrupamientos entre clientes que se encuentren más cercanos entre si, mientras que el **Complete Linkage** tiende a generar grupos que son más compactos.
**Average Linkage** busca un equilibrio al considerar las distancias promedio entre los elementos que conforman los grupos.
Entonces, a partir de los perfiles obtenidos, se pudo observar que las variables relacionadas con el **ingreso anual y el nivel de gasto** permiten diferenciar claramente entre determinados grupos de clientes. 
El método que presentó el comportamiento más favorable en este segundo experimento fue el Average Linkage que presentó el mejor desempeño en el dataset Mall Customers. Obtuvo un ARI de 0.2957 y un V-Measure de 0.6179, superando a Complete y Single en ambas métricas.

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

## 🔬 Metodología aplicada

Para realizar el experimento se seleccionó una imagen del conjunto de entrenamiento de BSDS500.

Debido al elevado número de píxeles de las imágenes originales, la imagen fue redimensionada a **150 × 150 píxeles**, obteniendo un total de:

**150 × 150 = 22,500 píxeles**

Cada píxel fue representado mediante sus valores RGB:

```text
[R, G, B]
```

## 🔎 Hallazgos

Los resultados muestran que este tipo de clustering jerárquico puede usarse para realizar una segmentación básica de imágenes basándose solamente en la información que ofrece el color.
Los píxeles que poseían valores RGB similares tienden a pertenecer al mismo clúster, permitiendo separar regiones visualmente diferenciadas. En el experimento se empleó una imagen que figura en el código y se aplicó los tres métodos correspondientes: Simple Linkage, Complete Linkage, Average Linkage. En este experimento, los métodos que considero presentaron mejor desempeño fueron el Complete y Average ya que lograron segmentar mejor las regiones en la imágenes tal como se aprecia en la reconstrucción de la imagen al final del código. La imagen empleada fueron dos caballos y en el resultado se puedo apreciar la silueta de ambos de manera más completa usando el Complete y Average Linkage. Asimismo, no se logró realizar muchas pruebas pero podría ser a futuro probar más los hiper parámetros y de esa manera quizá puedan obtenerse mejores resultados. 
---

## 👩‍💻 Autora

**Milesa Rocio Maquera Ramos**



---

