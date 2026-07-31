# 🎯 Proyecto Integrador
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

- Forma de onda.
- Espectro de magnitud.
- Espectrograma.

A partir del análisis realizado proponga una hipótesis sobre la ubicación de la interferencia.

---

## 🎛️ Etapa 2. Diseño de filtros digitales

Diseñe e implemente diferentes estrategias de filtrado utilizando técnicas clásicas de Procesamiento Digital de Señales.

Como mínimo deberán implementarse:

- Un filtro FIR.
- Un filtro IIR.

Para cada alternativa explique:

- criterios de diseño,
- parámetros seleccionados,
- ventajas,
- limitaciones observadas.

---

## 🤖 Etapa 3. Localización automática mediante IA

Implemente el algoritmo **DBSCAN** sobre el espectrograma con el fin de localizar automáticamente la interferencia tonal.

Utilice la frecuencia estimada por el algoritmo para apoyar el diseño del filtro digital correspondiente.

Finalmente compare:

- frecuencia estimada manualmente,
- frecuencia estimada mediante IA.

---

## 📊 Etapa 4. Comparación de soluciones

Todas las soluciones deberán evaluarse mediante el indicador

\[
R=\frac{E_{residual}}{E_{voz}}
\]

donde:

- **E_residual** corresponde a la energía residual calculada dentro de una ventana de **100 Hz** centrada en la frecuencia de la interferencia.

- **E_voz** corresponde a la energía de la señal de voz.

> 📌 **Interpretación**
>
> Valores menores de **R** indican una mejor eliminación de la interferencia.

La solución final deberá seleccionarse utilizando este indicador y no únicamente mediante inspección visual o auditiva.

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

| Criterio | Nivel 4 ⭐ Excelente | Nivel 3 ✅ Bueno | Nivel 2 🟡 Básico | Nivel 1 🔴 Inicial |
|:---|:---|:---|:---|:---|
| 🎛️ **Aplicación de filtros FIR e IIR** | Diseña correctamente ambos filtros, justifica técnicamente sus parámetros y analiza críticamente sus ventajas y limitaciones. | Implementa correctamente ambos filtros con una justificación adecuada. | Implementa ambos filtros, pero presenta deficiencias en el diseño o en la justificación. | La implementación es incompleta o presenta errores que afectan el funcionamiento. |
| 🤖 **Aplicación de Inteligencia Artificial** | Implementa correctamente DBSCAN, localiza automáticamente la interferencia e integra el resultado al diseño del filtro. | Implementa correctamente DBSCAN con una interpretación parcial de los resultados. | Implementa la técnica con dificultades en la localización o interpretación de la interferencia. | La implementación no permite localizar adecuadamente la interferencia. |
| 📊 **Evaluación y selección de la mejor solución** | Compara todas las alternativas utilizando el indicador **R**, interpreta los resultados y justifica rigurosamente la solución seleccionada. | Compara todas las alternativas y selecciona adecuadamente la mejor solución. | Presenta una comparación parcial o con escasa justificación técnica. | La selección de la solución no está sustentada mediante criterios objetivos. |

---

# 🎯 Resultado de Aprendizaje evaluado

## **RA 2.1**

> **Aplica y evalúa técnicas clásicas de filtrado digital y herramientas de Inteligencia Artificial para la reducción de ruido y/o el reconocimiento de patrones en señales de audio, utilizando criterios objetivos de desempeño.**

Este proyecto busca integrar los conocimientos desarrollados en los Capítulos 2 y 3 del libro mediante un caso de estudio donde el estudiante no solo implementa diferentes soluciones, sino que las compara objetivamente y selecciona la alternativa con mejor desempeño.
