a1805 Natalia Beatriz Diaz

e1401 Martin Nicolas Duarte

a1822 Cristian Patricio Salinas Talamilla

a1812 Ezequiel Eduardo Maudet

a1819 Manuel Pineyro

TP1: Algoritmos de búsqueda en Torre de Hanoi (18Co2024)

**Apertura:** jueves, 2 de mayo de 2024, 00:00

**Cierre:** domingo, 15 de septiembre de 2024, 23:59

En clase presentamos el problema de la torre de Hanoi. Además, vimos diferentes algoritmos de búsqueda que nos permitieron resolver este problema. Para este trabajo práctico, deberán implementar un método de búsqueda para resolver con 5 discos, del estado inicial y objetivo.

**Tareas y preguntas a resolver:**

1. ¿Cuáles son los PEAS de este problema? (Performance, Environment, Actuators, Sensors)
2. ¿Cuáles son las propiedades del entorno de trabajo?
3. En el contexto de este problema, establezca cuáles son los: estado, espacio de estados, árbol de búsqueda, nodo de búsqueda, objetivo, acción y frontera.
4. Implemente algún método de búsqueda. Puedes elegir cualquiera menos búsqueda en anchura primero (el desarrollado en clase). Sos libre de elegir cualquiera de los vistos en clases, o inclusive buscar nuevos.
5. A nivel implementación, ¿qué tiempo y memoria ocupa el algoritmo? (Se recomienda correr 10 veces y calcular promedio y desvío estándar de las métricas).
6. Si la solución óptima es 2k \-1 movimientos con k igual al número de discos. Qué tan lejos está la solución del algoritmo implementado de esta solución óptima (se recomienda correr al menos 10 veces y usar el promedio de trayecto usado).

El entregable es, por un lado, un archivo de txt/PDF/Word con las respuestas y por otro, los archivos con el código implementado, tambien pueden enviar una Notebook con el contenido y la solución. Si además agregan los json para usar en el simulador, es mejor. Pueden subir el contenido o proporcionar un enlace a un repositorio público (GitHub o GitLab) con el contenido. **No olvidar especificar en el entregable los autores del TP.**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**

**1**

**El problema de las Torres de Hanoi puede analizarse utilizando el marco PEAS (Performance, Environment, Actuators, Sensors), que es común en la inteligencia artificial para definir un agente racional. Aquí te explico los PEAS para este problema:**

### **1\. Performance (Desempeño):**

- **Criterios de rendimiento: El agente debe trasladar todos los discos desde la torre inicial hasta la torre objetivo siguiendo las reglas del problema:**
  - **Mover un disco a la vez.**
  - **No se puede colocar un disco más grande sobre uno más pequeño.**
- **Objetivos específicos: Minimizar el número de movimientos (que es 2n−12^n \- 12n−1 movimientos mínimos para nnn discos), y hacerlo en el menor tiempo posible, sin violar las reglas.**

### **2\. Environment (Entorno):**

- **El entorno incluye:**
  - **Tres torres (o postes).**
  - **Una cantidad determinada de discos de diferentes tamaños.**
- **Es un entorno discreto (las posiciones de los discos son fijas), determinístico (cada acción tiene un efecto predecible), estático (el entorno no cambia si el agente no hace nada) y completamente observable (el agente puede ver toda la configuración de los discos y torres en todo momento).**

### **3\. Actuators (Actuadores):**

- **Las acciones posibles del agente son mover un disco de una torre a otra, sujeto a las reglas del problema.**
- **El actuador principal es el movimiento de los discos, que se puede ver como una "mano" que toma un disco y lo coloca en otra torre.**

### **4\. Sensors (Sensores):**

- **Los sensores proporcionan información sobre:**
  - **El estado actual del juego, es decir, la posición de cada disco en las torres.**
- **El agente puede "ver" en todo momento la distribución actual de los discos en las torres y determinar cuál es el siguiente movimiento legal basado en esa información.**

**En resumen, un agente que resuelve el problema de las Torres de Hanoi utiliza esta información del entorno y sus sensores para ejecutar acciones que cumplan con los objetivos de rendimiento (minimizar movimientos y cumplir las reglas).**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**

**2**

**En el contexto del problema de las Torres de Hanoi, el entorno de trabajo tiene varias propiedades que pueden categorizarse de acuerdo con los criterios estándar utilizados en inteligencia artificial para analizar el entorno donde un agente opera. A continuación se describen las propiedades clave del entorno para este problema:**

### **1\. Totalmente observable vs. Parcialmente observable:**

- **Totalmente observable: El agente puede ver el estado completo del entorno en todo momento. En el caso de las Torres de Hanoi, el agente sabe siempre cuántos discos hay en cada torre y en qué orden están apilados. No hay información oculta.**

### **2\. Determinístico vs. Estocástico:**

- **Determinístico: El entorno es determinístico porque cualquier acción (mover un disco de una torre a otra) tiene un resultado predecible y siempre produce el mismo efecto. No hay incertidumbre en el resultado de las acciones.**

### **3\. Episódico vs. Secuencial:**

- **Secuencial: El problema es secuencial, ya que cada acción afecta al estado futuro del entorno y cada decisión afecta a las decisiones posteriores. Las acciones no son independientes entre sí.**

### **4\. Estático vs. Dinámico:**

- **Estático: El entorno es estático porque no cambia a menos que el agente realice una acción. No hay eventos que modifiquen el estado del entorno si el agente no hace nada.**

### **5\. Discreto vs. Continuo:**

- **Discreto: El entorno es discreto, ya que las posiciones posibles de los discos y las acciones (mover un disco de una torre a otra) son finitas y contables. Cada disco puede estar en una de las tres torres, y cada movimiento es una acción claramente definida.**

### **6\. Agente único vs. Multiagente:**

- **Agente único: Solo hay un agente que realiza las acciones en el entorno (mover los discos), por lo que no hay interacción con otros agentes. Es un entorno de agente único.**

### **Resumen de las propiedades del entorno:**

- **Totalmente observable: El estado completo es accesible en todo momento.**
- **Determinístico: Las acciones tienen resultados predecibles y no hay azar.**
- **Secuencial: Las acciones afectan el futuro estado del entorno.**
- **Estático: El entorno no cambia a menos que el agente realice una acción.**
- **Discreto: El número de posibles estados y acciones es finito y contable.**
- **Agente único: Solo un agente interactúa con el entorno.**

**Estas características permiten modelar el problema de las Torres de Hanoi de manera precisa y desarrollar algoritmos para resolverlo de forma eficiente.**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**

**3**

**En el contexto del problema de las Torres de Hanoi, podemos definir los elementos clásicos de los problemas de búsqueda, como el estado, espacio de estados, árbol de búsqueda, nodo de búsqueda, objetivo, acción y frontera, de la siguiente manera:**

### **1\. Estado:**

- **Un estado es una configuración completa de los discos en las tres torres. Cada estado indica la posición exacta de cada disco, es decir, en qué torre está y el orden en el que están apilados.**
- **Por ejemplo, un estado podría ser que todos los discos están en la torre inicial (posición de inicio), o que ciertos discos están distribuidos en las tres torres en un orden específico.**

### **2\. Espacio de estados:**

- **El espacio de estados es el conjunto de todas las configuraciones posibles de los discos en las tres torres.**
- **Para nnn discos, el número total de estados posibles es 3n3^n3n, ya que cada disco puede estar en una de las tres torres, independientemente de la posición de los demás. El espacio de estados crece exponencialmente a medida que aumenta el número de discos.**

### **3\. Árbol de búsqueda:**

- **El árbol de búsqueda es la representación de todas las secuencias posibles de movimientos desde el estado inicial hasta el estado objetivo.**
- **El nodo raíz del árbol es el estado inicial, donde todos los discos están apilados en una torre (generalmente la torre 1), y cada rama representa un movimiento legal de un disco de una torre a otra. Los nodos hijos son los estados resultantes de esos movimientos.**
- **Las hojas del árbol representan estados donde ya no se pueden hacer más movimientos o donde se ha alcanzado el objetivo.**

### **4\. Nodo de búsqueda:**

- **Un nodo de búsqueda es un punto en el árbol de búsqueda que representa un estado particular del problema. Cada nodo incluye:**
  - **El estado actual del problema.**
  - **El camino que se ha tomado para llegar a ese estado (es decir, la secuencia de acciones o movimientos).**
  - **El costo acumulado (en este caso, el número de movimientos realizados).**
  - **El nodo padre, que es el estado anterior que condujo al estado actual.**

### **5\. Objetivo:**

- **El objetivo del problema es lograr que todos los discos estén apilados en la torre de destino, respetando las reglas del juego (un disco más grande no puede estar sobre uno más pequeño, y solo se mueve un disco a la vez).**
- **El estado objetivo es aquel en el que todos los discos están en la torre final (generalmente la torre 3), en el mismo orden en que estaban en la torre inicial (de mayor a menor).**

### **6\. Acción:**

- **Una acción consiste en mover un disco de una torre a otra. Esta acción está restringida por las reglas del problema:**
  - **Solo se puede mover un disco a la vez.**
  - **Un disco solo puede colocarse en una torre vacía o sobre un disco más grande.**
- **Cada acción cambia el estado del problema, lo que se refleja en el árbol de búsqueda.**

### **7\. Frontera:**

- **La frontera (también llamada frontera de búsqueda) es el conjunto de nodos que han sido generados pero que aún no han sido explorados completamente. Es decir, son los estados a los que el agente podría moverse en los próximos pasos, pero cuyas secuencias de movimientos aún no han sido exploradas.**
- **En un algoritmo de búsqueda, la frontera es lo que se mantiene en una estructura de datos como una cola (FIFO o LIFO) dependiendo del tipo de búsqueda (en anchura o en profundidad).**

### **Ejemplo:**

- **Estado inicial: Todos los discos están en la torre 1\.**
- **Estado objetivo: Todos los discos están en la torre 3, apilados en orden de tamaño, con el disco más grande abajo.**
- **Acciones: Mover el disco más pequeño de la torre 1 a la torre 3, mover el segundo disco más pequeño de la torre 1 a la torre 2, etc.**
- **Frontera: Conjunto de movimientos posibles en el siguiente paso (los estados que surgen después de cada movimiento legal).**

**Estas definiciones permiten describir el problema de las Torres de Hanoi como un problema de búsqueda en un espacio de estados, con un árbol de búsqueda que explora todas las posibles soluciones respetando las reglas del problema.**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**

**4**

**LIFO (búsqueda en profundidad): Mas Rapida, Usa Menos Memoria pero la solucion no es la optima.**

**Ventajas: Menor uso de memoria, útil para soluciones profundas, más rápida para encontrar cualquier solución, fácil implementación recursiva. Desventajas: No garantiza la solución óptima y puede quedarse atrapada en ramas infinitas.**

**FIFO (búsqueda en anchura): Mas lenta, Usa Mas Memoria pero la solucion es la optima.**

**Ventajas: Garantiza encontrar la solución más corta (óptima) y no se queda atrapada en ramas infinitas. Desventajas: Usa más memoria y puede ser más lenta si la solución está en un nivel profundo. La elección entre LIFO y FIFO dependerá del tipo de problema que estés resolviendo y si te interesa encontrar la solución óptima o simplemente cualquier solución rápida.**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**

**5**

**GPU**

**19.9 ms ± 2.44 ms per loop (mean ± std. dev. of 7 runs, 10 loops each)**

**22.8 ms ± 918 µs per loop (mean ± std. dev. of 7 runs, 10 loops each)**

**15 ms ± 3.5 ms per loop (mean ± std. dev. of 7 runs, 100 loops each)**

**17.1 ms ± 5.42 ms per loop (mean ± std. dev. of 7 runs, 100 loops each)**

**TPU**

**12.1 ms ± 3.59 ms per loop (mean ± std. dev. of 7 runs, 100 loops each)**

**12.1 ms ± 3.15 ms per loop (mean ± std. dev. of 7 runs, 100 loops each)**

**12 ms ± 2.64 ms per loop (mean ± std. dev. of 7 runs, 100 loops each)**

**10.3 ms ± 507 µs per loop (mean ± std. dev. of 7 runs, 100 loops each)**

**11.6 ms ± 2.67 ms per loop (mean ± std. dev. of 7 runs, 100 loops each)**

**12 ms ± 2.93 ms per loop (mean ± std. dev. of 7 runs, 100 loops each)**

**11.6 ms ± 2.6 ms per loop (mean ± std. dev. of 7 runs, 100 loops each)**

**10.7 ms ± 534 µs per loop (mean ± std. dev. of 7 runs, 100 loops each)**

**11.6 ms ± 1.91 ms per loop (mean ± std. dev. of 7 runs, 100 loops each)**

**Máxima memoria ocupada: 0.26 \[MB\]**

**Máxima memoria ocupada: 0.26 \[MB\]**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**

**6**

**Solución 121 movimientos o caminos 3.90 veces más nodos que la solución mínima.**

**Explorando menos nodos en total 122\.**
