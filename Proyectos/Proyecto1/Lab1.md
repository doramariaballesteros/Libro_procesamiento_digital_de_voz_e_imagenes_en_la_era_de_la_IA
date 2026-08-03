# 🎯 Proyecto Sección I
# Eliminación Inteligente de una Interferencia Tonal en una Señal de Voz

> 📘 **Procesamiento Digital de Voz e Imágenes en la Era de la Inteligencia Artificial**
>
> **Capítulos relacionados**
>
> - 🔇 Capítulo 2. Eliminación de Ruido con Filtros Digitales
> - 🤖 Capítulo 3. Inteligencia Artificial para Localización de Interferencias y Filtrado Espectral

---

# 📖 Contexto

En aplicaciones reales de telecomunicaciones, sistemas biomédicos y procesamiento de audio, es frecuente encontrar señales de voz contaminadas por interferencias producidas por equipos electrónicos, motores, fuentes de alimentación o sistemas de comunicación cercanos.

A diferencia de los ejercicios tradicionales, donde todos los parámetros del problema son conocidos, en un escenario de ingeniería el primer reto consiste en **comprender la señal** antes de diseñar una solución.

En este proyecto asumirán el papel de un equipo de ingeniería encargado de desarrollar una metodología que permita identificar y reducir una interferencia tonal presente en una señal de voz utilizando herramientas clásicas de Procesamiento Digital de Señales e Inteligencia Artificial.

---

# 🎯 Problema a resolver

Cada grupo recibirá un archivo de audio contaminado con una interferencia tonal cuya frecuencia es **desconocida**.

El objetivo consiste en desarrollar una metodología que permita:

- 🔍 Analizar la señal.
- 📈 Localizar la interferencia.
- 🎛️ Diseñar diferentes filtros digitales (FIR e IIR).
- 🤖 Utilizar Inteligencia Artificial para apoyar la localización automática de la interferencia.
- 📊 Comparar objetivamente todas las soluciones (parámetros matemáticos de evaluación).
- 🏆 Seleccionar la alternativa con mejor desempeño.

> **Importante**
>
> La frecuencia de la interferencia **no será suministrada**. Cada grupo deberá estimarla utilizando las herramientas desarrolladas durante los Capítulos 2 y 3.

---

# 🧩 Etapas del proyecto

## 🔎 Etapa 1. Exploración de la señal

Realice un análisis exploratorio de la señal utilizando las herramientas vistas en clase.

Como mínimo deberán presentarse:

- Señal en el dominio del tiempo.
- Espectro de la señal en escala lineal.
- Espectrograma.
- Hipótesis inicial sobre la ubicación de la interferencia y justificación.

A partir del análisis realizado proponga una hipótesis sobre la ubicación de la interferencia.

---

## 🎛️ Etapa 2. Diseño de filtros digitales

Diseñe e implemente diferentes estrategias de filtrado utilizando técnicas clásicas de Procesamiento Digital de Señales. Justifique técnicamente la selección de los parámetros del filtro (frecuencia de corte o rechazo, ancho de banda, orden del filtro y demás parámetros relevantes).

Como mínimo deberán implementarse:

- Un filtro FIR.
- Un filtro IIR.

Para cada alternativa explique:

- tipo de filtro (pasa-bajos, pasa-altos, pasa-banda, rechaza-banda),
- parámetros seleccionados (frecuencia de corte, orden del filtro, ...),
- ventajas,
- limitaciones observadas.

---

## 🤖 Etapa 3. Localización automática mediante IA

Implemente el algoritmo **DBSCAN** sobre el espectrograma con el fin de localizar automáticamente la interferencia tonal.

Utilice la frecuencia estimada por el algoritmo para apoyar el diseño del filtro digital correspondiente. Posteriormente, utilice esa misma frecuencia para construir la máscara espectral empleada en la evaluación objetiva del desempeño.

Finalmente compare:

- frecuencia estimada manualmente,
- frecuencia estimada mediante IA.

---

## 📊 Etapa 4. Evaluación objetiva del desempeño

Con el fin de comparar objetivamente todas las soluciones implementadas, cada grupo deberá calcular los siguientes indicadores para **cada filtro desarrollado**:

- **E_voz:** Energía espectral conservada fuera de la ventana de **100 Hz** centrada en la frecuencia de la interferencia. Aunque en el código se conserva el nombre `Evoz`, este indicador no corresponde exclusivamente a la energía de la voz, sino a la energía de la señal ubicada fuera de la banda asociada con la interferencia.
- **E_residual:** Energía residual de la interferencia, calculada dentro de una ventana de **100 Hz** centrada en la frecuencia estimada automáticamente mediante **DBSCAN** durante la Etapa 3.
- **R:** Indicador de desempeño definido como:

$$
R=\frac{E_{\text{residual}}}{E_{\text{voz}}}
$$

📌 **Interpretación:** Entre menor sea el valor de **R**, menor será la energía residual de la interferencia con respecto a la energía espectral conservada fuera de la banda de interferencia y, por tanto, mejor será el desempeño de la técnica implementada.


> 💡 **Ejemplo**
>
> Suponga que, después de aplicar **DBSCAN**, se estima que la frecuencia de la interferencia se encuentra en **1800 Hz**.
>
> En este caso:
>
> - La **energía residual de la interferencia** se calculará sobre una ventana de **100 Hz** centrada en dicha frecuencia, es decir:
>
$$
1750 \leq f \leq 1850\ \text{Hz}
$$
>
> y se define como:
>
$$
E_{\text{residual}}
 =
 \sum_{t}
 \sum_{f=1750}^{1850}
 S(t,f)
$$
>
> - La **energía conservada de la señal** corresponderá a toda la energía espectral ubicada **fuera de esa ventana**, es decir:
>
$$
E_{\text{voz}}
=
\sum_{t}
\sum_{f\notin[1750,1850]}
S(t,f)
$$
>
> Finalmente, el indicador de desempeño se calcula como:
>
$$
R=
\frac{E_{\text{residual}}}
{E_{\text{voz}}}
$$
>
> Entre menor sea el valor de **R**, menor será la energía residual de la interferencia con respecto a la energía espectral conservada y, por tanto, mejor será el desempeño de la técnica implementada.

Una vez calculados estos indicadores, los estudiantes deberán:

1. Construir una tabla comparativa con los valores de **E_voz**, **E_residual** y **R** obtenidos para cada técnica implementada.
2. Comparar cuantitativamente todas las soluciones.
3. Seleccionar la alternativa con mejor desempeño.
4. Justificar técnicamente la decisión utilizando los resultados obtenidos.

> 📌 **Interpretación:** Entre menor sea el valor de **R**, menor será la energía residual de la interferencia con respecto a la energía de la voz y, por tanto, mejor será el desempeño de la técnica implementada.

---

# 📦 Entregables

Cada grupo deberá entregar:

- 📒 Notebook de Google Colab completamente funcional.
- 📄 Informe técnico en formato PDF.
- 🔊 Audio correspondiente a la mejor solución obtenida.
- 📊 Tabla comparativa de todas las alternativas implementadas.
- 🏆 Justificación técnica de la solución seleccionada.

---

# 📝 Rúbrica de evaluación

### 🎛️ Criterio 1. Aplicación de filtros digitales (500 puntos)

| Acción observable | Insuficiente (0–200) | En proceso (200–350) | Sobresaliente (350–500) |
|:---|:---|:---|:---|
| Diseña un filtro FIR. | No lo diseña o presenta errores que impiden su funcionamiento. | Diseña el filtro, pero con parámetros parcialmente correctos o insuficientemente justificados. | Diseña correctamente el filtro y justifica técnicamente los parámetros seleccionados. |
| Diseña un filtro IIR. | No lo diseña o presenta errores que impiden su funcionamiento. | Diseña el filtro, pero con parámetros parcialmente correctos o insuficientemente justificados. | Diseña correctamente el filtro y justifica técnicamente los parámetros seleccionados. |
| Analiza las ventajas y limitaciones de ambas soluciones. | No realiza el análisis o este es incorrecto. | Presenta un análisis parcial o superficial. | Presenta un análisis completo, correcto y sustentado técnicamente. |

### 🤖 Criterio 2. Aplicación de Inteligencia Artificial (500 puntos)

| Acción observable | Insuficiente (0–200) | En proceso (200–350) | Sobresaliente (350–500) |
|:---|:---|:---|:---|
| Implementa DBSCAN sobre el espectrograma. | No implementa correctamente el algoritmo. | Implementa el algoritmo, pero con dificultades en su configuración o ejecución. | Implementa correctamente DBSCAN sobre el espectrograma. |
| Localiza automáticamente la interferencia. | No identifica la interferencia. | Localiza parcialmente la interferencia o presenta errores en la estimación de la frecuencia. | Localiza correctamente la interferencia y estima adecuadamente su frecuencia. |
| Utiliza la frecuencia estimada para apoyar el diseño del filtro. | No utiliza la información obtenida por IA. | Utiliza parcialmente la información obtenida. | Integra correctamente la información obtenida mediante IA en el diseño del filtro. |

### 📊 Criterio 3. Evaluación y selección de la mejor solución (500 puntos)

| Acción observable | Insuficiente (0–200) | En proceso (200–350) | Sobresaliente (350–500) |
|:---|:---|:---|:---|
| Calcula **E<sub>voz</sub>**. | No calcula el indicador o el cálculo es incorrecto. | Calcula el indicador, pero presenta errores menores. | Calcula correctamente el indicador. |
| Calcula **E<sub>residual</sub>**. | No calcula el indicador o el cálculo es incorrecto. | Calcula el indicador, pero presenta errores menores. | Calcula correctamente el indicador. |
| Calcula **R**. | No calcula el indicador o el cálculo es incorrecto. | Calcula el indicador, pero presenta errores menores. | Calcula correctamente el indicador. |
| Compara objetivamente todas las soluciones implementadas. | No realiza la comparación o esta es incorrecta. | Realiza una comparación parcial entre las soluciones. | Compara objetivamente todas las soluciones utilizando los indicadores calculados. |
| Selecciona la mejor solución y justifica la decisión. | No justifica la selección o la justificación es incorrecta. | Justifica parcialmente la decisión tomada. | Justifica rigurosamente la selección utilizando criterios objetivos de desempeño. |

Nota final =  corresponde al promedio de las notas obtenidas en cada criterio de evaluación
---

# 🎯 Resultado de Aprendizaje evaluado

## **RA 2.1**

> **Aplica y evalúa técnicas clásicas de filtrado digital y herramientas de Inteligencia Artificial para la reducción de ruido y/o el reconocimiento de patrones en señales de audio, utilizando criterios objetivos de desempeño.**

Este proyecto busca integrar los conocimientos desarrollados en los Capítulos 2 y 3 del libro mediante un caso de estudio donde el estudiante no solo implementa diferentes soluciones, sino que las compara objetivamente y selecciona la alternativa con mejor desempeño.
