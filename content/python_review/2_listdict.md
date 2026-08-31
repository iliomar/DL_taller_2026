---
numbering:
  title:
    offset: 0

kernelspec:
  name: python3
  display_name: 'Python 3'
---

(listas_diccionarios)=
# Listas y Diccionarios

Hasta ahora guardamos un solo valor en cada variable. Pero en ciencia casi siempre trabajamos con **muchos datos al mismo tiempo**.

Python tiene estructuras para almacenar colecciones:

- **Lista** → colección ordenada de valores
- **Diccionario** → colección de pares clave–valor (como una tabla simple)

---

## Listas

Una lista guarda múltiples valores en orden.

```{code-block} python
temperaturas = [5600, 5800, 6000, 6200]

print(temperaturas)
```

```{tip} Salida
[5600, 5800, 6000, 6200]
```



### Acceder a elementos

```{code-block} python
print(temperaturas[0])   # primer elemento
print(temperaturas[2])   # tercer elemento
```

```{tip} Salida
5600<br>
6000
```

OJO: Python empieza a contar desde **0**



### Modificar valores

```{code-block} python
temperaturas[1] = 5900
print(temperaturas)
```

```{tip} Salida
[5600, 5900, 6000, 6200]
```



### Agregar elementos

```{code-block} python
temperaturas.append(6500)
print(temperaturas)
```

```{tip} Salida
[5600, 5900, 6000, 6200, 6500]
```



### Longitud de la lista

```{code-block} python
print(len(temperaturas))
```

```{tip} Salida
5
```



````{exercise}

**¿Qué imprime el código?**

```python
planetas = ["Mercurio","Venus","Tierra","Marte"]
print(planetas[3])
```

A. Tierra  
B. Marte  
C. Venus  
D. Error  

```{tip} Ver solución
:class: dropdown
Respuesta: **B**

El índice 3 corresponde al cuarto elemento: Marte.
```
`````

---

## Diccionarios

Un diccionario guarda información etiquetada (como columnas de una tabla).

```{code-block} python
estrella = {
    "nombre": "Sirius",
    "temperatura": 9940,
    "distancia": 8.6
}

print(estrella)
```

```{tip} Salida
{'nombre': 'Sirius', 'temperatura': 9940, 'distancia': 8.6}
```

---

### Acceder a valores

```{code-block} python
print(estrella["nombre"])
print(estrella["temperatura"])
```

```{tip} Salida
Sirius<br>
9940
```

---

### Modificar valores

```{code-block} python
estrella["temperatura"] = 10000
print(estrella)
```

---

### Agregar nueva propiedad

```{code-block} python
estrella["tipo"] = "Estrella blanca"
print(estrella)
```

---

````{exercise}

**¿Qué sucede?**

```python
objeto = {"masa":2.0,"radio":1.0}
print(objeto["masa"])
```

A. Error  
B. 2.0  
C. "masa"  
D. None  

```{tip} Ver solución
:class: dropdown
Respuesta: **B**

El diccionario devuelve el valor asociado a la clave.
```
````

---

`````{exercise}

**Mini base de datos astronómica**

Crea un diccionario llamado `galaxia` con:

- nombre: Andromeda
- distancia: 2.5 millones de años luz
- tipo: Espiral

Luego imprime solo la distancia.

````{tip} Pista
:class: dropdown
```python
galaxia = {
    "nombre": "Andromeda",
    "distancia": 2.5,
    "tipo": "Espiral"
}

print(galaxia["distancia"])
```
````

`````