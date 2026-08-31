---
title: Deep Neural Networks
---

# Deep Neural Networks

Hasta ahora hemos construido redes neuronales sencillas y hemos aprendido cómo ocurre el entrenamiento:

```text
Features
   ↓
Forward Pass
   ↓
Prediction
   ↓
Loss
   ↓
Backpropagation
   ↓
Update Parameters
```

En esta sección daremos un paso más y estudiaremos redes con **múltiples capas ocultas**.

Estas redes se conocen como **Deep Neural Networks (DNNs)**.

---

## ¿Qué hace que una red sea "deep"?

Una red sencilla podría tener una sola hidden layer:

```text
Input
  ↓
Hidden Layer
  ↓
Output
```

Por ejemplo:

```text
4 → 8 → 3
```

Una red profunda puede tener varias:

```text
4 → 32 → 16 → 8 → 3
```

Cada capa transforma la información recibida de la capa anterior.

Podemos pensar en el proceso como:

```text
Features originales
        ↓
Representaciones simples
        ↓
Representaciones intermedias
        ↓
Representaciones más complejas
        ↓
Predicción
```

La idea importante no es solamente tener más capas.

Es permitir que la red aprenda **combinaciones progresivamente más complejas de las features originales**.

---

# ¿Por qué utilizar una DNN?

En algunos problemas científicos, una relación sencilla entre variables puede ser suficiente.

Pero en otros casos, los patrones pueden ser mucho más complejos.

Por ejemplo:

### Astronomía

Una DNN podría utilizar:

- temperatura;
- luminosidad;
- color;
- radio;
- variabilidad;
- propiedades espectrales.

para distinguir diferentes tipos de objetos astronómicos.

### Meteorología

Podría combinar:

- temperatura;
- humedad;
- presión;
- viento;
- precipitación previa;
- radiación solar.

para identificar patrones atmosféricos complejos.

### Física

Puede combinar muchas mediciones de un detector para distinguir diferentes tipos de eventos.

En todos estos casos:

> una red más profunda puede aprender relaciones que no son fáciles de describir con una sola frontera simple.

---

# Más profundidad significa más capacidad

Una red más profunda suele tener más parámetros.

Por ejemplo:

```text
13 → 16 → 3
```

tiene menos parámetros que:

```text
13 → 32 → 16 → 8 → 3
```

Más parámetros significa mayor **capacity**.

Eso puede permitir que la red aprenda patrones más complejos.

Pero también introduce nuevos retos:

- mayor tiempo de entrenamiento;
- más parámetros que ajustar;
- mayor riesgo de overfitting;
- más sensibilidad a hyperparameters;
- necesidad de más datos.

---

# El problema del overfitting

Una red puede funcionar extremadamente bien en el training set y peor en datos nuevos.

Por ejemplo:

```text
Training accuracy   = 0.99
Validation accuracy = 0.75
```

Esto puede ser una señal de **overfitting**.

El modelo aprendió demasiado específicamente los ejemplos utilizados durante el entrenamiento.

Nuestro objetivo no es solamente minimizar training loss.

Queremos que el modelo **generalice**.

```text
Training Data
     ↓
 Learn Patterns
     ↓
New Data
     ↓
Good Predictions
```

---

# Training, Validation y Test

A partir de esta sección comenzaremos a distinguir con más cuidado entre:

```text
Training
Validation
Test
```

## Training set

Se utiliza para actualizar:

- weights;
- biases.

## Validation set

Se utiliza para tomar decisiones como:

- tamaño de la red;
- learning rate;
- número de epochs;
- Dropout;
- regularización.

## Test set

Se utiliza para la evaluación final.

Idealmente, no debemos utilizar el test set repetidamente para diseñar el modelo.

---

# Regularización

Para reducir overfitting existen varias técnicas.

En esta sección estudiaremos principalmente:

## Dropout

Durante training, Dropout desactiva aleatoriamente parte de las activaciones.

```text
o  o  o  o  o
↓  X  ↓  X  ↓
o     o     o
```

Esto puede evitar que la red dependa demasiado de neuronas particulares.

---

## Weight Decay

Weight decay penaliza, de forma aproximada, parámetros excesivamente grandes.

Podemos pensar conceptualmente en:

\[
L_{total}
=
L_{data}
+
\lambda \sum_i w_i^2
\]

donde:

- \(L_{data}\) mide el error de las predicciones;
- el segundo término penaliza ciertos weights grandes;
- \(\lambda\) controla la intensidad de la regularización.

---

## Early Stopping

También podemos detener el entrenamiento cuando validation loss deja de mejorar.

```text
Validation Loss

decreasing
   ↓
best point
   ↓
starts increasing
   ↓
stop training
```

---

# ¿Qué aprenderemos en esta sección?

La secuencia será:

```text
Deep Neural Networks
        ↓
Más capas y más parámetros
        ↓
Mayor capacidad
        ↓
Overfitting
        ↓
Regularización
        ↓
Comparación de modelos
        ↓
Ejercicio integrador
```

Trabajaremos con PyTorch y continuaremos utilizando datos científicos y datasets educativos.

---

# Notebooks de esta sección

## 1. Deep Neural Networks

En el primer notebook:

```text
01_deep_neural_networks.ipynb
```

compararemos:

```text
Red sencilla
13 → 16 → 3
```

con:

```text
DNN
13 → 32 → 16 → 8 → 3
```

y estudiaremos:

- profundidad;
- capacidad;
- parámetros;
- training loss;
- accuracy.

---

## 2. Overfitting y Regularización

En:

```text
02_overfitting_and_regularization.ipynb
```

estudiaremos:

- train vs validation;
- overfitting;
- Dropout;
- weight decay;
- early stopping;
- generalización.

---

## 3. Ejercicio Integrador

Finalmente:

```text
03_DNN_exercise.ipynb
```

aplicaremos todo el material en un problema científico de clasificación.

El ejercicio incluirá:

```text
Dataset
   ↓
Train / Validation / Test
   ↓
Standardization
   ↓
Deep Neural Network
   ↓
Training
   ↓
Regularization
   ↓
Evaluation
```

---

# Una pregunta importante

Antes de comenzar, considera:

> **Si una red más grande tiene más capacidad, ¿por qué no utilizar siempre la red más grande posible?**

La respuesta será uno de los temas centrales de esta sección.

<details>
<summary><strong>Pista</strong></summary>

Piensa en:

- cantidad de datos;
- tiempo de entrenamiento;
- overfitting;
- generalización.

</details>

<details>
<summary><strong>Mostrar solución</strong></summary>

Porque una red más grande puede aprender patrones más complejos, pero también puede:

- memorizar los datos de entrenamiento;
- requerir más datos;
- ser más difícil de entrenar;
- añadir complejidad innecesaria;
- generalizar peor.

La arquitectura adecuada depende del problema.

</details>

---

# Para recordar

Una DNN no es automáticamente mejor por tener más capas.

Queremos encontrar un balance entre:

```text
Capacidad suficiente
        +
Entrenamiento estable
        +
Buena generalización
```

En esta sección aprenderemos cómo evaluar ese balance antes de pasar al siguiente gran tema:

# Convolutional Neural Networks
