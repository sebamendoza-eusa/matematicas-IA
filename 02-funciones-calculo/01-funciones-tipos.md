## Funciones como modelos matemáticos

Una **función** es una regla que asigna a cada valor de entrada un único valor de salida. En notación matemática, escribimos

$$
f: X \to Y,\qquad f(x)=y,
$$

Esta definición, aunque abstracta, se entiende mejor con ejemplos cotidianos. Pensemos en la **temperatura de una ciudad en función de la hora del día**. Cada hora corresponde a un valor concreto de temperatura: a las 8 de la mañana, 15 °C; a las 3 de la tarde, 27 °C. Otro ejemplo es el cálculo de la **nota media en función de las horas de estudio**: más horas invertidas suelen traducirse en una mayor calificación. En ambos casos, existe una relación consistente entre lo que entra en el modelo (tiempo, horas de estudio) y lo que sale (temperatura, nota).

En inteligencia artificial, esta idea se convierte en el núcleo de los algoritmos. Un **modelo de aprendizaje automático** puede entenderse siempre como una función que transforma entradas en salidas. Las entradas pueden ser muy variadas: una imagen representada como un conjunto de píxeles, un texto convertido en una secuencia de números o un vector de características que describe a un usuario. La salida, a su vez, puede ser una etiqueta (“gato” o “perro”), una predicción numérica (el precio de una vivienda) o una probabilidad (la confianza de que un correo sea spam).

Es importante entender algunos conceptos asociados a esta definición. Al conjunto $X$ se le denomina **dominio** (el conjunto de entradas para las que la función está definida) e $Y$ es el **codominio** (el conjunto de posibles salidas permitidas por la definición de la función). La **imagen** o **recorrido** de $f$ es el conjunto de salidas que realmente se obtienen al aplicar $f$ a todo su dominio:

$$
Im(f)=\\{f(x):x\in X\\}\subseteq Y.
$$

Pensar con claridad en dominio, codominio e imagen evita ambigüedades. Si modelamos la **nota de un examen** en función de las **horas de estudio**, un dominio razonable sería $X=[0,\infty)$ (no hay horas negativas) y un codominio $Y=\mathbb{R}$ si permitimos cualquier número real como resultado. En la práctica, sabemos que las notas están acotadas, así que la imagen efectiva quedará en un intervalo, por ejemplo $[0,10]$, que es un subconjunto del codominio elegido. Esa diferencia entre “lo permitido por definición”, $Y$, y “lo que realmente ocurre”, $Im(f)$, es útil al diseñar y analizar modelos.

En inteligencia artificial, esta misma estructura describe cualquier modelo. El **espacio de características** hace de dominio: si representamos cada ejemplo como un vector con $d$ atributos numéricos, solemos escribir $X\subseteq\mathbb{R}^d$. El codominio depende de la tarea. En **regresión**, se toma típicamente $Y=\mathbb{R}$ y la imagen son valores reales (por ejemplo, precios). En **clasificación binaria**, podemos definir $Y=\\{0,1\\}$ y la función $f$ devuelve una etiqueta, o bien $Y=[0,1]$ si $f$ devuelve una **probabilidad**; en el caso multiclase, es común trabajar con $Y=\mathbb{R}^K$ antes de la capa *softmax* (logits) o con el **símplex de probabilidad**

$$
\Delta^{K-1}=\\{p\in\mathbb{R}^K:p_i\ge 0,\ \sum_{i=1}^K p_i=1\\}
$$

cuando la salida ya son probabilidades normalizadas.

Esta lectura como “máquina de transformar entradas en salidas” se visualiza con el **gráfico de la función**: cada punto $(x,f(x))$ muestra cómo una entrada concreta se convierte en una salida. En una dimensión, si el gráfico es una recta, la relación es lineal; si es curvilínea, la transformación es no lineal. En más dimensiones, la función define una **superficie** en la que cada punto del espacio de características tiene asociada una salida; en IA, esa superficie actúa como **frontera de decisión** o **paisaje de predicción** sobre la nube de datos.

Hay un matiz práctico relevante: que un modelo “genere” probabilidades o incorpore ruido no contradice la definición de función. El propio modelo sigue siendo una aplicación determinista $f_\theta(x)$ (fijados sus parámetros $\theta$); cuando queremos muestrear decisiones estocásticas, lo que hacemos es **componer** con otra función que toma como entrada $f_\theta(x)$ y una fuente de aleatoriedad. Desde el punto de vista matemático, seguimos trabajando con funciones bien definidas cuyo dominio y codominio hemos especificado.

Dominar estos conceptos básicos —dominio, codominio, imagen y representación gráfica— prepara el terreno para lo que viene a continuación: estudiar **cómo cambian** las funciones (derivadas), cómo **se ajustan** para acercarse a los datos (gradiente y optimización) y cómo **acumulan** información (integrales y expectativas). Esa es, en esencia, la ruta que conecta las funciones con el aprendizaje automático.



>**Para reflexionar...**
>**Si defines un clasificador con salida de probabilidad como $f:X\to[0,1]$, ¿qué ventajas te da declarar explícitamente ese codominio frente a decir solo $f\:X\to\mathbb{R}$? ¿Cómo condiciona esa decisión el diseño de la función de pérdida y la interpretación de los resultados?**



## Funciones lineales y modelos simples

Una de las funciones más sencillas y al mismo tiempo más influyentes en la historia de las matemáticas aplicadas es la **función lineal**. Su expresión general es

$$
f(x) = mx + b,
$$

donde $m$ representa la pendiente y $b$ la ordenada en el origen. Esta fórmula, que en apariencia es elemental, encierra la idea de describir un fenómeno mediante una **recta**. La pendiente nos dice cómo cambia la salida cuando la entrada varía: un $m$ positivo implica que $f(x)$ crece con $x$, un $m$ negativo que decrece. El término $b$ fija el punto donde la recta corta al eje vertical, es decir, el valor de salida cuando la entrada es cero.

Desde un punto de vista geométrico, la función lineal establece una relación de proporcionalidad entre las variables. Es el primer modelo que nos permite **predecir**: si conocemos la pendiente y la ordenada en el origen, podemos anticipar la salida para cualquier entrada. Este carácter predictivo convierte a la recta en el prototipo de los modelos de inteligencia artificial más básicos.

Un ejemplo paradigmático es la **regresión lineal**. En este caso, la recta no se traza a mano, sino que se ajusta a un conjunto de datos observados. Imaginemos que recogemos información sobre el número de horas de estudio y las notas obtenidas en un examen. Al representar los puntos en el plano, vemos que siguen una tendencia creciente: a más horas, mejores notas. La regresión lineal busca la recta que mejor se aproxima a esa nube de puntos, de forma que podamos usarla como regla predictiva para nuevos casos.

Esta idea se traslada sin fricción a más dimensiones. Cuando cada ejemplo está descrito por varias características, escribimos

$$
\hat y=\mathbf{w}\cdot\mathbf{x}+b=\sum_{j=1}^{d}w_j,x_j+b,
$$

que ya no es una recta sino un **hiperplano** en $\mathbb{R}^d$. El vector $\mathbf{w}$ actúa como una brújula: señala la dirección de mayor aumento de la predicción, y su norma controla la sensibilidad del modelo a cambios en las entradas. Aquí, $\mathbf{x}$ es el vector de características de cada ejemplo, $\mathbf{w}$ es el vector de coeficientes y $b$ el término de sesgo. En cualquier caso, la idea sigue siendo la misma: combinar linealmente las entradas para obtener una salida.

### Limitaciones de lo lineal frente a lo real

Las rectas son transparentes, rápidas y sorprendentemente eficientes cuando la relación es aproximadamente proporcional o cuando la dimensionalidad es alta pero la estructura subyacente es simple. Sin embargo, su **expresividad** es limitada en algunos escenarios. Vamos tres limitaciones concretas.

La primera grieta aparece cuando la relación subyacente **se curva**. Piensa de nuevo en las horas de estudio y la nota: al principio, cada hora extra marca una diferencia notable; sin embargo, a partir de cierto punto, añadir más horas apenas mejora el resultado. Esa **saturación** es natural en muchos procesos (aprendizaje, rendimiento físico, respuesta biológica). Una recta no puede abrazar esa forma en “S” o en “techo”; forzará un compromiso: irá por el medio, acertará en promedio y fallará en los extremos. La salida práctica es **cambiar la mirada sobre las entradas** para devolver la linealidad “por dentro”: introducir curvatura mediante nuevas características. Si trabajamos con una sola variable, basta con ampliar el diseño a potencias o transformaciones suaves, por ejemplo

$$
\phi(x)=\big(x,\ x^2\big)\quad \text{o}\quad \phi(x)=\big(\log x,\ \sqrt{x}\big),
$$

de modo que el modelo siga siendo lineal en los parámetros, pero capaz de dibujar curvas en el plano. En la práctica, esta idea se generaliza con polinomios, splines o funciones base que permiten aproximar formas suaves sin abandonar la estructura lineal del entrenamiento.

> **Ejemplo:**
>
> Imagina que recoges pares “horas de estudio → nota” en un curso con calificación máxima 10. Para pocas horas, cada hora extra ayuda mucho; a partir de cierto umbral, añadir más horas apenas cambia la nota porque ya rozas el máximo. Si intentas explicar esta relación con una recta, te obligas a que “una hora más” siempre valga lo mismo, lo cual contradice la experiencia.
>
> Piensa en una tendencia idealizada como esta: para $h$ horas,
>
> * de $0$ a $4$ horas, la nota sube casi una unidad por hora;
> * entre $4$ y $8$ horas, la mejora por hora se reduce;
> * más allá de $8$ horas, la curva se aplana cerca de $10$.
>
> Una recta $f(h)=mh+b$ puede aproximar “el promedio” de esa curva, pero cometerá dos tipos de error: infravalorará a quien estudia poco (porque la curva real arranca más empinada) y sobrevalorará a quien estudia mucho (porque la curva real se aplana). Además, extrapolará notas imposibles $f(h)>10$ si $h$ crece lo suficiente, algo que el fenómeno real nunca hace.
>
> La solución no es abandonar el marco lineal, sino **enriquecer la representación** para que la linealidad viva “por dentro”. Con una sola variable puede bastar añadir curvatura al espacio de características. Por ejemplo, construir
> 
>$$
> \phi(h)=\big(1,\ h,\ h^2\big)
> $$
>
> y ajustar un modelo lineal en esas nuevas coordenadas:
>
> $$
> \hat y = w_0 + w_1h + w_2h^2,\qquad w_2<0.
> $$
>
> Tambien pueden usarse transformaciones con **funciones logarítmicas** que funcionan bien en estos casos
>
> La enseñanza es doble. Una recta es un excelente punto de partida por su claridad e interpretabilidad, pero cuando el fenómeno presenta **saturación** conviene cambiar de coordenadas (polinomios, transformaciones suaves) o usar una forma con techo natural. Así evitamos sesgos sistemáticos y mantenemos las predicciones dentro de rangos plausibles.
>

El segundo límite aparece cuando los efectos no son meramente **aditivos**, sino que **interactúan**. Un modelo lineal puro asume que cada característica suma su contribución de manera independiente: duplicar “horas de estudio” siempre suma lo mismo, sea cual sea la “calidad del material”, y aumentar “ingresos” tiene el mismo efecto prediciendo gasto, tengas “20” o “60” años. En muchos fenómenos reales, la influencia de una variable **depende del valor de otra**. Esa dependencia cruzada se captura introduciendo **términos de interacción** en el propio espacio de características. Si $\mathbf{x}=(x_1,x_2)$, añadimos una nueva columna $x_1x_2$ y ajustamos

$$
\hat y = w_1 x_1 + w_2 x_2 + w_{12},(x_1x_2) + b.
$$

Interpretativamente, $w_{12}$ mide cómo cambia el efecto de $x_1$ cuando varía $x_2$ (y viceversa). Con un único gesto —multiplicar columnas— el modelo lineal aprende efectos “si... entonces...” y sinergias que una suma simple nunca podría reflejar. Este mismo principio se extiende a más variables y a interacciones de orden superior cuando el fenómeno lo exige.

> **Ejemplo**
>
> Supón que queremos predecir la **nota** a partir de las **horas de estudio** y de si el alumno usa **material de calidad**. Definimos una variable $q$ que vale $0$ si el material es básico y $1$ si es de calidad.
>
>| Horas (h) | Calidad (q) | Nota |
>|------------|--------------|------|
>| 1          | 0            | 4.5  |
>| 2          | 0            | 6.0  |
>| 3          | 0            | 7.0  |
>| 1          | 1            | 5.6  |
>| 2          | 1            | 7.9  |
>| 3          | 1            | 9.8  |
>
>
> Al dibujar los puntos, verás **dos rectas**, una para $q=0$ y otra para $q=1$. La clave es que **no son paralelas**: con material de calidad, **cada hora extra rinde más**. Eso es una **interacción**: el efecto de “horas” depende del valor de “calidad”.
>
> Un modelo lineal **sin** interacción,
>
> $$
> \hat y=b+w_1h+w_2q
> $$
>
> solo permite **desplazar** la recta de $q=0$ a $q=1$ (cambia la altura), pero **no** cambiar su **pendiente**. Intentará encajar ambas nubes con **paralelas**, y fallará sistemáticamente en uno de los dos grupos.
>
> Para capturar la interacción basta añadir el término producto:
>
> $$
> \hat y=b+w_1h+w_2q+w_3(h\cdot q).
> $$
>
> Ahora, si $q=0$, la pendiente es $w_1$; si $q=1$, la pendiente pasa a ser $w_1+w_3$. El modelo aprende que con material de calidad, **cada hora cuenta más** (pendiente mayor). Misma herramienta lineal, pero en un **espacio de características enriquecido**: hemos convertido un “no puedo” en un “sí, con interacción”.

El tercer tropiezo es geométrico: **la separación no lineal**. En clasificación, un modelo lineal dibuja un hiperplano que divide el espacio en dos mitades. Si los datos forman dos racimos alargados en direcciones opuestas, un hiperplano los separa con elegancia. Pero si los positivos rodean a los negativos en un **anillo concéntrico**, ninguna recta —ni ningún hiperplano— logrará trazar una frontera limpia. La salida, de nuevo, consiste en **re-describir el espacio** para que la frontera “curva” se haga lineal en coordenadas adecuadas. En dos dimensiones, basta añadir la variable radial $r^2=x_1^2+x_2^2$ y trabajar con $\phi(x)=(x_1,x_2,r^2)$: en este nuevo sistema, una superficie plana (lineal en $x_1,x_2,r^2$) puede cortar el anillo con precisión. Esta es la intuición que hay detrás de los **métodos de base** (crear características no lineales a mano), los **kernels** (crear productos internos no lineales sin construir explícitamente las nuevas variables) y las **redes neuronales** (encadenar escorados lineales con funciones de activación que curvan la frontera de decisión).

> **Ejemplo**
>
> Imagina un conjunto de puntos en el plano. Los que están **cerca del origen** (formando un pequeño círculo central) son de la clase A, y los que están **alrededor**, formando un **anillo** que rodea al centro, son de la clase B. Si dibujas una recta cualquiera, siempre cortará ambas regiones: es imposible dejar el centro a un lado y el anillo al otro con una frontera **lineal**. Esa es la limitación.
>
> La clave para resolverlo no es abandonar lo lineal, sino **cambiar de coordenadas**. En el plano $(x_1,x_2)$ introduce una nueva característica que capture la **distancia al origen**:
>
> $$
> r^2 = x_1^2 + x_2^2
> $$
> 
>
> Ahora describe cada punto con $\phi(x) = (x_1, x_2, r^2)$. En este espacio enriquecido, una regla **lineal** del tipo
>
> $$
> w_1 x_1 + w_2 x_2 + w_3 r^2 + b = 0
> $$
>
>  puede representar, en el plano original, una frontera **circular** (cuando el término en $r^2$ domina). Clasificar “por dentro vs. por fuera” se convierte en algo tan simple como **umbralizar** $r^2$: puntos con $r^2$ pequeño son A, con $r^2$ grande son B. La decisión vuelve a ser lineal, pero en las variables adecuadas.
>
> Esta es la idea que subyace a muchas técnicas: crear **características no lineales** que “desenreden” la geometría del problema (polinomios, funciones radiales), usar **kernels** para lograr ese efecto sin construir las variables explícitamente, o dejar que una **red neuronal** aprenda automáticamente esas transformaciones a través de capas con activaciones no lineales. En todos los casos, el objetivo es el mismo: encontrar un espacio donde una frontera lineal sea suficiente, aunque en las coordenadas originales la separación parezca imposible.


En las tres situaciones el hilo conductor es el mismo: lo lineal es un punto de partida claro, eficiente e interpretable. Cuando la realidad lo supera —porque se curva, porque mezcla efectos, o porque exige fronteras con forma— no abandonamos la disciplina, la **extendemos**. Cambiamos de coordenadas, enriquecemos el espacio de características o introducimos no linealidad en el propio modelo para que la “recta” vuelva a ser suficiente... pero ahora en el lugar correcto.

Hay dos caminos habituales para salvar estas barreras sin abandonar la claridad del marco lineal. Uno es el **ingeniería de características**, que consiste en crear transformaciones de las entradas (polinomios, logaritmos, productos cruzados) para que la relación vuelva a ser “lineal en los parámetros”. El otro es introducir **no linealidad** en el propio modelo, como se ve con el uso de términos cuadráticos, logaritmos o como hacen las funciones de activación en redes neuronales, en la que cada capa aplica una transformación lineal y, a continuación, una transformación no lineal que permite curvar la frontera de decisión y modelar patrones más ricos.

Pensar primero en rectas no es una limitación, es una **ventaja pedagógica y práctica**: da una referencia clara, ofrece una base geométrica sólida (hiperplanos, proyecciones, distancias) y conecta de forma directa con cómo se entrenan los modelos mediante gradiente. A partir de ahí, cuando lo lineal ya no alcanza, las extensiones no lineales resultan mucho más comprensibles.



>**Para reflexionar...**
>**¿Qué preferirías ante un conjunto de datos real: empezar con un modelo lineal bien interpretado y aumentar complejidad solo si es necesario, o saltar directamente a un modelo muy flexible? ¿Cómo influye esa elección en la explicabilidad, el riesgo de sobreajuste y el coste computacional?**



Aun así,  no todo en la realidad se comporta de manera lineal. Los modelos lineales son poderosos por su simplicidad, pero también están limitados: no pueden capturar curvas, saturaciones ni relaciones complejas entre variables. Un clasificador lineal, por ejemplo, no puede distinguir correctamente dos grupos de datos que se organizan en forma de círculo, porque ninguna recta —ni siquiera un hiperplano en dimensiones mayores— consigue separarlos.

En este punto es donde la inteligencia artificial va más allá de lo lineal. La introducción de **funciones no lineales** (cuadráticas, exponenciales, logarítmicas o funciones de activación en redes neuronales) permite modelar fenómenos más realistas. Aun así, la función lineal sigue siendo esencial: no solo como base histórica y conceptual, sino porque muchas técnicas más complejas se construyen sobre combinaciones lineales de entradas, enriquecidas después con transformaciones no lineales.



>**Para reflexionar...**
>**¿Por qué crees que la regresión lineal, siendo un modelo tan simple, sigue utilizándose hoy en día como herramienta fundamental en estadística y aprendizaje automático? ¿Qué aporta su simplicidad frente a modelos más sofisticados, y en qué momentos sus limitaciones se hacen evidentes?**



## Funciones no lineales en la modelización

La realidad rara vez sigue una recta. Muchos fenómenos crecen rápido al principio y luego se frenan, otros se disparan a un ritmo que aumenta con el tiempo, y no pocos dependen del producto de varias variables más que de su suma. Para captar estas formas, entran en escena las **funciones no lineales**. Tres familias aparecen una y otra vez en modelización: exponenciales, logarítmicas y polinómicas. Cada una aporta una “curvatura” distinta y una forma de pensar diferente.

La **función exponencial** describe procesos cuyo ritmo de cambio es proporcional al valor actual. Si $g(t)=g_0,a^{t}$ (o $g(t)=g_0,e^{kt}$), duplicar $t$ no suma una cantidad fija, multiplica. Ese comportamiento explica por qué ciertos conteos (descargas, visualizaciones, compartidos) parecen despegar repentinamente: al crecer de manera multiplicativa, durante un tiempo “no pasa nada” y, de pronto, la curva se acelera. Como regla rápida, un crecimiento que se curva hacia arriba y cuyo “incremento por unidad” también crece sugiere una forma exponencial. A la inversa, si representas los datos en escala logarítmica y la nube se vuelve casi una recta, estás viendo un crecimiento exponencial “linealizado” por el logaritmo.

La **función logarítmica** es la compañera natural de la exponencial y modela **rendimientos decrecientes**: $h(x)=\log(x)$ crece siempre, pero cada paso aporta menos que el anterior. Es una forma útil cuando los cambios relativos importan más que los absolutos. En práctica de datos, aplicar $\log$ a una variable positiva “comprime” valores grandes, reduce asimetrías y convierte relaciones multiplicativas en aditivas:

$$
y = c,x_1^{\alpha}x_2^{\beta} \quad \Longrightarrow \quad \log y = \log c + \alpha,\log x_1 + \beta,\log x_2
$$

De repente, una relación de productos se vuelve “lineal en las transformaciones”, lo que permite usar modelos lineales con interpretaciones en términos de **elasticidades** (cuánto cambia $\log y$ ante un cambio en $\log x$).

Las **funciones polinómicas** añaden curvatura con términos como $x^2$, $x^3$ o, en varias variables, potencias y productos cruzados. Con pocos términos se capturan máximos, mínimos y flexiones suaves. Por ejemplo, una respuesta con rendimientos decrecientes puede modelarse como $f(x)=w_0+w_1 x+w_2 x^2$ con $w_2<0$. En más dimensiones, incorporar $x_1x_2$ deja que el efecto de $x_1$ dependa de $x_2$, introduciendo **interacciones** sin abandonar la linealidad en los parámetros. Esa combinación —lineal “por dentro”, curva “por fuera”— es una de las claves de la modelización práctica.

Estas formas no lineales no son solo elegantes: resuelven necesidades concretas en IA. En **crecimiento de datos** (tráfico, usuarios, eventos), la curva exponencial describe fases de adopción temprana; usar escala logarítmica permite comparar series con órdenes de magnitud distintos y detectar cambios de tendencia que en escala lineal pasarían desapercibidos. En **probabilidades**, es habitual movernos entre el espacio de probabilidades $p\in(0,1)$ y una escala no acotada usando el **logit**,

$$
\mathrm{logit}(p)=\log!\left(\frac{p}{1-p}\right)
$$

porque muchas funciones de pérdida y modelos (como regresión logística) se vuelven lineales en esta coordenada. En **medidas de error**, el uso de logaritmos estabiliza el efecto de grandes desviaciones o hace que multiplicar errores equivalga a sumar en escala log (por ejemplo, al evaluar razones o verosimilitudes con **log-verosimilitud**; a nivel introductorio, basta con recordar que “sumar logs” es “multiplicar probabilidades”).

Una herramienta cotidiana que une todo esto son las **transformaciones de funciones** sobre los datos de entrada. Aplicar $\log(x+1)$ a una característica positiva reduce asimetría y mitiga la influencia de valores extremos; estandarizar $z=(x-\mu)/\sigma$ centra y escala, favoreciendo que un mismo paso de aprendizaje afecte por igual a todas las dimensiones; elevar a potencias suaves o añadir términos cuadráticos introduce la curvatura necesaria sin complicar el entrenamiento. El objetivo no es “forzar” al modelo, sino **colocar el problema en coordenadas en las que una regla simple funcione bien**.

Considera un ejemplo sencillo. Queremos predecir el gasto mensual en datos móviles ($y$) a partir del número de vídeos vistos ($x$). Una recta sobre $(x,y)$ penaliza mucho los usuarios intensivos: cada vídeo extra parece desproporcionado. Si, en cambio, trabajamos con $(\log x,\log y)$, la nube se alinea y un modelo lineal explica que “un 10% más de vídeos se asocia con aproximadamente un 10% más de gasto”, una relación más estable y fácil de generalizar. Lo que ha cambiado no es el modelo, sino el **punto de vista**.

Normalizar y transformar no es un adorno; es un paso que decide qué estructura ve el modelo. Al comprimir, centrar o curvar adecuadamente, se logra que la frontera de decisión o la superficie de predicción sea más simple en el espacio transformado. A partir de ahí, podemos optar por modelos lineales con buenas propiedades o, si hace falta más flexibilidad, introducir no linealidad en el propio modelo (activaciones) sabiendo que ya hemos hecho gran parte del trabajo al **elegir bien las coordenadas**.

>**Para reflexionar...**
>**Cuando una relación parece “explosiva” en escala lineal, ¿por qué mirar los datos en escala logarítmica suele revelar una estructura más simple? ¿En qué casos preferirías transformar las entradas (log, potencias, estandarización) antes de pasar a un modelo más complejo?**

## Funciones de activación

Imagina una app que decide **si recomendar o no un pack mixto de ocio (cine + gaming)** a sus usuarios. La lógica del producto es clara: el pack compensa cuando el usuario está **descompensado** en intereses —por ejemplo, **muy fan del cine** pero **poco del gaming**, o **muy fan del gaming** pero **poco del cine**. En cambio, si **le encantan ambas cosas** ya suele tener ambos servicios por separado, y si **no le interesa ninguna**, el pack no le aporta.

Representamos a cada usuario con dos puntajes normalizados: $x_1$ = interés en cine, $x_2$ = interés en gaming (valores entre 0 y 1). La decisión es binaria: **recomendar pack mixto** (sí/no).

Cuando la regla es del tipo “si la **media** de intereses sube de cierto umbral, recomienda”, basta una **frontera recta** en el plano $(x_1,x_2)$: todo lo que quede por encima de la línea es “sí”, lo que quede por debajo es “no”. Pero en la regla de **descompensación** ocurre lo contrario: queremos decir “sí” justo en las **esquinas cruzadas** (alto en cine y bajo en gaming; bajo en cine y alto en gaming) y “no” en **ambos altos** y **ambos bajos**. Dibujado en el plano, los “sí” están en las esquinas opuestas del cuadrado y los “no” en las otras dos. **Ninguna línea recta** puede separar esos dos grupos a la vez: cualquier recta que agrupe las esquinas cruzadas se llevará por delante una de las otras esquinas. Es la versión cotidiana del patrón **XOR**.

¿Cómo lo resolvemos sin renunciar a reglas simples? La idea es ***doblar* el espacio** entre pasos con una **función de activación**. En lugar de buscar una única línea imposible, construimos **dos piezas** sencillas y luego las combinamos. Por ejemplo, dos “tests” lineales:

* “¿cine supera a gaming?” (mirar $x_1 - x_2$),
* “¿gaming supera a cine?” (mirar $x_2 - x_1$).

Si tras cada test aplicamos una activación (como ReLU) que deja pasar lo positivo y anula lo negativo, obtenemos dos señales no lineales:

$$
h_1=\mathrm{ReLU}(x_1 - x_2), \qquad h_2=\mathrm{ReLU}(x_2 - x_1).
$$

Luego sumamos $h_1+h_2$ y ponemos un umbral (o una sigmoide) para decidir. Geométricamente, cada $h_i$ define medio plano; su combinación crea una **frontera en forma de V** que separa justo a los usuarios “descompensados” de los “ambos altos/ambos bajos”. Ya no es una sola recta: es una **frontera no lineal por tramos** construida encadenando “suma + activación + suma”.

La función de activación nos permite que un modelo sencillo llegue a una **frontera que una recta jamás puede dibujar**.

Desde un punto de vista mas formal. Imagina una cadena de “capas” que toman un vector de entrada, lo multiplican por una matriz, le suman un sesgo y lo pasan a la siguiente capa. Si todas esas capas fueran estrictamente lineales, toda la cadena se podría **comprimir** en una sola operación lineal. Es como apilar filtros de cristal perfectamente planos: por mucho que apiles, sigues viendo una transformación plana. Matemáticamente, componer dos capas lineales produce otra capa lineal:

$$
\mathbf{W}_2(\mathbf{W}_1\mathbf{x}+\mathbf{b}_1)+\mathbf{b}_2 = \mathbf{W}\mathbf{x}+\mathbf{b}.
$$

Sin un ingrediente extra, esta sucesión de capas de transformación no sería más expresiva que un modelo lineal. No podría curvar fronteras de decisión, describir saturaciones ni capturar interacciones complejas. Ese ingrediente extra es la **función de activación**: una pequeña no linealidad aplicada tras cada escor lineal que “dobla” el espacio y permite a la red modelar formas que una recta jamás alcanzaría. Con activación, apilar capas deja de ser redundante: cada capa puede corregir y curvar lo que hizo la anterior, construyendo representaciones cada vez más ricas.

### Tipos

La **sigmoide** introduce una S suave que comprime cualquier escalar en el intervalo $(0,1)$:

$$
\sigma(z)=\frac{1}{1+e^{-z}}.
$$

Es natural cuando la salida se interpreta como probabilidad en clasificación binaria. Al aplicar $\sigma$ a un escor lineal, obtenemos un valor acotado y diferenciable. Su inconveniente en capas ocultas es la **saturación**: para $z$ muy positivos o muy negativos, la derivada $\sigma'(z)=\sigma(z)!\big(1-\sigma(z)\big)$ se aproxima a 0 y el gradiente se atenúa al retropropagar, además de no estar centrada en cero.

La **tangente hiperbólica** es una alternativa “centrada” alrededor de 0:

$$
\tanh(z)=\frac{e^{z}-e^{-z}}{e^{z}+e^{-z}},
$$

con rango $(-1,1)$. Suele facilitar la optimización frente a sigmoide por esa centralidad, aunque comparte el problema de saturación en las colas: si $|z|$ es grande, la derivada casi desaparece y el aprendizaje se vuelve lento.

La **ReLU** cambia el guion con una regla simple y efectiva:

$$
\mathrm{ReLU}(z)=\max(0,z).
$$

No satura en la parte positiva (derivada $=1$ para $z>0$), lo que favorece que el gradiente fluya incluso en redes profundas y acelera el entrenamiento. Además induce representaciónes dispersas (muchas activaciones quedan exactamente en 0), algo parecido a una regularización implícita y eficiente en cómputo. Su riesgo son las “ReLUs muertas”: neuronas que quedan atrapadas en $z\le 0$ y dejan de actualizarse; variantes como *Leaky ReLU*, *ELU* o *GELU* mantienen buena dinámica de gradiente y suavizan ese problema.

Más allá de la fórmula, lo esencial es su efecto en la **capacidad de aprendizaje**. Con activaciones no lineales, una red neuronal puede aproximar funciones que un modelo lineal no puede. Bajo condiciones suaves, una sola capa oculta suficientemente ancha ya aproxima funciones continuas sobre conjuntos compactos. Aun así, la **profundidad** aporta algo distinto a la mera anchura: permite **componer** transformaciones simples en estructuras jerárquicas, donde capas tempranas capturan patrones elementales y capas posteriores combinan esos patrones en conceptos más abstractos. La activación influye directamente en cómo fluye el gradiente por esa jerarquía, en la estabilidad numérica de las actualizaciones y en la rapidez con que se alcanza un buen ajuste.
