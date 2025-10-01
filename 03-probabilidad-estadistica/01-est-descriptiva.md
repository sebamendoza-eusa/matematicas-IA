Fundamentos de estadística descriptiva 
===

Concepto general de estadística descriptiva
---

Cuando trabajamos con datos, lo primero que nos encontramos suele ser una colección enorme de números. Pueden ser las calificaciones de una clase, los ingresos de una empresa, las mediciones de sensores o la cantidad de interacciones que recibe una publicación en redes sociales. En bruto, esa información resulta difícil de comprender: una tabla con miles de registros no nos dice nada a simple vista. La mente humana necesita **resúmenes** que nos permitan captar la esencia de los datos sin perdernos en el detalle.

La **estadística descriptiva** nace precisamente para eso. Su objetivo es **condensar la información** en unos pocos números que la representen de manera sintética. Estos valores actúan como una especie de “radiografía” de los datos, ofreciendo al instante una idea de cuál es su centro, cuánta variabilidad presentan o si tienden a concentrarse en torno a ciertos valores. Es lo que llamamos medidas de tendencia central y de dispersión, que veremos más adelante.

La importancia de esta condensación es doble. Por un lado, facilita la comprensión de un conjunto de datos en un vistazo rápido, sin necesidad de recorrer cada elemento uno por uno. Por otro, permite **comparar conjuntos distintos** de manera justa. Si dos grupos de estudiantes tienen calificaciones muy diferentes en número y extensión, podemos usar medidas descriptivas para valorar de forma objetiva cuál es su rendimiento típico y si ambos grupos muestran comportamientos similares o no.

En inteligencia artificial este paso inicial es crucial. Antes de entrenar un modelo, necesitamos conocer la “personalidad” de los datos: si están equilibrados o descompensados, si presentan valores extremos que podrían sesgar las conclusiones, o si hay patrones simples que ya se vislumbran sin necesidad de algoritmos complejos. La estadística descriptiva es, en ese sentido, **la primera capa de inteligencia** aplicada a los datos: nos orienta, nos alerta y nos prepara para decisiones posteriores.

Podemos pensar en ella como la diferencia entre hojear un resumen ejecutivo y leer un informe de cien páginas. El detalle completo siempre está ahí, pero lo que guía la acción es esa síntesis que capta lo fundamental. En el caso de los datos, la estadística descriptiva es ese resumen: un puente entre la complejidad del mundo real y la claridad que necesita la mente —y, por extensión, los modelos de IA— para aprender de él.

> **Para reflexionar…**
>  ¿Hasta qué punto crees que es seguro tomar decisiones basadas únicamente en resúmenes estadísticos? ¿En qué situaciones sería suficiente trabajar con medidas agregadas, y en cuáles podría ocultar detalles importantes que cambian la interpretación de los datos?

Medidas de tendencia central
---

Al enfrentarnos a un conjunto de datos, una de las primeras preguntas que surge es: **¿dónde está el centro?**. En otras palabras, ¿cuál es el valor típico que resume la colección? Las medidas de tendencia central buscan responder a esa cuestión ofreciendo distintos modos de definir lo “central”. Cada una lo hace con una lógica distinta y, por ello, conviene comprender sus matices y cuándo resulta más adecuada.

La **media aritmética** es la más familiar. Se calcula sumando todos los valores y dividiendo entre el número de observaciones. Puede pensarse como el **centro de gravedad** de los datos: si cada dato fuese un peso colocado sobre una línea, la media sería el punto en el que la balanza queda equilibrada. Su popularidad se debe a que aprovecha toda la información disponible y ofrece un valor representativo en muchos contextos. En inteligencia artificial aparece constantemente. El **error cuadrático medio**, una de las funciones de coste más utilizadas, se basa en medir las desviaciones respecto a la media. Sin embargo, la media tiene una debilidad: es muy sensible a valores extremos. Un solo dato anormalmente grande o pequeño puede arrastrar su valor de forma desproporcionada.

Cuando los datos presentan esa clase de valores extremos, la **mediana** ofrece una alternativa más robusta. La mediana es simplemente el valor que queda justo en el centro una vez que los datos están ordenados. Divide al conjunto en dos mitades iguales: la mitad de las observaciones quedan por debajo y la otra mitad por encima. Esa simplicidad le da una gran resistencia frente a valores atípicos. Imagina un grupo de sueldos donde la mayoría de las personas cobran en torno a 1.500 euros, pero hay un directivo con un salario de 100.000. La media subiría bruscamente, dando la impresión de que el salario “típico” es mucho más alto. La mediana, en cambio, seguiría reflejando con fidelidad el valor central de la mayoría. En análisis de datos, usar la mediana en lugar de la media puede mejorar la **robustez** del modelo y evitar que unos pocos valores distorsionen el panorama general.

La tercera medida de tendencia central es la **moda**, el valor que más veces se repite. Aunque puede parecer menos refinada, tiene un papel clave cuando el interés se centra en la **frecuencia**. Es especialmente útil con variables categóricas, donde no tiene sentido calcular medias o medianas. Si recogemos el color de los coches que circulan por una avenida, la moda indica el color más común. En el terreno de la inteligencia artificial, esta idea se conecta con algoritmos de clasificación. Un ejemplo claro es el método de los **vecinos más cercanos (k-NN)**: al clasificar un nuevo dato, el algoritmo mira a los ejemplos más próximos en el conjunto de entrenamiento y asigna la clase más frecuente entre ellos. Es decir, aplica la lógica de la moda en un contexto local.

Cada una de estas medidas responde a una visión distinta de lo que significa ser “típico”. La media busca el equilibrio numérico, la mediana apunta al punto que divide en dos y la moda resalta la frecuencia. En conjunto forman un tríptico que, utilizado con criterio, permite describir con precisión el centro de un conjunto de datos y anticipar cómo estos resúmenes influyen en la construcción de modelos de IA.

> **Para reflexionar…**
>  Si tuvieras que resumir los resultados de un examen para informar a los alumnos, ¿qué medida escogerías? ¿La media, que da un promedio general, la mediana, que refleja la posición central, o la moda, que muestra la nota más repetida? ¿Crees que cada una transmitiría un mensaje distinto sobre el mismo grupo?

### Fórmulas y ejemplos

Las tres medidas de tendencia central —media, mediana y moda— no son solo conceptos intuitivos; también tienen expresiones matemáticas precisas que permiten calcularlas y aplicarlas a problemas de datos. Veamos cada una con más detalle y con ejemplos sencillos que ilustren su papel en el análisis y en la inteligencia artificial.

#### Media aritmética

Si tenemos un conjunto de $n$ observaciones $x_1, x_2, \dots, x_n$, la media aritmética se define como

$$
\bar{x} = \frac{1}{n}\sum_{i=1}^n x_i
$$

Por ejemplo, si las calificaciones de un alumno en cuatro tareas son $[6, 7, 9, 8]$, su media sería

$$
\bar{x} = \frac{6+7+9+8}{4} = 7.5
$$

La interpretación es que, en promedio, el rendimiento del alumno se sitúa en 7.5.

En inteligencia artificial, esta fórmula aparece de manera recurrente. El **Error Cuadrático Medio (MSE)**, que es una de las funciones de coste más utilizadas, no es más que la media de los errores al cuadrado entre las predicciones $\hat{y}_i$ y los valores reales $y_i$:

$$
MSE = \frac{1}{n}\sum_{i=1}^n (\hat{y}_i - y_i)^2
$$

Aquí la media actúa como resumen del rendimiento global del modelo sobre todo el conjunto de datos.

#### Mediana

La mediana requiere ordenar los datos de menor a mayor. Si $n$ es impar, la mediana es el valor central; si $n$ es par, se toma la media de los dos valores centrales.

Por ejemplo, con los datos $[5, 7, 8, 9, 12]$, la mediana es $8$, porque es el valor en la tercera posición. Con $[5, 7, 8, 9]$, la mediana se obtiene promediando los dos valores centrales:

$$
\text{Mediana} = \frac{7+8}{2} = 7.5
$$

En IA, la mediana es muy útil en tareas de **preprocesamiento de datos**. Si tenemos valores perdidos en una variable, sustituirlos por la mediana suele ser más robusto que usar la media, porque evita que valores atípicos distorsionen el resultado. También se utiliza en métricas como el **Error Absoluto Mediano (MedAE)**, que mide la desviación típica de las predicciones sin dejarse arrastrar por grandes errores aislados.

### Moda

La moda es el valor más frecuente en el conjunto de datos. Si tenemos $[2, 4, 4, 6, 7, 7, 7, 9]$, la moda es $7$, porque aparece más veces que el resto.

En variables categóricas, como en este ejemplo de conjunto de colores, $[\text{rojo}, \text{azul}, \text{azul}, \text{verde}]$, la moda sería “azul”.

### Comparación y uso en IA

Imaginemos un conjunto de datos que contiene el número de visitas diarias a una página web durante una semana:

$$
[100, 120, 150, 110, 105, 300, 115]
$$

* La **media** es
  $$
  \bar{x} = \frac{100+120+150+110+105+300+115}{7} = 157.14
  $$

* La **mediana**, al ordenar los datos $[100, 105, 110, 115, 120, 150, 300]$, es $115$.

* La **moda** no existe en sentido estricto porque ningún valor se repite, aunque en datos grandes siempre suele aparecer un valor más frecuente.

¿Qué aprendemos? La media está claramente arrastrada hacia arriba por el día con 300 visitas (un valor atípico). La mediana refleja mejor el comportamiento típico de la mayoría de los días. Esto es exactamente lo que ocurre en IA al analizar variables con outliers: según la métrica elegida, el modelo se verá más o menos influido por esos extremos.

> **Para reflexionar…**
> En un sistema de recomendación, ¿crees que sería más útil calcular la media de las calificaciones de un usuario, o la mediana? ¿Qué pasaría si ese usuario tiende a dar puntuaciones extremas (muy bajas o muy altas) que podrían distorsionar la media?

Medidas de dispersión
---

Las medidas de dispersión nos cuentan una parte de la historia que la media, la mediana o la moda no alcanzan a revelar. Saber que la nota media de una clase es un 7 no es lo mismo si casi todos los estudiantes rondan ese valor, o si en realidad hay una mezcla de sobresalientes y suspensos que se compensan. La dispersión mide justamente ese “grado de acuerdo” entre los datos: cuando es baja, los valores son parecidos y describen un comportamiento homogéneo; cuando es alta, los datos se dispersan por todo el rango posible y muestran gran diversidad.

En el contexto de la inteligencia artificial, esta diferencia es clave. Un modelo entrenado con datos muy dispersos afronta más dificultad para encontrar patrones estables, porque cada ejemplo parece distinto del anterior. En cambio, con datos poco dispersos, los patrones son más consistentes y el modelo puede captarlos con más facilidad. Así, entender la dispersión no es solo un ejercicio matemático: es tomar conciencia de cuánto “ruido” y cuánta “regularidad” hay en la información con la que trabajará el algoritmo.

En resumen, las **medidas de dispersión**, nos indican cuánto se alejan los datos de su centro. Estas medidas son la clave para entender la “forma” de los datos más allá de su posición central y resultan fundamentales en inteligencia artificial, porque la dispersión afecta directamente al rendimiento y la estabilidad de los modelos.

### Rango

La medida más sencilla de dispersión es el **rango**, definido como la diferencia entre el valor máximo y el valor mínimo de los datos.

$$
R = \max(x_i) - \min(x_i)
$$

Si las calificaciones de un grupo son $[5,6,7,8,9]$, el rango es $9-5=4$. Si otro grupo tiene $[2,4,8,10]$, el rango es $10-2=8$. Aunque las medias pueden ser similares, el segundo grupo muestra una mayor amplitud de notas.

En IA, el rango puede alertarnos de la **escala de los datos**. Si una característica tiene un rango de 0 a 1000 y otra solo de 0 a 10, la primera dominará en cálculos de distancia o productos escalares. Por eso se suele aplicar **escalado** o normalización antes de entrenar un modelo.

### Varianza y desviación estándar

El rango es útil, pero depende únicamente de dos valores (máximo y mínimo) y no refleja cómo se distribuyen los datos intermedios. Para una visión más completa usamos la **varianza** y la **desviación estándar**, que miden la dispersión respecto a la media.

La varianza se define como la media de los cuadrados de las desviaciones de cada dato respecto a la media:

$$
\sigma^2 = \frac{1}{n}\sum_{i=1}^n (x_i - \bar{x})^2
$$

La desviación estándar es simplemente la raíz cuadrada de la varianza:

$$
\sigma = \sqrt{\frac{1}{n}\sum_{i=1}^n (x_i - \bar{x})^2}
$$

Si tomamos los datos $[6,7,9,8]$ con media $7.5$, la varianza es

$$
\sigma^2 = \frac{(6-7.5)^2 + (7-7.5)^2 + (9-7.5)^2 + (8-7.5)^2}{4} = 1.25
$$

y la desviación estándar es $\sigma = \sqrt{1.25} \approx 1.12$. Esto nos dice que, en promedio, los datos se alejan poco más de una unidad de la media.

En IA, la desviación estándar es clave en procesos de **normalización**: restar la media y dividir entre la desviación estándar convierte una variable en una distribución con media cero y varianza uno. Este paso asegura que todas las características contribuyan de manera equilibrada durante el entrenamiento, evitando que una variable domine a las demás por estar en otra escala.

### Coeficiente de variación

La varianza y la desviación estándar miden dispersión en términos absolutos. Pero ¿cómo comparar la variabilidad de variables medidas en escalas distintas? Para ello usamos el **coeficiente de variación (CV)**, que relaciona la desviación estándar con la media:

$$
CV = \frac{\sigma}{\bar{x}}
$$

El CV permite comparar dispersión relativa. Supongamos dos variables: en un grupo de alumnos, la nota media es $8$ con desviación estándar $1$, mientras que el número de horas de estudio semanales tiene media $20$ y desviación estándar $5$. Aunque en valor absoluto $5$ parece más dispersión que $1$, el CV muestra que, en proporción a la media, las notas tienen un $CV=0.125$ y las horas un $CV=0.25$. Esto indica que el estudio es relativamente más variable entre estudiantes que las calificaciones.

En IA, el coeficiente de variación se conecta con la idea de **estabilidad de los modelos**. En problemas de validación cruzada, comparar la media del rendimiento de un modelo con la variabilidad de ese rendimiento puede ayudarnos a decidir si un modelo es consistente o si depende demasiado de la partición de los datos.

---

> **Para reflexionar…**
> ¿Qué pasaría si entrenas un modelo con una variable que tiene un rango enorme y otra con un rango diminuto? ¿Por qué normalizar los datos (restando la media y dividiendo por la desviación estándar) ayuda a que el entrenamiento sea más equilibrado y estable?

## Medidas de posición

Además de conocer el centro y la dispersión de los datos, también resulta útil saber cómo se distribuyen alrededor de ese centro y en qué lugares se concentran. Las **medidas de posición** permiten responder a esta pregunta dividiendo el conjunto de datos en partes que nos ayuden a describir su forma.

La idea es sencilla: si colocamos todos los datos en orden de menor a mayor, podemos marcar ciertos puntos de referencia que dividen esa secuencia en segmentos. Estos puntos son los **cuartiles** y los **percentiles**.

Los cuartiles dividen los datos en cuatro partes iguales. El primer cuartil (Q1) señala el valor por debajo del cual se encuentra el 25% de los datos. El segundo cuartil coincide con la mediana, que divide al conjunto en dos mitades, y el tercer cuartil (Q3) marca el valor por debajo del cual está el 75% de los datos. Estos cortes nos permiten describir cómo se distribuye la información: si los valores se agrupan mucho en un extremo, los cuartiles quedarán más juntos en esa zona, mientras que si los datos están más dispersos se separarán más.

Los percentiles siguen la misma lógica, pero dividen los datos en cien partes iguales. El percentil 90, por ejemplo, es el valor que deja por debajo al 90% de los datos. Esta medida se utiliza mucho en contextos donde interesa entender los extremos de la distribución. Un ejemplo cercano para un alumno sería el cálculo de notas de admisión: estar en el percentil 95 de una prueba significa haber obtenido mejor resultado que el 95% de los participantes.

Esta idea intuitiva se puede formalizar con el concepto de **cuantil**. Si $X$ es una variable y $F(x)$ su función de distribución acumulada (la proporción de datos $\le x$), el **cuantil de nivel** $p\in(0,1)$ es cualquier valor $q$ tal que
$$
F(q);\ge;p\quad\text{y}\quad F(q^-);\le;p.
$$
En datos finitos, con valores ordenados $x_{(1)}\le \cdots \le x_{(n)}$, el cuantil empírico $Q(p)$ se suele obtener por **posición fraccionaria**: $k=(n+1)p$ y, si $k$ no es entero, se interpola entre $x_{(\lfloor k\rfloor)}$ y $x_{(\lceil k\rceil)}$. Los **cuartiles** son los cuantiles $Q(0{.}25), Q(0{.}50), Q(0{.}75)$; el segundo cuartil coincide con la **mediana**. Los **percentiles** son los cuantiles $Q(p)$ con $p$ expresado en tanto por ciento (p. ej., el percentil 90 es $Q(0{.}90)$).

Vamos a fijar ideas con un ejemplo

> 
>
> Tomemos una lista de “visitas diarias” (ordenada ya de menor a mayor)
> $$
> \boxed{2,\ 3,\ 4,\ 6,\ 7,\ 9,\ 13,\ 15,\ 21,\ 50}\qquad (n=10)
> $$
> La **mediana** es el punto medio entre las posiciones 5 y 6: $Q(0{.}5)=\tfrac{7+9}{2}=8$.
> Para el **primer cuartil**, $k=(n+1),0{.}25=2{.}75$. Interpolamos entre $x_{(2)}=3$ y $x_{(3)}=4$ con fracción $0{.}75$:
> $$
> Q(0{.}25)=3+0{.}75,(4-3)=3{.}75.
> $$
> Para el **tercer cuartil**, $k=(n+1),0{.}75=8{.}25$. Interpolamos entre $x_{(8)}=15$ y $x_{(9)}=21$ con fracción $0{.}25$:
> $$
> Q(0{.}75)=15+0{.}25,(21-15)=16{.}5.
> $$
> El **rango intercuartílico** (IQR) mide la “anchura” de la mitad central:
> $$
> \mathrm{IQR}=Q(0{.}75)-Q(0{.}25)=16{.}5-3{.}75=12{.}75.
> $$
> Con estos números, el **percentil 90** (posición $k=0{.}9\cdot 11=9{.}9$) estará casi en el máximo, muy cerca de $x_{(10)}=50$:
> $$
> Q(0{.}90)\approx x_{(9)} + 0{.}9,(x_{(10)}-x_{(9)}) = 21 + 0{.}9,(50-21)=47{.}1.
> $$
>



### Diagrama de caja: lectura rápida (y outliers)

Una forma visual de representar estas ideas es el **diagrama de caja**, también llamado boxplot. En él, la “caja” central se extiende desde Q1 hasta Q3, mostrando el rango intercuartílico, que recoge la mitad central de los datos. Dentro de la caja se dibuja la línea de la mediana, y a partir de sus extremos salen líneas llamadas “bigotes”, que se prolongan hacia los valores más alejados sin ser considerados atípicos. Los datos que caen mucho más allá de esos límites suelen representarse como puntos aislados y se interpretan como **outliers**.

La fuerza del diagrama de caja es que condensa en una sola imagen la posición central, la dispersión y la presencia de valores atípicos. Mientras un histograma necesita muchos datos para mostrar la forma de la distribución, un boxplot resume en segundos lo esencial. En inteligencia artificial, esta visualización se convierte en una herramienta rápida de diagnóstico, pues permite detectar enseguida si una variable está sesgada, si presenta outliers que podrían desestabilizar un modelo o si la variabilidad es similar entre diferentes grupos de datos.

> **Para reflexionar…**
> ¿Por qué puede ser más informativo representar los datos con un diagrama de caja que limitarse a dar la media y la desviación estándar? ¿Qué nos dice un boxplot sobre los valores atípicos que una media nunca revelaría?

> **Ejemplo:**
>
> Aquí tienes un ejemplo de **boxplot** construido a partir de los datos de visitas diarias a una web. La caja azul muestra el rango intercuartílico (Q1–Q3), la línea roja indica la mediana, los “bigotes” marcan el rango sin outliers y el punto naranja representa el valor extremo de 50 visitas, identificado como atípico.
>
> <img src="./assets/image-20251001095632885.png" alt="image-20251001095632885" />
>
> Vamos a leer este boxplot paso a paso
>
> 1. **La caja central (azul)** va de $Q1=3.75$ a $Q3=16.5$. Eso significa que la mitad central de los días tiene entre 4 y 17 visitas. Este rango intercuartílico (IQR) refleja el comportamiento más común.
> 2. **La línea roja dentro de la caja** marca la **mediana**, que en este caso es 8. Nos dice que la mitad de los días la web recibe menos de 8 visitas y la otra mitad más.
> 3. **Los bigotes** se extienden desde el mínimo no atípico (2) hasta el máximo no atípico (21). Son los valores que todavía se consideran dentro del rango habitual según la regla de Tukey (1.5 veces el IQR).
> 4. **El punto aislado en naranja** representa el día con 50 visitas. El boxplot lo detecta como **outlier**, porque se aleja demasiado del comportamiento normal. Visualmente, se resalta que es un día excepcional.











### 3.1.5 Representaciones gráficas en EDA

- Histogramas: distribución de frecuencias.
- Diagramas de dispersión: relación entre dos variables.
- Conexión con la exploración de datasets en IA.

### 3.1.6 Conexiones con la IA

- Media y MSE como función de coste.
- Desviación estándar en normalización de datos.
- Mediana y robustez frente a outliers.
- Moda en algoritmos de clasificación (k-NN).
