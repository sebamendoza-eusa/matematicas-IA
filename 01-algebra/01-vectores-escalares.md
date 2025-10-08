Vectores y escalares: la base del lenguaje de la IA
===

Definiciones
---


Los conceptos de **vector** y **escalar**, aunque parezcan abstractos, son la base sobre la que se construyen los modelos de *machine learning* y *deep learning*.

Para empezar, imaginemos que **los escalares son los "números"** con los que estamos familiarizados, es decir, una magnitud única. Un escalar representa una sola cantidad. Por ejemplo, la temperatura de una habitación (25°C), el precio de un producto (50€) o la edad de una persona (30 años) son todos ejemplos de escalares. En el contexto de la programación, podríamos pensarlo simplemente como una variable que almacena un valor numérico. En un modelo de IA, un escalar podría ser un único *hiperparámetro*, como la tasa de aprendizaje.

Por otro lado, un **vector** es una colección ordenada de escalares. Es más que una simple lista de números; es una entidad matemática que tiene tanto magnitud como dirección. Visualmente, podemos representar un vector como una flecha en el espacio, que parte de un punto de origen y apunta hacia otro. Cada uno de los escalares que lo componen se denomina "componente" del vector.

> **Ejemplo:**
> 
> En un sistema de recomendación de películas, el perfil de un usuario podría representarse como un vector. Cada componente del vector podría indicar la calificación que el usuario le ha dado a una película específica. Por ejemplo, un vector como [5,3,4,1] podría significar que el usuario calificó la película 1 con 5 estrellas, la película 2 con 3, etc. Cada calificación es un escalar, y juntos forman el vector que representa el perfil de preferencias del usuario.

En el mundo de la IA, los vectores son omnipresentes. Los datos con los que trabajamos, como imágenes, texto o audio, se transforman en representaciones numéricas que son, en esencia, vectores. Por ejemplo, una imagen digital puede ser un vector donde cada componente es la intensidad de color de un píxel. Un texto puede ser un vector donde cada componente representa la frecuencia de una palabra en un vocabulario.

La capacidad de representar información compleja en forma de vectores es lo que permite que los algoritmos de aprendizaje automático puedan procesar y encontrar patrones en los datos. El álgebra lineal nos proporciona las herramientas para manipular estos vectores, permitiéndonos realizar operaciones como la suma, la resta, o el producto escalar, que son fundamentales para los cálculos internos de los modelos.

>**Para reflexionar...**
>**¿Por qué es más útil representar los datos como vectores en lugar de simplemente como una lista de números sin ninguna estructura?**
>*Considera cómo la estructura de un vector, y la capacidad de realizar operaciones matemáticas con él, nos permite capturar no solo la información individual, sino también las relaciones y distancias entre los distintos puntos de datos. Piensa en cómo calcular la "distancia" entre dos perfiles de usuario, o la "similitud" entre dos imágenes, se convierte en un problema matemático manejable cuando los datos están representados como vectores.*

### Ejemplo práctico: Vectores y escalares en Machine Learning

Para entender mejor cómo estos conceptos se aplican en la práctica, pensemos en un problema común en el campo del *machine learning*: la clasificación. Supongamos que estamos construyendo un modelo para predecir si un correo electrónico es spam o no.

Un **escalar** podría ser un valor único asociado a un correo. Por ejemplo, la longitud del correo en caracteres, el número de enlaces que contiene, o la cantidad de veces que aparece una palabra específica, como "gratis". Cada uno de estos valores es una sola magnitud, un escalar que describe una característica del correo electrónico.

Sin embargo, para tomar una decisión informada, el modelo necesita considerar múltiples características a la vez. Aquí es donde entran en juego los **vectores**. Podemos representar cada correo electrónico como un vector **de características**. Cada componente de este vector es un escalar que representa una de las características que hemos medido. Por ejemplo, un vector para un correo podría ser

$$
\text{correo-ejemplo=[longitud,enlaces,frecuencia-gratis,…]}
$$

Si nuestro modelo considera la longitud del correo, el número de enlaces y la frecuencia de la palabra "gratis", un correo concreto podría ser representado por el vector [500,3,5].

- 500 es el escalar que representa la longitud.
- 3 es el escalar que representa el número de enlaces.
- 5 es el escalar que representa la frecuencia de la palabra "gratis".

Este vector, con tres dimensiones, nos da una "huella" numérica del correo electrónico. A medida que recopilamos más datos, estos vectores se convierten en los puntos con los que el algoritmo de aprendizaje trabaja. El modelo busca patrones en estos puntos: por ejemplo, podría aprender que los correos que son spam tienden a tener vectores con valores altos en las componentes de "enlaces" y "frecuencia de 'gratis'".

Las **operaciones con vectores** nos permiten medir la "distancia" o la "similitud" entre correos electrónicos, lo cual es fundamental para muchos algoritmos de clasificación. El producto escalar, por ejemplo, es una operación que nos permite determinar cuán similares son dos vectores en dirección, lo cual se traduce en qué tan similares son dos correos en sus características. De esta manera, las matemáticas abstractas se convierten en las herramientas prácticas que permiten a la IA tomar decisiones.

>**Para reflexionar...**\
> ¿Cómo crees que podríamos representar una imagen en blanco y negro como un vector para que un algoritmo de IA la procese? ¿Y una imagen a color?
> *Considera cómo los píxeles de una imagen pueden ser vistos como los componentes de un vector. Piensa en qué representa el valor de cada píxel y cómo el color podría añadir más "dimensiones" a este vector.*

Operaciones básicas con vectores
---


Ahora que hemos comprendido el concepto de vector como una representación de datos, es crucial entender cómo podemos manipularlos a través de operaciones matemáticas. Estas operaciones están en la base de la gran mayoría de algoritmos usados en IA.

### Suma y Resta de vectores

La suma y resta de vectores se realiza componente a componente. Para sumar dos vectores, simplemente se suman sus elementos correspondientes. Lo mismo aplica para la resta. Para vectores $\mathbf{v} = [v_1, v_2, \dots, v_n]$ y $\mathbf{w} = [w_1, w_2, \dots, w_n]$, la suma es:

$$
\mathbf{v} + \mathbf{w} = [v_1 + w_1, v_2 + w_2, \dots, v_n + w_n]
$$

En el contexto de la IA, estas operaciones pueden ser útiles para combinar o ajustar representaciones de datos. Por ejemplo, en el **procesamiento del lenguaje natural (NLP)**, la suma de vectores de palabras (**word embeddings**) puede capturar relaciones semánticas. El vector de la palabra "Rey" más el vector de "Mujer" podría ser similar al vector de "Reina".

> **Ejemplo**:
> En un sistema de recomendación, si un usuario está representado por un vector de preferencias $\mathbf{u}$ y la película que ve está representada por un vector de características $\mathbf{p}$, un ajuste en la preferencia del usuario después de ver la película podría modelarse como $\mathbf{u}_{\text{nueva}} = \mathbf{u} + \mathbf{p}_{\text{ajuste}}$, donde $\mathbf{p}_{\text{ajuste}}$ es un pequeño vector que modifica las preferencias del usuario.

### Multiplicación por un escalar

La **multiplicación de un vector por un escalar** es la operación que nos permite cambiar la magnitud (longitud) del vector, manteniendo su dirección original (o invirtiéndola si el escalar es negativo). Un escalar ($\alpha$) es simplemente un número real, mientras que el vector $\mathbf{v}$ es una colección ordenada de números.

Para multiplicar un vector $\mathbf{v}$ por un escalar $\alpha$, se multiplica cada componente del vector por dicho escalar:


$$
\alpha \mathbf{v} = \begin{bmatrix}
\alpha v_1 \\
\alpha v_2 \\
\vdots \\
\alpha v_n
\end{bmatrix}
$$


> **Ejemplo**:
> Si un vector de datos $\mathbf{v} = [2, 4]$ es escalado por $\alpha = 0.5$, el nuevo vector $\mathbf{w} = 0.5 \cdot \mathbf{v} = [1, 2]$. El vector se ha encogido a la mitad de su longitud original, pero sigue apuntando en la misma dirección. En un modelo de IA, esto podría representar la reducción de la contribución de una característica a la mitad.

### Normalización de vectores

El **álgebra lineal** en **Inteligencia Artificial** requiere herramientas que nos permitan cuantificar el "tamaño", la "magnitud" de un vector de datos o el "error" entre una predicción y el valor real. Para esto, utilizamos el concepto matemático de **norma**. Una norma es, esencialmente, una función que asigna una longitud o tamaño a un vector o una matriz, estableciendo una medida consistente y útil.

La norma de un vector v, denotada como $\Vert\mathbf{v}\Vert$, es fundamental en el *machine learning* porque permite establecer métricas de distancia, evaluar la calidad de las predicciones y, de manera crucial, controlar la complejidad de los modelos a través de la **regularización**. En la práctica de la IA, dominan dos tipos de normas: la Norma L2 y la Norma L1, cada una con una interpretación geométrica y un impacto en la optimización radicalmente distintos.

#### La norma euclídea o norma $L_2$: Distancia y magnitud

La que hemos visto en la definición anterior es la norma más común, y la que utilizamos intuitivamente. Se denomina  **norma Euclídea** o **norma $L_2$**. Esta norma mide la longitud de un vector desde el origen en el espacio, o la distancia "en línea recta" entre dos vectores. Es una extensión directa del **Teorema de Pitágoras**.

Como se ha comentado, para un vector $\mathbf{v}$ de $n$ componentes, su Norma $L_2$ se calcula como la raíz cuadrada de la suma de sus componentes al cuadrado:

$$
||\mathbf{v}|| = \sqrt{v_1^2 + v_2^2 + \dots + v_n^2} = \sqrt{\sum_{i=1}^n v_i^2}
$$

En **Inteligencia Artificial**, el cuadrado de esta norma ($||\mathbf{v}||^2$) es de gran relevancia, pues define la **pérdida cuadrática media** (*Mean Squared Error* - MSE), la función de pérdida más utilizada en los modelos de **regresión**. Además, la Norma $L_2$ se utiliza en la **Regularización *Ridge*** (o penalización $L_2$), una técnica para evitar el sobreajuste al penalizar fuertemente los pesos (los elementos del vector de parámetros) que son muy grandes. Lo veremos en el tema dedicado a los modelos de **regresión lineal**

Un vez definida la norma podemos conseguir un **vector normalizado** dividiendo cada componente de un vector por su norma $L_2$

En el caso de un vector $\mathbf{v}$ se podría calcular como la raíz cuadrada de la suma de los cuadrados de sus componentes.

El vector normalizado $\hat{\mathbf{v}}$ sería entonces:

$$
\hat{\mathbf{v}} = \frac{\mathbf{v}}{\Vert\mathbf{v}\Vert}
$$




#### La norma $L_1$: Suma de valores absolutos y escasez

Otra norma de gran importancia es la **Norma $L_1$**, también conocida como la **distancia de Manhattan** o distancia del "taxista", pues mide la distancia que se recorrería si solo se pudiera mover en direcciones paralelas a los ejes de coordenadas.

Se calcula como la suma de los valores absolutos de las componentes del vector:

$$
||\mathbf{v}|| = |v_1| + |v_2| + \dots + |v_n| = \sum_{i=1}^n |v_i|
$$
En contraste con la Norma $L_2$, la Norma $L_1$ tiene una propiedad fundamental que la hace valiosa en el *machine learning*: promueve la **escasez (*sparsity*)**. Cuando se aplica como término de penalización (**Regularización *Lasso***), la optimización tiende a forzar a que muchos de los pesos del modelo sean exactamente cero. Esto resulta ser un mecanismo efectivo de **selección de características**, ya que los pesos nulos eliminan la contribución de las características irrelevantes.

> **Ejemplo**:
> Al optimizar una **red neuronal**, el vector de pesos $\mathbf{w}$ podría ser sometido a una penalización $L_2$. Si un peso es $w_i=10$, su penalización $L_2$ es $100$. Si otro peso es $w_j=1$, su penalización es $1$. El modelo se ve forzado a distribuir los pesos de manera más uniforme. En cambio, si usamos la penalización $L_1$, es más probable que el peso $w_j$ se fuerce a cero, simplificando el modelo.

> **Para reflexionar...**
> **Si un modelo de *machine learning* tiene miles de características de entrada, pero solo unas pocas son realmente relevantes, ¿qué tipo de regularización, $L_1$ o $L_2$, sería más efectiva para eliminar automáticamente las características irrelevantes y por qué?**
> *Considera el efecto de cada norma sobre los pesos pequeños y grandes. Piensa en cómo la Norma $L_1$ es capaz de llevar los pesos a cero (escasez) mientras que la $L_2$ simplemente los acerca a cero, pero rara vez los elimina por completo.*

---

La normalización es esencial en muchos algoritmos de IA, especialmente en aquellos que utilizan distancias o productos escalares. Al normalizar los vectores, se asegura que la magnitud de los datos no influya indebidamente en el cálculo, haciendo que el modelo se enfoque en la dirección y la relación entre ellos. Esto es crucial para **regular la magnitud de los gradientes** en el *deep learning*, evitando problemas como el **desvanecimiento del gradiente**.

>**Para reflexionar...**
> **¿Cómo podría el producto escalar ser utilizado para determinar la "similitud" entre dos documentos de texto? ¿Qué desafíos crees que podrían surgir si los vectores de palabras no estuvieran normalizados?**
> *Considera que los documentos de texto pueden ser representados como vectores donde cada componente es la frecuencia de una palabra. Piensa en cómo el producto escalar mide la similitud direccional y cómo la normalización asegura que un documento más largo no sea automáticamente más "similar" a otro.*

### Producto escalar

El producto escalar de dos vectores es una de las operaciones más importantes en la IA. A diferencia de la suma, el resultado de esta operación no es otro vector, sino un único escalar. Se calcula multiplicando los elementos correspondientes de los dos vectores y sumando todos los productos.

$$
\mathbf{v} \cdot \mathbf{w} = \sum_{i=1}^n v_i w_i = v_1w_1 + v_2w_2 + \dots + v_nw_n
$$

Podemos imaginar el valor del producto escalar como una medida de la relación geométrica entre los dos vectores. Un producto escalar grande y positivo indica que los vectores apuntan en direcciones similares. Si es cero, son ortogonales (perpendiculares). Si es grande y negativo, apuntan en direcciones opuestas.

Esta propiedad es fundamental en los algoritmos de **regresión lineal** y en las **redes neuronales**. En una neurona, el producto escalar entre el vector de entradas y el vector de pesos determina la activación de la neurona, es decir, el grado en que las entradas influyen en la salida. También es una operación crucial en el procesamiento del lenguaje natural.

#### Interpretación geométrica del producto escalar

Para ser más rigurosos, profundicemos en la interpretación geométrica del **producto escalar**. Más allá de ser una simple operación algebraica, el producto escalar de dos vectores, $\mathbf{v}$ y $\mathbf{w}$, está íntimamente relacionado con la longitud de estos vectores y el ángulo que se forma entre ellos.

La fórmula que nos permite entender esta relación es:

$$
\mathbf{v} \cdot \mathbf{w} = \Vert\mathbf{v}\Vert \Vert\mathbf{w}\Vert \cos(\theta)
$$

Donde $\Vert\mathbf{v}\Vert$ y $\Vert\mathbf{w}\Vert$ son las normas (o longitudes) de los vectores $\mathbf{v}$ y $\mathbf{w}$, respectivamente, y $\cos(\theta)$ es el coseno del ángulo $\theta$ que forman los dos vectores.

Esta fórmula revela la verdadera naturaleza del producto escalar. Nos dice que el producto escalar es una medida de la **proyección de un vector sobre otro**. Piensa en la proyección como la "sombra" que un vector arroja sobre el otro. El producto escalar es el producto de la longitud de esa sombra por la longitud del vector sobre el que se proyecta.

- Cuando los vectores apuntan en la misma dirección ($\theta = 0^\circ$), el coseno es $1$. El producto escalar es positivo y máximo, igual al producto de sus longitudes.
- Cuando los vectores son **ortogonales** (perpendiculares, $\theta = 90^\circ$), el coseno es $0$. El producto escalar es cero, lo que significa que no hay proyección de un vector sobre el otro.
- Cuando los vectores apuntan en direcciones opuestas ($\theta = 180^\circ$), el coseno es $-1$. El producto escalar es negativo y su valor absoluto es máximo.

Esta interpretación es la clave para entender por qué el producto escalar se usa para medir la **similitud de cosenos** en la IA. Al normalizar los vectores (dividiendo por sus normas), la fórmula se simplifica a $\cos(\theta) = \frac{\mathbf{v} \cdot \mathbf{w}}{\Vert\mathbf{v}\Vert \Vert\mathbf{w}\Vert}$. El valor resultante es el coseno del ángulo entre los vectores. Cuanto más cercano a 1 sea este valor, más similares son los vectores en dirección, lo que se traduce en una mayor similitud entre los datos que representan.

Esta técnica se utiliza, por ejemplo, en los sistemas de recomendación para encontrar elementos similares a los que un usuario ya ha valorado positivamente, o en el procesamiento del lenguaje natural para medir la similitud semántica entre palabras o documentos.



>**Para reflexionar...**
> **¿Qué diferencia fundamental existe entre la similitud de coseno y la distancia euclidiana (la longitud de la línea recta que une los puntos) para medir la similitud entre dos vectores? ¿En qué escenarios de la IA crees que una podría ser más adecuada que la otra?**
> *Considera que la similitud de coseno se centra en la dirección de los vectores, mientras que la distancia euclidiana considera tanto la dirección como la magnitud. Piensa en el problema de la clasificación de documentos de texto, donde la longitud del documento puede variar enormemente, o en el caso de la detección de anomalías, donde la magnitud de los datos puede ser un factor clave.*

> **Ejemplo**:
> Imaginemos que queremos predecir el precio de una casa. El vector de características de la casa podría ser $\mathbf{c} = [\text{metros}^2, \text{habitaciones}, \text{baños}]$ y el modelo de regresión lineal tiene un vector de pesos $\mathbf{w} = [w_1, w_2, w_3]$. La predicción del precio $\hat{y}$ se calcula como el producto escalar de ambos vectores, más un término de sesgo (bias): $\hat{y} = \mathbf{w} \cdot \mathbf{c} + b$.

Espacios Vectoriales: la estructura del universo de datos de la IA


Para que la **Inteligencia Artificial** pueda procesar y aprender de la información, los datos deben estar estructurados en un marco matemático coherente. Este marco constituye un concepto fundamental conocido como **espacio vectorial**. Formalmente, un espacio vectorial es un conjunto de elementos, a los que llamamos **vectores**, en el que se definen dos operaciones: la suma de vectores y la multiplicación de un vector por un escalar. En el ámbito del *machine learning*, nos referimos a este espacio como el **espacio de características**, donde cada instancia de datos (como un documento de texto o una imagen) es un vector cuya posición está determinada por los valores de sus características.

> **Ejemplo:**
> 
> Imagina un modelo que clasifica el sentimiento de reseñas de películas. El espacio de características podría tener una dimensión para la frecuencia de la palabra "genial", otra para "aburrido", y otra para "increíble". Una reseña, como "La película fue genial y muy increíble", sería representada como un vector como [1,0,1]. Este vector es un punto en el espacio de características que representa la reseña.

## Espacio vectorial: una definición formal

Un **espacio vectorial** es la estructura matemática fundamental que dota a los vectores de un contexto y unas reglas de comportamiento perfectamente definidas. No basta con entender un vector como "una simple lista de números"; para que el álgebra lineal funcione y sea predictiva en la **Inteligencia Artificial**, necesitamos un **marco** que establezca cómo interactúan esos vectores entre sí y cómo se comportan al ser escalados. Piensa en el espacio vectorial como el **taller donde todas las transformaciones y combinaciones entre vectores tienen sentido y son válidas**.

Formalmente, un espacio vectorial es un conjunto $\mathbf{V}$ (cuyos elementos podrían ser los vectores), definido sobre un **cuerpo (o campo)** $\mathbb{K}$ —que en el ámbito de la IA es casi siempre el conjunto de los **números reales** $\mathbb{R}$—, junto con dos operaciones bien definidas:

La primera es la **suma de vectores**: Una regla que combina dos vectores de $\mathbf{V}$ para obtener un tercer vector que también pertenece a $\mathbf{V}$.

La segunda es la **multiplicación por escalares**: Una regla que toma un número real (escalar) de $\mathbb{K}$ y un vector de $\mathbf{V}$ para producir un vector escalado que, de nuevo, pertenece a $\mathbf{V}$.

Para que un conjunto $(\mathbf{V}, +, \cdot)$ sea considerado un espacio vectorial, estas dos operaciones deben cumplir un conjunto de ocho **axiomas fundamentales**. Estos axiomas no son opcionales; son las leyes que garantizan que el espacio es coherente, predecible y que cualquier operación que realicemos en el ámbito del *machine learning* será matemáticamente consistente.

* **Clausura bajo la suma y la multiplicación escalar:** la suma de dos vectores y el producto de un vector por un escalar permanecen en $V$. Es decir, son **operaciones de composición interna**
* **Asociatividad y conmutatividad de la suma:** $(\mathbf{u} + \mathbf{v}) + \mathbf{w} = \mathbf{u} + (\mathbf{v} + \mathbf{w})$, y $\mathbf{u} + \mathbf{v} = \mathbf{v} + \mathbf{u}$.
* **Existencia del vector neutro:** existe un vector $\mathbf{0} \in V$ tal que $\mathbf{v} + \mathbf{0} = \mathbf{v}$ para todo $\mathbf{v}$.
* **Existencia del opuesto:** para cada $\mathbf{v} \in V$ existe un vector $-\mathbf{v}$ tal que $\mathbf{v} + (-\mathbf{v}) = \mathbf{0}$.
* **Compatibilidad de la multiplicación escalar con el producto de escalares:** $(ab)\mathbf{v} = a(b\mathbf{v})$.
* **Elemento neutro para el producto escalar:** $1 \cdot \mathbf{v} = \mathbf{v}$ para todo $\mathbf{v} \in V$.
* **Distributividad de la multiplicación escalar respecto a la suma de escalares:** $(a+b)\mathbf{v} = a\mathbf{v} + b\mathbf{v}$.
* **Distributividad de la multiplicación escalar respecto a la suma de vectores:** $a(\mathbf{u} + \mathbf{v}) = a\mathbf{u} + a\mathbf{v}$.

Estos ocho axiomas se pueden agrupar en tres leyes que definen la robustez del espacio:

### Ley de la Clausura: Permanencia en el Sistema

La ley más intuitiva y crucial es la **clausura** (o composición interna). Simplemente establece que si tomamos elementos del espacio y realizamos las operaciones permitidas (suma o multiplicación escalar), el resultado **nunca saldrá del espacio original** $\mathbf{V}$. Es decir, la suma de dos vectores es un vector, y el escalado de un vector es otro vector. Esta ley es vital, ya que garantiza que las transformaciones de datos en una red neuronal, por ejemplo, siempre producirán un vector que puede ser procesado por la siguiente capa.

### Leyes de la Suma: Las Reglas de la Geometría

Estas leyes aseguran que la combinación de datos es ordenada y consistente, sin importar el orden en que se haga:

* **Asociatividad y Conmutatividad:** Nos dicen que podemos sumar vectores en cualquier orden que queramos (el orden de los sumandos no altera el resultado).
* **Existencia del Neutro y el Opuesto:** Garantizan la reversibilidad. El **vector neutro** ($\mathbf{0}$) nos permite sumar sin cambiar el vector original (el "cero" del espacio), y el **opuesto** ($-\mathbf{v}$) nos permite deshacer cualquier suma, asegurando que las operaciones sean totalmente controlables.

### Leyes de la Escala: El Comportamiento Lineal

Estas leyes describen cómo los escalares interactúan con los vectores, definiendo la naturaleza **lineal** del espacio:

Por un lado la **distributividad**. La multiplicación escalar se distribuye correctamente, tanto si sumamos dos escalares antes de multiplicar un vector, como si sumamos dos vectores antes de multiplicar por un escalar. Esto es lo que permite que las combinaciones lineales se expandan y simplifiquen.

Por otro la **compatibilidad y Neutro Escalar.** Existe un escalar que debe dejar al vector inalterado ($1 \cdot \mathbf{v} = \mathbf{v}$), y la multiplicación de escalares debe ser asociativa (el orden en que escalamos es irrelevante, $(ab)\mathbf{v} = a(b\mathbf{v})$).

Con estas leyes, el espacio vectorial se convierte en un entorno robusto y confiable donde cualquier **combinación lineal** de vectores tiene sentido y se mantiene dentro del conjunto $\mathbf{V}$. En esencia, estas ocho reglas son las que nos permiten asegurar que la **Regresión Lineal**, las **Redes Neuronales** y el **PCA** funcionen tal como esperamos.

> **Ejemplo**:
> El conjunto $\mathbb{R}^n$ de todas las $n$-tuplas de números reales, junto con la suma y multiplicación definidas componente a componente, es el **espacio vectorial canónico** del *machine learning*. Cada vector de $\mathbb{R}^n$ representa un dato con $n$ características, y los escalares $\mathbb{R}$ nos permiten ajustar su peso o magnitud.

> **Para reflexionar...**
> **La ley de clausura es esencial para las redes neuronales. Si una operación en una capa neuronal violara la clausura (por ejemplo, al aplicar una función que produce un vector que ya no es compatible con el espacio de entrada de la siguiente capa), ¿qué tipo de error fundamental surgiría en el proceso de *forward propagation*?**
> *Piense en cómo las dimensiones de los vectores se convierten en la interfaz entre las capas. Si una operación produce un vector con una dimensión diferente a la esperada, la multiplicación matricial de la siguiente capa fallaría automáticamente.*

### La necesidad de un espacio vectorial en Inteligencia Artificial

Para entender por qué los **espacios vectoriales** son tan importantes en inteligencia artificial, no hace falta empezar por las matemáticas, sino por una idea mucho más simple: las máquinas necesitan una forma coherente de **representar el mundo con números**. Todo modelo de IA, por muy sofisticado que sea, se alimenta de datos, y esos datos deben tener una estructura que permita compararlos, transformarlos y combinarlos. Esa estructura es precisamente la que nos da un **espacio vectorial**.

Podemos pensarlo así: un vector no es solo una lista de números, sino una **forma ordenada de describir algo**. Una imagen, un texto o una grabación de voz pueden convertirse en un vector. En ese momento, cada objeto —una palabra, una foto, un sonido— se transforma en un punto dentro de un espacio matemático. Y ese espacio tiene una propiedad maravillosa: podemos **medir distancias**, **sumar puntos**, **calcular direcciones** y **descubrir patrones geométricos**.

Un espacio vectorial, entonces, actúa como el escenario donde los algoritmos de IA pueden operar. Sin él, los datos serían solo colecciones desconectadas de valores. En cambio, al organizarlos dentro de un espacio con reglas claras (como la posibilidad de sumar vectores o multiplicarlos por un número), el modelo puede “moverse” entre ellos, ajustarse, aprender trayectorias y detectar regularidades.

> **Ejemplo**
> Imagina que representamos a cada estudiante por dos características: horas de estudio y nota media. Cada estudiante es un punto en un plano. Si dibujamos todos esos puntos, el conjunto forma una nube de datos. En ese espacio, conceptos como la “distancia” entre estudiantes o la “dirección” en la que aumentan las notas adquieren significado matemático. Un modelo puede aprender que moverse hacia la derecha (más horas) suele implicar moverse hacia arriba (mejores notas).

En IA, esta idea se multiplica en miles de dimensiones. Una palabra en un modelo de lenguaje no está definida por dos o tres números, sino por cientos, cada uno reflejando un matiz de su significado. Pero la esencia sigue siendo la misma: **vivimos dentro de un espacio donde los datos se comportan como vectores**.

La estructura de espacio vectorial también nos da una forma unificada de trabajar. Todos los modelos —desde la regresión lineal hasta las redes neuronales profundas— se basan en operaciones vectoriales. Multiplicar matrices, calcular productos escalares o encontrar combinaciones lineales son, en realidad, maneras de explorar el espacio en busca de las regiones donde los datos se separan mejor, donde los errores son menores o donde la predicción se ajusta al patrón que buscamos.

> **Para reflexionar…**
> **¿Qué pasaría si los datos de un modelo de IA no se pudieran representar como vectores? ¿Cómo podríamos medir similitudes, direcciones o distancias sin una estructura común?**
> *Piensa en cómo el espacio vectorial no es solo una herramienta matemática, sino el lenguaje compartido que permite a los algoritmos aprender, comparar y generalizar entre datos tan distintos como imágenes, textos o sonidos.*

## Dependencia lineal, base y cambio de base

Dentro de esta estructura matemática a la que hemos llamado espacio vectorial, la noción de **dependencia lineal** es de suma importancia. Un conjunto de vectores es linealmente dependiente si al menos uno de ellos puede ser expresado como una **combinación lineal** de los demás. Una combinación lineal no es más que una suma de vectores multiplicados por escalares. Si podemos construir un vector a partir de otros, esto nos indica que ese vector no contiene información nueva y, por lo tanto, es redundante. Esta redundancia es un problema serio para los algoritmos, a menudo manifestado como **multicolinealidad**, que confunde a los modelos y puede llevar a soluciones inestables.

> Ejemplo:
> 
> Considera un modelo que usa dos características: la edad de un cliente en años y su edad en días. El vector que representa "edad en días" es simplemente el vector "edad en años" multiplicado por el escalar 365. Estos dos vectores son linealmente dependientes, ya que uno es una combinación lineal del otro. Un modelo de regresión lineal no podría determinar la contribución única de cada característica al resultado final.

La comprensión de la independencia lineal nos lleva a un concepto crucial: la **base** de un espacio vectorial. Una base es el conjunto más pequeño de vectores linealmente independientes que nos permite representar cualquier otro vector en el espacio a través de una combinación lineal. Piensa en la base como el sistema de coordenadas subyacente de nuestro universo de datos.

> Ejemplo:
> 
> En el caso de los datos de reseñas de películas, si solo usamos las palabras "genial" y "aburrido", nuestra base estaría formada por el vector de "genial" [1,0] y el vector de "aburrido" [0,1]. Cualquier otra reseña en este espacio puede ser descrita como una combinación de estos dos vectores.

La habilidad de encontrar una nueva base que sea más eficiente para nuestro problema es la clave de las técnicas de **reducción de dimensionalidad**, como el **Análisis de Componentes Principales (PCA)**. Estos algoritmos buscan una nueva base que capture la mayor varianza de los datos con el menor número de dimensiones. Al proyectar nuestros datos en esta nueva base, eliminamos la redundancia y comprimimos la información, lo que no solo mejora la eficiencia computacional de los modelos, sino que también puede reducir el ruido y mejorar su rendimiento.

>**Para reflexionar...**
> **Si un modelo de machine learning para predecir precios de casas utiliza como características tanto el tamaño de la casa en metros cuadrados como el tamaño en pies cuadrados, ¿qué implicaciones tendría esto en la dependencia lineal de los datos? ¿Por qué los algoritmos de reducción de dimensionalidad, como el Análisis de Componentes Principales (PCA), buscan encontrar una nueva base para los datos?**
> *Considera cómo el tamaño en metros y pies cuadrados son redundantemente lineales. Piensa en cómo una nueva base podría permitirnos capturar la misma información en un espacio de menor dimensión, eliminando esta redundancia y facilitando el trabajo del modelo.*

#### Cambio de base en espacios vectoriales

Si en un espacio vectorial, la **base** es el conjunto mínimo de vectores linealmente independientes que permite representar cualquier otro vector mediante combinaciones lineales. Cambiar de base significa expresar los mismos vectores en un sistema de coordenadas diferente. Aunque los vectores en sí no cambian —siguen ocupando el mismo lugar en el espacio—, sus **coordenadas** sí lo hacen, porque ahora se describen con respecto a nuevos ejes de referencia.

Matemáticamente, si tenemos una base original $B = {\mathbf{e}_1, \mathbf{e}_2}$ y una nueva base $B' = {\mathbf{b}_1, \mathbf{b}_2}$, cualquier vector $\mathbf{v}$ que en la base original se expresa como

$$
\mathbf{v} = x_1 \mathbf{e}_1 + x_2 \mathbf{e}_2
$$

puede representarse en la nueva base como

$$
\mathbf{v} = y_1 \mathbf{b}_1 + y_2 \mathbf{b}_2
$$

donde $(x_1, x_2)$ y $(y_1, y_2)$ son las coordenadas del mismo vector en bases distintas.



##### Ejemplo en dos dimensiones

Consideremos el plano $\mathbb{R}^2$. La base canónica está formada por los vectores

$$
\mathbf{e}_1 = \begin{bmatrix}1 \\ 0\end{bmatrix}, \quad 
\mathbf{e}_2 = \begin{bmatrix}0 \\ 1\end{bmatrix}.
$$

Supongamos que definimos una nueva base $B'$ con los vectores

$$
\mathbf{b}_1 = \begin{bmatrix}1 \\ 1\end{bmatrix}, \quad 
\mathbf{b}_2 = \begin{bmatrix}-1 \\ 1\end{bmatrix}.
$$

Ahora tomemos un vector en coordenadas canónicas:

$$
\mathbf{v} = \begin{bmatrix}2 \\ 3\end{bmatrix}.
$$

Para expresarlo en la nueva base $B'$, necesitamos encontrar los escalares $y_1$ y $y_2$ que cumplen:

$$
\mathbf{v} = y_1 \mathbf{b}_1 + y_2 \mathbf{b}_2
= y_1 \begin{bmatrix}1 \\ 1\end{bmatrix} + y_2 \begin{bmatrix}-1 \\ 1\end{bmatrix}.
$$

Es decir:

$$
\begin{bmatrix}2 \\ 3\end{bmatrix} = \begin{bmatrix} y_1 - y_2 \\ y_1 + y_2 \end{bmatrix}.
$$

Esto nos da el sistema:

$$
\begin{cases}
y_1 - y_2 = 2 \\
y_1 + y_2 = 3
\end{cases}
$$

Resolviendo:

$$
y_1 = \tfrac{5}{2}, \quad y_2 = \tfrac{1}{2}.
$$

Por tanto, en la base $B'$ el vector $\mathbf{v}$ se representa como

$$
[\mathbf{v}]_{B'} = \begin{bmatrix}\tfrac{5}{2} \\ \tfrac{1}{2}\end{bmatrix}.
$$

El vector $\mathbf{v}$ sigue ocupando la misma posición en el plano, pero dependiendo de la base elegida, sus **coordenadas numéricas cambian**. En la base canónica lo describimos como $(2,3)$, mientras que en la base $B'$ lo describimos como $(2.5, 0.5)$.

Este cambio de perspectiva es esencial en IA porque permite elegir bases que simplifiquen los cálculos o eliminen redundancias en los datos, como ocurre en métodos de reducción de dimensionalidad (por ejemplo, PCA).

> **Para reflexionar…**
> **¿Qué ventajas podría tener usar una base “adaptada a los datos” en lugar de la base canónica? ¿Por qué crees que técnicas como PCA buscan una nueva base que maximice la varianza explicada de los datos?**

#### Aplicaciones del cambio de base en inteligencia artificial

El cambio de base no es un simple artificio matemático, sino una herramienta poderosa en el tratamiento de datos para la inteligencia artificial. Al modificar el sistema de referencia en el que representamos los vectores, los datos conservan su esencia, pero adquieren nuevas propiedades que pueden ser más útiles para los algoritmos de aprendizaje.

Una primera aplicación es la **decorrelación de variables**. En muchos problemas de aprendizaje supervisado, las características originales están fuertemente correlacionadas entre sí, lo que provoca inestabilidad en modelos como la regresión lineal o la logística. Cambiar de base permite generar un nuevo sistema de coordenadas en el que las variables se comportan de manera más independiente, facilitando la interpretación y mejorando la robustez del modelo.

Otra aplicación esencial es la relacionada con las **métricas de distancia y similitud**. Algoritmos como $k$-means o $k$-NN dependen críticamente de cómo medimos la proximidad entre instancias. En la base original, dos puntos pueden parecer cercanos o lejanos de manera engañosa debido a la escala o correlación entre las variables. Al redefinir la base, podemos situar los datos en un espacio donde las distancias sean más significativas y reflejen mejor la estructura subyacente de los datos.

El cambio de base también desempeña un papel clave en la **optimización numérica**. En algoritmos como el descenso de gradiente, la forma de las curvas de nivel de la función de coste depende de la base en la que nos situemos. Si los datos se expresan en un sistema con escalas equilibradas y sin redundancias, el descenso se vuelve más directo y eficiente, evitando zigzags innecesarios y acelerando la convergencia hacia el mínimo.

En el ámbito de la **extracción de características latentes**, el cambio de base permite descubrir factores ocultos que explican la variabilidad de los datos. Técnicas como el análisis de componentes principales (PCA), el análisis de componentes independientes (ICA) o los autoencoders se apoyan en esta idea: encontrar un nuevo sistema de referencia que concentre la información en menos dimensiones o que revele estructuras que permanecían ocultas en la representación original.

Finalmente, el cambio de base puede favorecer la **interpretabilidad de los modelos**. En visión por computador, por ejemplo, es habitual que tras una transformación los ejes del nuevo espacio se alineen con patrones visuales concretos, como bordes, texturas o colores. Estos nuevos ejes no solo simplifican el cálculo, sino que también facilitan la comprensión del proceso interno por el que un modelo toma sus decisiones.

> **Para reflexionar…**
>  **Si un modelo de clasificación no logra distinguir entre dos clases en el espacio de características original, ¿cómo podría ayudar un cambio de base a que las clases fueran más separables? ¿Qué papel juega aquí la geometría de los datos?**

##### Ejemplo práctico: cambio de base en un espacio de características bidimensional

Imaginemos que tenemos un conjunto de puntos en el plano, cada uno representando a un estudiante según dos características muy simples:

* **Horas de estudio** ($x$).
* **Horas de descanso** ($y$).

Así, un estudiante que estudia 4 horas y descansa 6 se representaría como el vector:

$$
\mathbf{v} = \begin{bmatrix}4 \\ 6\end{bmatrix}.
$$

En la **base canónica** (los ejes habituales $x$ e $y$), este vector se describe como “4 hacia la derecha y 6 hacia arriba”.

Ahora pensemos que queremos analizar la relación entre el **equilibrio** entre estudio y descanso, y la **carga total** de horas. Para ello, definimos una **nueva base** con dos vectores:

$$
\mathbf{b}_1 = \begin{bmatrix}1 \\ 1\end{bmatrix}, \quad
\mathbf{b}_2 = \begin{bmatrix}1 \\ -1\end{bmatrix}.
$$

* $\mathbf{b}_1$ representa el eje “total de horas” (suma de estudio y descanso).
* $\mathbf{b}_2$ representa el eje “diferencia entre estudio y descanso”.

Queremos expresar el vector $\mathbf{v} = \begin{bmatrix}4 \ 6\end{bmatrix}$ en esta nueva base. Buscamos $y_1, y_2$ tales que:

$$
\mathbf{v} = y_1 \mathbf{b}_1 + y_2 \mathbf{b}_2
= y_1 \begin{bmatrix}1 \\ 1\end{bmatrix} + y_2 \begin{bmatrix}1 \\ -1\end{bmatrix}.
$$

Esto equivale a resolver:

$$
\begin{bmatrix}4 \\ 6\end{bmatrix} =
\begin{bmatrix} y_1 + y_2 \\ y_1 - y_2 \end{bmatrix}.
$$

De donde obtenemos el sistema:

$$
\begin{cases}
y_1 + y_2 = 4 \\
y_1 - y_2 = 6
\end{cases}
$$

Resolviendo:

$$
y_1 = 5, \quad y_2 = -1.
$$

En la nueva base, el mismo vector se representa como:

$$
[\mathbf{v}]_{B'} = \begin{bmatrix}5 \\ -1\end{bmatrix}.
$$

Es decir, en la base original, veíamos al estudiante como “4 horas de estudio, 6 horas de descanso”. En la nueva base, lo vemos como “5 horas totales, con un desequilibrio de -1 (más descanso que estudio)”.

El vector no ha cambiado de lugar en el plano, pero el **punto de vista matemático** nos ofrece ahora información más alineada con la pregunta que queremos responder:

* ¿Cuántas horas totales dedica el estudiante?
* ¿Está equilibrado entre estudio y descanso, o favorece uno sobre el otro?

Este ejemplo muestra cómo un cambio de base no altera los datos, pero **resalta propiedades distintas** según el problema que queramos analizar.

Elegir una base es como elegir el **punto de vista matemático** desde el que miramos los datos.

- Si el objetivo es eliminar redundancia, elegimos una base donde las variables estén decorrelacionadas (como en PCA).
- Si el objetivo es mejorar la separación entre clases, podemos buscar una base donde las categorías sean más distinguibles (como en *Linear Discriminant Analysis*).
- Si el objetivo es interpretar mejor, podemos escoger ejes que se correspondan con factores significativos (por ejemplo, “total de horas” y “equilibrio”).

Así, el cambio de base es un paso consciente: no se trata de cambiar por cambiar, sino de **alinear la representación de los datos con el objetivo del análisis o del modelo**.

> **Para reflexionar...**\
> **Si en lugar de estudiantes quisiéramos analizar dietas (proteínas y carbohidratos), ¿cómo podríamos definir una nueva base que refleje el “total de calorías” y el “equilibrio entre nutrientes”?**

