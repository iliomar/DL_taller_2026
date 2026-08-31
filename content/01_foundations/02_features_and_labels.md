---
title: Features y Labels
---

# Features y Labels

Antes de construir una red neuronal, necesitamos entender con claridad **qué información recibe el modelo** y **qué queremos que aprenda a predecir**.

Dos conceptos fundamentales aparecen una y otra vez en Machine Learning:

- **Features**: las variables o mediciones que utilizamos como entrada del modelo.
- **Labels**: las respuestas o categorías que queremos que el modelo aprenda a predecir.

En ciencias, estas ideas aparecen de forma muy natural porque constantemente trabajamos con **observaciones, mediciones y resultados**.

---

# Un ejemplo científico: clasificar flores

Supongamos que queremos construir un modelo que identifique la especie de una flor a partir de mediciones físicas.

Para cada flor medimos:

- largo del sépalo,
- ancho del sépalo,
- largo del pétalo,
- ancho del pétalo.

Y conocemos su especie.

| Largo sépalo (cm) | Ancho sépalo (cm) | Largo pétalo (cm) | Ancho pétalo (cm) | Especie |
| ---: | ---: | ---: | ---: | :--- |
| 5.1 | 3.5 | 1.4 | 0.2 | Setosa |
| 6.4 | 3.2 | 4.5 | 1.5 | Versicolor |
| 6.7 | 3.1 | 5.6 | 2.4 | Virginica |

En este problema:

```text
Largo del sépalo ─────┐
Ancho del sépalo ─────┤
Largo del pétalo ─────┼──► Modelo ───► Especie
Ancho del pétalo ─────┘
       Features                        Label
```

Las mediciones son las **features**.

La especie es la **label**.

---

# ¿Qué es una feature?

Una **feature** es una característica, medición o variable que describe cada ejemplo del dataset.

En contextos científicos, una feature puede ser una cantidad que medimos directamente con un instrumento.

Por ejemplo:

## Meteorología

- temperatura,
- humedad,
- presión atmosférica,
- velocidad del viento,
- precipitación acumulada.

## Astronomía

- brillo,
- color,
- temperatura estimada,
- período de variabilidad,
- intensidad en diferentes bandas de longitud de onda.

## Biología

- longitud,
- masa,
- concentración de una sustancia,
- número de estructuras observadas,
- características morfológicas.

## Física

- energía,
- momento,
- velocidad,
- tiempo,
- posición,
- intensidad de una señal.

:::{important}
Las features representan la **información que el modelo puede utilizar** para encontrar patrones.

Si una característica importante no está presente en los datos, el modelo no puede utilizarla.
:::

---

# ¿Qué es una label?

La **label** es el resultado, categoría o cantidad que queremos que el modelo aprenda a predecir.

Algunos ejemplos científicos:

| Problema | Features | Label |
|---|---|---|
| Clasificar flores | medidas de sépalos y pétalos | especie |
| Clasificar estrellas | brillo, color, temperatura | tipo de estrella |
| Identificar partículas | energía, momento, señales del detector | tipo de partícula |
| Clasificar células | tamaño, forma, textura | tipo de célula |
| Predecir lluvia | temperatura, humedad, presión | lluvia / no lluvia |
| Predecir una propiedad física | mediciones experimentales | valor de la propiedad |

---

# Samples, Features y Labels

Otra palabra importante es **sample**.

Un *sample* es una observación individual.

Por ejemplo, si cada fila de nuestro dataset corresponde a una flor:

| Largo sépalo | Ancho sépalo | Largo pétalo | Ancho pétalo | Especie |
|---:|---:|---:|---:|:---|
| 5.1 | 3.5 | 1.4 | 0.2 | Setosa |

esa fila representa **un sample**.

Contiene:

```text
4 features
1 label
```

Si observamos 150 flores:

```text
150 samples
4 features por sample
1 label por sample
```

---

# Cómo representamos los datos

En Machine Learning es común representar las features con:

\[
X
\]

y las labels con:

\[
y
\]

Por ejemplo:

\[
X =
\begin{bmatrix}
5.1 & 3.5 & 1.4 & 0.2 \\
6.4 & 3.2 & 4.5 & 1.5 \\
6.7 & 3.1 & 5.6 & 2.4
\end{bmatrix}
\]

y:

\[
y =
\begin{bmatrix}
\text{Setosa} \\
\text{Versicolor} \\
\text{Virginica}
\end{bmatrix}.
\]

Cada fila de \(X\) corresponde a un sample.

Cada columna corresponde a una feature.

---

# ¿Qué significa `X.shape`?

La forma o *shape* de los datos nos dice cuántos ejemplos y cuántas features tenemos.

En general:

```text
X.shape = (n_samples, n_features)
```

Por ejemplo:

```text
X.shape = (150, 4)
```

significa:

```text
150 observaciones
4 features por observación
```

Esta idea será muy importante cuando comencemos a construir redes neuronales.

Si tenemos cuatro features, nuestra red debe poder recibir cuatro valores por sample.

---

# Ejemplo científico: datos meteorológicos

Imagine que tenemos mediciones realizadas cada hora:

| Temperatura (°C) | Humedad (%) | Presión (hPa) | Viento (km/h) | ¿Llovió? |
| ---: | ---: | ---: | ---: | :---: |
| 29 | 78 | 1007 | 12 | Sí |
| 31 | 55 | 1014 | 8 | No |
| 27 | 88 | 1004 | 18 | Sí |

Podríamos utilizar:

```text
Temperatura
Humedad
Presión
Velocidad del viento
```

como features.

Y utilizar:

```text
Lluvia / No lluvia
```

como label.

El modelo intentaría aprender patrones como:

```text
mediciones atmosféricas
          │
          ▼
        modelo
          │
          ▼
probabilidad de lluvia
```

:::{tip}
Este tipo de ejemplo puede convertirse fácilmente en una actividad de clase utilizando datos meteorológicos públicos de Puerto Rico o de la región donde se encuentre la escuela.
:::

---

# Ejemplo científico: clasificación de estrellas

En astronomía, una estrella puede describirse utilizando mediciones como:

- temperatura,
- luminosidad,
- color,
- radio,
- magnitud.

Podemos imaginar un problema de clasificación:

```text
Temperatura ──┐
Luminosidad ──┤
Color ────────┼──► Modelo ───► Tipo de estrella
Radio ────────┤
Magnitud ─────┘
```

Esto permite conectar Machine Learning con conceptos de:

- evolución estelar,
- diagrama Hertzsprung–Russell,
- clasificación espectral,
- análisis de datos observacionales.

---

# Ejemplo científico: física de partículas

En un detector de partículas, un evento puede producir muchas mediciones.

Algunas features podrían ser:

- energía,
- momento transversal,
- dirección,
- número de partículas reconstruidas,
- energía depositada en diferentes partes del detector.

El objetivo podría ser distinguir entre diferentes tipos de eventos:

```text
Mediciones del detector
          │
          ▼
     Neural Network
          │
          ▼
   Tipo de evento
```

Este es un ejemplo real de cómo las redes neuronales se utilizan en experimentos científicos modernos.

---

# ¿Y qué pasa con las imágenes?

Una imagen también puede convertirse en datos numéricos.

Por ejemplo, una imagen en escala de grises de:

```text
28 × 28 pixels
```

contiene:

\[
28 \times 28 = 784
\]

valores de píxeles.

Cada píxel contiene un número relacionado con su intensidad.

```text
0    0   12   45  120 ...
0    5   80  200  255 ...
...
```

En una imagen RGB tenemos tres canales:

```text
Red
Green
Blue
```

Por ejemplo:

```text
32 × 32 × 3
```

como las imágenes de CIFAR-10.

Más adelante veremos que las **Convolutional Neural Networks (CNN)** están diseñadas para trabajar con la estructura espacial de estos datos.

---

# Imágenes científicas

Las imágenes no tienen que ser fotografías comunes.

En ciencias encontramos muchos tipos de imágenes:

- imágenes microscópicas de células,
- imágenes astronómicas,
- imágenes satelitales,
- mapas meteorológicos,
- radiografías,
- mapas de detectores,
- fotografías de especies y plantas.

Por ejemplo:

```text
Imagen microscópica
        │
        ▼
       CNN
        │
        ▼
Tipo de célula
```

o:

```text
Imagen satelital
        │
        ▼
       CNN
        │
        ▼
Tipo de cobertura terrestre
```

---

# ¿Todas las features son igual de útiles?

No.

Supongamos que estamos estudiando el crecimiento de una planta.

Podemos medir:

- cantidad de agua,
- horas de luz,
- temperatura,
- concentración de nutrientes,
- altura inicial.

Estas variables tienen una relación científica razonable con el crecimiento.

Pero una variable como:

```text
número asignado a la maceta
```

no debería contener información física relevante.

Esto introduce una idea muy importante:

> **Las features deben seleccionarse pensando en el fenómeno científico que estamos estudiando.**

---

# Machine Learning no reemplaza el razonamiento científico

Un modelo puede encontrar patrones en los datos.

Pero encontrar una correlación no significa descubrir una relación causal.

Imagine que observamos:

```text
Temperatura ↑
Consumo de energía ↑
```

Puede existir una relación, pero debemos investigar qué mecanismo físico o social produce el patrón.

:::{important}
Machine Learning puede ayudarnos a encontrar patrones, pero la interpretación científica sigue siendo esencial.
:::

---

# De las features a una red neuronal

Supongamos que tenemos cuatro mediciones:

\[
x_1,\;x_2,\;x_3,\;x_4
\]

Estas mediciones pueden convertirse directamente en las entradas de una red neuronal:

```text
Feature x₁ ─────► ○
Feature x₂ ─────► ○
Feature x₃ ─────► ○
Feature x₄ ─────► ○
                  │
                  ▼
            Neural Network
                  │
                  ▼
              Prediction
```

En el próximo módulo veremos qué ocurre cuando estas features llegan a una **neurona artificial**.

---

# En el salón de clases: pensar como científicos de datos

La meta no es utilizar Machine Learning para evaluar estudiantes.

La meta es utilizarlo como una herramienta para **investigar preguntas científicas**.

Los estudiantes pueden comenzar con una pregunta como:

> **¿Qué mediciones necesitaríamos para estudiar este fenómeno?**

Después pueden identificar:

1. qué observar,
2. qué medir,
3. cuáles son las features,
4. cuál es la label,
5. cómo obtener los datos,
6. qué limitaciones podrían tener esos datos.

---

# Actividad científica 1 — Clasificación de hojas

Los estudiantes pueden fotografiar diferentes especies de hojas.

Pueden recopilar:

- largo,
- ancho,
- área aproximada,
- color promedio,
- forma.

La label sería:

```text
especie de planta
```

Preguntas para discutir:

- ¿Qué características permiten distinguir las especies?
- ¿El tamaño es suficiente?
- ¿Qué ocurre con hojas jóvenes y maduras?
- ¿Necesitamos más ejemplos?

---

# Actividad científica 2 — Meteorología

Utilice datos meteorológicos públicos.

Los estudiantes pueden investigar:

> ¿Podemos predecir lluvia utilizando mediciones atmosféricas?

Features:

- temperatura,
- humedad,
- presión,
- viento.

Label:

```text
lluvia / no lluvia
```

Esto conecta Machine Learning con:

- ciencias ambientales,
- física,
- estadística,
- análisis de datos.

---

# Actividad científica 3 — Astronomía

Utilice un pequeño dataset de estrellas.

Features:

- temperatura,
- luminosidad,
- radio,
- color.

Label:

```text
tipo de estrella
```

Los estudiantes pueden visualizar primero los datos y luego investigar si un modelo puede aprender a separar diferentes categorías.

---

# Actividad científica 4 — Calidad del agua

Si se dispone de un dataset público, se pueden estudiar variables como:

- pH,
- temperatura,
- turbidez,
- conductividad,
- concentración de algunos compuestos.

Una posible pregunta sería:

> ¿Podemos identificar diferentes condiciones del agua a partir de estas mediciones?

Esto permite discutir también la importancia de:

- calibración,
- incertidumbre,
- unidades,
- calidad de los datos.

---

# Diseña una investigación

En grupos, seleccione una pregunta científica.

Por ejemplo:

- ¿Podemos clasificar diferentes especies de plantas?
- ¿Podemos identificar patrones meteorológicos?
- ¿Podemos clasificar estrellas?
- ¿Podemos distinguir materiales usando mediciones físicas?
- ¿Podemos clasificar imágenes microscópicas?

Complete:

| Pregunta | Propuesta |
|---|---|
| Pregunta científica | |
| ¿Qué observaremos? | |
| Feature 1 | |
| Feature 2 | |
| Feature 3 | |
| Label | |
| ¿Dónde obtendríamos los datos? | |
| ¿Qué limitaciones podría tener el experimento? | |

:::{tip}
El objetivo no es solamente entrenar un modelo.

Queremos que los estudiantes practiquen el proceso científico:

**pregunta → medición → datos → modelo → interpretación**
:::

---

# Preguntas para discutir

1. ¿Qué diferencia existe entre una observación y una feature?
2. ¿Cómo decidiríamos qué variables medir en un experimento?
3. ¿Todas las mediciones disponibles deben utilizarse?
4. ¿Qué ocurre si un sensor produce mediciones incorrectas?
5. ¿Qué ocurre si nuestro dataset contiene muy pocos ejemplos?
6. ¿Puede una imagen científica convertirse en features?
7. ¿Por qué debemos interpretar científicamente los patrones encontrados por el modelo?

---

# Recursos recomendados

## Scikit-learn — Iris Dataset

El dataset Iris es un excelente ejemplo para comenzar porque contiene mediciones físicas reales de flores y un problema de clasificación sencillo.

## NOAA / National Weather Service

Los datos meteorológicos públicos pueden utilizarse para construir actividades relacionadas con:

- temperatura,
- lluvia,
- humedad,
- presión,
- viento.

## NASA Open Data

NASA mantiene numerosos datasets públicos que pueden servir como inspiración para actividades de astronomía, ciencias de la Tierra y observación satelital.

## UCI Machine Learning Repository

Contiene numerosos datasets científicos y técnicos que pueden adaptarse para actividades educativas.

---

# Para recordar

:::{important}

En Machine Learning:

\[
X = \text{features}
\]

\[
y = \text{label}
\]

Las **features** son las mediciones que proporcionamos al modelo.

La **label** es lo que queremos que el modelo aprenda a predecir.

:::

Y, en un contexto científico:

> **Las features deben representar mediciones relevantes para la pregunta que estamos investigando.**

En la siguiente actividad utilizaremos un dataset científico real para explorar estas ideas con Python.
