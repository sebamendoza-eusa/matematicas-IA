El álgebra lineal en la representación de datos
===

## Datos como vectores

El primer paso para que una máquina pueda aprender de los datos es traducirlos a un lenguaje que pueda procesar: ese lenguaje es el de los **números**. En matemáticas, la forma más natural de agrupar números relacionados entre sí es mediante un **vector**. Así, representar los datos como vectores se convierte en el puente entre el mundo real y el mundo de los algoritmos.

Hemos visto que un vector no es más que una lista ordenada de valores, y cada valor suele corresponder a una **característica** del objeto que estamos describiendo. Por ejemplo, si pensamos en el perfil de un estudiante, podríamos asignar un valor a su edad, otro a su nota media y otro al número de asignaturas aprobadas. El vector resultante tendría la forma $(20, 7.5, 8)$ y serviría como una “huella matemática” de ese estudiante.

El poder de esta representación es que permite colocar a cada individuo dentro de un espacio de coordenadas. Así, los estudiantes no son ya solo nombres o personas, sino **puntos en un espacio de características**, donde podemos medir distancias, buscar semejanzas y encontrar patrones.

La misma lógica se aplica a otros tipos de datos. Un correo electrónico puede representarse como un vector en el que cada componente refleja la presencia de una palabra concreta o la frecuencia con que aparece. Una imagen puede transformarse en un vector donde cada número corresponde a la intensidad de color de un píxel. Incluso un sonido puede convertirse en un vector que refleja la amplitud de la onda en distintos momentos.

En todos estos casos, lo esencial es que los datos —independientemente de su naturaleza original— se acaban describiendo como **colecciones de números**. Esta homogeneidad hace posible que los algoritmos de inteligencia artificial operen siempre en el mismo terreno: el de los vectores.



>**Para reflexionar…**
>**¿Qué ventaja crees que tiene representar datos tan distintos como un texto, una imagen o un audio en la misma forma matemática de un vector? ¿Cómo facilita esto que un mismo tipo de algoritmo pueda aplicarse a problemas aparentemente muy diferentes?**

#### Ejemplo: un correo electrónico como vector

Imagina que queremos entrenar un sistema muy básico que distinga entre correos “spam” y “no spam”. Para hacerlo, debemos representar cada correo como un conjunto de números que recojan algunas de sus características más simples.

Podemos fijarnos, por ejemplo, en tres aspectos:

- la **longitud del correo** en caracteres,
- el **número de enlaces** que contiene,
- la **frecuencia de la palabra “gratis”**.

Supongamos que tenemos un correo con el siguiente texto:

> “Consigue un viaje gratis ahora. Haz clic en este enlace.”

Si lo analizamos, obtenemos:

- longitud: $50$ caracteres,
- enlaces: $1$,
- frecuencia de la palabra “gratis”: $1$.

Esto nos da el vector
$$
\mathbf{v} = [50, 1, 1].
$$
Ese vector es la representación numérica del correo. Otro correo diferente, con $200$ caracteres, $3$ enlaces y la palabra “gratis” apareciendo $5$ veces, sería
$$
\mathbf{v} = [200, 3, 5].
$$
Aunque ambos textos se ven muy distintos a simple vista, en el mundo del álgebra lineal se convierten en **puntos dentro de un mismo espacio de características**.

Si situamos cada correo como un punto en un espacio tridimensional (una dimensión por cada característica), veremos que los correos “spam” tienden a agruparse en zonas donde hay muchos enlaces y una alta frecuencia de la palabra “gratis”. En cambio, los correos “no spam” aparecen en zonas con valores bajos en esas dimensiones.

Este ejemplo muestra la esencia de la IA: lo que para nosotros es un texto o una imagen, para el algoritmo es un vector de números en un espacio geométrico.



>**Para reflexionar…**
>**¿Cómo crees que cambiaría la precisión del modelo si, en lugar de tres características, usáramos cien o mil? ¿Qué problema podría surgir al aumentar tanto el número de dimensiones?**

## Conjuntos de datos como matrices

Cuando trabajamos con un único objeto, como un correo o una imagen, resulta suficiente representarlo como un vector. Sin embargo, en inteligencia artificial rara vez nos interesa un solo dato: lo que necesitamos es analizar **muchos ejemplos al mismo tiempo**. Para ello, en lugar de pensar en vectores aislados, organizamos los datos en forma de **matriz**.

En esta matriz, cada **fila** representa una instancia (un ejemplo del conjunto de datos), mientras que cada **columna** corresponde a una característica. De este modo, un conjunto de datos de tamaño moderado puede verse como una tabla de números donde las filas son individuos y las columnas describen atributos.

Podemos imaginar un ejemplo sencillo con tres correos electrónicos representados por las mismas características que antes: longitud, número de enlaces y frecuencia de la palabra “gratis”. La matriz de datos sería:

$$
\mathbf{X} =
\begin{bmatrix}
50 & 1 & 1 \\
200 & 3 & 5 \\
120 & 0 & 0
\end{bmatrix}
$$

Aquí, cada fila es un correo y cada columna una característica. La primera columna recoge las longitudes, la segunda el número de enlaces y la tercera la frecuencia de la palabra “gratis”.

Esta forma matricial no solo es práctica para organizar los datos, sino que también permite aplicar directamente operaciones algebraicas. Sumar, escalar o multiplicar matrices equivale a transformar simultáneamente todo el conjunto de ejemplos, lo que es esencial cuando entrenamos modelos.

La interpretación geométrica de esta representación es especialmente poderosa. Podemos pensar que cada fila de la matriz es un punto en un espacio de características. Al juntar todos esos puntos, obtenemos una nube de datos que revela patrones, agrupaciones y relaciones que, en dimensiones bajas, puede incluso ser visualizada. Sin embargo, en general, se trabaja en espacios de muchas dimensiones, del orden de miles o cientos de miles. En estos casos la geometría sigue siendo la clave para que los algoritmos encuentren patrones y estructuras.



>**Para reflexionar…**
>**¿Qué ventaja tiene organizar los datos en forma matricial frente a tratar cada vector por separado? ¿Cómo facilita esto que un algoritmo aprenda patrones comunes a partir de muchos ejemplos a la vez?**

### La matriz como transformación

Hasta aquí hemos entendido la matriz como un **almacén de datos**. Pero en inteligencia artificial también debemos verla como un **operador que transforma esos datos**. Si $\mathbf{X}$ es nuestra matriz de ejemplos y $\mathbf{W}$ una matriz de pesos, el producto

$$
\mathbf{X}\mathbf{W}
$$

nos da una **nueva representación** de los mismos ejemplos en otro espacio de características. Así ocurre, por ejemplo, en un modelo lineal de clasificación o en una capa de una red neuronal: la información original se proyecta en otro espacio donde resulta más fácil separar o reconocer patrones.

De este modo, las matrices cumplen una doble función: **organizan datos y al mismo tiempo actúan como reglas de transformación**. Esta visión es la que da sentido a muchas operaciones que veremos más adelante en el curso.



>**Para reflexionar…**
>**¿Qué diferencia hay entre entender una matriz como un simple “contenedor de datos” y verla como un “operador de transformación”? ¿Cómo cambia nuestra forma de pensar sobre el aprendizaje automático si aceptamos esta doble naturaleza?**

##### Ejemplo: transformación de un conjunto de datos

Supongamos que tenemos una matriz que representa a tres estudiantes con dos características: su **nota media** y las **horas de estudio semanales**.

$$
\mathbf{X} =
\begin{bmatrix}
7 & 10 \\
8 & 12 \\
5 & 6
\end{bmatrix}
$$

Cada fila es un estudiante y cada columna una característica.

Ahora definimos una matriz de pesos $\mathbf{W}$ que sirve para combinar estas dos características en una sola medida global:

$$
\mathbf{W} =
\begin{bmatrix}
0.5 \\
0.5
\end{bmatrix}
$$

Al calcular

$$
\mathbf{X}\mathbf{W} =
\begin{bmatrix}
7 & 10 \\
8 & 12 \\
5 & 6
\end{bmatrix}
\begin{bmatrix}
0.5 \\
0.5
\end{bmatrix},
$$

obtenemos

$$
\begin{bmatrix}
8.5 \\
10 \\
5.5
\end{bmatrix}.
$$

El resultado es un nuevo vector que asigna a cada estudiante una puntuación combinada, donde se da el mismo peso a la nota media y a las horas de estudio. En este ejemplo tan básico, la matriz $\mathbf{W}$ ha actuado como una **regla de transformación lineal**, convirtiendo dos características en una sola.

Esto muestra cómo el producto de matrices permite construir nuevas representaciones a partir de los datos originales, algo que está en el corazón de modelos como la regresión lineal o las redes neuronales.

## Operaciones con datos en forma matricial

La verdadera potencia del álgebra lineal aplicada a la inteligencia artificial no está solo en representar los datos como vectores o matrices, sino en las **operaciones** que podemos realizar con ellos. Cada operación matricial encierra una interpretación: a veces significa combinar información, otras proyectar los datos en un espacio diferente o incluso medir relaciones entre ejemplos. Entender esta lógica es lo que permite ver cómo los algoritmos “piensan” cuando procesan información.

### Combinaciones lineales y suma de vectores

Si tenemos dos vectores que representan ejemplos de datos, su suma o resta nos da un nuevo vector que puede interpretarse como una combinación de los anteriores. Esto es útil porque nos permite **construir representaciones derivadas**.

Imaginemos que un vector describe las preferencias de un usuario de música y otro vector representa un artista. La suma de ambos puede dar lugar a un perfil ajustado del usuario tras escuchar ese artista. Este mecanismo de ajuste se utiliza en sistemas de recomendación, donde los vectores no solo describen, sino que también **evolucionan mediante combinaciones lineales**.

### Producto escalar y similitud

El producto escalar entre dos vectores no es una simple operación numérica: mide cuán alineados están esos vectores en el espacio. Cuando trabajamos con datos representados como vectores, esta operación se convierte en una herramienta para medir **similitud**.

Por ejemplo, si dos documentos se representan como vectores de frecuencias de palabras, el producto escalar refleja la cercanía en el uso del vocabulario. Esta idea está en la base de métodos clásicos de búsqueda de información y sigue presente en modelos modernos de procesamiento del lenguaje natural.

### Multiplicación de una matriz por un vector

Cuando multiplicamos una matriz por un vector, no estamos solo haciendo cálculos mecánicos: estamos aplicando una **transformación**. Si la matriz contiene pesos, el resultado es una nueva representación del vector original.

Por ejemplo, en un modelo lineal de predicción, este producto equivale a combinar las características de entrada para generar una salida. En redes neuronales, cada capa funciona exactamente así: recibe un vector de activaciones, lo multiplica por una matriz de pesos y lo transforma en otro vector que pasa a la siguiente capa.

### Multiplicación de matrices

Cuando la operación se extiende a matrices completas, la interpretación se amplifica. Multiplicar $\mathbf{X}$ (una matriz de datos con muchos ejemplos como filas) por una matriz de pesos $\mathbf{W}$ equivale a aplicar **la misma transformación a todos los ejemplos simultáneamente**.

Esto es crucial porque permite aprovechar la estructura matricial para procesar miles de ejemplos en paralelo. De este modo, lo que sería un proceso repetitivo se convierte en una sola operación algebraica. La eficiencia computacional de la IA moderna depende en gran medida de este principio.

Un caso práctico es la propagación de datos en un modelo de clasificación: la matriz de entrenamiento $\mathbf{X}$ se multiplica por los pesos $\mathbf{W}$ y genera una matriz de predicciones $\mathbf{Y}$. Cada fila de $\mathbf{Y}$ corresponde a la salida de un ejemplo del conjunto de datos, transformado en la misma operación.

### Normalización y escalado

Otra aplicación fundamental de las operaciones matriciales es la **normalización de los datos**. Al escalar las filas o columnas de una matriz de datos, conseguimos que ninguna característica domine a las demás por tener valores más grandes.

Por ejemplo, si en un dataset de viviendas una columna mide metros cuadrados y otra mide precio en euros, la magnitud del precio podría eclipsar a las demás variables. Aplicar transformaciones matriciales que normalizan columnas garantiza que cada característica tenga un peso comparable. Este ajuste es esencial en algoritmos como el descenso de gradiente, que funcionan mejor cuando todas las dimensiones están en escalas similares.

### Conexión con embeddings y representaciones

En procesamiento del lenguaje natural, una palabra puede representarse como un vector (embedding). Cuando aplicamos una matriz de transformación a estos embeddings, estamos proyectando las palabras en un nuevo espacio semántico, donde las relaciones resultan más fáciles de detectar. Lo mismo ocurre en visión por computador: los píxeles de una imagen se combinan mediante matrices para generar representaciones más compactas y ricas.

La idea general es que cada operación matricial acerca los datos un paso más hacia una forma que el algoritmo pueda aprovechar. Así, la matemática no se queda en un cálculo abstracto, sino que se convierte en el mecanismo que hace posible que la máquina **entienda** patrones.



>**Para reflexionar…**
>**¿Por qué es tan poderoso que una misma operación matricial pueda aplicarse a todo un conjunto de ejemplos a la vez? ¿Cómo crees que influye esto en la rapidez y la eficiencia de los algoritmos de IA modernos?**

## Espacios vectoriales y reducción de dimensionalidad

Al representar los datos en forma de vectores, entramos en lo que se denomina un **espacio vectorial**. Este espacio no es más que el conjunto de todos los vectores posibles que podemos construir a partir de nuestras características, junto con las operaciones que permiten sumarlos y multiplicarlos por escalares. Dicho de otro modo, el espacio vectorial es el escenario matemático en el que “viven” nuestros datos.

En apuntes anteriores ya hemos visto cómo los vectores describen instancias individuales y cómo las matrices agrupan conjuntos completos de ejemplos. También hemos introducido nociones como **independencia lineal** y **autovectores**, que son piezas fundamentales para comprender la estructura interna de un espacio vectorial. Lo que interesa ahora es entender cómo estas ideas se aplican a un problema central en inteligencia artificial: la **complejidad de la dimensionalidad**.

Cuando el número de características es pequeño, como en los ejemplos de correos o estudiantes, podemos visualizar los datos en dos o tres dimensiones y captar con facilidad patrones y relaciones. Sin embargo, en IA lo habitual es trabajar con cientos o miles de dimensiones: cada palabra de un vocabulario puede ser una característica, cada píxel de una imagen puede convertirse en una coordenada. A este fenómeno se le conoce como **maldición de la dimensionalidad**, y su efecto es que los datos se dispersan y los patrones se vuelven más difíciles de identificar.

El álgebra lineal ofrece una respuesta poderosa a este problema mediante las técnicas de **reducción de dimensionalidad**. La idea central es que, aunque nuestros datos estén descritos con muchas características, no todas son igual de importantes. A menudo existen relaciones lineales entre ellas que nos permiten describir la información esencial con un número mucho menor de dimensiones.

Aquí reaparece el papel de los autovalores y autovectores. Cuando aplicamos un método como el **Análisis de Componentes Principales (PCA)**, lo que estamos haciendo es encontrar una nueva base del espacio vectorial formada por autovectores de la matriz de covarianza. Esa base tiene la propiedad de que cada dirección captura una parte de la variabilidad de los datos, medida por los autovalores. Manteniendo solo las direcciones asociadas a autovalores grandes, logramos representar los datos en un espacio de menor dimensión, pero sin perder lo que realmente los caracteriza.

Esta compresión no es solo una cuestión de ahorro computacional. Al eliminar redundancia y ruido, los modelos pueden centrarse en las relaciones verdaderamente significativas. Así, la reducción de dimensionalidad cumple una doble función: hace más eficiente el cálculo y al mismo tiempo mejora la calidad del aprendizaje.

Podemos pensar en un ejemplo intuitivo. Imagina un conjunto de datos sobre casas donde registramos la superficie en metros cuadrados y también en pies cuadrados. Ambas características contienen la misma información con distinta escala, de modo que añadir las dos no aporta nada nuevo. El PCA detectaría que una de esas direcciones no añade variabilidad real y nos permitiría prescindir de ella, simplificando el espacio vectorial sin perder información.



>**Para reflexionar…**\
>**¿Qué implicaciones tiene para un algoritmo de IA que los datos se encuentren en un espacio de miles de dimensiones? ¿Cómo ayuda la reducción de dimensionalidad a que la máquina no se “pierda” en ese espacio demasiado amplio?**



## Interpretación geométrica de la representación

Al traducir datos en vectores y matrices, no solo obtenemos una estructura numérica manejable por los algoritmos. También entramos en un terreno geométrico donde conceptos como **distancia, dirección y ángulo** nos permiten dar sentido a las relaciones entre ejemplos.

Cada fila de una matriz de datos puede pensarse como un punto en un espacio de características. Cuando colocamos todos los ejemplos juntos, lo que tenemos es una **nube de puntos**. La geometría de esa nube encierra información sobre el problema: si los puntos se agrupan en regiones separadas, puede que esas regiones correspondan a distintas clases; si se alinean a lo largo de una dirección dominante, puede que esa dirección represente un factor común a todos ellos.

En este marco, las **distancias** son fundamentales. La distancia euclidiana, que mide la longitud del segmento que une dos puntos, nos dice qué ejemplos están más próximos entre sí. En problemas de clasificación o recomendación, esa cercanía se traduce en similitud: usuarios con vectores próximos tienden a tener preferencias parecidas; imágenes con vectores similares suelen pertenecer a la misma categoría.

Junto a la distancia aparece el concepto de **ángulo** entre vectores. Medir el coseno de ese ángulo nos permite saber si dos vectores apuntan en direcciones similares, independientemente de su tamaño. Esta métrica, conocida como **similitud de coseno**, es muy utilizada en procesamiento de lenguaje natural, porque dos documentos pueden ser largos o cortos, pero lo que realmente interesa es si hablan de lo mismo, es decir, si están alineados en el espacio de características.

La interpretación geométrica nos lleva a una conclusión poderosa: los algoritmos de IA no trabajan directamente con “correos”, “imágenes” o “usuarios”, sino con posiciones en un espacio de coordenadas. Clasificar, agrupar o recomendar no es más que buscar relaciones geométricas en esa nube de puntos.



>**Para reflexionar…**\
>**¿Qué crees que significa, en términos prácticos, que dos vectores de datos sean “ortogonales”, es decir, que formen un ángulo recto en el espacio? ¿Podría interpretarse como que representan ejemplos totalmente distintos, sin relación alguna?**





