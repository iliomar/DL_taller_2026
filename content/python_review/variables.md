---
numbering:
  title:
    offset: 0
---
(variables)=
# Variables y Tipos de Datos

Antes de analizar datos, primero debemos entender cómo Python guarda información.

Una **variable** es una caja donde almacenamos un valor para usarlo luego.



## Crear variables

```{code-block} python
temperatura = 23
masa = 1.989e30
nombre = "Sol"

print(temperatura)
print(masa)
print(nombre)
```

```{tip} Salida
23<br>
1.989e+30<br>
Sol
```



## Tipos de datos básicos

Python detecta automáticamente el tipo de dato.

```{code-block} python
entero = 10
decimal = 3.14
texto = "estrella"
booleano = True

print(type(entero))
print(type(decimal))
print(type(texto))
print(type(booleano))
```

```{tip} Salida
<class 'int'><br>
<class 'float'><br>
<class 'str'><br>
<class 'bool'>
```



## Operaciones con variables

Podemos usar variables en cálculos físicos:

```{code-block} python
distancia = 150_000_000      # km Tierra-Sol
tiempo = 500                 # segundos luz
velocidad = distancia/tiempo

print(velocidad)
```

```{tip} Salida
300000.0
```

 Acabas de calcular la velocidad de la luz aproximada.



## Strings (texto)

```{code-block} python
estrella = "Betelgeuse"
mensaje = "La estrella observada es " + estrella

print(mensaje)
```

```{tip} Salida
La estrella observada es Betelgeuse
```



## Booleanos

Sirven para tomar decisiones.

```{code-block} python
temperatura = 6000

es_caliente = temperatura > 5000
print(es_caliente)
```

```{tip} Salida
True
```



## Conversión de tipos

```{code-block} python
numero = "42"
numero = int(numero)

print(numero + 8)
```

```{tip} Salida
50
```



````{exercise}

**¿Qué tipo de dato es el resultado?**

```python
masa = 2
radio = 4.0
densidad = masa / radio
print(type(densidad))
```

A. int  
B. float  
C. str  
D. bool  

```{tip} Ver solución
:class: dropdown
Respuesta: **B**

Cuando un entero se divide por un decimal,
Python produce un número decimal (float).
```