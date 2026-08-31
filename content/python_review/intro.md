(python_review-start)=
# Análisis de Datos con Python

Antes de hablar de *Machine Learning*, primero debemos entender algo fundamental:

> La inteligencia artificial no empieza con algoritmos… empieza con datos.

En este primer día aprenderemos a usar **Python como herramienta científica** para observar, explorar y hacer preguntas a la información.

No necesitas experiencia previa en programación.  
Aquí no vamos a memorizar código, vamos a aprender a **pensar como científicos usando datos**.



## ¿Qué aprenderemos hoy?

Durante esta sesión vas a:
- Aprender como importar librerías
- Usar librerías como numpy, pandas, matplotlib, y seaborn
- Comprender qué es un *dataset* (conjunto de datos)
- Leer datos reales usando Python
- Explorar información y encontrar patrones
- Realizar cálculos simples sobre datos
- Crear gráficas para visualizar resultados

---

## ¿Por qué es importante?

Los algoritmos de Machine Learning no “adivinan”.

Ellos hacen exactamente lo que hoy vas a hacer manualmente:

1. Observar datos
2. Detectar patrones
3. Tomar decisiones basadas en esos patrones

Hoy tú serás el algoritmo.

---

:::{tip}
Durante el taller evita pensar:

> *¿Qué significa este código?*

Mejor pregúntate:

> *¿Qué me están diciendo los datos?*

Python solo será nuestro cuaderno de laboratorio.
:::



---

## Requisitos

Para esta actividad solo necesitas:

- Una computadora (no tablet ni celular)
- Una cuenta de Google
- Acceso a Google Colab

No instalaremos nada.

---

## Al final del día podrás

✔ Usar librerías comunes en análisis de datos
✔ Leer datasets reales  
✔ Analizar información científicamente  
✔ Crear gráficas para interpretar datos  
✔ Entender qué problema resuelve Machine Learning  

Y lo más importante:

> Estarás listo para una introducción a Machine Learning mañana.


`````{tip} Instrucciones antes de continuar

1. Accesa a [Google Colab](https://colab.research.google.com).

```{figure} figures/colab1.png
:name: openingColab
:width: 70%

Google Colab (Colaboratory) es un servicio gratuito en la nube de Google basado en Jupyter Notebooks que permite escribir y ejecutar código Python desde el navegador sin configuraciones previas
```

2. Crea una nueva libreta.

```{figure} figures/colab2.png
:name: NewNotebook
:width: 70%

En la parte superior izquerda presione ```File``` y luego ```New Notebook in Drive```
```

3. Recomendación: renombre su libreta con el siguiente formato: ```<nombre>_dia1_taller_ML.ipynb```

```{figure} figures/colab3.png
:name: Rename
:width: 70%

El nombre debe ser descriptivo, corto y utilizar preferiblemente minúsculas, separando palabras con guiones bajos.
```

4. Note que tiene las opciones de agregar una celda de código ```+ Code```, donde se escribe código y otra de texto ```+ Text```, donde se escribe texto en formato [Markdown](https://www.markdownguide.org/basic-syntax/). Agregue una celda código.

`````

```{div}
:class: text-center
# Comencemos! 🤖
```