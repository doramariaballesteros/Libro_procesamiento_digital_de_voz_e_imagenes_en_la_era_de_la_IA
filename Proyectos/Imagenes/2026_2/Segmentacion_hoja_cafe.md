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

Por esta razón, el **primer paso consiste en segmentar la imagen**, separando la hoja -incluyendo sus manchas, lesiones e imperfecciones- del resto de la escena. El resultado esperado es una máscara que permita identificar los píxeles pertenecientes a la hoja y descartar aquellos correspondientes al fondo.

Este problema puede resolverse desde dos perspectivas. La primera utiliza **técnicas clásicas de Procesamiento Digital de Imágenes (PDI)**, en las cuales las reglas de segmentación son definidas explícitamente. La segunda utiliza **Inteligencia Artificial**, mediante una arquitectura **U-Net** que aprende a segmentar la hoja a partir de imágenes y máscaras de referencia (*Ground Truth*).

En este proyecto se implementarán y compararán ambas estrategias utilizando imágenes del dataset **RoCoLe (*Robusta Coffee Leaf Images Dataset*)**.

---

# 📂 1. Dataset

Para el desarrollo del proyecto se utilizará el dataset:

**RoCoLe – Robusta Coffee Leaf Images Dataset**

Disponible en Kaggle:

🔗 https://www.kaggle.com/datasets/nirmalsankalana/rocole-a-robusta-coffee-leaf-images-dataset

En este proyecto trabajaremos únicamente con imágenes pertenecientes a tres categorías:

- `coffee__healthy`
- `coffee__red_spider_mite`
- `coffee__rust`

Aunque las imágenes pertenecen a diferentes categorías, **el objetivo de este proyecto no es realizar clasificación**. Las categorías se utilizarán para construir un conjunto variado de imágenes sobre el cual estudiar el problema de **segmentación de la hoja respecto al fondo**.

---

# 🌿 2. Selección de imágenes

Cada grupo deberá seleccionar **50 imágenes** del dataset RoCoLe.

La selección deberá ser aproximadamente balanceada entre las tres categorías, utilizando **16 o 17 imágenes de cada una**, hasta completar las 50 imágenes.

Además del balance entre categorías, se deberán seleccionar imágenes con diferentes características visuales, evitando construir un conjunto formado por imágenes demasiado similares.

Las 50 imágenes seleccionadas constituirán el **dataset de trabajo** y deberán mantenerse durante todo el desarrollo del proyecto.

---

# 🎯 3. Construcción del *Ground Truth*

Para evaluar una segmentación necesitamos conocer previamente cuál sería el resultado esperado.

Para **cada una de las 50 imágenes** se deberá construir una máscara de referencia o ***Ground Truth*** que identifique la región correspondiente a la hoja.

La máscara deberá conservar **toda la hoja**, incluyendo manchas, lesiones, cambios de color e imperfecciones, ya que estas características podrían contener información relevante para una futura clasificación de su estado de salud.

Para eliminar el fondo y generar las máscaras puede utilizarse:

🔗 **iLoveIMG – Remove Background**  
https://www.iloveimg.com/remove-background

También podrá utilizarse otra herramienta equivalente.

Al finalizar esta etapa deberán existir **50 parejas imagen–máscara**:

$$
(I_i, GT_i), \qquad i = 1, \ldots, 50
$$

donde:

- $I_i$ corresponde a la imagen original.
- $GT_i$ corresponde a su máscara *Ground Truth*.

---

# ✂️ 4. Partición del Dataset

Antes de realizar el entrenamiento se deberán separar las imágenes que serán utilizadas para evaluar los diferentes métodos.

Las 50 parejas imagen–máscara se dividirán en:

$$
\begin{aligned}
40\ \text{parejas} &\rightarrow \text{Entrenamiento} \\
10\ \text{parejas} &\rightarrow \text{Prueba}
\end{aligned}
$$

El conjunto de prueba deberá contener:

- **4 imágenes** `coffee__healthy`
- **3 imágenes** `coffee__red_spider_mite`
- **3 imágenes** `coffee__rust`

Las **10 imágenes de prueba deberán reservarse antes del entrenamiento** y no podrán ser utilizadas para entrenar la U-Net.

Estas mismas 10 imágenes serán utilizadas posteriormente para evaluar los métodos clásicos de PDI, garantizando que todos los métodos sean comparados utilizando exactamente el mismo conjunto de prueba.

---

# 🧠 5. Segmentación mediante U-Net

Utilizando exclusivamente las **40 parejas imagen–máscara del conjunto de entrenamiento**, se deberá entrenar una arquitectura **U-Net** para realizar automáticamente la segmentación de las hojas.

La entrada del modelo estará constituida por las imágenes originales y la salida esperada por sus correspondientes máscaras *Ground Truth*.

Una vez finalizado el entrenamiento, la U-Net deberá utilizarse para realizar la predicción sobre las **10 imágenes reservadas para prueba**.

Para cada imagen se obtendrá:

$$
I_i \rightarrow \text{U-Net} \rightarrow \widehat{GT}_{i,\text{U-Net}}
$$

Las 10 máscaras obtenidas deberán almacenarse para su posterior evaluación.

---

# 🖼️ 6. Segmentación mediante técnicas clásicas de PDI

Las **mismas 10 imágenes reservadas para prueba** deberán segmentarse utilizando los tres métodos clásicos estudiados en el caso de estudio.

## Método 1 – HSV

Realizar la segmentación mediante una **máscara por color en el espacio HSV**, seleccionando los rangos de H, S y V apropiados para identificar la hoja.

## Método 2 – HSV + Contornos

A partir de la máscara HSV:

1. Identificar los contornos externos.
2. Calcular el área de los contornos encontrados.
3. Seleccionar el contorno de mayor área.
4. Construir la máscara correspondiente a la hoja.

## Método 3 – HSV + Morfología + Centroides

A partir de la máscara HSV:

1. Aplicar operaciones morfológicas para mejorar la máscara.
2. Identificar los componentes resultantes.
3. Analizar características como área y posición.
4. Utilizar los centroides para seleccionar la región correspondiente a la hoja.

Al finalizar esta etapa, cada una de las 10 imágenes de prueba tendrá cuatro máscaras estimadas:

- HSV.
- HSV + Contornos.
- HSV + Morfología + Centroides.
- U-Net.

---

# 📐 7. Evaluación mediante Intersection over Union (IoU)

Cada máscara obtenida deberá compararse con su correspondiente máscara *Ground Truth* utilizando la métrica **Intersection over Union (IoU)**:

$$
IoU =
\frac{|GT \cap P|}
{|GT \cup P|}
$$

donde:

- $GT$ corresponde a la máscara *Ground Truth*.
- $P$ corresponde a la máscara predicha por el método evaluado.
- $GT \cap P$ representa la intersección entre ambas máscaras.
- $GT \cup P$ representa su unión.

Un valor de **IoU cercano a 1** indica una alta coincidencia entre la segmentación obtenida y el *Ground Truth*, mientras que un valor cercano a **0** indica una baja coincidencia.

Se deberá calcular el **IoU individual de cada una de las 10 imágenes para cada método**.

Por tanto, se obtendrán:

$$
10\; \text{imágenes}
\times
4\; \text{métodos}
=
40\; \text{valores de IoU}
$$

Los resultados deberán organizarse en una tabla similar a la siguiente:

| Imagen | Categoría | HSV | HSV + Contornos | HSV + Morfología + Centroides | U-Net |
|---|---|---:|---:|---:|---:|
| Imagen 1 | Healthy | | | | |
| Imagen 2 | Healthy | | | | |
| ... | ... | | | | |
| Imagen 10 | Rust | | | | |

---

# 📊 8. Comparación de los métodos

Para cada método se deberá calcular el **IoU promedio** obtenido sobre las 10 imágenes:

$$
\overline{IoU}
=
\frac{1}{10}
\sum_{i=1}^{10}IoU_i
$$

También se deberá calcular la **desviación estándar** de los valores de IoU.

Los resultados deberán resumirse en una tabla:

| Método | IoU promedio | Desviación estándar |
|---|---:|---:|
| HSV | | |
| HSV + Contornos | | |
| HSV + Morfología + Centroides | | |
| U-Net | | |

El IoU promedio permitirá analizar el **desempeño general** de cada estrategia, mientras que la desviación estándar permitirá estudiar qué tan **consistente** es su comportamiento frente a diferentes imágenes.

---

# 🔎 9. Análisis de resultados

A partir de los resultados obtenidos, realizar un análisis comparativo de los cuatro métodos.

El análisis deberá considerar tanto los valores cuantitativos de IoU como la inspección visual de las máscaras obtenidas.

Discuta, entre otros aspectos:

- ¿Qué método obtuvo el mayor IoU promedio?
- ¿Qué método presentó la menor variabilidad entre imágenes?
- ¿En qué imágenes se obtuvieron los valores más altos y más bajos de IoU?
- ¿Qué características de las imágenes pueden explicar estos resultados?
- ¿Cómo afectan los cambios de tonalidad de la hoja a los métodos basados en HSV?
- ¿Los métodos clásicos logran conservar adecuadamente manchas, lesiones e imperfecciones de las hojas?
- ¿Qué diferencias se observan entre las reglas definidas mediante PDI y la segmentación aprendida por U-Net?
- ¿Qué errores de segmentación podrían afectar posteriormente un sistema encargado de clasificar el estado de salud de la hoja?

Finalmente, establezca las principales **conclusiones del experimento**, teniendo en cuenta tanto el desempeño promedio como la estabilidad y los tipos de errores observados en cada método.
