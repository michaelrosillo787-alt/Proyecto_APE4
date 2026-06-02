# APE 4 — Grafos: Mapa del Campus UTA

## Integrantes

Grupo 8 — Estructura de Datos

## Descripción

Este proyecto implementa un grafo mediante listas de adyacencia para representar diferentes ubicaciones dentro del Campus Huachi de la Universidad Técnica de Ambato (UTA).

El objetivo principal es comparar el comportamiento de dos algoritmos de búsqueda de rutas:

* BFS (Breadth-First Search)
* Dijkstra

Ambos algoritmos permiten encontrar caminos entre dos ubicaciones del campus, pero utilizan criterios diferentes para determinar la mejor ruta.

---

## Estructura del Grafo

Los nodos representan lugares del campus:

* Universidad
* FISEI
* Idiomas
* Biblioteca
* Estadio
* Comedor

Las aristas representan caminos entre estos lugares y poseen un peso asociado que representa la distancia.

Ejemplo:

Universidad → FISEI = 50 m

FISEI → Idiomas = 40 m

Idiomas → Biblioteca = 30 m

Biblioteca → Estadio = 70 m

Universidad → Comedor = 20 m

Comedor → Estadio = 200 m

---

## Modificaciones Realizadas

Se completaron los métodos marcados como `TODO` en el archivo `APE4_Grafos.java`.

### 1. Método agregarNodo()

Se implementó la creación de nuevos nodos dentro del grafo.

Funciones realizadas:

* Crear un objeto Nodo.
* Guardarlo en la colección de nodos.
* Inicializar su lista de adyacencia.

Código implementado:

```java
nodos.put(id, new Nodo(id, nombre));
adyacencia.put(id, new ArrayList<>());
```

---

### 2. Método agregarArista()

Se implementó la creación de conexiones entre nodos.

Características:

* Grafo no dirigido.
* Cada conexión se registra en ambos sentidos.
* Permite almacenar el peso o distancia.

Código implementado:

```java
adyacencia.get(origen)
    .add(new Arista(destino, peso));

adyacencia.get(destino)
    .add(new Arista(origen, peso));
```

---

### 3. Algoritmo BFS

Se implementó la búsqueda en amplitud (Breadth-First Search).

Objetivo:

Encontrar la ruta con la menor cantidad de paradas o saltos entre dos ubicaciones.

Características:

* Utiliza una cola (Queue).
* Mantiene una lista de nodos visitados.
* Explora primero todos los vecinos cercanos.

Resultado esperado:

Universidad → Comedor → Estadio

Esta ruta tiene menos paradas, aunque no necesariamente la menor distancia.

---

### 4. Algoritmo Dijkstra

Se implementó el algoritmo de caminos mínimos de Dijkstra.

Objetivo:

Encontrar la ruta con la menor distancia total.

Características:

* Utiliza una cola de prioridad.
* Mantiene un registro de distancias mínimas.
* Guarda los nodos anteriores para reconstruir la ruta final.

Resultado esperado:

Universidad → FISEI → Idiomas → Biblioteca → Estadio

Aunque posee más paradas, la distancia total es menor.

---

## Comparación de Algoritmos

### BFS

Criterio:

Menor número de paradas.

Ruta encontrada:

Universidad → Comedor → Estadio

Cantidad de saltos:

2

Distancia total:

220 metros

---

### Dijkstra

Criterio:

Menor distancia acumulada.

Ruta encontrada:

Universidad → FISEI → Idiomas → Biblioteca → Estadio

Cantidad de saltos:

4

Distancia total:

190 metros

---

## Resultado Esperado

Al ejecutar el programa se debe obtener una salida similar a:

```text
===== BFS =====
Universidad (uta) -> Comedor (comedor) -> Estadio (estadio)

===== DIJKSTRA =====
Universidad (uta) -> FISEI (fisei) -> Idiomas (idiomas) -> Biblioteca (biblioteca) -> Estadio (estadio)
```

---

## Compilación

Compilar el proyecto:

```bash
javac APE4_Grafos.java
```

---

## Ejecución

Ejecutar el programa:

```bash
java APE4_Grafos
```

---

## Conclusiones

* La lista de adyacencia permite representar grafos de manera eficiente.
* BFS encuentra rutas con menos paradas, pero no considera las distancias.
* Dijkstra encuentra rutas óptimas considerando los pesos de las aristas.
* Ambos algoritmos son útiles dependiendo del criterio de optimización requerido.
* El proyecto permite comprender aplicaciones reales de los grafos en sistemas de navegación y planificación de rutas.

---

## Estructura del Proyecto

```text
Proyecto_APE4/
│
├── src/
│   └── APE4_Grafos.java
│
├── captura/
│   ├── captura1.png
│   ├── captura2.png
│   └── captura3.png
│
└── README.md
```
