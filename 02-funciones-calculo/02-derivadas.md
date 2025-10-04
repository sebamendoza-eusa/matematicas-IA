# Diferenciación de funciones. Concepto de gradiente

## La derivada como herramienta de cambio

La derivada es una de las ideas más potentes del cálculo porque pone números a algo que percibimos a simple vista: **cómo cambia una cantidad cuando varía otra**. Si una función relaciona una entrada $x$ con una salida $f(x)$, la derivada nos dice qué tan rápido se modifica $f(x)$ cuando damos un pequeño paso en $x$.

La imagen más intuitiva es la de una **pendiente**. Si dibujamos la función en un gráfico, en cada punto podemos imaginar una recta tangente que toca la curva en ese lugar. La pendiente de esa recta es precisamente la derivada en ese punto. Si la pendiente es positiva, la función crece; si es negativa, decrece; si es cero, nos encontramos en un máximo, un mínimo o un punto de inflexión.

Un ejemplo sencillo es el de una recta $f(x)=2x+1$. Su pendiente es siempre $2$, y la derivada, en cualquier punto, es constante: $f'(x)=2$. En cambio, si tomamos una parábola como $f(x)=x^2$, la pendiente no es la misma en todas partes: en $x=1$ la curva sube con pendiente $2$, en $x=2$ sube con pendiente $4$, y en $x=-1$ baja con pendiente $-2$. La derivada $f'(x)=2x$ refleja exactamente esa variación.

Las **reglas de derivación** nos permiten calcular rápidamente estas pendientes locales sin tener que volver a la definición con límites. Algunas de las más básicas son:

- La derivada de una constante es $0$, porque no cambia nunca.
- La derivada de $x^n$ es $nx^{n-1}$, lo que nos da la regla general para potencias.
- La derivada de una suma es la suma de derivadas: $(f+g)'=f'+g'$.
- La derivada de un producto o un cociente tiene sus propias fórmulas, que veremos con calma más adelante.

Lo importante es comprender la idea de fondo: **derivar es medir la velocidad del cambio local**. Igual que en física la velocidad instantánea nos dice qué tan rápido se mueve un objeto en un momento preciso, la derivada de una función nos dice qué tan rápido sube o baja en un punto concreto.

Geométricamente, si ampliamos mucho la curva alrededor de un punto, esta se parece a una línea recta. Esa recta es la **tangente**, y su pendiente es el valor de la derivada en ese punto. En inteligencia artificial esta idea se vuelve crucial, porque los algoritmos de optimización necesitan saber hacia dónde “moverse” y con qué rapidez ajustar los parámetros. El gradiente, que veremos más adelante, no es otra cosa que la generalización de esta pendiente a funciones de varias variables.

> **Para reflexionar...**\
> Cuando piensas en la derivada como una pendiente local, ¿cómo cambia tu forma de ver una función? ¿Qué significa, en términos de comportamiento de un modelo, que la pendiente sea muy grande en una zona concreta o que se anule en otra?

### La derivada como sensibilidad y herramienta de aprendizaje

La derivada, además de ser una herramienta que refleja como cambia una función, en el contexto de la inteligencia artificial es una forma de medir **sensibilidad**. Si tenemos una función $f(x)$, su derivada $f'(x)$ en un punto nos dice cuánto cambia la salida al variar ligeramente la entrada. En términos más cotidianos, es como comprobar cuánto afecta girar un poco un mando de volumen: ¿el sonido cambia mucho o apenas nada? Esa idea es la misma en los modelos de IA: la derivada nos indica cuánto se altera la predicción del modelo si modificamos un poco uno de sus parámetros. Una derivada grande implica que ese parámetro influye fuertemente en el resultado; una derivada pequeña, que apenas lo hace.

La derivada también actúa como **herramienta de ajuste**. Al conocer la pendiente de la función en un punto, sabemos en qué dirección movernos para reducir su valor. Si la pendiente es positiva, al desplazarnos hacia la izquierda la función disminuye; si es negativa, el descenso ocurre hacia la derecha. Este principio se traduce directamente en el descenso de gradiente, el algoritmo de optimización más utilizado en aprendizaje automático: los parámetros del modelo “caminan” paso a paso en la dirección contraria a la pendiente, acercándose a un mínimo de error. Así, la derivada funciona como una brújula que siempre señala hacia dónde movernos para mejorar.

Aunque hasta ahora hemos trabajado con funciones de una sola variable, en la práctica los modelos dependen de cientos, miles o incluso millones de parámetros. En ese caso, la derivada se generaliza al gradiente, que no es más que un vector donde cada componente recoge la pendiente respecto a uno de los parámetros. El gradiente concentra toda la información de sensibilidad de la función en varias direcciones a la vez y guía las actualizaciones en el espacio multidimensional de parámetros. Esa noción es fundamental para entender cómo se entrenan redes neuronales complejas: cada paso de aprendizaje consiste en calcular el gradiente y usarlo como instrucción para ajustar todos los parámetros en la dirección adecuada.

> **Para reflexionar...**\
> ¿Cómo cambia tu percepción de la derivada al pensarla como una brújula práctica que orienta los pasos del aprendizaje automático, en lugar de como un número aislado en un ejercicio de matemáticas?

## Derivadas parciales y gradiente

Hasta ahora hemos considerado funciones de una sola variable, pero en la práctica de la inteligencia artificial la mayoría de los problemas son **multivariables**. Un modelo depende de muchos parámetros, y la función de error que queremos minimizar (la que mide la diferencia entre predicciones y datos reales) depende de todos ellos a la vez.

En este contexto hablamos de **derivadas parciales**. Para una función de dos variables $f(x,y)$, la derivada parcial respecto a $x$ se escribe $\tfrac{\partial f}{\partial x}$ y nos dice cómo cambia $f$ si variamos $x$ manteniendo fijo $y$. De forma análoga, $\tfrac{\partial f}{\partial y}$ mide el cambio al variar $y$ manteniendo fijo $x$. La idea se extiende a tantas variables como necesitemos: cada derivada parcial captura la **sensibilidad local** de la función a un solo parámetro, con los demás congelados.

Al reunir todas esas derivadas parciales en un único objeto obtenemos el **gradiente**:

$$
\nabla f(x_1,x_2,\dots,x_n)=
\left( \frac{\partial f}{\partial x_1},\frac{\partial f}{\partial x_2},\dots,\frac{\partial f}{\partial x_n} \right).
$$

El gradiente no es un número, sino un vector, y tiene una interpretación geométrica muy clara: **apunta en la dirección en la que la función crece más rápidamente.** Dicho de otro modo, si en el espacio de parámetros das un paso en la dirección del gradiente, $f$ aumentará lo máximo posible; si avanzas en la dirección contraria, $f$ disminuirá lo más rápido posible.

Esta idea tiene una aplicación directa en la IA: el **descenso de gradiente**. Los parámetros de un modelo se actualizan en pasos sucesivos desplazándose en la dirección contraria al gradiente de la función de error. Cada actualización equivale a moverse “cuesta abajo” en el paisaje de la función, buscando valles donde el error sea mínimo. Así, el gradiente actúa como guía que indica hacia dónde y con qué fuerza hay que ajustar los parámetros en cada iteración.

Con un ejemplo sencillo, si la función de error de un modelo depende de dos parámetros $w_1$ y $w_2$, podemos representarla como una superficie en tres dimensiones. En cada punto de esa superficie, el gradiente es una flecha que apunta hacia la máxima pendiente de subida. El algoritmo de optimización simplemente toma el camino opuesto, bajando la ladera hasta llegar a un valle. Ese valle corresponde a los valores de parámetros donde el modelo se ajusta mejor a los datos.

> **Para reflexionar...**\
> ¿Por qué crees que en lugar de buscar directamente el mínimo, los algoritmos de aprendizaje se conforman con seguir paso a paso la dirección opuesta al gradiente? ¿Qué ventajas tiene moverse con esta brújula local en problemas con miles o millones de parámetros?

## Optimización y descenso de gradiente

El concepto de derivada nos conduce de manera natural a la idea de **optimización**, es decir, a encontrar el punto en el que una función alcanza su mínimo o su máximo. En inteligencia artificial lo que nos interesa es, casi siempre, el mínimo: buscamos los valores de los parámetros de un modelo que reducen al máximo el **error** entre lo que el modelo predice y lo que los datos muestran.

La intuición más clara es imaginar la función de error como un **paisaje montañoso**. Cada punto del terreno representa un conjunto de parámetros, y la altura en ese punto representa el error. El objetivo es descender hasta un valle lo más profundo posible, porque allí el error es bajo y el modelo se ajusta bien a los datos.

Aquí es donde la derivada y el gradiente desempeñan su papel. En una dimensión, la derivada te indica si la función sube o baja al mover ligeramente el parámetro, y cuánto cambia. En varias dimensiones, el **gradiente** es la flecha que apunta hacia la subida más pronunciada del terreno. Si seguimos el gradiente subimos la montaña; si caminamos en la dirección contraria, bajamos. Este es el principio del **descenso de gradiente**.

El algoritmo consiste en moverse paso a paso en dirección contraria al gradiente, con un tamaño de paso controlado por la llamada **tasa de aprendizaje**. Un paso demasiado grande puede hacer que “rebotemos” y salgamos del valle; uno demasiado pequeño nos hará avanzar con lentitud. El equilibrio entre ambos es lo que determina la eficacia del entrenamiento.

En el **entrenamiento de modelos de machine learning**, cada iteración calcula el gradiente de la función de error con respecto a todos los parámetros y luego actualiza cada uno en la dirección contraria. Repetido muchas veces, este proceso ajusta la red de manera que el error desciende y el modelo aprende los patrones de los datos.

Esta estrategia es tan poderosa porque, incluso en espacios con miles o millones de dimensiones, el gradiente sigue siendo una brújula local que señala el camino más prometedor. Aunque no garantiza llegar al valle absoluto más profundo (el mínimo global), en la práctica basta con encontrar un valle suficientemente bajo donde el modelo funcione bien.

> **Para reflexionar...**\
> Si el gradiente solo nos da información local, ¿qué problemas pueden surgir al entrenar un modelo en paisajes de error con muchos valles y colinas? ¿Cómo crees que se pueden diseñar estrategias para evitar quedarse atrapado en un valle poco profundo?
