# 🌿 Proyecto – Segmentación de Hojas de Café

> **Procesamiento Digital de Voz e Imágenes en la era de la Inteligencia Artificial**  
> Dora María Ballesteros  
> Primera edición, 2026  
> ISBN: 978-1-957395-68-5

> 🔗 **[Consultar el libro en Editorial REDIPE](https://editorial.redipe.org/index.php/1/catalog/book/260)**

## 📌 Contexto

Imaginemos que queremos desarrollar una solución capaz de **capturar la foto de una hoja de café y determinar automáticamente su estado de salud**, considerando tres posibles categorías:

- **Hoja sana (*healthy*)**
- **Hoja afectada por ácaro rojo (*red spider mite*)**
- **Hoja afectada por roya (*rust*)**

Antes de realizar esta clasificación, es necesario identificar qué región de la foto corresponde realmente a la hoja. La imagen puede contener otros elementos en el fondo que no aportan información sobre su estado y que podrían interferir en un análisis posterior.

Por esta razón, el **primer paso consiste en segmentar la imagen**, separando la hoja —incluyendo sus manchas, lesiones e imperfecciones— del resto de la escena. El resultado esperado es una máscara que permita identificar los píxeles pertenecientes a la hoja y descartar aquellos correspondientes al fondo.

Este problema puede resolverse desde dos perspectivas. La primera utiliza **técnicas clásicas de Procesamiento Digital de Imágenes (PDI)**, en las cuales las reglas de segmentación son definidas explícitamente. La segunda utiliza **Inteligencia Artificial**, mediante una arquitectura **U-Net** que aprende a segmentar la hoja a partir de imágenes y máscaras de referencia (*Ground Truth*).

En este proyecto implementarás y compararás ambas estrategias utilizando imágenes del dataset **RoCoLe (*Robusta Coffee Leaf Images Dataset*)**.

---

# 📂 1. Dataset

Para el desarrollo del proyecto utiliza el dataset:

**RoCoLe – Robusta Coffee Leaf Images Dataset**

Disponible en Kaggle:

🔗 https://www.kaggle.com/datasets/nirmalsankalana/rocole-a-robusta-coffee-leaf-images-dataset

Trabaja únicamente con imágenes pertenecientes a tres categorías:

- `coffee__healthy`
- `coffee__red_spider_mite`
- `coffee__rust`

Aunque las imágenes pertenecen a diferentes categorías, **el objetivo de este proyecto no es realizar clasificación**. Las categorías se utilizarán para construir un conjunto variado de imágenes sobre el cual estudiar el problema de **segmentación de la hoja respecto al fondo**.

---

# 🌿 2. Selección de imágenes

Selecciona **50 imágenes** del dataset RoCoLe.

Realiza una selección aproximadamente balanceada entre las tres categorías, utilizando **16 o 17 imágenes de cada una**, hasta completar las 50 imágenes.

Además del balance entre categorías, selecciona imágenes con diferentes características visuales y evita construir un conjunto formado por imágenes demasiado similares.

Las 50 imágenes seleccionadas constituirán el **dataset de trabajo** y deberán mantenerse durante todo el desarrollo del proyecto.

---

# 🎯 3. Construcción del *Ground Truth*

Para evaluar una segmentación necesitamos conocer previamente cuál sería el resultado esperado.

Para **cada una de las 50 imágenes**, construye una máscara de referencia o ***Ground Truth*** que identifique la región correspondiente a la hoja.

La máscara debe conservar **toda la hoja**, incluyendo manchas, lesiones, cambios de color e imperfecciones, ya que estas características podrían contener información relevante para una futura clasificación de su estado de salud.

Para eliminar el fondo y generar las máscaras utiliza:

🔗 **iLoveIMG – Remove Background**  
https://www.iloveimg.com/remove-background

Al finalizar esta etapa debes tener **50 parejas imagen–máscara**:

$$
(I_i, GT_i), \qquad i = 1, \ldots, 50
$$

donde:

- $I_i$ corresponde a la imagen original.
- $GT_i$ corresponde a su máscara *Ground Truth*.

---

# ✂️ 4. Partición del Dataset

Antes de realizar el entrenamiento, separa las imágenes que serán utilizadas para evaluar los diferentes métodos.

Divide las 50 parejas imagen–máscara en:

$$
\begin{aligned}
40\ \text{parejas} &\rightarrow \text{Entrenamiento} \\
10\ \text{parejas} &\rightarrow \text{Prueba}
\end{aligned}
$$

El conjunto de prueba debe contener:

- **4 imágenes** `coffee__healthy`
- **3 imágenes** `coffee__red_spider_mite`
- **3 imágenes** `coffee__rust`

Reserva las **10 imágenes de prueba antes del entrenamiento**. Estas imágenes no podrán utilizarse para entrenar la U-Net.

Utiliza posteriormente estas mismas 10 imágenes para evaluar los métodos clásicos de PDI. De esta manera, todos los métodos serán comparados utilizando exactamente el mismo conjunto de prueba.

---

# 🧠 5. Segmentación mediante U-Net

Utiliza exclusivamente las **40 parejas imagen–máscara del conjunto de entrenamiento** para entrenar una arquitectura **U-Net** que realice automáticamente la segmentación de las hojas.

Utiliza las imágenes originales como entrada del modelo y sus correspondientes máscaras *Ground Truth* como salida esperada.

Una vez finalizado el entrenamiento, utiliza la U-Net para realizar la predicción sobre las **10 imágenes reservadas para prueba**.

Para cada imagen obtendrás:

$$
I_i \rightarrow \text{U-Net} \rightarrow \widehat{GT}_{i,\text{U-Net}}
$$

Almacena las 10 máscaras obtenidas para su posterior evaluación.

---

# 🖼️ 6. Segmentación mediante técnicas clásicas de PDI

Segmenta las **mismas 10 imágenes reservadas para prueba** utilizando los tres métodos clásicos estudiados en el caso de estudio.

## Método 1 – HSV

Realiza la segmentación mediante una **máscara por color en el espacio HSV**, seleccionando los rangos de H, S y V apropiados para identificar la hoja.

## Método 2 – HSV + Contornos

A partir de la máscara HSV:

1. Identifica los contornos externos.
2. Calcula el área de los contornos encontrados.
3. Selecciona el contorno de mayor área.
4. Construye la máscara correspondiente a la hoja.

## Método 3 – HSV + Morfología + Centroides

A partir de la máscara HSV:

1. Aplica operaciones morfológicas para mejorar la máscara.
2. Identifica los componentes resultantes.
3. Analiza características como área y posición.
4. Utiliza los centroides para seleccionar la región correspondiente a la hoja.

Al finalizar esta etapa, cada una de las 10 imágenes de prueba tendrá cuatro máscaras estimadas:

- HSV.
- HSV + Contornos.
- HSV + Morfología + Centroides.
- U-Net.

---

# 📐 7. Evaluación mediante Intersection over Union (IoU)

Compara cada máscara obtenida con su correspondiente máscara *Ground Truth* utilizando la métrica **Intersection over Union (IoU)**:

$$
IoU =
\frac{|GT \cap P|}
{|GT \cup P|}
$$

donde:

- $GT$ corresponde a la máscara *Ground Truth*.
- $P$ corresponde a la máscara predicha por el método evaluado.
- $GT \cap P$ representa la intersección entre ambas máscaras.
- $GT \cup P$ representa la unión entre ambas máscaras.

Un valor de **IoU cercano a 1** indica una alta coincidencia entre la segmentación obtenida y el *Ground Truth*, mientras que un valor cercano a **0** indica una baja coincidencia.

Calcula el **IoU individual de cada una de las 10 imágenes para cada método**.

Por tanto, obtendrás:

$$
10\ \text{imágenes} \times 4\ \text{métodos}
= 40\ \text{valores de IoU}
$$

Organiza los resultados en una tabla similar a la siguiente:

| Imagen | Categoría | HSV | HSV + Contornos | HSV + Morfología + Centroides | U-Net |
|---|---|---:|---:|---:|---:|
| Imagen 1 | Healthy | | | | |
| Imagen 2 | Healthy | | | | |
| ... | ... | | | | |
| Imagen 10 | Rust | | | | |

---

# 📊 8. Comparación de los métodos

Para cada método, calcula el **IoU promedio** obtenido sobre las 10 imágenes:

$$
IoU_{\text{prom}} =
\frac{1}{10}\sum_{i=1}^{10} IoU_i
$$

Calcula también la **desviación estándar** de los valores de IoU.

Resume los resultados en una tabla:

| Método | IoU promedio | Desviación estándar |
|---|---:|---:|
| HSV | | |
| HSV + Contornos | | |
| HSV + Morfología + Centroides | | |
| U-Net | | |

Utiliza el IoU promedio para analizar el **desempeño general** de cada estrategia y la desviación estándar para estudiar qué tan **consistente** es su comportamiento frente a diferentes imágenes.

---

# 🔎 9. Análisis de resultados

A partir de los resultados obtenidos, responde:

1. ¿Qué diferencias observas en el desempeño de los cuatro métodos, teniendo en cuenta el IoU promedio y su desviación estándar?

2. ¿En qué imágenes obtuviste los mejores y peores resultados? Analiza qué características de las imágenes pueden explicar estos comportamientos.

3. ¿Qué ventajas y limitaciones presentan los métodos clásicos de PDI y U-Net para la segmentación de las hojas de café? Considera aspectos como desempeño, estabilidad, ajuste de parámetros, necesidad de *Ground Truth* y costo computacional.

Finalmente, establece las principales **conclusiones del experimento**, teniendo en cuenta el desempeño promedio, la estabilidad y los tipos de errores observados en cada método.

---

# 📓 10. Entregables

Entrega los siguientes productos:

## A. Notebook

Un **Notebook desarrollado en Python** que documente de manera organizada y reproducible el desarrollo completo del proyecto.

El Notebook debe incluir el desarrollo de los métodos, las visualizaciones de las segmentaciones obtenidas, el cálculo de las métricas, la comparación de los resultados y el análisis final.

## B. Póster

Un **póster académico** que sintetice los principales elementos y resultados del proyecto.

Presenta de forma gráfica y concisa:

- Problema y objetivo del proyecto.
- Metodología desarrollada.
- Ejemplos representativos de las segmentaciones obtenidas.
- Comparación de los cuatro métodos mediante IoU.
- Principales conclusiones.

# 📋 Rúbrica de Evaluación

## 🎯 Resultado de Aprendizaje

**RA 2.2. Aplica y evalúa técnicas clásicas de procesamiento digital de imágenes y herramientas de Inteligencia Artificial para el mejoramiento, filtrado y/o reconocimiento de patrones, utilizando métricas objetivas de desempeño.**

**Caso de estudio:** Segmentación de hojas de café.

---

## Criterio de evaluación

*Aplica y evalúa técnicas clásicas de PDI e Inteligencia Artificial para resolver un problema de segmentación, utilizando métricas objetivas de desempeño.*

| Acción observable | Bajo (0) | Medio (250–349) | Alto (350–500) |
|---|---|---|---|
| **A1. Implementa técnicas clásicas de PDI para segmentar hojas de café mediante HSV, contornos y operaciones morfológicas con análisis de centroides.** | No implementa los métodos clásicos de PDI solicitados. | Implementa parcialmente los métodos clásicos de PDI, sin completar los tres métodos solicitados. | Implementa correctamente los tres métodos clásicos de PDI solicitados: HSV, HSV + contornos y HSV + morfología + centroides. |
| **A2. Implementa una arquitectura U-Net para la segmentación de hojas de café, utilizando imágenes y máscaras *Ground Truth* para su entrenamiento y evaluación.** | No implementa la arquitectura U-Net para la segmentación de las hojas de café. | Implementa parcialmente la arquitectura U-Net, sin completar adecuadamente el proceso de entrenamiento y predicción sobre las imágenes de prueba. | Implementa correctamente la arquitectura U-Net, utilizando las imágenes y máscaras *Ground Truth* de entrenamiento y generando las máscaras de las imágenes reservadas para prueba. |
| **A3. Evalúa y compara las soluciones de segmentación mediante IoU, analizando el desempeño, la variabilidad y los errores observados en los métodos implementados.** | No evalúa ni compara las soluciones de segmentación mediante IoU. | Evalúa parcialmente las soluciones de segmentación, sin completar el cálculo del IoU, la comparación de los métodos o el análisis de los resultados. | Evalúa y compara correctamente las cuatro soluciones de segmentación, utilizando el IoU individual, el IoU promedio y la desviación estándar, y analiza los resultados obtenidos. |

> *La nota total es el promedio de la nota obtenida en cada acción observable*
