---
numbering:
  title:
    offset: 0
---
(fundamentals)=
# Módulos Útiles

## Métodos comunes de Numpy

Aquí veremos funciones que se usarán constantemente antes de hacer Machine Learning.


### Crear arreglos

```{code-block} python
import numpy as np

a = np.array([1,2,3,4,5])
print(a)
```

```{tip} Salida
[1 2 3 4 5]
```


### Generar Secuencia de Valores
```{code-block} python
valores = np.linspace(0,10,5)   # 5 números entre 0 y 10
secuencia = np.arange(0,10,2)     # de 2 en 2

print(valores)
print(secuencia)
```

```{tip} Salida
[ 0.   2.5  5.   7.5 10. ]<br>
[0 2 4 6 8]
```


### Operaciones estadísticas básicas
```{code-block} python
datos = np.array([23,25,24,26,28])

print("Promedio", datos.mean()) #  calcula el promedio aritmético (la media) de los elementos
print("Desviación Estandar", datos.std()) # calcular la desviación estándar de un conjunto de datos
print("Mínimo", datos.min()) # encuentra el valor mínimo en un array
print("Maximo", datos.max()) # encuentra el valor máximo en un array
```

```{tip} Salida
Promedio 25.2<br>
Desviación Estandar 1.7204650534085253<br>
Mínimo 23<br>
Maximo 28
```

### Operaciones matemáticas vectorizadas

```{code-block} python
x = np.linspace(0,5,5)

print(x**2)
print(np.sqrt(x))
print(np.log(x+1))
```

```{tip} Salida
[ 0.      1.5625  6.25   14.0625 25.    ]<br>
[0.         1.11803399 1.58113883 1.93649167 2.23606798]<br>
[0.         0.81093022 1.25276297 1.55814462 1.79175947]
```

````{exercise} 

**Predice el resultado**

```python
import numpy as np
a = np.array([1,2,3])
print(a + 1)
```

A. Error  
B. [2,3,4]  
C. [1,2,3,1]  
D. 2

```{tip} Ver solución
:class: dropdown
Respuesta: **B**

NumPy aplica la operación a cada elemento automáticamente.
Esto se llama vectorización.
```
````

---

## Métodos comunes de Pandas

Con la libreria pandas podemos leer un documento en formato csv

```{code-block} python
import pandas as pd

df = pd.read_csv("datos.csv")
```

como también podemos crear nuestra propia data usando el método DataFrame

```{code-block} python
import pandas as pd

df = pd.DataFrame({
    "estrella":["Sol","Alfa Centauri A","Sirius"],
    "masa":[1, 1.1, 2.02],
    "distancia":[0.000016, 4.39, 8.6]
})
```



### Inspeccionar Datos

```{code-block} python
df.head() # muestra las primeras filas del DataFrame
df.info() # muestra resumen de la información sobre el DataFrame
df.describe() # muestra estadísticas descriptivas de las columnas del DataFrame
```

También podemos obtener el máximo, mínimo, y promedio de ciertas columnas en específico.

```{code-block} python
df["masa"].mean()
df["distancia"].max()
df["masa"].min()
```


Para crear nuevas columnas

```{code-block} python
df["radio"] = 3,958.8* (df["masa"] / 1)**0.8
```


````{exercise} 

**¿Qué hace df.head(5)?**

A. Borra datos<br>
B. Muestra primeras 5 filas<br>
C. Ordena la tabla hasta la fila 5<br>
D. Calcula promedio de la columna 5

```{tip} Ver solución
:class: dropdown
Respuesta: **B**

Inspeccionar rápidamente las primeras 5 filas del conjunto de datos.
```
````

---

## Métodos Comunes de Matplotlib

Matplotlib es la librería base para hacer gráficas en Python.
Es poderosa y muy flexible (pero más manual que seaborn).


### Crear figura

```python
plt.figure(figsize=(6,4))
```

### Línea

```python
plt.plot(x, y)
```

### Puntos (scatter)

```python
plt.scatter(x, y)
```

### Histograma

```python
plt.hist(datos, bins=20)
```

### Etiquetas

```python
plt.xlabel("Edad")
plt.ylabel("Altura")
plt.title("Relación Edad vs Altura")
```

### Leyenda

```python
plt.legend()
```

### Mostrar gráfica

```python
plt.show()
```

---

## Ejemplo

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0,10,50)
y = np.sin(x)

plt.plot(x,y)
plt.title("Onda seno")
plt.xlabel("x")
plt.ylabel("sin(x)")
plt.show()
```

`````{tip} Salida
```{figure} figures/sine.png
:width: 50%
```
`````

---

````{exercise}

**¿Qué tipo de gráfica crea `plt.scatter(x, y)`?**

A. Histograma<br>
B. Gráfica de barras<br>
C. Gráfica de puntos<br>
D. Gráfica circular

```{tip} Ver solución
:class: dropdown
Respuesta: **C**

`scatter` dibuja cada observación como un punto individual.
```
````

---

````{exercise}

**¿Para qué sirve `plt.show()`?**

A. Guardar la gráfica<br>
B. Mostrar la gráfica en pantalla<br>
C. Borrar la gráfica<br>
D. Exportar a Excel

```{tip} Ver solución
:class: dropdown
Respuesta: **B**

Hace que la figura se renderice en pantalla.
```
````

---

#  Métodos comunes de Seaborn

Seaborn es una librería basada en Matplotlib pero especializada en **análisis de datos**.

 En ciencia de datos real, se usa seaborn el 90% del tiempo.

---


### Histograma inteligente

```python
sns.histplot(data=df, x="edad")
```

### Relación entre variables

```python
sns.scatterplot(data=df, x="altura", y="peso")
```

### Boxplot

```python
sns.boxplot(data=df, x="genero", y="salario")
```

### Conteo de categorías

```python
sns.countplot(data=df, x="clase")
```

### Correlaciones

```python
sns.heatmap(df.corr(), annot=True)
```

---

## Ejemplo

```python
import seaborn as sns
import pandas as pd

df = sns.load_dataset("tips")

sns.scatterplot(data=df, x="total_bill", y="tip", hue="sex")
```

`````{tip} Salida
```{figure} figures/sex.png
:width: 50%
```
`````

---

````{exercise}

**¿Qué hace `hue="sex"` en seaborn?**

A. Filtra los datos<br>
B. Cambia el tamaño de puntos<br>
C. Colorea por categoría<br>
D. Calcula promedio

```{tip} Ver solución
:class: dropdown
Respuesta: **C**

Divide los datos por categorías usando colores diferentes.
```
````

---

````{exercise}

**¿Qué gráfica es mejor para ver correlaciones entre variables?**

A. scatterplot<br>
B. heatmap<br>
C. countplot<br>
D. histplot

```{tip} Ver solución
:class: dropdown
Respuesta: **B**

Un heatmap muestra correlaciones de muchas variables al mismo tiempo.
```
````


---

`````{tip} Ahora tu turno 

**Analizando una señal astronómica**

Un telescopio midió el brillo relativo de una estrella a lo largo del tiempo.
Las estrellas variables cambian su brillo periódicamente debido a pulsaciones físicas.

Tu trabajo será comportarte como un científico:
cargar datos → analizarlos → descubrir el patrón.



## 1) Crear el tiempo de observación

Crea un arreglo de tiempo de 0 a 10 horas con 200 mediciones:

````{tip} Pista
:class: dropdown
Crea una variable llamada tiempo y utiliza el método de numpy, linspace.
```python
import numpy as np

tiempo = np.linspace(0,10,200)
```
````

---

## 2) Simular el brillo observado

El brillo de la estrella sigue aproximadamente una señal sinusoidal
(una oscilación física real) más ruido instrumental. Agrega el brillo observado ()

```python
ruido = np.random.normal(0,0.2,200)
brillo = 2 + np.sin(2*np.pi*tiempo/3) + ruido

brillo[:10]
```

---

## 3) Estadísticas científicas

Calcula:

* brillo promedio
* brillo máximo
* desviación estándar (variabilidad de la estrella)


````{tip} Pista
:class: dropdown
```python
print("Promedio:", brillo.mean())
print("Maximo:", brillo.max())
print("Desviacion:", brillo.std())
```

La desviación estándar mide qué tan variable es la estrella.
````

---

## 4) Encontrar momentos más brillantes

Encuentra el índice donde la estrella fue más brillante:

```python
indice_max = np.argmax(brillo)
print(tiempo[indice_max], brillo[indice_max])
```

Ese fue el momento del máximo de luminosidad

---

## 5) Graficar la observación

```python
import matplotlib.pyplot as plt

plt.plot(tiempo, brillo)
plt.xlabel("Tiempo (horas)")
plt.ylabel("Brillo relativo")
plt.title("Curva de luz de estrella variable")
plt.show()
```

`````