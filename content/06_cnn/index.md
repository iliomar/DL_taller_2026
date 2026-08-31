---
title: Convolutional Neural Networks
---

# Convolutional Neural Networks

Hasta ahora hemos trabajado principalmente con datos tabulares:

```text
sample
  ↓
feature 1
feature 2
feature 3
...
  ↓
Neural Network
  ↓
Prediction
```

Pero muchos problemas científicos no vienen naturalmente en forma de tablas.

A veces nuestros datos son **imágenes**:

- imágenes astronómicas;
- imágenes microscópicas;
- imágenes satelitales;
- mapas meteorológicos;
- imágenes de plantas;
- mapas de detectores;
- imágenes experimentales.

En estos casos aparece una pregunta importante:

> **¿Cómo podemos construir una red neuronal que aproveche la estructura espacial de una imagen?**

La respuesta son las **Convolutional Neural Networks**, o **CNNs**.

---

# ¿Por qué no tratar una imagen como una lista de números?

Una imagen puede representarse numéricamente.

Por ejemplo, una imagen en escala de grises de:

```text
28 × 28 pixels
```

contiene:

\[
28 \times 28 = 784
\]

valores.

Podríamos convertirla en un vector:

```text
pixel 1
pixel 2
pixel 3
...
pixel 784
```

y usar una red completamente conectada.

Pero al hacerlo perdemos algo muy importante:

> **la posición espacial de los píxeles.**

En una imagen, los píxeles cercanos suelen estar relacionados.

Por ejemplo, una pequeña región puede contener:

- un borde;
- una textura;
- una curva;
- una estructura;
- una forma.

Una CNN está diseñada para aprovechar esa información local.

---

# Una imagen es un tensor

En Deep Learning, una imagen puede representarse como un tensor.

## Escala de grises

```text
Height × Width
```

por ejemplo:

```text
28 × 28
```

## Imagen RGB

Tenemos tres canales:

```text
Red
Green
Blue
```

y la imagen puede representarse como:

```text
3 × Height × Width
```

Por ejemplo:

```text
3 × 32 × 32
```

En PyTorch, cuando trabajamos con un batch de imágenes, la forma típica es:

```text
Batch × Channels × Height × Width
```

o:

\[
N \times C \times H \times W.
\]

---

# La idea central: la convolución

Una CNN utiliza pequeños filtros llamados **kernels**.

Por ejemplo:

```text
3 × 3
```

Un kernel se mueve sobre la imagen:

```text
Imagen

+---+---+---+---+---+
|   |   |   |   |   |
+---+---+---+---+---+
|   |[ ][ ][ ]|   |
+---+---+---+---+---+
|   |[ ][ ][ ]|   |
+---+---+---+---+---+
|   |[ ][ ][ ]|   |
+---+---+---+---+---+
|   |   |   |   |   |
+---+---+---+---+---+

       3 × 3 kernel
```

En cada posición realiza productos y sumas.

El resultado es un nuevo mapa llamado:

```text
feature map
```

Conceptualmente:

```text
Image
  ↓
Convolution
  ↓
Feature Map
```

---

# ¿Qué puede detectar un filtro?

Durante el entrenamiento, los filtros también aprenden.

Una CNN puede aprender filtros sensibles a patrones como:

```text
bordes
líneas
texturas
curvas
formas
```

Las primeras capas suelen detectar patrones relativamente simples.

Capas posteriores pueden combinar esos patrones.

```text
Pixels
  ↓
Edges
  ↓
Textures
  ↓
Shapes
  ↓
Complex patterns
  ↓
Prediction
```

Esta jerarquía de representaciones es una de las ideas más importantes detrás de las CNNs.

---

# Un ejemplo científico

Imaginemos imágenes de galaxias.

Queremos clasificar:

```text
espiral
elíptica
irregular
```

Una CNN podría procesar:

```text
Imagen de galaxia
        ↓
Convolution
        ↓
Edges / estructuras locales
        ↓
Convolution
        ↓
Patrones más complejos
        ↓
Classifier
        ↓
Tipo de galaxia
```

La red no recibe manualmente:

```text
"tiene brazos espirales"
```

En cambio, aprende patrones visuales a partir de los ejemplos.

---

# Otro ejemplo: microscopía

En una imagen microscópica, una CNN puede utilizar patrones relacionados con:

- forma;
- tamaño;
- bordes;
- textura;
- distribución espacial.

Por ejemplo:

```text
Microscopy Image
       ↓
CNN
       ↓
Cell Type
```

Esto permite conectar Deep Learning con:

- biología;
- medicina;
- física;
- química;
- análisis de imágenes.

---

# Componentes principales de una CNN

Durante esta sección estudiaremos cuatro ideas principales.

## 1. Convolutional Layer

En PyTorch:

```python
nn.Conv2d(...)
```

Esta capa aprende filtros.

Conceptualmente:

```text
Image
  ↓
Filters
  ↓
Feature Maps
```

---

## 2. Activation Function

Después de la convolución normalmente aplicamos una activación:

```python
nn.ReLU()
```

```text
Convolution
    ↓
ReLU
    ↓
Feature Map activado
```

---

## 3. Pooling

Pooling reduce las dimensiones espaciales.

Por ejemplo:

```python
nn.MaxPool2d(2)
```

puede transformar:

```text
28 × 28
```

en:

```text
14 × 14
```

Esto reduce:

- tamaño de los datos;
- costo computacional;
- sensibilidad a pequeñas variaciones espaciales.

---

## 4. Fully Connected Layers

Después de extraer patrones espaciales, podemos utilizar capas completamente conectadas para realizar la clasificación.

```text
Image
  ↓
Conv
  ↓
ReLU
  ↓
Pool
  ↓
Conv
  ↓
ReLU
  ↓
Pool
  ↓
Flatten
  ↓
Linear
  ↓
Prediction
```

---

# Una arquitectura típica

Una CNN sencilla puede verse así:

```text
Input Image
    ↓
Conv2D
    ↓
ReLU
    ↓
MaxPool
    ↓
Conv2D
    ↓
ReLU
    ↓
MaxPool
    ↓
Flatten
    ↓
Linear
    ↓
Output
```

En PyTorch, conceptualmente:

```python
nn.Conv2d(...)
nn.ReLU()
nn.MaxPool2d(...)

nn.Conv2d(...)
nn.ReLU()
nn.MaxPool2d(...)

nn.Flatten()
nn.Linear(...)
```

---

# Las dimensiones importan

En una CNN debemos seguir cuidadosamente:

```text
Channels
Height
Width
```

Por ejemplo:

```text
Input:
1 × 28 × 28
```

después de una convolución podría convertirse en:

```text
16 × 28 × 28
```

y después de pooling:

```text
16 × 14 × 14
```

Luego otra convolución:

```text
32 × 14 × 14
```

y otro pooling:

```text
32 × 7 × 7
```

Antes de una capa `Linear`, necesitamos convertir:

\[
32\times7\times7
\]

en un vector.

Eso se hace con:

```python
nn.Flatten()
```

---

# ¿Qué significa el número de canales?

En una imagen RGB:

```text
3 input channels
```

porque tenemos:

```text
Red
Green
Blue
```

Pero después de una convolución podemos tener:

```text
16 channels
32 channels
64 channels
```

Estos ya no representan colores.

Representan diferentes **feature maps aprendidos**.

Cada canal puede responder a distintos patrones visuales.

---

# CNNs en ciencias

Las CNNs se utilizan en muchos tipos de datos científicos.

## Astronomía

- clasificación de galaxias;
- detección de objetos;
- identificación de estructuras;
- análisis de imágenes telescópicas.

## Biología

- clasificación de células;
- análisis de tejidos;
- morfología;
- imágenes microscópicas.

## Meteorología

- imágenes satelitales;
- mapas de nubes;
- estructuras de tormentas;
- patrones espaciales.

## Física

- imágenes de detectores;
- calorímetros;
- mapas de energía;
- reconstrucción de patrones.

## Ciencias ambientales

- cobertura terrestre;
- imágenes satelitales;
- vegetación;
- cambios en superficie.

---

# ¿Qué aprenderemos en esta sección?

La secuencia será:

```text
Images as Data
      ↓
Convolutions
      ↓
Feature Maps
      ↓
CNN Architecture
      ↓
Training a CNN
      ↓
CNN Exercise
```

---

# Notebooks de esta sección

## 1. Imágenes como datos

En:

```text
01_images_as_data.ipynb
```

estudiaremos:

- cómo se representa una imagen;
- pixels;
- canales;
- shape;
- grayscale vs RGB;
- visualización de imágenes;
- batches.

---

## 2. Convoluciones

En:

```text
02_convolutions.ipynb
```

exploraremos:

- kernels;
- convolución;
- feature maps;
- stride;
- padding;
- efectos de distintos filtros.

La idea será **ver la convolución funcionando**, no solamente leer la fórmula.

---

## 3. Arquitectura de una CNN

En:

```text
03_cnn_architecture.ipynb
```

construiremos una CNN paso a paso:

```text
Conv
↓
ReLU
↓
Pool
↓
Conv
↓
ReLU
↓
Pool
↓
Flatten
↓
Linear
```

y seguiremos las dimensiones después de cada capa.

---

## 4. Entrenando una CNN

En:

```text
04_training_cnn.ipynb
```

conectaremos nuevamente:

```text
Forward Pass
    ↓
Loss
    ↓
Backpropagation
    ↓
Optimizer
    ↓
Training
```

pero esta vez con imágenes.

---

## 5. Ejercicio Integrador

Finalmente:

```text
05_cnn_exercise.ipynb
```

los participantes construirán, entrenarán y evaluarán una CNN de manera más independiente.

---

# Antes de comenzar

Considera esta pregunta:

> **¿Por qué una CNN podría ser mejor que una red completamente conectada para analizar imágenes?**

<details>
<summary><strong>Pista</strong></summary>

Piensa en qué significa que dos píxeles estén uno al lado del otro.

</details>

<details>
<summary><strong>Mostrar solución</strong></summary>

Porque una CNN preserva y utiliza la **estructura espacial** de la imagen.

Los filtros examinan regiones locales y pueden aprender patrones que aparecen en distintas posiciones.

Una red completamente conectada puede procesar píxeles, pero no incorpora esa estructura espacial de forma tan natural.

</details>

---

# Una idea importante

Una CNN no "ve" una imagen como nosotros.

Recibe números.

```text
Image
  ↓
Pixel values
  ↓
Convolutions
  ↓
Learned feature maps
  ↓
Prediction
```

El objetivo del entrenamiento es aprender qué patrones numéricos son útiles para resolver la pregunta que estamos estudiando.

---

# Para recordar

La gran diferencia entre una DNN completamente conectada y una CNN es que la CNN aprovecha la **estructura espacial**.

```text
DNN:
features → fully connected layers → prediction

CNN:
image → local filters → feature maps → classifier → prediction
```

En esta sección pasaremos de trabajar principalmente con **mediciones tabulares** a trabajar con **imágenes científicas**.
