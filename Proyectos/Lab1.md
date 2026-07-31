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

A partir del análisis realizado proponga una hipótesis sobre la ubicación de la interferencia.

---

## 🎛️ Etapa 2. Diseño de filtros digitales

Diseñe e implemente diferentes estrategias de filtrado utilizando técnicas clásicas de Procesamiento Digital de Señales.

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

Utilice la frecuencia estimada por el algoritmo para apoyar el diseño del filtro digital correspondiente. Aplique una máscara. 

Finalmente compare:

- frecuencia estimada manualmente,
- frecuencia estimada mediante IA.

---

## 📊 Etapa 4. Evaluación objetiva del desempeño

Con el fin de comparar objetivamente todas las soluciones implementadas, cada grupo deberá calcular los siguientes indicadores para **cada filtro desarrollado**:

- **E_voz:** Energía de la señal de voz.
- **E_residual:** Energía residual de la interferencia, calculada dentro de una ventana de **100 Hz** centrada en la frecuencia de la interferencia.
- **R:** Indicador de desempeño definido como:

$$
R=\frac{E_{\text{residual}}}{E_{\text{voz}}}
$$

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

| Criterio | Nivel Excelente ⭐ 4–5 | Nivel Bueno ✅ 3 | Nivel Básico 🟡 2 | Nivel Inicial 🔴 1 |
|:---|:---|:---|:---|:---|
| 🎛️ **Aplicación de filtros digitales (FIR e IIR)** | Diseña e implementa correctamente filtros FIR e IIR, justifica técnicamente los parámetros seleccionados y analiza las ventajas y limitaciones de cada alternativa. | Diseña e implementa correctamente filtros FIR e IIR, aunque la justificación técnica es parcial. | Implementa los filtros, pero presenta errores en el diseño o una justificación técnica limitada. | No implementa correctamente los filtros o la solución propuesta no funciona adecuadamente. |
| 🤖 **Aplicación de Inteligencia Artificial** | Implementa correctamente DBSCAN para localizar automáticamente la interferencia e integra los resultados en el diseño de la solución de filtrado. | Implementa correctamente DBSCAN, aunque la integración o el análisis de los resultados es parcial. | Implementa DBSCAN con dificultades en la localización de la interferencia o en la interpretación de los resultados. | No implementa correctamente la técnica de IA o los resultados obtenidos no son funcionales. |
| 📊 **Evaluación y selección de la mejor solución** | Calcula correctamente **E<sub>voz</sub>**, **E<sub>residual</sub>** y **R** para todas las técnicas implementadas; compara objetivamente los resultados e identifica y justifica rigurosamente la mejor solución utilizando criterios objetivos de desempeño. | Calcula correctamente los indicadores requeridos, compara todas las técnicas implementadas y selecciona adecuadamente la mejor solución, aunque la interpretación o la justificación son parciales. | Calcula parcialmente los indicadores o presenta errores en su interpretación, lo que limita la comparación objetiva entre las técnicas implementadas. | No calcula los indicadores requeridos o la selección de la solución no está sustentada mediante criterios objetivos de desempeño. |

---

# 🎯 Resultado de Aprendizaje evaluado

## **RA 2.1**

> **Aplica y evalúa técnicas clásicas de filtrado digital y herramientas de Inteligencia Artificial para la reducción de ruido y/o el reconocimiento de patrones en señales de audio, utilizando criterios objetivos de desempeño.**

Este proyecto busca integrar los conocimientos desarrollados en los Capítulos 2 y 3 del libro mediante un caso de estudio donde el estudiante no solo implementa diferentes soluciones, sino que las compara objetivamente y selecciona la alternativa con mejor desempeño.
