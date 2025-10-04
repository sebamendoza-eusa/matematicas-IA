# Fundamentos de Probabilidad

Para entender el razonamiento probabilístico, es clave conocer los conceptos que forman su marco matemático. Esto nos permite modelar sistemas donde el resultado es incierto y los sucesos posibles se tratan como eventos aleatorios.

## Concepto de probababilidad y eventos

### Experimento Aleatorio y Espacio Muestral

Un **experimento aleatorio** es un proceso cuyo resultado no se puede predecir con certeza, pero que se puede repetir bajo condiciones controladas. A diferencia de los procesos deterministas, cada realización puede dar un resultado distinto.

Por ejemplo, lanzar una moneda es un experimento aleatorio. El **espacio muestral** ($S$) es el conjunto de todos los resultados posibles. En el caso de la moneda, $S = \{\text{cara, cruz}\}$. Para experimentos más complejos, el espacio muestral puede ser mucho más grande, y conocerlo es fundamental.

### **Cálculo de Probabilidad: La Regla de Laplace**

La forma más sencilla y común de calcular la probabilidad de un evento ($A$) es a través de la **regla de Laplace**, que se aplica cuando todos los resultados en el espacio muestral son igualmente probables. 

$$
P(A) = \frac{\text{Número de casos favorables}}{\text{Número total de resultados posibles}}
$$

Por ejemplo, si lanzas un dado de seis caras, cada número tiene la misma probabilidad de salir. La probabilidad de obtener un 4 es de $1/6$, ya que hay un solo resultado favorable de seis posibles.

### **Eventos y Operaciones entre Eventos**

Un **evento** es cualquier subconjunto del espacio muestral que nos interese. Los eventos pueden ser **simples** (un solo resultado, como $A=\{4\}$) o **compuestos** (varios resultados, como $B=\{2, 4, 6\}$).

#### Unión de Eventos

La **unión** de dos eventos, $A$ y $B$, son los resultados que están en $A$, en $B$, o en ambos. Representa la ocurrencia de al menos uno de los dos eventos.

$$
P(A \cup B) = P(A) + P(B) - P(A \cap B)
$$

> **Ejemplo:** En un dado, sea $A$: obtener un número par ($A=\{2,4,6\}$) y $B$: obtener un número mayor que 4 ($B=\{5,6\}$). La **intersección** es $A \cap B = \{6\}$.
> Usando la regla de Laplace, $P(A) = 3/6$, $P(B) = 2/6$, y $P(A \cap B) = 1/6$.
> Entonces, $P(A \cup B) = \frac{3}{6} + \frac{2}{6} - \frac{1}{6} = \frac{4}{6} = \frac{2}{3}$.

#### Intersección de Eventos

La **intersección** de los eventos $A$ y $B$ son los resultados que están en ambos. Representa la ocurrencia simultánea de ambos eventos.

$$
P(A \cap B)
$$

**Ejemplo:** Si $ A $ es obtener un número par y $B$ es obtener un número mayor que 3, la intersección es $A \cap B = \{4, 6\}$. Por la regla de Laplace, $P(A \cap B) = 2/6 = 1/3$.

#### Complemento de un Evento

El **complemento** de un evento $A$ son los resultados en el espacio muestral que no están en $ A $. Representa la no ocurrencia de $A$.

$$
P(A^c) = 1 - P(A)
$$

### Independencia y dependencia de eventos

En probabilidad, no todos los eventos están relacionados entre sí. A veces la ocurrencia de uno no influye en absoluto sobre el otro, y en otros casos sí lo hace. Esta distinción entre **independencia** y **dependencia** es fundamental porque determina cómo calculamos probabilidades conjuntas.

#### Independencia de eventos

Decimos que dos eventos son **independientes** cuando la probabilidad de que ambos ocurran es simplemente el producto de sus probabilidades individuales:

$$
 P(A \cap B) = P(A) \cdot P(B) 
$$


En términos intuitivos, saber que ocurrió uno no cambia nuestra estimación de que ocurra el otro.

> **Ejemplo:** al lanzar dos dados distintos, el resultado del primero no afecta al segundo. La probabilidad de obtener un 3 en el primero y un 5 en el segundo es
>
> $$
>  \frac{1}{6} \cdot \frac{1}{6} = \frac{1}{36}.
> $$
> 

#### Dependencia de eventos

En contraste, dos eventos son **dependientes** cuando la ocurrencia de uno modifica la probabilidad del otro.

> **Ejemplo:** si tenemos una bolsa con 5 bolas rojas y 5 azules y sacamos una sin reemplazo, la probabilidad de la segunda extracción depende de lo que ocurrió en la primera. Si la primera bola fue roja, habrá menos rojas disponibles en la segunda extracción y, por tanto, la probabilidad de cada color habrá cambiado.

> Este concepto de independencia no solo es importante para cálculos sencillos, sino que será clave en inteligencia artificial. Muchos modelos probabilísticos hacen suposiciones de independencia para simplificar problemas muy complejos. Más adelante veremos cómo esta idea reaparece en el **Teorema de Bayes** y en algoritmos como **Naive Bayes**, donde se asume que ciertas variables se comportan como si fueran independientes para poder construir modelos eficientes.



### Interpretaciones de la probabilidad

Cuando hablamos de probabilidad, solemos pensar en una medida de incertidumbre. Sin embargo, a lo largo de la historia se han desarrollado distintas **interpretaciones** de lo que significa asignar un número entre 0 y 1 a un evento. Comprender estas perspectivas es útil para la inteligencia artificial, ya que en diferentes contextos se aplican distintas formas de razonar con probabilidades.

#### Interpretación clásica

La visión clásica, formulada por Laplace, entiende la probabilidad como una relación entre casos favorables y casos posibles, siempre que todos sean igualmente probables.

$$
P(A) = \frac{\text{número de casos favorables}}{\text{número de casos posibles}}
$$

Por ejemplo, la probabilidad de sacar un 4 al lanzar un dado justo es $1/6$, pues hay un solo resultado favorable de seis posibles.

Esta interpretación funciona bien en juegos de azar y situaciones simétricas, pero presenta límites cuando los resultados no son equiprobables. En un dado cargado, por ejemplo, algunos resultados tienen más probabilidad que otros, y el razonamiento clásico deja de ser aplicable.

> **Para reflexionar…**
> ¿Crees que podemos usar la interpretación clásica para calcular la probabilidad de que un correo electrónico sea spam? ¿Por qué ese contexto no encaja con un cálculo de “casos favorables / casos posibles” como en un dado?

#### Interpretación frecuentista

En la interpretación frecuentista, la probabilidad de un evento se entiende como la frecuencia relativa que se observa al repetir el experimento muchas veces:

$$
P(A) = \lim_{n \to \infty} \frac{\text{número de veces que ocurre } A}{n}
$$

Si lanzamos una moneda justa muchas veces, la proporción de caras tenderá a 0.5. Esa proporción se convierte en la probabilidad.

Esta visión conecta directamente con la práctica del análisis de datos: se estiman probabilidades observando **muestras grandes** y confiando en que reflejan el comportamiento de la población. En inteligencia artificial, la mayoría de los modelos se basan en este enfoque: entrenamos algoritmos con miles de ejemplos y a partir de ahí inferimos qué patrones son más probables.

> **Ejemplo**:
> Si en un dataset de 10.000 correos encontramos que 3.000 son spam, podríamos estimar la probabilidad de spam como $P(\text{spam}) \approx 0.3$.

> **Para reflexionar…**
> ¿Hasta qué punto crees que esa probabilidad de 0.3 es “real”? ¿Y si mañana cambia el tipo de correos que recibimos y la proporción de spam aumenta al 50%?

#### Interpretación bayesiana o subjetiva

En el enfoque bayesiano, la probabilidad se interpreta como un **grado de creencia racional**. No depende únicamente de frecuencias observadas, sino también de la información disponible y del conocimiento previo.

Por ejemplo, si el parte meteorológico anuncia un 70% de probabilidad de lluvia mañana, no significa que podamos repetir “mañana” muchas veces y que 7 de cada 10 veces llueva. Significa que, dado lo que sabemos hoy (presión atmosférica, humedad, temperatura, modelos climáticos), nuestra confianza en que llueva es del 70%.

En IA, este enfoque es central: los modelos bayesianos asignan probabilidades iniciales (priors) y luego las actualizan conforme reciben nueva evidencia. Así funciona un filtro de spam basado en Bayes: comienza con creencias sobre qué palabras son típicas en correos spam, y cada nuevo mensaje ajusta esas creencias.

> **Ejemplo**:
> Si recibes un correo con la palabra “gratis”, un modelo bayesiano calcularía la probabilidad de que sea spam combinando tu creencia previa con la evidencia de que “gratis” aparece con más frecuencia en correos no deseados.

> **Para reflexionar…**
> Imagina que un sistema de recomendación te sugiere una película con una probabilidad del 85% de que te guste. ¿Crees que esa probabilidad refleja una frecuencia observada en muchos “tus iguales”, o más bien una creencia actualizada del sistema sobre ti en particular?



Cada interpretación de la probabilidad ilumina un aspecto distinto de esta: la **clásica** en escenarios equiprobables, la **frecuentista** en situaciones repetibles con grandes muestras, y la **bayesiana** en contextos de incertidumbre y actualización de información.

En inteligencia artificial, estas tres miradas conviven. Los juegos de azar siguen siendo el ejemplo perfecto de la clásica, el entrenamiento con grandes datasets responde al enfoque frecuentista, y la personalización de predicciones con información en tiempo real se nutre del enfoque bayesiano.

> **Para reflexionar…**
> ¿Tiene sentido hablar de “la probabilidad verdadera” de un evento, o deberíamos aceptar que depende de la interpretación que adoptemos?

## Definición de función de probabilidad y axiomas de Kolmogórov

Cuando hablamos de probabilidad de forma cotidiana, solemos manejar reglas intuitivas que funcionan en muchos casos simples. Una es la idea de **contar casos favorables y casos posibles** (la llamada probabilidad clásica de Laplace), que usamos en juegos de azar como dados o cartas. Otra es la noción de **frecuencia relativa**, donde consideramos la probabilidad como el porcentaje de veces que ocurre un evento al repetir el experimento muchas veces. Estas dos visiones nos resultan naturales y útiles, pero presentan límites. La primera solo es válida cuando los resultados son equiprobables, y la segunda exige pensar en repeticiones infinitas, algo que rara vez es posible en la práctica.

Para superar estas limitaciones y unificar el concepto, en 1933 el matemático soviético **Andréi Kolmogórov** propuso un enfoque revolucionario: en lugar de definir probabilidad caso por caso, estableció un pequeño conjunto de **axiomas**, es decir, reglas fundamentales que toda probabilidad debe cumplir siempre, independientemente de si hablamos de dados, de temperaturas, de redes neuronales o de secuencias de ADN.

Este paso fue crucial, porque convirtió a la probabilidad en una rama rigurosa de las matemáticas. A partir de esas reglas mínimas (no negatividad, normalización y aditividad) se puede deducir todo lo demás: desde las fórmulas de unión e intersección de eventos hasta el cálculo de probabilidades en distribuciones continuas. Es decir, **los axiomas son el suelo firme sobre el que se construye todo el edificio de la estadística moderna**.

En inteligencia artificial, esta formalización resulta indispensable. Cuando un modelo asigna probabilidades a clases (“este correo es spam con probabilidad 0.8”), o a secuencias de palabras en un modelo de lenguaje, no basta con que los números “parezcan razonables”: deben cumplir siempre esas reglas axiomáticas para que los cálculos tengan coherencia y puedan usarse en decisiones posteriores. Por eso decimos que la base axiomática de Kolmogórov es el **lenguaje común que conecta la teoría matemática con la práctica en IA**.

### Axiomas de Kolmogorov

De manera formal, si $\Omega$ es el **espacio muestral** (el conjunto de todos los resultados posibles) y $\mathcal{F}$ es la colección de **eventos** (subconjuntos de $\Omega$), una **función de probabilidad** es una aplicación

$$
 P : \mathcal{F} \longrightarrow [0,1]
$$

que asigna a cada evento $A \in \mathcal{F}$ un número real entre 0 y 1. Esta función cumple tres reglas básicas o **axiomas:**

1. **No negatividad:**
   Ningún evento puede tener probabilidad negativa:

$$
P(A) \geq 0
$$

2. **Normalización:**
   El suceso seguro, es decir, todo el espacio muestral, siempre tiene probabilidad 1:

$$
P(\Omega) = 1
$$

3. **Aditividad (o σ-aditividad):**
   Si tenemos eventos mutuamente excluyentes (que no pueden ocurrir a la vez), la probabilidad de que ocurra “uno u otro” es la suma de las probabilidades individuales:

$$
 P\Big(\bigcup_{i=1}^{n} A_i\Big) = \sum_{i=1}^{n} P(A_i)
$$



> **Ejemplo**:
>
> Si lanzamos un dado justo, el espacio muestral es $\Omega = {1,2,3,4,5,6}$. La probabilidad de cada cara es $1/6$.
>
> La **no negatividad** asegura que no tiene sentido hablar de probabilidades como $-0.2$.
>
> La **normalización** garantiza que la probabilidad total de obtener “algún número” es 1.
>
> La **aditividad** nos dice que la probabilidad de obtener un número par es
>
> $$
> P({2,4,6}) = P(2) + P(4) + P(6) = \tfrac{1}{6}+\tfrac{1}{6}+\tfrac{1}{6} = \tfrac{3}{6}.
> $$

### Consecuencias útiles de los axiomas de Kolmogórov y sus aplicaciones

Una vez que tenemos claros los tres axiomas de Kolmogórov —no negatividad, normalización y aditividad—, podemos derivar de ellos una serie de propiedades que usamos constantemente en estadística, en el análisis de datos y, de manera muy directa, en modelos de inteligencia artificial. Estas consecuencias no son “nuevas reglas”, sino corolarios inevitables de los axiomas, y su importancia radica en que simplifican cálculos y dan coherencia a los modelos.

#### Probabilidad del suceso imposible

Si el suceso seguro tiene probabilidad 1, entonces el suceso imposible (el conjunto vacío, $\emptyset$) debe tener probabilidad 0. Es una consecuencia inmediata de la aditividad: si $A \cup \emptyset = A$, entonces $P(A) = P(A) + P(\emptyset)$, lo que implica $P(\emptyset)=0$.
En IA, esto asegura que nunca asignemos probabilidad positiva a un evento “imposible”, por ejemplo, que una clase inexistente en un clasificador tenga alguna probabilidad de ocurrir.

#### Complemento de un evento

Si $A$ es un evento, su complemento $A^c$ representa que “$A$ no ocurre”. De los axiomas se deduce que:

$$
P(A^c) = 1 - P(A).
$$

Este resultado, sencillo pero poderoso, aparece constantemente en aplicaciones. Por ejemplo, si un modelo de lenguaje asigna probabilidad 0.8 a que la próxima palabra sea “hola”, entonces la probabilidad de que sea “cualquier otra palabra” debe ser 0.2. No necesitamos calcular la suma de todas las demás posibilidades; basta con usar el complemento.

#### Unión de dos eventos cualesquiera

Cuando los eventos no son disjuntos, la probabilidad de la unión se corrige restando la intersección:

$$
P(A \cup B) = P(A) + P(B) - P(A \cap B).
$$

Este principio se utiliza en tareas como la detección de spam, donde puede interesarnos calcular la probabilidad de que un correo contenga la palabra “gratis” o la palabra “premio”. Si simplemente sumáramos ambas probabilidades, estaríamos contando dos veces los correos que incluyen ambas palabras.

#### Monotonía de la probabilidad

Si un evento $A$ está contenido en otro evento $B$ ($A \subseteq B$), entonces su probabilidad es menor o igual:

$$
P(A) \leq P(B).
$$

Esto refleja que ampliar las condiciones de un evento nunca puede reducir la probabilidad de que ocurra. En IA, este principio se ve en modelos jerárquicos: la probabilidad de que “una imagen contenga un perro de raza labrador” siempre será menor o igual que la probabilidad de que “contenga un perro”.

#### Cotas de probabilidad y consistencia

De los axiomas se deduce que toda probabilidad está acotada: $0 \leq P(A) \leq 1$. Aunque esto parezca obvio, en la práctica actúa como un control de calidad de los modelos de IA. Si durante el entrenamiento un algoritmo produce una probabilidad mayor que 1 o menor que 0, sabemos que hay un error numérico o conceptual.

### Conexión con la inteligencia artificial

¿Por qué importan tanto estos axiomas en inteligencia artificial? La respuesta está en que actúan como garantía de coherencia en todos los modelos probabilísticos que usamos. Pensemos, por ejemplo, en un **clasificador bayesiano**. Cuando decide si un correo es spam o no, debe asignar probabilidades a cada clase, y esas probabilidades han de ser no negativas y sumar exactamente 1. De lo contrario, el modelo podría devolver valores imposibles de interpretar, como una “probabilidad” de 1.3 o un conjunto de clases cuya suma exceda la unidad.

Lo mismo ocurre en los **modelos de lenguaje**. Estos modelos calculan probabilidades sobre secuencias de palabras, y la regla de aditividad asegura que, al considerar todas las frases posibles, la suma de sus probabilidades sea 1. Sin este requisito, las probabilidades asignadas a frases y palabras dejarían de tener sentido y el modelo no sería consistente.

En el caso del **aprendizaje por refuerzo**, un agente debe asignar probabilidades a las distintas acciones que puede tomar en cada estado. Los axiomas de Kolmogórov garantizan que esas probabilidades representen un conjunto de elecciones válidas, sin duplicaciones ni incoherencias. Si se violaran, el agente podría acabar en situaciones absurdas, como elegir acciones “más de una vez” o no tener ninguna acción posible.

En resumen, los axiomas no son un detalle técnico accesorio: son la condición que evita que la probabilidad se convierta en un número arbitrario. Sin ellos, los modelos perderían su interpretación matemática y no podrían servir como base fiable para tomar decisiones en IA.

