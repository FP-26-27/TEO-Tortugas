# Ejercicios: Carrera de tortugas
Autor: Toñi Reina

## Ejercicio 1
Implementa una función ```tortugas``` para simular una carrera de dos tortugas que están compitiendo en una carrera. Cada tortuga comienza en la posición 0, pero avanzan a diferentes velocidades. Tu objetivo es simular la carrera y mostrar quién llega primero a la meta, que está en la posición que se pasa como parámetro a la función.

Reglas:

- La tortuga A avanza 1 ó 2 pasos aleatorios en cada turno.
- La tortuga B avanza 1, 2, ó 3 pasos aleatorios en cada turno.
- El bucle `while` debe ejecutarse hasta que una de las tortugas llegue a la posición de la meta (o más).
- En cada iteración del bucle, el programa debe mostrar las posiciones actuales de ambas tortugas.

Instrucciones:

- Usa la estructura `while` para hacer que las tortugas avancen mientras ninguna ha alcanzado la meta.
- Usa la función `random.randint()` para generar de forma aleatoria el número de pasos que avanzan. Por ejemplo, `random.randint(1,3)` genera un número aleatorio entre 1 y 3, ambos inclusive.
- Al finalizar el bucle, indica qué tortuga ganó o si fue un empate.

Ejemplos de ejecuciones son las siguientes:

- La meta está en la posición 10 y gana la tortuga B.
```python
    >>tortuga(10)
    Tortuga A está en 2, Tortuga B está en 1
    Tortuga A está en 3, Tortuga B está en 4
    Tortuga A está en 4, Tortuga B está en 5
    Tortuga A está en 6, Tortuga B está en 7
    Tortuga A está en 8, Tortuga B está en 10
    ¡Tortuga B ganó!
```
- La meta está en la posición 3 y hay un empate.
```python
    >>tortuga(3)
    Tortuga A está en 2, Tortuga B está en 1
    Tortuga A está en 3, Tortuga B está en 4
    ¡Es un empate!
```
 - La meta está en la posición 3 y gana la tortuga A.
```python
    >> tortugas(3)
    Tortuga A está en 2, Tortuga B está en 1
    Tortuga A está en 4, Tortuga B está en 2
    ¡Tortuga A ganó!
```


## Ejercicio 2: 

Implementa una segunda versión de la simulación llamada `tortuga_con_sorpresas`, que además de la meta tiene como parámetro una probabilidad (un número entre 0 y 1), que indica la probabilidad de que una tortuga resbale en la carrera y retroceda una serie de casillas de forma aleatoria.

Instrucciones:

- Probabilidad de resbalón:  Para implementar esto genere un número entre 0 y 1. Por ejemplo, si la probabilidad de resbalón es del 5% y el número aleatorio que ha generado número es menor que 0.05, significa que la tortuga ha resbalado. Usa `random.random()`para generar un número aleatorio entre 0 y 1.
- El número de pasos que retrocede la tortuga también debe ser aleatorio. 
- Las tortugas no pueden retroceder a posiciones negativas. Use la función`max(0, posicion)`, que devolverá 0 si posicion tiene un valor negativo, en otro caso devolverá posición, ya que max devuelve el máximo de dos números.


Ejemplos de ejecuciones son las siguientes:

- La meta está en la posición 10 y hay un 20% de probabilidad de resbalón.
    ```python
    >>tortuga_con_sorpresas(10, 0.2)
    Tortuga A está en 2, Tortuga B está en 3
    Tortuga A está en 4, Tortuga B está en 6
    Tortuga A está en 3, Tortuga B está en 8   # (Tortuga A resbaló)
    Tortuga A está en 5, Tortuga B está en 10
    ¡Tortuga B ganó!
    ```
- La meta está en la posición 5 y hay un 50% de probabilidad de resbalón.
  
    ``python
    >>tortuga_con_sorpresas(5, 0.5)
    Tortuga A está en 2, Tortuga B está en 1
    Tortuga A está en 3, Tortuga B está en 2
    Tortuga A está en 5, Tortuga B está en 4
    ¡Tortuga A ganó!

- La meta está en la posición 3 y hay un 30% de probabilidad de resbalón.
    ```python
    >>tortuga_con_sorpresas(3, 0.3)
    Tortuga A está en 2, Tortuga B está en 1
    Tortuga A está en 3, Tortuga B está en 4
    ¡Es un empate!
    '''

## Ejercicio 3: Carrera de tortugas modularizada

En esta tercera versión vamos a reorganizar el código de la carrera de tortugas para hacerlo más claro, reutilizable y fácil de mantener. La idea es modularizar el programa dividiendo la lógica en funciones auxiliares que realicen tareas concretas: avanzar tortugas, aplicar resbalones, mostrar posiciones y anunciar al ganador.

De esta forma:
1. Se evita la repetición de código entre la versión básica y la versión con sorpresas.
2. Cada función tiene una única responsabilidad, lo que hace que el código sea más legible.
3. Es más fácil de ampliar: por ejemplo, si quisiéramos añadir más tortugas, diferentes reglas de avance o nuevas sorpresas, bastaría con modificar una parte sin tocar todo el programa.

En un módulo llamado `tortuga_modular.py` implementa de nuevo las funciones `tortuga` y `tortuga_con_sorpresas` haciendo uso de las siguientes funciones auxiliares:

- `avanzar_tortuga` que, dadas la posición actual de una tortuga y el número máximo de pasos que puede avanzar, devuelva la nueva posición de la tortuga.
- `resbalar` que, dadas la posición actual de una tortuga, la probabilidad de resbalón, y el número máximo de pasos que puede retroceder, devuelva la nueva posición de la tortuga. Ten en cuenta que la nueva posición nunca puede ser negativa.
- `mostrar_posiciones` que, dadas las posiciones de las dos tortugas, muestre por consola un mensaje que indique en qué posición está cada tortuga. Por ejemplo, "Tortuga A está en 2, Tortuga B está en 5".
- `anunciar_ganador` que, dadas las posiciones de las dos tortugas y la posición de la meta, muestre un mensaje con el resultado final de la carrera.
