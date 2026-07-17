# 📘 Procesamiento Digital de Voz e Imágenes en la Era de la Inteligencia Artificial

> **Repositorio oficial del libro**
>
> **Procesamiento Digital de Voz e Imágenes en la Era de la Inteligencia Artificial**  
> **Dora María Ballesteros**  
> **Editorial Redipe, 2026**

> **📌 Nota:** Este repositorio corresponde al libro actualmente **en proceso de evaluación editorial**. La información bibliográfica definitiva (ISBN y datos de publicación) se actualizará una vez finalice el proceso editorial.

---

## 📖 Sobre este repositorio

Este repositorio contiene el material práctico del libro **Procesamiento Digital de Señales e Imágenes en la Era de la Inteligencia Artificial**.

El libro integra los fundamentos clásicos del Procesamiento Digital de Señales con herramientas modernas de Inteligencia Artificial mediante ejemplos y casos de estudio completamente reproducibles desarrollados en Python utilizando Jupyter Notebooks.

Los notebooks acompañan los capítulos prácticos del libro e incluyen el desarrollo paso a paso de algoritmos para el procesamiento de señales, imágenes y audio, permitiendo al lector experimentar y comprender cada una de las técnicas estudiadas.

El objetivo del repositorio es facilitar un aprendizaje activo, donde el lector pueda ejecutar, modificar y extender cada uno de los ejemplos desarrollados en el libro.

---

# 📚 Contenido del libro

| Cap. | Tema | Descripción | 📒 Notebook |
|:---:|------|-------------|:----------:|
| **1** | 🎙️ **Fundamentos del Procesamiento Digital de Señales y Filtros Digitales** | Introducción a los fundamentos del procesamiento digital de señales, diseño y análisis de filtros FIR e IIR mediante ejemplos implementados en Python. | [Abrir](Capitulo_1.ipynb) |
| **2** | 🔇 **Eliminación de Ruido con Filtros Digitales** | Aplicación de filtros digitales para la reducción de ruido en señales de voz, comparando diferentes estrategias de filtrado en los dominios del tiempo y la frecuencia. | [Abrir](Capitulo_2.ipynb) |
| **3** | 🤖 **Inteligencia Artificial para Localización de Interferencias y Filtrado Espectral** | Uso de técnicas de Inteligencia Artificial para la localización automática de interferencias y el filtrado espectral de señales de voz mediante algoritmos de aprendizaje no supervisado. | [Abrir](Capitulo_3.ipynb) |
| **4** | 🖼️ **Fundamentos del Procesamiento Digital de Imágenes** | Introducción a las principales técnicas de procesamiento digital de imágenes, incluyendo ecualización, detección de bordes y segmentación mediante el modelo HSV. | [Abrir](Capitulo_4.ipynb) |
| **5** | ✂️ **Segmentación de Imágenes con Técnicas Clásicas de PDI** | Aplicación de técnicas clásicas de segmentación utilizando máscaras binarias, contornos, operaciones morfológicas y análisis de centroides. | [Abrir](Capitulo_5.ipynb) |
| **6** | 🧠 **Segmentación Automática con Inteligencia Artificial** | Desarrollo de un modelo basado en U-Net para la segmentación automática de imágenes, utilizando un conjunto de datos real y herramientas modernas de aprendizaje profundo. | [Abrir](Capitulo_6.ipynb) |

---

## 📖 Organización del libro

## Sección I. Procesamiento Digital de Audio e Inteligencia Artificial

### Capítulo 1. Fundamentos del Procesamiento Digital de Señales y filtros digitales

Notebook del capítulo:

- Ejemplo 1. Señal discreta en Python de duración finita.
- Ejemplo 3. Polos y ceros a partir de la función de transferencia.
- Ejemplo 4. Respuesta en frecuencia de un filtro de promedio.
- Ejemplo 5. Diseño de un filtro FIR mediante el método de ventaneo.
- Ejemplo 6. Efecto de la longitud de la ventana.
- Ejemplo 7. Diseño de un filtro Butterworth pasa-bajo mediante Transformada Bilineal.
- Ejemplo 8. Diseño de un filtro Butterworth pasa-alto mediante Transformada Bilineal.

---

### Capítulo 2. Eliminación de ruido con filtros digitales

Notebook del capítulo:

- Ejemplo 11. Lectura y visualización en los dominios del tiempo y la frecuencia de una señal de voz.
- Ejemplo 12. Análisis de una señal de voz con ruido.
- Ejemplo 13. Filtrado mediante un filtro de promedio.
- Ejemplo 14. Filtrado con un filtro FIR diseñado mediante el método de ventaneo.
- Ejemplo 15. Filtrado con un filtro IIR Butterworth utilizando Transformada Bilineal.
- Ejemplo 16. Filtrado mediante un filtro Leaky.
- Ejemplo 17. Comparación entre filtros de promedio, FIR (ventana Blackman), Butterworth e IIR Leaky.

---

### Capítulo 3. IA para localización de interferencias y filtrado espectral

Notebook del capítulo:

- Ejemplo 18. Algoritmo K-Means aplicado al filtrado de ruido tonal en una señal de voz.
- Ejemplo 19. Algoritmo DBSCAN aplicado al filtrado de ruido tonal en una señal de voz.
- Ejemplo 20. Comparación cuantitativa entre filtros FIR, IIR y una máscara espectral basada en inteligencia artificial.

---

## Sección II. Procesamiento Digital de Imágenes e Inteligencia Artificial

### Capítulo 4. Fundamentos del Procesamiento Digital de Imágenes

Notebook del capítulo:

- Ejemplo 22. Ecualización de imágenes en escala de grises.
- Ejemplo 23. Ecualización de imágenes a color utilizando el modelo HSV.
- Ejemplo 24. Detección de bordes mediante el algoritmo Canny.
- Ejemplo 25. Segmentación de imágenes utilizando el modelo HSV.

---

### Capítulo 5. Segmentación de imágenes con técnicas clásicas de PDI

Notebook del capítulo:

- Ejemplo 27. Segmentación de una hoja mediante una máscara binaria en el modelo HSV.
- Ejemplo 28. Segmentación de una hoja mediante contornos y máscara binaria.
- Ejemplo 29. Segmentación mediante contornos, operaciones morfológicas y análisis de centroides.

---

### Capítulo 6. Segmentación automática con Inteligencia Artificial

Notebook del capítulo:

- Ejemplo 30. Entrenamiento de una U-Net para la segmentación automática de la hoja principal del dataset RoCoLe.

---

## ▶️ Ejecución

Los notebooks pueden ejecutarse en:

- Google Colab (100% compatible)
- Jupyter Notebook
- JupyterLab
- Visual Studio Code

---

## 🎓 Público objetivo

Este material está dirigido a:

- Estudiantes de ingeniería (telecomunicaciones, electrónica, multimedia, mecatrónica, sistemas, y carreras afines)
- Profesores de ingeniería y de matemática aplicada.
- Investigadores en PDS e Inteligencia Artificial.
- Profesionales interesados en procesamiento digital de señales (voz e imágenes) e inteligencia artificial.

---

## 📚 Cómo citar

Si este material resulta útil para su trabajo académico o de investigación, agradecemos citar el libro correspondiente.

**Dora María Ballesteros**

*Procesamiento Digital de Voz e Imágenes en la Era de la Inteligencia Artificial.*

Editorial Redipe, 2026.

---

## 📄 Licencia

Este repositorio se distribuye únicamente con fines educativos y de investigación.

Consulte el archivo **LICENSE** para más información.

---


# 📧 Contacto

**Dora María Ballesteros**  
Profesora e Investigadora  
Universidad Militar Nueva Granada

📧 **dora.ballesteros@unimilitar.edu.co**

📍 Bogotá, Colombia
