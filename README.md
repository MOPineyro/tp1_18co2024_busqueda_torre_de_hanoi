# Torre de Hanoi - Algoritmos de búsqueda (TP1)

## Información General

- **Curso:** 18Co2024
- **Apertura:** jueves, 2 de mayo de 2024, 00:00
- **Cierre:** domingo, 15 de septiembre de 2024, 23:59

## Integrantes del Grupo

- a1805 Natalia Beatriz Diaz
- e1401 Martin Nicolas Duarte
- a1822 Cristian Patricio Salinas Talamilla
- a1812 Ezequiel Eduardo Maudet
- a1819 Manuel Pineyro

## Descripción del Proyecto

Este trabajo práctico se centra en la implementación de algoritmos de búsqueda para resolver el problema de la Torre de Hanoi con 5 discos.

## Tareas y Preguntas

### 1. PEAS del problema

- **Performance (Desempeño):**
  - Criterios: Trasladar todos los discos siguiendo las reglas.
  - Objetivos: Minimizar el número de movimientos y el tiempo.
- **Environment (Entorno):**
  - Tres torres y discos de diferentes tamaños.
  - Entorno discreto, determinístico, estático y completamente observable.
- **Actuators (Actuadores):**
  - Mover un disco de una torre a otra.
- **Sensors (Sensores):**
  - Información sobre el estado actual del juego.

### 2. Propiedades del entorno de trabajo

- Totalmente observable
- Determinístico
- Secuencial
- Estático
- Discreto
- Agente único

### 3. Elementos del problema de búsqueda

- **Estado:** Configuración completa de los discos en las tres torres.
- **Espacio de estados:** Conjunto de todas las configuraciones posibles.
- **Árbol de búsqueda:** Representación de todas las secuencias posibles de movimientos.
- **Nodo de búsqueda:** Punto en el árbol que representa un estado particular.
- **Objetivo:** Lograr que todos los discos estén apilados en la torre de destino.
- **Acción:** Mover un disco de una torre a otra.
- **Frontera:** Conjunto de nodos generados pero no explorados completamente.

### 4. Implementación de métodos de búsqueda

Se analizaron dos métodos de búsqueda:

#### LIFO (búsqueda en profundidad)

- **Características:** Más rápida, usa menos memoria, pero la solución no es óptima.
- **Ventajas:**
  - Menor uso de memoria
  - Útil para soluciones profundas
  - Más rápida para encontrar cualquier solución
  - Fácil implementación recursiva
- **Desventajas:**
  - No garantiza la solución óptima
  - Puede quedarse atrapada en ramas infinitas

#### FIFO (búsqueda en anchura)

- **Características:** Más lenta, usa más memoria, pero la solución es óptima.
- **Ventajas:**
  - Garantiza encontrar la solución más corta (óptima)
  - No se queda atrapada en ramas infinitas
- **Desventajas:**
  - Usa más memoria
  - Puede ser más lenta si la solución está en un nivel profundo

**Nota:** La elección entre LIFO y FIFO dependerá del tipo de problema que se esté resolviendo y si interesa encontrar la solución óptima o simplemente cualquier solución rápida.

### 5. Tiempo y memoria del algoritmo

#### GPU

- Media: 18.7 ms
- Desviación estándar: 3.32 ms

#### TPU

- Media: 11.5 ms
- Desviación estándar: 2.44 ms

**Máxima memoria ocupada:** 0.26 [MB]

### 6. Comparación con la solución óptima

- Solución implementada: 121 movimientos
- Comparación: 3.90 veces más nodos que la solución mínima
- Nodos explorados en total: 122

## Entregables

- Archivo de texto Word con las respuestas
- Archivos con el código implementado
- Notebook con el contenido y la solución

## Notas adicionales

- Se puede proporcionar un enlace a un repositorio público (GitHub o GitLab) con el contenido.
- No olvidar especificar los autores del TP en el entregable.
