# 🧠 Quiz — Solución destacada

Después de revisar la solución destacada del proyecto **Reducción de una Interferencia Tonal en una Señal de Voz**, responde las siguientes preguntas.

El propósito de este quiz es analizar las decisiones tomadas durante el desarrollo del proyecto y comprender la lógica experimental utilizada para seleccionar la mejor solución.

---

### 1. Análisis inicial

El grupo analizó la señal en el **dominio del tiempo**, mediante la **FFT** y mediante el **espectrograma** antes de diseñar los filtros.

¿Cuál es la principal ventaja de utilizar las tres representaciones?

- [ ] a) Permiten calcular tres valores diferentes de la frecuencia de interferencia.
- [ ] b) Aportan evidencias complementarias sobre la naturaleza, frecuencia y permanencia temporal de la interferencia.
- [ ] c) Permiten determinar directamente cuál filtro tendrá menor valor de R.
- [ ] d) Son necesarias para poder aplicar un filtro FIR.

---

### 2. Integración de Inteligencia Artificial

Mediante el análisis manual se estimó la interferencia en **389 Hz**, mientras que DBSCAN obtuvo una frecuencia de **387,60 Hz**.

¿Qué hicieron los autores con este nuevo resultado?

- [ ] a) Sustituyeron el filtrado digital por DBSCAN.
- [ ] b) Lo utilizaron únicamente para verificar la estimación manual.
- [ ] c) Rediseñaron los filtros utilizando la frecuencia obtenida mediante DBSCAN.
- [ ] d) Modificaron la señal original para que coincidiera con 387,60 Hz.

---

### 3. Diseño experimental

Después de incorporar el resultado obtenido mediante DBSCAN, se evaluaron cuatro alternativas:

- FIR Blackman manual.
- IIR Butterworth manual.
- FIR Blackman con DBSCAN.
- IIR Butterworth con DBSCAN.

¿Qué ventaja experimental ofrece esta comparación?

- [ ] a) Permite analizar simultáneamente el efecto del tipo de filtro y del uso de la frecuencia estimada mediante DBSCAN.
- [ ] b) Garantiza que alguna alternativa basada en IA sea la mejor.
- [ ] c) Permite eliminar la necesidad de evaluar la señal original.
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
- [ ] c) Presenta una mejor relación entre la energía residual de la interferencia y la energía de señal conservada.
- [ ] d) Produce una señal de mayor amplitud.

---

### 5. Toma de decisiones

Para el filtro FIR Blackman se obtuvieron aproximadamente los siguientes resultados:

| Alternativa | R |
|---|---:|
| FIR Blackman manual | 0,06561 |
| FIR Blackman con DBSCAN | **0,06412** |

Un estudiante afirma:

> *“Como la diferencia entre los dos valores es pequeña, no podemos concluir que utilizar DBSCAN haya aportado al resultado.”*

**¿Estás de acuerdo con esta afirmación? Justifica brevemente tu respuesta a partir de los resultados del experimento.**

<br>

**Respuesta:**

____________________________________________________________________

____________________________________________________________________

____________________________________________________________________

---

## 💡 Para reflexionar

Más allá de identificar cuál alternativa obtuvo el mejor resultado, piensa en la metodología utilizada durante el proyecto:

**¿Qué elementos permitieron que la selección de la solución final estuviera sustentada en evidencia experimental y no solamente en una apreciación subjetiva?**
