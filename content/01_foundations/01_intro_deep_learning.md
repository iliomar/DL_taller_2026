---
title: Introducción a Deep Learning
---

# Introducción a Deep Learning

En el taller anterior estudiamos los fundamentos de **Machine Learning** y vimos cómo una computadora puede aprender patrones a partir de datos para realizar predicciones o clasificaciones.

En esta segunda parte daremos un paso más: estudiaremos **redes neuronales** y **Deep Learning**, comenzando desde sus ideas más básicas y avanzando progresivamente hacia arquitecturas más complejas.

Nuestro objetivo no será únicamente ejecutar código.

Queremos entender:

> **¿Qué información recibe una red neuronal, qué ocurre dentro de ella y cómo aprende a partir de datos científicos?**

A lo largo del taller utilizaremos ejemplos relacionados con:

- biología,
- astronomía,
- física,
- meteorología,
- ciencias ambientales,
- imágenes científicas,
- sensores y mediciones experimentales.

La meta es que los participantes puedan no solo comprender estos modelos, sino también **adaptar ideas similares para inspirar a sus estudiantes a explorar problemas científicos con datos reales**.

---

# De Machine Learning a Deep Learning

Deep Learning no es algo completamente separado de Machine Learning.

Podemos visualizar la relación de esta manera:

```text
Artificial Intelligence
        │
        └── Machine Learning
                │
                ├── Linear Regression
                ├── Logistic Regression
                ├── Decision Trees
                │
                └── Neural Networks
                         │
                         └── Deep Learning
```

Una red neuronal es un modelo formado por unidades matemáticas conectadas entre sí.

Cuando estas redes contienen múltiples capas capaces de aprender representaciones cada vez más complejas, hablamos de **Deep Learning**.

---

# ¿Por qué utilizar redes neuronales?

Muchos problemas científicos pueden describirse utilizando unas pocas variables.

Por ejemplo, para clasificar una flor podemos medir:

- largo del sépalo,
- ancho del sépalo,
- largo del pétalo,
- ancho del pétalo.

Podemos representar esas mediciones como:

\[
X =
\begin{bmatrix}
x_1 & x_2 & x_3 & x_4
\end{bmatrix}.
\]

Un modelo puede aprender relaciones entre esas mediciones y la especie de la flor.

```text
Mediciones de la flor
        │
        ▼
      Modelo
        │
        ▼
      Especie
```

Pero existen problemas mucho más complejos.

Por ejemplo:

> **¿Cómo puede una computadora identificar una galaxia en una imagen astronómica?**

o:

> **¿Cómo puede distinguir diferentes tipos de células en una imagen microscópica?**

o:

> **¿Cómo puede identificar patrones asociados con una tormenta utilizando mediciones atmosféricas?**

En estos casos, los datos pueden contener miles o millones de valores y relaciones difíciles de describir manualmente.

Las redes neuronales pueden aprender muchas de estas relaciones directamente a partir de los datos.

---

# Una idea inspirada en el cerebro

El término *red neuronal* está inspirado en las redes de neuronas biológicas.

De manera muy simplificada, una neurona biológica recibe señales, procesa información y puede producir una señal de salida.

```text
Señales de entrada
        │
        ▼
      Neurona
        │
        ▼
 Señal de salida
```

Una neurona artificial utiliza una idea matemática similar:

```text
Features
   │
   ▼
Entradas
   │
   ▼
Pesos + Bias
   │
   ▼
Función de activación
   │
   ▼
Salida
```

:::{important}
Una red neuronal artificial **no es una reproducción del cerebro humano**.

La inspiración original es biológica, pero las redes neuronales utilizadas en Machine Learning son modelos matemáticos.
:::

Más adelante estudiaremos cuidadosamente cada una de estas partes.

---

# Un poco de historia

Las redes neuronales no son una tecnología reciente.

Muchas de las ideas fundamentales del Deep Learning moderno comenzaron a desarrollarse hace varias décadas.

## 1943 — Primeros modelos matemáticos de una neurona

Warren McCulloch y Walter Pitts propusieron uno de los primeros modelos matemáticos de una neurona artificial.

La idea era sencilla pero importante:

> varias entradas pueden combinarse para producir una salida.

---

## 1958 — El perceptrón

Frank Rosenblatt desarrolló el **perceptrón**, uno de los primeros modelos capaces de ajustar parámetros a partir de ejemplos.

Conceptualmente:

```text
Inputs
  │
  ▼
Perceptron
  │
  ▼
Prediction
```

Aunque era mucho más sencillo que las redes actuales, introdujo una idea central:

> **una máquina puede aprender parámetros utilizando datos.**

---

## 1960–1970 — Limitaciones

Las primeras redes neuronales tenían limitaciones importantes.

Además:

- las computadoras eran mucho menos poderosas,
- existían pocos datos digitales,
- entrenar modelos grandes era extremadamente costoso,
- todavía faltaban técnicas eficientes para entrenar redes profundas.

Por esta razón, el interés en redes neuronales disminuyó durante algunos períodos.

---

## 1980s — Backpropagation

Durante la década de 1980 se popularizó el uso de **backpropagation** para entrenar redes neuronales con múltiples capas.

La idea general es:

```text
              FORWARD PASS

Datos ──► Red neuronal ──► Predicción
                              │
                              ▼
                             Loss


              BACKWARD PASS

          Gradientes ◄── Loss
               │
               ▼
       Ajustar los pesos
```

Backpropagation permite calcular cómo deben cambiar los parámetros internos de la red para reducir el error.

No necesitamos dominar esta matemática todavía.

La construiremos paso a paso más adelante.

---

## 1990–2000 — Más datos y mejores computadoras

Durante estas décadas ocurrieron varios cambios importantes:

1. aumentó enormemente la cantidad de datos digitales;
2. las computadoras se hicieron más rápidas;
3. las GPUs comenzaron a utilizarse para cálculos científicos y posteriormente para entrenamiento de redes neuronales;
4. mejoraron los algoritmos y las técnicas de entrenamiento.

Estas condiciones hicieron posible entrenar redes mucho más grandes.

---

## 2012 — AlexNet

En 2012, una red neuronal convolucional conocida como **AlexNet** obtuvo resultados sobresalientes en la competencia ImageNet de clasificación de imágenes.

Este resultado ayudó a demostrar que redes neuronales profundas, grandes datasets y GPUs podían producir avances importantes en visión computacional.

A partir de este período, Deep Learning comenzó a expandirse rápidamente.

---

# Deep Learning en la ciencia actual

Hoy las redes neuronales forman parte de muchas áreas de investigación científica.

```text
                     Deep Learning
                          │
       ┌──────────────────┼──────────────────┐
       │                  │                  │
       ▼                  ▼                  ▼
    Imágenes          Señales            Datos tabulares
       │                  │                  │
       ▼                  ▼                  ▼
 Microscopía          Sensores          Experimentos
 Astronomía           Audio             Meteorología
 Satélites            Detectores        Biología
```

Algunos ejemplos:

## Astronomía

Las redes neuronales pueden utilizarse para:

- clasificar galaxias,
- identificar objetos astronómicos,
- analizar curvas de luz,
- buscar eventos poco comunes en grandes observaciones.

## Física

Pueden ayudar a:

- clasificar eventos,
- reconstruir cantidades físicas,
- analizar señales de detectores,
- identificar patrones difíciles de modelar manualmente.

## Biología

Pueden utilizarse para:

- clasificar especies,
- analizar imágenes microscópicas,
- estudiar células,
- reconocer patrones en datos biológicos.

## Meteorología y ciencias ambientales

Pueden utilizarse para:

- analizar patrones meteorológicos,
- estudiar imágenes satelitales,
- predecir variables ambientales,
- clasificar tipos de cobertura terrestre.

---

# ¿Qué hace realmente una red neuronal?

Aunque una red neuronal pueda parecer complicada, podemos comenzar con una idea sencilla.

La red recibe **datos de entrada**.

Por ejemplo:

```text
Temperatura
Humedad
Presión
Velocidad del viento
```

Estas variables pueden utilizarse como **features**.

```text
Features
   │
   ▼
Neural Network
   │
   ▼
Prediction
```

Durante el entrenamiento, la predicción se compara con la respuesta conocida:

```text
Prediction ──┐
             ├──► Error / Loss
True value ──┘
```

Luego la red utiliza ese error para modificar sus parámetros.

```text
Datos
  │
  ▼
Forward Pass
  │
  ▼
Predicción
  │
  ▼
Loss
  │
  ▼
Backpropagation
  │
  ▼
Actualizar pesos
  │
  └──────────────► repetir
```

Esta secuencia será uno de los conceptos centrales del taller.

---

# ¿Qué significa "Deep"?

Una red neuronal sencilla puede tener una sola capa intermedia:

```text
INPUT           HIDDEN          OUTPUT

 ○ ────────────── ○
 ○ ────────────── ○ ───────────── ○
 ○ ────────────── ○
 ○ ────────────── ○
```

Si añadimos múltiples capas:

```text
INPUT       HIDDEN       HIDDEN       HIDDEN       OUTPUT

 ○ ───────── ○ ────────── ○ ────────── ○ ────────── ○
 ○ ───────── ○ ────────── ○ ────────── ○
 ○ ───────── ○ ────────── ○ ────────── ○
 ○ ───────── ○ ────────── ○ ────────── ○
```

tenemos una red más **profunda**.

De ahí proviene el término:

> **Deep Neural Network**

y, de manera más general:

> **Deep Learning**

---

# ¿Qué aprenderemos?

Construiremos el conocimiento progresivamente.

```text
Datos científicos
       │
       ▼
Features y Labels
       │
       ▼
Neurona Artificial
       │
       ▼
Weights + Bias
       │
       ▼
Funciones de Activación
       │
       ▼
Red Neuronal
       │
       ▼
Forward Pass
       │
       ▼
Loss
       │
       ▼
Gradient Descent
       │
       ▼
Backpropagation
       │
       ▼
Entrenamiento
       │
       ▼
Deep Neural Networks
       │
       ▼
Convolutional Neural Networks
       │
       ▼
Proyectos científicos
```

No queremos utilizar una red neuronal como una **caja negra**.

Queremos entender qué está ocurriendo dentro de ella y cómo conectar ese proceso con datos y preguntas científicas.

---

# Deep Learning en el salón de clases

Una meta importante de este taller es que los maestros puedan utilizar estas ideas para **inspirar a sus estudiantes a explorar ciencia con datos**.

No es necesario comenzar con ecuaciones complicadas.

Una buena actividad puede comenzar simplemente con una pregunta científica.

Por ejemplo:

> **¿Podemos identificar una especie de planta utilizando fotografías de sus hojas?**

o:

> **¿Podemos encontrar patrones meteorológicos utilizando datos de temperatura, humedad y presión?**

o:

> **¿Puede una computadora distinguir diferentes tipos de galaxias?**

La secuencia puede ser:

```text
Pregunta científica
        │
        ▼
Recolectar u obtener datos
        │
        ▼
Identificar features
        │
        ▼
Entrenar un modelo
        │
        ▼
Evaluar resultados
        │
        ▼
Interpretar científicamente
```

---

# Ideas de actividades científicas para estudiantes

## 1. Clasificación de hojas

Los estudiantes pueden recopilar fotografías de hojas de diferentes especies.

Preguntas:

- ¿Qué características permiten distinguirlas?
- ¿Forma?
- ¿Color?
- ¿Tamaño?
- ¿Textura?

Luego pueden entrenar un clasificador y evaluar cuándo falla.

---

## 2. Meteorología

Utilizando datos meteorológicos públicos, los estudiantes pueden investigar:

> **¿Qué variables están relacionadas con la lluvia?**

Features posibles:

- temperatura,
- humedad,
- presión,
- velocidad del viento.

Esto permite integrar:

- física,
- ciencias ambientales,
- estadística,
- programación,
- Machine Learning.

---

## 3. Astronomía

Con un pequeño dataset de estrellas:

```text
Temperatura
Luminosidad
Radio
Color
```

los estudiantes pueden investigar si diferentes tipos de estrellas ocupan regiones distintas del espacio de features.

Esto puede conectarse directamente con el **diagrama Hertzsprung–Russell**.

---

## 4. Imágenes científicas

Los estudiantes pueden trabajar con:

- imágenes microscópicas,
- imágenes de plantas,
- imágenes satelitales,
- imágenes astronómicas.

La pregunta central puede ser:

> **¿Qué patrones utiliza el modelo para distinguir diferentes categorías?**

---

## 5. Sensores y experimentos

También pueden recopilar datos utilizando sensores simples:

- temperatura,
- luz,
- humedad,
- aceleración,
- sonido.

Esto permite construir experiencias donde el estudiante participa en todo el proceso:

```text
experimento → medición → dataset → modelo → conclusión
```

---

# Una actividad introductoria sin programación

Antes de comenzar con Python, se puede presentar una colección de imágenes científicas.

Por ejemplo:

```text
Galaxia espiral
Galaxia elíptica
Galaxia irregular
```

Pida a los estudiantes que expliquen:

1. ¿Qué características utilizan ellos para distinguirlas?
2. ¿Color?
3. ¿Forma?
4. ¿Brillo?
5. ¿Estructura?

Luego haga la conexión:

> Una red neuronal también necesita encontrar características útiles para distinguir categorías.

Esto introduce de forma natural la idea de **features**.

---

# Preguntas para discutir

1. ¿Cómo puede una computadora representar una observación científica?
2. ¿Qué significa "aprender" para una red neuronal?
3. ¿Cómo sabemos si un modelo realmente aprendió un patrón útil?
4. ¿Qué ocurre si nuestros datos contienen errores?
5. ¿Qué ocurre si tenemos pocos ejemplos?
6. ¿Puede un modelo encontrar un patrón que no tenga una explicación científica?
7. ¿Una red neuronal siempre es la mejor herramienta?
8. ¿Cómo podemos utilizar estos modelos para formular nuevas preguntas?

---

# Video recomendado

Un excelente recurso visual para esta introducción es:

**3Blue1Brown — _But what is a neural network?_**

El video presenta de forma visual:

- neuronas,
- capas,
- pesos,
- bias,
- activaciones,
- y la idea de cómo una red procesa información.

:::{tip}
No es necesario utilizar el video completo en el salón.

Puede mostrar pequeños fragmentos y detenerse para discutir las visualizaciones con los estudiantes.
:::

---

# Recursos recomendados

## 3Blue1Brown — Neural Networks

La serie de redes neuronales de 3Blue1Brown utiliza excelentes visualizaciones para desarrollar intuición matemática.

**Recomendado para:** introducir conceptos antes de estudiar las ecuaciones formalmente.

---

## Google Teachable Machine

Permite entrenar modelos utilizando imágenes, sonidos y poses directamente desde el navegador.

Puede ser útil para actividades científicas sencillas como:

- clasificación de hojas,
- reconocimiento de objetos,
- clasificación de sonidos,
- identificación de diferentes patrones visuales.

**Recomendado para:** primeras demostraciones sin programación.

---

## TensorFlow Playground

Permite observar de forma interactiva cómo una red neuronal aprende a separar datos.

Los estudiantes pueden modificar:

- features,
- número de capas,
- número de neuronas,
- learning rate,
- funciones de activación.

**Recomendado para:** visualizar cómo cambia una red cuando modificamos su arquitectura.

---

## NASA Open Data

NASA ofrece numerosos datasets públicos relacionados con:

- astronomía,
- ciencias de la Tierra,
- atmósfera,
- satélites,
- clima.

**Recomendado para:** buscar inspiración para proyectos científicos.

---

## NOAA / National Weather Service

Proporciona datos meteorológicos que pueden utilizarse para actividades de análisis y predicción.

**Recomendado para:** proyectos relacionados con meteorología y ciencias ambientales.

---

## PyTorch — Learn the Basics

La documentación oficial de PyTorch incluye tutoriales sobre:

- tensors,
- datasets,
- redes neuronales,
- automatic differentiation,
- optimización,
- entrenamiento.

La utilizaremos como referencia cuando comencemos a programar nuestras primeras redes.

---

# Imágenes recomendadas para esta sección

Para mantener el Jupyter Book visual y atractivo, recomendamos incluir algunas figuras sencillas.

### Figura 1 — Historia de Deep Learning

```text
1943          1958            1980s             2012              Hoy
  │             │                │                 │                │
  ▼             ▼                ▼                 ▼                ▼
Neuronas → Perceptrón → Backpropagation → AlexNet/GPU → Deep Learning
```

### Figura 2 — Neurona biológica vs. neurona artificial

Mostrar ambas lado a lado, aclarando que la red artificial es únicamente una inspiración matemática.

### Figura 3 — Machine Learning dentro de AI

```text
Artificial Intelligence
        ↓
Machine Learning
        ↓
Neural Networks
        ↓
Deep Learning
```

### Figura 4 — Ciclo de entrenamiento

```text
Data
 ↓
Forward Pass
 ↓
Prediction
 ↓
Loss
 ↓
Backpropagation
 ↓
Update Weights
 ↺
```

:::{tip}
Es recomendable utilizar el mismo estilo gráfico para todos los diagramas del taller.

Esto ayuda a que los estudiantes reconozcan visualmente conceptos que aparecerán nuevamente en módulos posteriores.
:::

---

# Para recordar

:::{important}

Deep Learning no comienza con una arquitectura complicada.

Comienza con unas pocas ideas fundamentales:

**datos → features → parámetros → predicción → error → aprendizaje**

:::

Y para un científico o estudiante, la pregunta más importante siempre debe venir primero:

> **¿Qué fenómeno queremos estudiar y qué datos necesitamos para estudiarlo?**

En el próximo módulo comenzaremos con uno de los conceptos fundamentales para responder esa pregunta:

# Features y Labels
