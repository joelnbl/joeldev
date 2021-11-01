---
title: Qué son las f-strings en Python
date: '2021-10-31'
tags: ['python', 'code', 'f-string']
draft: false
summary: Una de las cosas más comunes que solemos realizar en cualquier programa de software es imprimir un texto en pantalla dependiendo de las variables, errores o condiciones.
---

![F-string](https://res.cloudinary.com/practicaldev/image/fetch/s--S_-WagGT--/c_imagga_scale,f_auto,fl_progressive,h_900,q_auto,w_1600/https://dev-to-uploads.s3.amazonaws.com/i/2pb0bys42zgr1l6cawvn.png)
Los literales de cadenas formateados o f-string de Python es una herramienta que facilita crear interpolaciones en cadenas de texto. Simplificando de este modo tanto la lectura como la escritura de estas. Las f-string se introdujo en la versión 3.6 de Python, por lo que es algo relativamente nuevo. Veamos cómo se pueden usar para crear mensajes de una forma más fácil.

## ¿Qué son las f-string de Python?

Las f-string se construyen como una cadena de texto normar el Python, pero precedidas de una f o F. Lo que hace que sea posible interpolar código encerrando este en llaves {'({})'} dentro de la cadena. Obteniendo como resultado una cadena de texto. Por ejemplo, se podría imprimir el resultado de una suma con f'La suma es {'1 + 2'}', lo que devolverá la cadena de texto 'La suma es 3'.

## Interpolación de variables

Al decir que se puede interpolar código también se puede situar una variable entre las llaves de la f-string. Lo que permite crear mensajes de texto personalizados en función de los valores, por ejemplo:

```python
a = 2
b = 10
f'La suma de {a} y {b} es {a + b}'
```

Lo que devuelve la cadena de texto 'La suma de 2 y 10 es 12'. Ahora, en el caso de que sea necesario incluir unas llaves dentro de la cadena de texto se puede conseguir escribiendo dos, tanto para la inicial como el final. Algo que se puede ver en el siguiente ejemplo: f'La suma de {'{a:{a}}'} y {'{b:{b}}'} es {'a + b'}', con el que se obtiene la cadena 'La suma de {'a:2'} mas {'b:10'} es 12'.

```python
f'La suma de {{a:{a}}} y {{b:{b}}} es {a + b}'
```

## Formatos numéricos de las f-string

Otra de las ventajas de las f-string es que ofrecen la posibilidad de dar formato a los números. Lo que facilita crear cadenas de texto para los usuarios con un muermo fijo de decimales. Para lo que solamente hay que escribir entre las llaves la variable seguida de dos puntos y el formato deseado. Pudiéndose usar f para indicar números decimales, % para indicar porcentajes, lo que ya multiplicará los valores por 100, o e para el formato exponencial. En todos los casos se puede proceder de una expresión n.m donde n es el número de dígitos y m el número de decimales. Algo que se puede ver en el siguiente ejemplo.

```python
number = 0.123456789
print(f'Formatear el valor con cuatro dígitos: {number:.4f}')
print(f'Imprimir el valor como un porcentaje: {number:.2%}')
print(f'Formato exponencial: {number:e}')
```

---

Formatear el valor con cuatro dígitos: 0.1235
Imprimir el valor como un porcentaje: 12.35%
Formato exponencial: 1.234568e-01

---

A la hora de indicar el número de decimales también se puede indicar que se complete con ceros las posiciones a la izquierda. Lo que se consigue indicado un 0 antes del número de decimales.

```python
numbers = [1,10,100]
for number in numbers:
    print(f'El valor con ceros es: {number:04}')
```

---

El valor con ceros es: 0001
El valor con ceros es: 0010
El valor con ceros es: 0100

---

Además, también se puede indicar que signo se indique en todos los casos, tanto cuando el valor sea positivo como negativo. Para lo que solamente se tiene que usar + como formato.

```python
numbers = [-1,0,1]
for number in numbers:
    print(f'El valor con signo es: {number:+}')
```

---

El valor con signo es: -1
El valor con signo es: +0
El valor con signo es: +1

---

## Alienar las cadenas de texto

Otra opción bastante interesante es aligerar los mensajes a la izquierda, derecha o centro. Lo que se indica respectivamente con >, < y ^ seguido del número de caracteres que tiene la cadena texto. Algo que se puede ver cómo funciona en el siguiente ejemplo.

```python
name = 'analytics'
print(f'12345678901234567890')
print(f'{name : >20}')
print(f'{name : <20}')
print(f'{name : ^20}')
```

---

12345678901234567890
analytics
analytics  
 analytics

---

En esta ocasión se ha creado inicialmente una cadena de 20 caracteres el resto de las cadenas se ha visto como ha alineado una cadena la izquierda, derecha y centro de esos 20 caracteres.

## Uso avanzado de las f-string de Python

La interpolación de código permite incluir condiciones para que se incluya una u otra subcadena de texto dentro de la principal. Con lo que se puede personalizar los mensajes. Por ejemplo, en el caso de tener un objeto persona con una característica que sea el género, se puede personalizar el mensaje. Algo como lo que se muestra a continuación.

```python
person = {
    'name': 'Alice',
    'gender': 'female'
}
f'{"El usuario" if person.get("gender") == "male" else "La usuaria"} {person.get("name")} se encuentra en línea'
```

Con lo que se obtiene la cadena de texto 'La usuaria Alice se encuentra en línea'.

Nótese que para indicar una cadena dentro de la f-string es necesario emplear unas comillas diferentes a las principales. Esto es, si se crea el f-string con comillas sencillas es necesario usar comillas dobles dentro de este para indicar una cadena. Esto es lo que se hace en el ejemplo para indicar una cadena o acceder a los valores de un diccionario.

## Conclusiones

Las f-string de Python son una opción perfecta para crear cadenas de texto de forma dinámica. Siendo a la vez vaciles de escribir y leer, por lo que hace que el código resultante sea sencillo y fácil de mantener. Además, la posibilidad de incluir evaluar código dentro de las f-string hace que las posibilidades de estas sean casi ilimitadas. Siendo un método mucho más flexible que el uso de str para convertir valores numéricos en cadenas.
