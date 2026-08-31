---
numbering:
  title:
    offset: 0
---
(visualizacion)=
# Visualización de datos

En este capítulo repasamos las herramientas esenciales para visualizar datos antes de entrar a Machine Learning.
Veremos cómo crear gráficas básicas, cómo mejorar su apariencia y cómo combinar Matplotlib con Seaborn para resultados claros y reproducibles.

---

## Matplotlib

### Crear una figura y un eje
```{code-block} python
import matplotlib.pyplot as plt
fig, ax = plt.subplots(figsize=(6,4))
````

### De línea

```{code-block} python
x = [0,1,2,3,4]
y = [0,1,4,9,16]
plt.plot(x, y, label="y = x^2")
plt.xlabel("x")
plt.ylabel("y")
plt.title("Ejemplo: línea")
plt.legend()
plt.show()
```

### De puntos (scatter)

```{code-block} python
plt.scatter(x, y, c="C1", marker="o")
plt.xlabel("x")
plt.ylabel("y")
plt.title("Ejemplo: scatter")
plt.show()
```

### Histograma

```{code-block} python
import numpy as np
datos = np.random.normal(loc=0, scale=1, size=500)
plt.hist(datos, bins=30)
plt.title("Histograma de datos (normal)")
plt.show()
```

### Subplots (múltiples gráficos)

```{code-block} python
fig, axes = plt.subplots(1,2, figsize=(10,4))
axes[0].plot(x, y)
axes[0].set_title("Línea")
axes[1].hist(datos, bins=20)
axes[1].set_title("Histograma")
plt.tight_layout()
plt.show()
```

### Guardar figura

```{code-block} python
plt.plot(x,y)
plt.savefig("mi_grafica.png", dpi=150, bbox_inches="tight")
```

---

## Seaborn — visualizaciones estadísticas

Seaborn trabaja encima de Matplotlib y suele producir gráficos más informativos por defecto.

### Histograma con KDE

```{code-block} python
import seaborn as sns
sns.histplot(datos, kde=True)
plt.title("Histograma + KDE")
plt.show()
```

### Scatter con separación por categoría

```{code-block} python
# df es un DataFrame con columnas 'x','y','clase'
# ejemplo: sns.scatterplot(data=df, x="x", y="y", hue="clase")
```

### Boxplot (comparar distribuciones)

```{code-block} python
# sns.boxplot(x="categoria", y="valor", data=df)
```

### Countplot (conteo de categorías)

```{code-block} python
# sns.countplot(x="clase", data=df)
```

### Heatmap (matriz de correlación)

```{code-block} python
# sns.heatmap(df.corr(), annot=True, fmt=".2f", cmap="coolwarm")
```

### Pairplot (exploración rápida)

```{code-block} python
# sns.pairplot(df, hue="clase", vars=["u","g","r"])
```

---

## Buenas prácticas rápidas

* Añade etiquetas (`xlabel`, `ylabel`) y título (`title`) siempre.
* Usa `plt.tight_layout()` para evitar que textos se corten.
* Para publicación, guarda en PNG o PDF con `dpi` alto.
* Cuando uses `hue` en seaborn, verifica desequilibrio de clases (countplot).
* Si combinas seaborn y matplotlib, coloca llamadas a `plt.*` después de `sns.*` según necesites.

---

## Ejercicio guiado (práctico) — Visualización científica

En este ejercicio vas a analizar y visualizar una **señal astronómica simulada**. Hazlo en una libreta (Colab / Jupyter). Sigue los pasos y usa las pistas si te quedas atascado.

````{exercise}

**Analiza y visualiza una curva de luz simulada**

Tareas (hazlas en orden):

1. Crea un arreglo de tiempo `t` que vaya de 0 a 10 (horas) con 300 puntos usando `np.linspace`.
2. Simula una señal de brillo `flux` que consista en:
   - componente base = 1.5
   - señal periódica = `0.8 * np.sin(2*np.pi*t / P)` con periodo `P = 2.5`
   - ruido gaussiano con `np.random.normal(0, 0.18, size=t.shape)`
   - por tanto: `flux = 1.5 + 0.8 * np.sin(2*np.pi*t / P) + ruido`
3. Grafica la curva de luz con Matplotlib:
   - eje x = tiempo (horas)
   - eje y = brillo relativo
   - añade título y etiquetas
4. Grafica un histograma del brillo con Seaborn mostrando KDE.
5. Haz un scatter con líneas que muestre la curva suavizada:
   - usa `plt.plot(t, flux, ".", alpha=0.6, label="datos")`
   - calcula una versión suavizada con un filtro simple: usa un promedio móvil de ventana `window=7` y grafícalo encima en línea continua roja.
6. Guarda la figura final como `curva_luz.png`.

**Entrega:** copia el código que ejecutaste y pega la imagen guardada.

````{tip} Pistas paso a paso
:class: dropdown

- Paso 1:  
  ```python
  import numpy as np
  t = np.linspace(0, 10, 300)
  ```

- Paso 2:  
  ```python
  P = 2.5
  ruido = np.random.normal(0, 0.18, size=t.shape)
  flux = 1.5 + 0.8 * np.sin(2*np.pi*t / P) + ruido
  ```

- Paso 3 (Matplotlib básico):  
  ```python
  import matplotlib.pyplot as plt
  plt.figure(figsize=(8,4))
  plt.plot(t, flux, ".", alpha=0.6)
  plt.xlabel("Tiempo (horas)")
  plt.ylabel("Brillo relativo")
  plt.title("Curva de luz simulada")
  plt.show()
  ```

- Paso 4 (Histograma con KDE):  
  ```python
  import seaborn as sns
  sns.histplot(flux, bins=30, kde=True)
  plt.title("Distribución del brillo")
  plt.show()
  ```

- Paso 5 (Promedio móvil simple — suavizado):  
  ```python
  window = 7
  kernel = np.ones(window) / window
  flux_smooth = np.convolve(flux, kernel, mode="same")
  plt.figure(figsize=(8,4))
  plt.plot(t, flux, ".", alpha=0.4, label="datos")
  plt.plot(t, flux_smooth, "-", color="C3", linewidth=2, label="suavizado (mov. avg)")
  plt.legend()
  plt.show()
  ```

- Paso 6 (Guardar figura):  
  ```python
  plt.savefig("curva_luz.png", dpi=150, bbox_inches="tight")
  ```

Si algo no funciona, revisa que hayas importado `numpy`, `matplotlib.pyplot` y `seaborn` correctamente antes de ejecutar las celdas.
````

````{tip} Solución (código completo)
:class: dropdown

```python
# Código completo sugerido (copia y ejecuta)
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# datos
t = np.linspace(0,10,300)
P = 2.5
np.random.seed(42)  # para reproducibilidad en el ejemplo
ruido = np.random.normal(0, 0.18, size=t.shape)
flux = 1.5 + 0.8 * np.sin(2*np.pi*t / P) + ruido

# figura: curva de luz
plt.figure(figsize=(10,4))
plt.plot(t, flux, ".", alpha=0.6, label="datos")
plt.xlabel("Tiempo (horas)")
plt.ylabel("Brillo relativo")
plt.title("Curva de luz simulada")
plt.legend()
plt.tight_layout()
plt.show()

# histograma con KDE
plt.figure(figsize=(6,3))
sns.histplot(flux, bins=30, kde=True)
plt.title("Distribución del brillo")
plt.tight_layout()
plt.show()

# suavizado (mov average)
window = 7
kernel = np.ones(window)/window
flux_smooth = np.convolve(flux, kernel, mode="same")

plt.figure(figsize=(10,4))
plt.plot(t, flux, ".", alpha=0.35, label="datos")
plt.plot(t, flux_smooth, "-", color="C3", linewidth=2, label="suavizado (mov. avg)")
plt.xlabel("Tiempo (horas)")
plt.ylabel("Brillo relativo")
plt.title("Curva de luz con suavizado")
plt.legend()
plt.tight_layout()

# guardar
plt.savefig("curva_luz.png", dpi=150, bbox_inches="tight")
plt.show()
````

La imagen `curva_luz.png` se creará en el directorio de trabajo.
Puedes ajustar `window` para un suavizado más o menos agresivo.