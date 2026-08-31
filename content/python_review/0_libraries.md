---
numbering:
  title:
    offset: 0
---

# Librerías en Python

Hasta ahora usamos Python como calculadora y para trabajar con listas.

Pero en la vida real nadie analiza datos así.

Los científicos, ingenieros y analistas usan **librerías**.

---

## ¿Qué es una librería?

Una librería es un conjunto de herramientas ya construidas por otras personas para resolver problemas específicos.

Es como:

| Área | Herramienta |
|------|-------------|
| Carpintería | martillo |
| Matemática | calculadora |
| Ciencia de datos | librerías |

En vez de programar todo desde cero… usamos conocimiento acumulado.

```{figure} figures/libraries.png
:name: librerias
:width: 100%

Diferentes librerias que se utilizan en análisis de datos y machine learning.
```

---

## Importar una librería

```python
import numpy as np
```

Esto significa:

> "Trae las herramientas matemáticas avanzadas para poder usarlas"

`np` es solo un apodo (alias) para escribir menos.

---

````{exercise}

**¿Qué significa `import pandas as pd`?**

A. Crear una variable llamada pandas<br>
B. Descargar pandas de internet<br>
C. Traer herramientas externas para usarlas en el programa<br>
D. Crear un archivo nuevo

```{tip} Ver solución
:class: dropdown
Respuesta: **C**

Importar una librería significa traer código ya existente para usar sus funciones.
````

---

# NumPy — matemáticas y vectores

NumPy permite trabajar con **arreglos numéricos eficientes**.

Es la base de casi toda la computación científica en Python.

Se usa cuando:
- hay muchos números
- necesitamos rapidez
- trabajamos con mediciones



## Ejemplo


```{code-block} python
import numpy as np

temperaturas = np.array([23, 25, 24, 26, 28])

print(temperaturas.mean())
print(temperaturas.max())
```

```{tip} Salida
25.2<br>
28
```

---

## Diferencia con listas

```python
lista = [1,2,3,4]
array = np.array([1,2,3,4])

lista * 2
array * 2
```

```{tip} Salida
[1, 2, 3, 4, 1, 2, 3, 4]<br>
array([2, 4, 6, 8])
```

---

# Pandas — tablas inteligentes

Pandas permite trabajar con **tablas de datos reales**.

Es lo más importante para análisis de datos.

Se usa cuando:

* hay archivos CSV
* encuestas
* mediciones experimentales



## Ejemplo


Con la libreria pandas podemos leer un documento en formato csv

```{code-block} python
import pandas as pd

df = pd.read_csv("datos.csv")
```

pero también podemos crear nuestra propia data usando el método DataFrame

```{code-block} python
import pandas as pd

df = pd.DataFrame({
    "estrella":["Sol","Alfa Centauri A","Sirius"],
    "masa":[1, 1.1, 2.02],
    "distancia":[0.000016, 4.39, 8.6]
})
```


---

# Matplotlib — graficar

Permite visualizar datos.

Es la herramienta básica de gráficos.

---

## Ejemplo

```python
import matplotlib.pyplot as plt

plt.plot([1,2,3],[4,5,6])
plt.show()
```

---

Se usa cuando queremos:

- ver tendencias
- explicar resultados
- enseñar a estudiantes

---

````{exercise}

**¿Para qué sirve graficar?**

A. Decorar el código<br>
B. Ver patrones en los datos<br>
C. Acelerar cálculos <br>
D. Guardar archivos

```{tip} Ver solución
:class: dropdown

Respuesta: **B**

El cerebro humano entiende mejor visualmente que numéricamente.
````

---

# Seaborn — gráficos estadísticos

Es una mejora de matplotlib.

Hace gráficos más claros automáticamente.



## Ejemplo

```python
import seaborn as sns

sns.histplot(df["nota"])
```

---

Se usa cuando queremos:

* histogramas claros
* comparar grupos
* visualizar distribuciones

---

````{exercise} 

**¿Por qué usar seaborn en vez de matplotlib?**

A. Es obligatorio  
B. Hace gráficos estadísticos automáticamente  
C. Es más rápido  
D. No usa Python

```{tip} Ver solución
:class: dropdown
Respuesta: **B**

Seaborn está diseñado para análisis de datos, no solo dibujo.
```
````

---

# Librerías futuras (Machine Learning)

Estas no las usaremos todavía, pero existen:

| Librería     | Uso                          |
| ------------ | ---------------------------- |
| scikit-learn | Machine Learning clásico     |
| tensorflow   | redes neuronales             |
| pytorch      | deep learning investigación  |
| xgboost      | modelos predictivos potentes |

---

`````{tip}
Primero:

> entender datos

Después:

> predecir datos

Machine Learning viene luego.
`````

---

# Resumen

| Librería   | Para qué sirve        |
| ---------- | --------------------- |
| NumPy      | cálculos numéricos    |
| Pandas     | tablas de datos       |
| Matplotlib | gráficos básicos      |
| Seaborn    | gráficos estadísticos |

---

En ciencia de datos, la mayor parte del trabajo NO es Machine Learning.
Es entender los datos.

`````{tip} Ahora tu turno

1.  En una celda de código, agrega el comentario ```importando librerias```. Recuerde los comentarios en python: ```#``` para comentarios de una sola línea y ```""" """``` para comentarios de multiples líneas.

2. Finalmente importe las cuatro librerias (con sus respectivos aliases) que estaremos utilizando.

Resultado final de su celda debería ser

```{code-block} python
# importando librerías

import numpy as np
import matplotlib.pyplot as plt
import seaborn as sb
import pandas as pd
```

`````