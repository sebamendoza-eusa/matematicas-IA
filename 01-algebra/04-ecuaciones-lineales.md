# Sistemas de ecuaciones lineales

## Qué es un sistema de ecuaciones lineales

Un sistema de ecuaciones lineales aparece siempre que tenemos varias incógnitas y, al mismo tiempo, distintas condiciones que deben cumplirse de forma simultánea. Cada condición se expresa como una ecuación lineal, es decir, una ecuación en la que las incógnitas aparecen elevadas a la primera potencia y combinadas mediante sumas y multiplicaciones.

Un ejemplo sencillo es el siguiente:

$$
\begin{cases}
x + y = 10 \\
2x - y = 3
\end{cases}
$$

Aquí se busca encontrar valores de $x$ e $y$ que satisfagan ambas ecuaciones a la vez. Resolver el sistema no significa resolver cada ecuación por separado, sino identificar el punto que es común a las dos condiciones.

La interpretación geométrica nos ayuda a entender mejor el problema. Cada ecuación representa una recta en el plano, y la solución es el punto donde ambas rectas se cortan. En tres dimensiones, un sistema de tres ecuaciones con tres incógnitas representa tres planos, y la solución sería el punto en el que los tres planos coinciden. Cuando el número de dimensiones aumenta, la idea se generaliza: cada ecuación define un hiperplano, y resolver el sistema significa encontrar la intersección de todos ellos.

Este planteamiento muestra que resolver sistemas lineales es, en esencia, un problema de geometría: buscar la posición en el espacio que satisface simultáneamente todas las restricciones. De este modo, los sistemas lineales se convierten en una herramienta fundamental para modelar situaciones en las que varias condiciones deben cumplirse al mismo tiempo, algo que aparece de forma natural en aplicaciones de la inteligencia artificial.



>**Para reflexionar…**
>**¿Qué significa, desde un punto de vista geométrico, que un sistema no tenga solución? ¿Podría interpretarse como que las restricciones que imponemos a los datos son incompatibles entre sí?**

## Representación matricial de un sistema

Una de las ventajas del álgebra lineal es que nos permite expresar problemas aparentemente complejos de una forma compacta y elegante. Esto ocurre con los sistemas de ecuaciones lineales, que pueden escribirse en forma **matricial**.

Si un sistema tiene varias ecuaciones y varias incógnitas, podemos organizar los coeficientes en una **matriz de coeficientes**, las incógnitas en un **vector de variables** y los resultados en un **vector independiente**. De este modo, un sistema como

$$
\begin{cases}
x + y = 10 \\
2x - y = 3
\end{cases}
$$

se reescribe como

$$
\begin{bmatrix}
1 & 1 \\
2 & -1
\end{bmatrix}
\begin{bmatrix}
x \\
y
\end{bmatrix}
=
\begin{bmatrix}
10 \\
3
\end{bmatrix}.
$$

La expresión general de un sistema de este tipo es

$$
\mathbf{A}\mathbf{x} = \mathbf{b},
$$

donde $\mathbf{A}$ es la matriz de coeficientes, $\mathbf{x}$ es el vector de incógnitas y $\mathbf{b}$ el vector de resultados.

Esta forma matricial no solo simplifica la escritura, sino que también abre la puerta al uso de todas las herramientas del álgebra lineal. Resolver un sistema se convierte en estudiar si la transformación definida por $\mathbf{A}$ puede llevarnos al vector $\mathbf{b}$. Desde este punto de vista, las soluciones son el conjunto de vectores $\mathbf{x}$ que, al transformarse por $\mathbf{A}$, producen exactamente $\mathbf{b}$.

La notación matricial conecta de manera natural con el trabajo en inteligencia artificial, donde la mayoría de los algoritmos se formulan precisamente en términos de productos de matrices y vectores. Así, lo que en un curso introductorio de matemáticas es un método de simplificación, en IA se convierte en la forma natural de pensar los problemas.



>**Para reflexionar…**
>**¿Qué ventajas aporta expresar un sistema en forma matricial frente a mantenerlo como un conjunto de ecuaciones por separado? ¿Cómo puede esto ayudarnos a conectar con los cálculos que ya realizan los ordenadores de manera optimizada?**



El ejemplo con dos ecuaciones y dos incógnitas nos da una primera intuición, pero el verdadero poder de la notación matricial aparece cuando extendemos el planteamiento a un sistema de **$n$ ecuaciones con $n$ incógnitas**.

En forma desarrollada, un sistema lineal general puede escribirse como

$$
\begin{cases}
a_{11}x_1 + a_{12}x_2 + \dots + a_{1n}x_n = b_1 \\
a_{21}x_1 + a_{22}x_2 + \dots + a_{2n}x_n = b_2 \\
\hspace{1.2cm} \vdots \\
a_{n1}x_1 + a_{n2}x_2 + \dots + a_{nn}x_n = b_n
\end{cases}
$$

donde cada $a_{ij}$ es un coeficiente, $x_j$ son las incógnitas y $b_i$ los términos independientes.

Toda esta información puede organizarse de manera compacta en la notación matricial:

$$
\mathbf{A}\mathbf{x} = \mathbf{b},
$$

donde

$$
\mathbf{A} =
\begin{bmatrix}
a_{11} & a_{12} & \dots & a_{1n} \\
a_{21} & a_{22} & \dots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{n1} & a_{n2} & \dots & a_{nn}
\end{bmatrix}, \quad
\mathbf{x} =
\begin{bmatrix}
x_1 \\
x_2 \\
\vdots \\
x_n
\end{bmatrix}, \quad
\mathbf{b} =
\begin{bmatrix}
b_1 \\
b_2 \\
\vdots \\
b_n
\end{bmatrix}.
$$

La ecuación $\mathbf{A}\mathbf{x} = \mathbf{b}$ condensa en una sola expresión lo que antes necesitábamos escribir con muchas ecuaciones. Desde el punto de vista algebraico, significa que la matriz $\mathbf{A}$ actúa como una **transformación lineal** que lleva al vector $\mathbf{x}$ hasta el vector $\mathbf{b}$. Resolver el sistema consiste en encontrar ese vector $\mathbf{x}$, si existe.

Esta notación es mucho más que un atajo. Permite aplicar directamente conceptos como determinante, rango o inversa para estudiar la existencia y unicidad de soluciones. Además, conecta con el modo en que los algoritmos de IA manejan la información: cada conjunto de parámetros de un modelo se organiza en matrices, y el entrenamiento consiste en resolver, de forma directa o aproximada, expresiones que no son otra cosa que sistemas lineales de gran tamaño.



>**Para reflexionar…**
>**¿Qué significa, en términos de transformación lineal, que la ecuación $\mathbf{A}\mathbf{x} = \mathbf{b}$ no tenga solución? ¿Podría interpretarse como que el vector $\mathbf{b}$ no pertenece al espacio generado por las columnas de $\mathbf{A}$?**



## Tipos de soluciones y condiciones de existencia

No todos los sistemas de ecuaciones lineales se comportan de la misma manera. En algunos casos encontramos una única solución clara, en otros existen infinitas posibilidades y a veces ni siquiera es posible hallar una solución. El álgebra lineal nos da criterios precisos para identificar cada situación.

Cuando un sistema tiene **una única solución**, decimos que es un sistema **compatible determinado**. Geométricamente, en el plano significa que dos rectas se cruzan en un único punto, o en el espacio tridimensional que tres planos coinciden en un punto común. En general, en dimensiones más altas equivale a que todos los hiperplanos definidos por las ecuaciones se intersectan en un único vector.

En contraste, un sistema puede ser **compatible indeterminado**, lo que ocurre cuando hay **infinitas soluciones**. En el plano, esto sucede cuando dos rectas son la misma; en tres dimensiones, cuando los planos coinciden parcialmente a lo largo de una línea o un plano entero. En términos algebraicos, significa que las ecuaciones no aportan información suficiente para fijar un único valor a cada incógnita, de modo que algunas variables quedan libres.

El tercer escenario es el de los sistemas **incompatibles**, que no tienen solución. En el plano, se ve fácilmente cuando dos rectas son paralelas y nunca se cruzan. En espacios de más dimensiones ocurre cuando las condiciones impuestas por las ecuaciones se contradicen entre sí, haciendo imposible encontrar un vector que satisfaga todas al mismo tiempo.

El álgebra lineal nos proporciona criterios para reconocer estos casos. El más importante es el **rango de la matriz de coeficientes**, comparado con el rango de la matriz ampliada (la que incluye también los términos independientes). Si ambos rangos coinciden, el sistema es compatible; si además ese rango es máximo (igual al número de incógnitas), la solución es única. Si los rangos difieren, el sistema es incompatible.

Otra herramienta clave es el **determinante** en el caso de matrices cuadradas. Cuando $\det(\mathbf{A}) \neq 0$, la matriz es invertible y el sistema $\mathbf{A}\mathbf{x} = \mathbf{b}$ tiene solución única. Si el determinante es cero, la situación es más delicada: el sistema puede tener infinitas soluciones o ninguna, dependiendo de la relación entre las ecuaciones.

Esta clasificación no es solo un ejercicio teórico. En IA, cuando entrenamos un modelo, muchas veces estamos resolviendo sistemas enormes. Saber si el sistema tiene solución única, infinitas o ninguna es lo que determina si el modelo puede aprender de los datos, si existen redundancias o si las restricciones que imponemos son imposibles de satisfacer.



>**Para reflexionar…**
>**¿Qué interpretación intuitiva tiene el hecho de que un sistema sea incompatible? ¿Podría verse como que intentamos imponer a los datos condiciones contradictorias que ningún vector puede cumplir a la vez?**

### Ejemplos de discusión de sistemas de ecuaciones usando matrices

Para ver cómo la teoría de sistemas de ecuaciones se aplica más allá de dos incógnitas, consideremos un sistema con tres variables. En este caso, cada ecuación representa un plano en el espacio tridimensional, y resolver el sistema equivale a encontrar el punto donde se cruzan esos planos.

#### Caso 1: sistema con solución única

Tomemos el sistema

$$
\begin{cases}
x + y + z = 6 \\
2x - y + z = 3 \\
x + 2y - z = 4
\end{cases}
$$

En forma matricial:

$$
\mathbf{A} =
\begin{bmatrix}
1 & 1 & 1 \\
2 & -1 & 1 \\
1 & 2 & -1
\end{bmatrix}, \quad
\mathbf{x} =
\begin{bmatrix}
x \\ y \\ z
\end{bmatrix}, \quad
\mathbf{b} =
\begin{bmatrix}
6 \\ 3 \\ 4
\end{bmatrix}.
$$

La ecuación compacta es $\mathbf{A}\mathbf{x} = \mathbf{b}$.

El determinante de $\mathbf{A}$ es distinto de cero, lo que garantiza que $\mathbf{A}$ es invertible. Por tanto, existe una única solución. Geométricamente, los tres planos definidos por las ecuaciones se cruzan en un único punto del espacio.



#### Caso 2: sistema con infinitas soluciones

Consideremos ahora

$$
\begin{cases}
x + y + z = 6 \\
2x + 2y + 2z = 12 \\
x - y = 0
\end{cases}
$$

La representación matricial es

$$
\mathbf{A} =
\begin{bmatrix}
1 & 1 & 1 \\
2 & 2 & 2 \\
1 & -1 & 0
\end{bmatrix}, \quad
\mathbf{b} =
\begin{bmatrix}
6 \\ 12 \\ 0
\end{bmatrix}.
$$

Aquí la segunda ecuación es múltiplo de la primera, lo que significa que en realidad solo tenemos dos condiciones independientes para tres incógnitas. El rango de la matriz de coeficientes es menor que el número de variables, lo que implica infinitas soluciones. Geométricamente, los planos se cruzan a lo largo de una recta: cualquier punto de esa recta es solución.



#### Caso 3: sistema sin solución

Por último, observemos

$$
\begin{cases}
x + y + z = 6 \\
2x + 2y + 2z = 15 \\
x - y = 0
\end{cases}
$$

En este caso, la segunda ecuación contradice a la primera (los planos son paralelos pero no coinciden). La matriz ampliada $\begin{bmatrix} \mathbf{A} ,|, \mathbf{b}\end{bmatrix}$ tiene rango mayor que la matriz de coeficientes, lo que indica que no existe ninguna solución. En el espacio, los planos no llegan a encontrarse en ningún punto común.



Estos tres casos muestran cómo la notación matricial simplifica la discusión. Basta con observar el rango de la matriz de coeficientes y compararlo con el rango de la matriz ampliada:

* Si los rangos coinciden y son máximos, hay solución única.
* Si coinciden pero no son máximos, hay infinitas soluciones.
* Si difieren, no hay solución.

En inteligencia artificial, esta discusión se traduce a una pregunta práctica: ¿tienen los datos la suficiente información para identificar de manera única los parámetros de un modelo? O, por el contrario, ¿existen redundancias o contradicciones que hacen que el sistema sea indeterminado o imposible de resolver?



>**Para reflexionar…**
>**¿Qué implicaciones crees que tiene, en el contexto de un modelo de IA, que los datos den lugar a un sistema con infinitas soluciones? ¿Y qué significado tendría que el sistema fuera incompatible?**



## Métodos matriciales de resolución de sistemas

El álgebra lineal ofrece herramientas específicas para resolver sistemas de ecuaciones de manera compacta y eficiente. En lugar de métodos elementales como sustitución o reducción manual, lo que resulta verdaderamente útil en inteligencia artificial son los **métodos matriciales**, ya que son los que permiten escalar los cálculos a cientos o miles de variables.

El punto de partida es siempre la representación compacta del sistema:

$$
\mathbf{A}\mathbf{x} = \mathbf{b}.
$$

Resolver el sistema significa encontrar el vector $\mathbf{x}$ que satisface esta igualdad.

### Resolución mediante la inversa

Cuando la matriz $\mathbf{A}$ es cuadrada e invertible, la solución puede escribirse de manera directa como

$$
\mathbf{x} = \mathbf{A}^{-1}\mathbf{b}.
$$

Esta fórmula tiene un valor teórico muy importante porque muestra que la solución existe y es única siempre que $\det(\mathbf{A}) \neq 0$. Sin embargo, en la práctica rara vez se utiliza el cálculo explícito de la inversa, ya que resulta costoso y numéricamente inestable en sistemas grandes.

### Método de Gauss-Jordan

Una alternativa mucho más práctica es el método de **Gauss-Jordan**, que consiste en aplicar transformaciones elementales por filas hasta reducir la matriz aumentada $[\mathbf{A} ,|, \mathbf{b}]$ a una forma equivalente en la que la solución se lee directamente.

Este procedimiento es sistemático y puede implementarse fácilmente en un ordenador, lo que lo convierte en la base de muchos algoritmos numéricos. Además, permite detectar con claridad si un sistema es indeterminado o incompatible, ya que en el proceso de reducción aparecen filas nulas o inconsistencias.

### Descomposición LU

Otra estrategia muy utilizada en la práctica es la **descomposición LU**, que consiste en escribir la matriz de coeficientes como el producto de una matriz triangular inferior $\mathbf{L}$ y una matriz triangular superior $\mathbf{U}$:

$$
\mathbf{A} = \mathbf{L}\mathbf{U}.
$$

Con esta factorización, el sistema original se resuelve en dos pasos: primero se resuelve $\mathbf{L}\mathbf{y} = \mathbf{b}$ y luego $\mathbf{U}\mathbf{x} = \mathbf{y}$. Como las matrices triangulares son mucho más fáciles de manejar, el procedimiento resulta más eficiente que calcular la inversa.

### Métodos avanzados: QR y SVD

En contextos más complejos, como los sistemas sobredeterminados (cuando hay más ecuaciones que incógnitas), entran en juego otros métodos. La **descomposición QR** permite resolver sistemas en el sentido de mínimos cuadrados, es decir, encontrando la solución aproximada que minimiza el error global.

De manera similar, la **descomposición en valores singulares (SVD)** ofrece un enfoque robusto incluso cuando la matriz de coeficientes es mal condicionada. El SVD no solo permite resolver sistemas, sino que también abre la puerta a técnicas de reducción de dimensionalidad y regularización, muy presentes en IA.



> **Interpretación práctica**
>
> Todos estos métodos comparten la misma lógica: en lugar de resolver las ecuaciones una a una, transforman el sistema en una forma que hace evidente la solución. La elección del método depende de las propiedades de la matriz de coeficientes y del tamaño del problema.
>
> En inteligencia artificial, donde los sistemas suelen ser muy grandes, no se utiliza la inversa de manera explícita. En su lugar, se recurre a descomposiciones como LU, QR o SVD, que son más estables y se adaptan mejor a los cálculos numéricos. La clave es que, aunque los problemas puedan tener millones de variables, siguen siendo en esencia sistemas de ecuaciones lineales que se resuelven aplicando estas técnicas matriciales.
>



>**Para reflexionar…**
>**¿Por qué crees que en IA no se utiliza casi nunca la fórmula $\mathbf{x} = \mathbf{A}^{-1}\mathbf{b}$ para resolver sistemas, a pesar de ser la más sencilla en apariencia? ¿Qué ventajas tienen los métodos basados en descomposiciones frente al cálculo directo de la inversa?**

## Aplicaciones en inteligencia artificial

Los sistemas de ecuaciones lineales no son solo un recurso académico: forman parte del núcleo matemático de muchos algoritmos de IA. Aunque rara vez nos detengamos a escribir las ecuaciones explícitamente, en el trasfondo de los modelos siempre está presente la lógica de resolver sistemas lineales.

Un ejemplo directo es la **regresión lineal**. Cuando tratamos de ajustar una recta o un hiperplano a un conjunto de datos, lo que realmente hacemos es resolver el sistema de ecuaciones que relaciona las características de los ejemplos con la variable que queremos predecir. En notación matricial, la estimación de los parámetros $\boldsymbol{\beta}$ se obtiene a partir de

$$
X^T X \boldsymbol{\beta} = X^T y,
$$

que no es más que un sistema de ecuaciones lineales en el que $X$ representa la matriz de datos y $y$ el vector de resultados. Resolver este sistema equivale a encontrar los coeficientes que mejor explican los datos observados.

En escalas mayores, como en el entrenamiento de **redes neuronales**, el número de parámetros es tan grande que no podemos resolver el sistema de una sola vez. Sin embargo, la lógica sigue siendo la misma: cada paso del entrenamiento busca una solución aproximada a un conjunto de relaciones que, en su esencia, son ecuaciones lineales o aproximaciones lineales locales de un problema más complejo.

Los sistemas lineales también aparecen en el análisis de **modelos dinámicos**, donde describen cómo cambia un sistema con el tiempo. Un ejemplo puede ser la propagación de información en una red social: cada estado futuro depende de una combinación lineal de los estados actuales, lo que se traduce en un sistema de ecuaciones. Resolverlo permite anticipar la evolución del sistema y detectar equilibrios o comportamientos inestables.

En **optimización numérica**, que es el motor de muchos algoritmos de aprendizaje, resolver sistemas lineales es un paso recurrente. Métodos como el gradiente conjugado o las técnicas de mínimos cuadrados generalizados no hacen más que aplicar, una y otra vez, estrategias para aproximar la solución de sistemas muy grandes.

La enseñanza que podemos extraer es que, aunque en la práctica rara vez se vean escritas las ecuaciones, **gran parte de la IA consiste en resolver sistemas lineales a gran escala**. Por eso, comprender cómo funcionan y qué significan geométricamente es esencial para interpretar lo que los algoritmos hacen con los datos.



>**Para reflexionar…**
>**¿Qué implica para un modelo de IA que los datos generen un sistema de ecuaciones que no tiene solución exacta? ¿Por qué puede ser más útil buscar una aproximación mediante mínimos cuadrados que insistir en encontrar una solución perfecta?**

## Interpretación geométrica avanzada

La visión geométrica de los sistemas lineales va más allá del caso sencillo de dos rectas en el plano o tres planos en el espacio. En un sistema general, cada ecuación representa un **hiperplano** en un espacio de $n$ dimensiones, y resolver el sistema significa encontrar el punto, la recta, el plano o la región donde todos esos hiperplanos se cruzan.

Cuando el sistema tiene solución única, la intersección es un solo punto: el lugar exacto que cumple todas las restricciones. Si existen infinitas soluciones, la intersección no se reduce a un punto, sino que se extiende a lo largo de una recta, un plano o, en dimensiones mayores, un subespacio. Cuando no hay solución, significa que los hiperplanos no llegan a coincidir en ningún punto común: se cortan parcialmente o se mantienen separados de forma incompatible.

Esta perspectiva geométrica es clave para entender un caso muy frecuente en inteligencia artificial: el de los sistemas **sobredeterminados**, es decir, aquellos que tienen más ecuaciones que incógnitas. En principio, no es posible encontrar un punto que satisfaga todas las condiciones exactamente, pero sí podemos buscar el punto que queda “lo más cerca posible” de todos los hiperplanos a la vez. Este enfoque se conoce como el **método de los mínimos cuadrados**.

En lugar de exigir una solución exacta, lo que buscamos es el vector $\mathbf{x}$ cuya imagen $\mathbf{A}\mathbf{x}$ se aproxime lo mejor posible al vector de resultados $\mathbf{b}$. Geométricamente, esto equivale a proyectar $\mathbf{b}$ sobre el espacio generado por las columnas de $\mathbf{A}$. La proyección es el punto más cercano a $\mathbf{b}$ que puede alcanzarse con combinaciones lineales de las columnas de $\mathbf{A}$.

Este concepto conecta directamente con algoritmos fundamentales en aprendizaje automático. En la regresión lineal, por ejemplo, no siempre es posible ajustar una recta o un hiperplano que pase por todos los puntos de datos, pero sí podemos encontrar la que minimiza la distancia total a esos puntos. Lo que en geometría es una proyección, en estadística se convierte en un ajuste por mínimos cuadrados.



>**Para reflexionar…**
>**¿Qué enseñanza podemos extraer del hecho de que, en la práctica, muchos sistemas no tengan solución exacta? ¿No es esto similar a la forma en que los modelos de IA nunca reproducen los datos de entrenamiento de manera perfecta, sino que buscan una representación aproximada que capte la esencia de los patrones?**
