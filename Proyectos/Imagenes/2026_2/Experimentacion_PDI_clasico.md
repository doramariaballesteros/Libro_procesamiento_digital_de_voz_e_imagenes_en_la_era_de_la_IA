# 🧪 Experimentación con los métodos de segmentación

Los tres métodos implementados contienen **parámetros y reglas definidas explícitamente** que pueden modificar el resultado de la segmentación. A partir de los códigos desarrollados, realiza pequeños experimentos modificando algunos de estos elementos y observa su efecto sobre las máscaras obtenidas.

---

## 🔹 Método 1 – Segmentación HSV

La máscara inicial depende de los límites definidos para los canales H, S y V:

```python
lim_inf = np.array([25, 35, 25])
lim_sup = np.array([95, 255, 255])
```

Experimenta modificando los rangos de **H (Hue)**, **S (Saturation)** y **V (Value)**.

Observa qué ocurre cuando los rangos son más amplios o más restrictivos y cómo estos cambios afectan la capacidad de conservar la hoja y eliminar elementos del fondo.

> **Analiza:** ¿Qué efecto tiene cada componente H, S y V sobre la máscara obtenida?

---

## 🔹 Método 2 – HSV + Contornos

En este método, después de generar la máscara HSV, se identifican las diferentes regiones mediante sus contornos y se selecciona aquella que presenta la **mayor área**:

```python
mayor = max(contornos, key=cv2.contourArea)
```

Experimenta modificando los **límites HSV** y observa cómo cambia el número y tamaño de los contornos encontrados.

Puedes visualizar todos los contornos antes de seleccionar el de mayor área y comparar sus áreas para comprender por qué una determinada región es seleccionada.

> **Analiza:** ¿La región de mayor área corresponde siempre a la hoja? Identifica situaciones en las que esta regla puede producir una segmentación incorrecta.

---

## 🔹 Método 3 – HSV + Morfología + Centroides

Este método incorpora operaciones morfológicas y diferentes características de las regiones para seleccionar aquella que tiene mayor probabilidad de corresponder a la hoja.

### Morfología

Experimenta con el tamaño del kernel:

```python
kernel = np.ones((5, 5), np.uint8)
```

Prueba diferentes tamaños, por ejemplo:

```python
kernel = np.ones((3, 3), np.uint8)
kernel = np.ones((5, 5), np.uint8)
kernel = np.ones((9, 9), np.uint8)
```

Modifica también el número de iteraciones de las operaciones de **apertura** y **cierre**.

Observa cómo estos parámetros afectan la eliminación de pequeñas regiones, el cierre de huecos y la forma de la máscara resultante.

### Selección de la región

La selección de la región utiliza un puntaje que combina diferentes características:

```python
puntaje = area * (1 + 3 * proporcion_central) * cercania * penalizacion
```

Experimenta incorporando progresivamente las diferentes características:

```python
# Solo área
puntaje = area

# Área + posición central
puntaje = area * (1 + 3 * proporcion_central)

# Área + posición central + cercanía
puntaje = area * (1 + 3 * proporcion_central) * cercania

# Regla completa
puntaje = area * (1 + 3 * proporcion_central) * cercania * penalizacion
```

También puedes modificar el peso asignado a la posición central:

```python
1 + 1 * proporcion_central
1 + 3 * proporcion_central
1 + 6 * proporcion_central
```

o cambiar la penalización aplicada cuando una región toca los bordes de la imagen:

```python
penalizacion = 0.20 if toca_borde else 1.0
penalizacion = 0.40 if toca_borde else 1.0
penalizacion = 0.80 if toca_borde else 1.0
```

> **Analiza:** ¿Cómo cambia la región seleccionada al incorporar progresivamente información de área, posición, cercanía al centro y contacto con los bordes?

---

## 🔎 Reflexión

A partir de los experimentos realizados, identifica cuáles parámetros y reglas tienen mayor influencia sobre la segmentación.

Observa cómo cada método incorpora nuevas decisiones:

**HSV → selección de píxeles candidatos**

**HSV + Contornos → selección de una región**

**HSV + Morfología + Centroides → limpieza de la máscara y selección de la región utilizando diferentes características**

En las técnicas clásicas de Procesamiento Digital de Imágenes, estas decisiones son definidas explícitamente por el diseñador mediante **parámetros, operaciones y reglas**. Por tanto, modificar estas decisiones permite analizar directamente su efecto sobre el resultado de la segmentación.
