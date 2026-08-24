# 🧠 Quiz — Solución destacada

Esta es la última etapa del proceso de aprendizaje de la Sección I.  Es un quiz de retroalimentación.  
Su propósito es generar reflexión sobre una de las soluciones presentadas en el curso, considerada como una solución destacada.

---

### Instrucciones Generales:

A partir de **Solución_destacada_2026_II** del proyecto *Reducción de una Interferencia Tonal en una Señal de Voz*, responde las siguientes preguntas.
**Se debe justificar la respuesta, mas allá de simplemente seleccionar una opción**.

⏱️ **Tiempo disponible: 60 minutos**

---

### 1. Análisis inicial

En el análisis presentado se incluyó **dominio del tiempo**, espectral con la **FFT** y tiempo-frecuencia mediante **espectrograma**, antes de diseñar los filtros.

¿Cuál es la principal ventaja de utilizar las tres representaciones?

- [ ] a) Permiten calcular tres valores diferentes de la frecuencia de interferencia.
- [ ] b) Aporta información complementaria en relación al inicio y duración del ruido, frecuencia y relación tiempo-frecuencia.
- [ ] c) Permiten determinar directamente cuál filtro tendrá menor valor de R.
- [ ] d) Son necesarias para poder aplicar un filtro FIR.

---

### 2. Integración de Inteligencia Artificial

A partir de un análisis manual se indentificó que el ruido tonal se ubicaba en **389 Hz**, mientras que con DBSCAN se obtuvo que estaba ubicado en la frecuencia de **387,60 Hz**.

¿Qué hicieron los autores con este nuevo resultado?

- [ ] a) Sustituyeron la etapa de filtrado con filtros FIR e IIR con el bloque DBSCAN.
- [ ] b) Utilizaron DBSCAN únicamente para verificar la ubicación obtenida de forma manual y calcular un error porcentual.
- [ ] c) Rediseñaron los filtros utilizando la frecuencia obtenida mediante DBSCAN.
- [ ] d) Modificaron la señal original para que coincidiera con 387,60 Hz.

---

### 3. Diseño experimental

En el artículo presentaron cuatro soluciones, así:

- FIR Blackman manual.
- IIR Butterworth manual.
- FIR Blackman con DBSCAN.
- IIR Butterworth con DBSCAN.

¿Qué ventaja se obtiene al diseñar el experimento de esta forma?

- [ ] a) Permite eliminar la necesidad de evaluar la señal original.
- [ ] b) Garantiza que alguna alternativa basada en IA sea la mejor.
- [ ] c) Permite analizar simultáneamente el efecto del tipo de filtro (FIR/IIR) y la frecuencia identificada del tono (manual/DBSCAN).
- [ ] d) Demuestra que DBSCAN siempre mejora cualquier filtro.

---

### 4. Criterio de comparación

El desempeño de las soluciones se evaluó mediante el indicador:

$$
R = \frac{E_{residual}}{E_{voz}}
$$

donde:

- $E_{residual}$ representa la energía asociada a la interferencia.
- $E_{voz}$ representa la energía de la señal conservada fuera de la ventana de evaluación.

Si una solución obtiene un valor de **R menor** que otra, ¿cuál es la interpretación más adecuada?

- [ ] a) Conservó necesariamente más energía total.
- [ ] b) Eliminó completamente la interferencia.
- [ ] c) Elimina de mejor manera el tono sin sacrificar significativamente la energía de la señal de voz.
- [ ] d) Produce una señal de mayor amplitud.

---

### 5. Toma de decisiones

Para el filtro FIR Blackman se obtuvieron aproximadamente los siguientes resultados:

| Alternativa | R |
|---|---:|
| FIR Blackman manual | 0,06561 |
| FIR Blackman con DBSCAN | **0,06412** |

Más allá de identificar cuál alternativa obtuvo el mejor resultado, piensa en la metodología utilizada durante el proyecto:

**¿Qué elementos permitieron que la selección de la solución final estuviera sustentada en evidencia experimental y no solamente en una apreciación subjetiva?**

---

## 📊 Rúbrica de evaluación — Quiz

**Resultado de Aprendizaje (RA 1.1):**  
Comprende las particularidades del filtrado digital mediante filtros FIR e IIR en términos de parámetros de diseño, respuesta al impulso, función de transferencia, polos y ceros, y respuesta en frecuencia.

> En este quiz se evalúan específicamente aspectos relacionados con **parámetros de diseño y respuesta en frecuencia**.

| Pregunta | Acción observable | Insuficiente (0) | En proceso (300) | Excelente (500) |
|---|---|---|---|---|
| **1. Análisis inicial** | Identifica la principal ventaja de utilizar diferentes representaciones de la señal como insumo para seleccionar los parámetros de diseño de los filtros. | Identifica incorrectamente la respuesta o no la contesta. | Identifica correctamente la respuesta, pero la justificación es incorrecta o incompleta. | Identifica correctamente la respuesta y la justificación es correcta y completa. |
| **2. Integración de Inteligencia Artificial** | Identifica el uso del resultado obtenido mediante DBSCAN en el proceso de diseño de los filtros. | Identifica incorrectamente la respuesta o no la contesta. | Identifica correctamente la respuesta, pero la justificación es incorrecta o incompleta. | Identifica correctamente la respuesta y la justificación es correcta y completa. |
| **3. Diseño experimental** | Identifica la ventaja de diseñar el experimento considerando las cuatro alternativas de filtrado. | Identifica incorrectamente la respuesta o no la contesta. | Identifica correctamente la respuesta, pero la justificación es incorrecta o incompleta. | Identifica correctamente la respuesta y la justificación es correcta y completa. |
| **4. Criterio de comparación** | Identifica el significado de un valor bajo de R en relación con el desempeño del filtro diseñado. | Identifica incorrectamente la respuesta o no la contesta. | Identifica correctamente la respuesta, pero la justificación es incorrecta o incompleta. | Identifica correctamente la respuesta y la justificación es correcta y completa. |
| **5. Toma de decisiones** | Identifica los elementos que sustentan la selección de la mejor solución a partir de evidencia experimental. | Identifica incorrectamente la respuesta o no la contesta. | Identifica correctamente la respuesta, pero la justificación es incorrecta o incompleta. | Identifica correctamente la respuesta y la justificación es correcta y completa. |


