# Probabilídad condicional. Teorema de Bayes

## Concepto de probabilidad condicional: cómo cambia la probabilidad de un evento al conocer información adicional

En teoría de la probabilidad, la **probabilidad condicional** describe cómo se modifica la probabilidad de un suceso cuando disponemos de información adicional. No se trata de cambiar el fenómeno en sí, sino de **ajustar nuestra medida de incertidumbre** en función de lo que sabemos.

Un ejemplo cotidiano lo aclara. Supongamos que la probabilidad de que llueva mañana en una ciudad es del 20%. Sin embargo, si recibimos la información de que hoy ha descendido bruscamente la presión atmosférica, esa probabilidad puede aumentar al 60%. El suceso “llueva mañana” no cambia, lo que cambia es la **información disponible** que nos permite evaluar de forma más precisa la incertidumbre asociada.

Otro ejemplo es el de los diagnósticos médicos. Antes de una prueba, la probabilidad de que un paciente tenga una enfermedad puede ser baja, digamos del 1%. Pero si el test resulta positivo, la probabilidad de que esté enfermo se incrementa, porque ahora estamos condicionando el cálculo al resultado de la prueba.

Formalmente, se habla de la probabilidad de un evento $A$ dado que se conoce la ocurrencia de otro evento $B$, y se representa como $P(A|B)$. La clave es entender que la información $B$ reduce el espacio de incertidumbre: ya no consideramos todos los casos posibles, sino solo aquellos en los que $B$ ocurre. En ese nuevo marco, recalculamos la proporción de casos en que ocurre $A$.

En términos prácticos, la probabilidad condicional es la herramienta que nos permite **incorporar nueva información** al razonamiento probabilístico, y es el fundamento de muchos algoritmos de Inteligencia Artificial. Desde sistemas de diagnóstico médico hasta filtros de spam, lo que hacen estos modelos es continuamente actualizar probabilidades a medida que observan nuevas evidencias.

## Definición formal: regla de la probabilidad condicional y multiplicación de probabilidades

Hasta ahora hemos visto la idea de forma intuitiva: la **probabilidad condicional** es la manera de ajustar la probabilidad de un suceso cuando tenemos nueva información. Matemáticamente, esta idea se expresa con la fórmula:

$$
 P(A|B) = \frac{P(A \cap B)}{P(B)} \quad \text{si } P(B) > 0 
$$

Aquí, $P(A|B)$ representa la probabilidad de que ocurra $A$ sabiendo que $B$ ha ocurrido. En el numerador aparece $P(A \cap B)$, la probabilidad de que ambos sucesos ocurran conjuntamente. En el denominador está $P(B)$, que limita el cálculo al universo de casos donde $B$ ya se cumple.

La interpretación es clara: la probabilidad condicional se obtiene al **restringir el espacio muestral** a los casos en los que $B$ ocurre y calcular qué fracción de esos casos corresponde también a $A$.

A partir de esta definición surge la **regla de la multiplicación de probabilidades**:

$$
 P(A \cap B) = P(A|B),P(B)
$$


Esta fórmula nos dice que la probabilidad conjunta de dos sucesos se puede calcular como la probabilidad de uno de ellos (por ejemplo $B$) multiplicada por la probabilidad del otro condicionado al primero. Simétricamente, también se cumple:

$$
 P(A \cap B) = P(B|A),P(A)
$$

Esta simetría es fundamental, porque permite expresar relaciones entre sucesos desde diferentes puntos de vista, y será precisamente la base del **Teorema de Bayes** que veremos más adelante.

En el análisis de datos y en la Inteligencia Artificial, estas expresiones se convierten en la gramática del razonamiento probabilístico. Cada vez que un sistema debe evaluar la probabilidad de que ocurra un evento complejo en función de otros, aplica estas mismas reglas de forma sistemática, aunque lo haga en escenarios con miles o millones de variables.

> **Ejemplo numérico:**
>
> Imaginemos un escenario sencillo con una baraja de 52 cartas. Queremos calcular la probabilidad de que una carta robada sea un **as de corazones** bajo diferentes condiciones de información.
>
> **Probabilidad simple**
> Sin información adicional, la probabilidad de sacar el as de corazones es
> 
> $$
>  P(A) = \frac{1}{52}.
> $$
> 
> **Probabilidad condicional**
> Supongamos ahora que alguien nos dice que la carta robada es de corazones. El espacio muestral ya no son 52 cartas, sino solo las 13 de corazones. En ese nuevo contexto, la probabilidad de que sea el as de corazones se recalcula como
> 
> $$
>  P(A|B) = \frac{P(A \cap B)}{P(B)} = \frac{1/52}{13/52} = \frac{1}{13}.
> $$
> 
> Aquí $B$ representa “la carta es de corazones”. El numerador es $P(A \cap B)$, la probabilidad de que la carta sea el as de corazones (evento conjunto). El denominador es $P(B)$, la probabilidad de que la carta sea de corazones.
>
> **Multiplicación de probabilidades**
> Podemos recuperar la probabilidad conjunta $P(A \cap B)$ usando la regla de multiplicación:
> 
>$$
>  P(A \cap B) = P(A|B),P(B) = \frac{1}{13} \cdot \frac{13}{52} = \frac{1}{52}.
> $$
>
> Este resultado coincide con el cálculo directo de $P(A)$, lo que confirma la consistencia de la regla.
>
> Este ejemplo deja ver claramente la lógica: al conocer información adicional (que la carta es de corazones), **actualizamos la probabilidad** del suceso que nos interesa (que sea el as de corazones). La probabilidad condicional siempre se entiende como un **recalculo dentro de un espacio reducido**.

## Independencia de eventos

La noción de **independencia** es uno de los pilares de la teoría de la probabilidad. En términos intuitivos, dos eventos son independientes cuando saber que uno ha ocurrido **no cambia** la probabilidad del otro. Formalmente, esta idea se expresa a través de la probabilidad condicional.

### Definición formal

Sean $A$ y $B$ dos eventos definidos sobre un espacio de probabilidad. Diremos que $A$ y $B$ son **independientes** si y solo si:

$$
P(A|B) = P(A) \quad \text{y, de forma equivalente,} \quad P(B|A) = P(B).
$$

Esto significa que conocer que $B$ ha ocurrido no altera nuestra estimación sobre $A$, y viceversa.

Una formulación equivalente, muy utilizada en cálculos prácticos, es:

$$
P(A \cap B) = P(A) \cdot P(B).
$$

Ambas expresiones son equivalentes y expresan la misma idea: la probabilidad conjunta se descompone en el producto de probabilidades individuales.

> **Ejemplo**:
>
> Si lanzamos dos dados independientes, la probabilidad de que el primero muestre un 3 y el segundo un 5 es:
>
> $$
> P(\text{3 en el primero} \cap \text{5 en el segundo}) \\ = P(\text{3 en el primero}) \cdot P(\text{5 en el segundo}) = \frac{1}{6} \cdot \frac{1}{6} = \frac{1}{36}.
> $$
>
> Aquí, la independencia es evidente: el resultado de un dado no influye en el otro.
>

### Dependencia de eventos

Si $P(A|B) \neq P(A)$, decimos que $A$ y $B$ son **dependientes**. En ese caso, la ocurrencia de uno modifica la probabilidad del otro.

> **Ejemplo:** supongamos una bolsa con 5 bolas rojas y 5 azules. Si extraemos una bola sin reemplazo, el resultado de la primera extracción afecta las probabilidades de la segunda. Si en la primera extracción salió una bola roja, entonces la probabilidad de obtener otra bola roja en la segunda ya no es $5/10=0.5$, sino $4/9$. Aquí la información previa altera la probabilidad del segundo evento.

### Independencia condicional

En muchos problemas reales, la independencia absoluta no es realista. Sin embargo, puede aparecer una **independencia condicional**: dos eventos $A$ y $B$ pueden ser dependientes en general, pero convertirse en independientes **condicionados** a un tercer evento $C$.

Formalmente:

$$
P(A \cap B ,|, C) = P(A|C) \cdot P(B|C).
$$

Esto significa que, una vez que conocemos $C$, la información sobre $A$ no aporta nada nuevo sobre $B$, y viceversa.

> **Ejemplo:** 
> En un modelo de spam, las palabras “gratis” y “descuento” no son independientes en general (suelen aparecer juntas en correos de spam). Pero **condicionado al hecho de que el correo es spam**, su aparición puede tratarse como independiente. Esta es la hipótesis central del clasificador **Naive Bayes**, que simplifica el cálculo de probabilidades conjuntas de muchas características asumiendo independencia condicional respecto a la clase.

### Importancia en inteligencia artificial

La independencia, y en particular la independencia condicional, constituye la herramienta que hace posible construir modelos probabilísticos manejables. Si no pudiéramos hacer estas suposiciones, el cálculo de probabilidades conjuntas entre muchas variables resultaría inabordable. Un buen ejemplo es el clasificador **Naive Bayes**, donde se asumirá que las características de los datos, como las palabras en un texto, son independientes entre sí una vez conocida la clase a la que pertenecen. Esta hipótesis, aunque no siempre exacta, permite reducir un problema de miles de variables a un simple producto de probabilidades, manteniendo el modelo operativo y sorprendentemente eficaz.

En las **redes bayesianas** la situación se hace aún más interesante: allí las dependencias y las independencias condicionales se representan explícitamente mediante grafos, lo que ofrece una visión estructurada de fenómenos complejos y permite razonar sobre ellos de manera clara.

Algo similar ocurre en el **aprendizaje por refuerzo**, donde se suele asumir que el estado futuro de un agente depende únicamente de su estado actual y no de toda la secuencia previa. Esta hipótesis, conocida como **propiedad de Markov**, es otra manifestación de independencia condicional y constituye la base para que los algoritmos de este campo puedan funcionar de forma práctica.

De este modo, la independencia condicional se revela no solo como una definición teórica, sino como la clave que abre la puerta a modelos eficientes y aplicables en inteligencia artificial.

> **Para reflexionar…**
> En el mundo real, las variables rara vez son completamente independientes. ¿Por qué, entonces, crees que tantos algoritmos en IA asumen independencia (o independencia condicional)? ¿Qué ganamos con esa simplificación y qué riesgos asumimos al aceptar una hipótesis que sabemos que no se cumple al 100%?

## El Teorema de Bayes: actualizar creencias con nueva información

El **Teorema de Bayes** es una de las piezas más influyentes de la probabilidad, porque convierte la definición de probabilidad condicional en una herramienta para **actualizar creencias**.

Recordemos la regla de la multiplicación:

$$
P(A \cap B) = P(A|B),P(B) = P(B|A),P(A).
$$

De aquí podemos despejar $P(A|B)$ en función de $P(B|A)$:

$$
P(A|B) = \frac{P(B|A),P(A)}{P(B)}.
$$

Esta fórmula es el **Teorema de Bayes**. Lo que nos dice es que la probabilidad de que ocurra un evento $A$ dado que hemos observado $B$ se calcula como el producto entre:

1. La **probabilidad previa** $P(A)$, es decir, la creencia que teníamos antes de observar nada.
2. La **verosimilitud** $P(B|A)$, que indica cuánto explica $A$ la observación de $B$.
3. Normalizado por $P(B)$, que asegura que todas las probabilidades condicionadas sumen uno.

En notación más cercana al lenguaje de la inferencia:

* $P(A)$ se llama **prior** (probabilidad a priori).
* $P(B|A)$ es la **verosimilitud** de la evidencia.
* $P(A|B)$ es el **posterior**, es decir, la probabilidad actualizada tras conocer la evidencia.

El Teorema de Bayes, por tanto, es un **mecanismo de actualización**. Empieza con una creencia inicial (el prior), incorpora la información observada (la evidencia), y produce una nueva creencia revisada (el posterior).

Este esquema es esencial en estadística y en Inteligencia Artificial. Cada vez que un algoritmo “aprende” de nuevas observaciones, lo que está haciendo en muchos casos es aplicar, de manera explícita o implícita, este principio de actualización bayesiana.

## Interpretación en términos de *prior*, verosimilitud y *posterior*

El **Teorema de Bayes** se interpreta como un mecanismo de actualización de probabilidades. En primer lugar aparece el **prior**, que expresa lo que sabemos antes de observar nada. Por ejemplo, si en una población solo el 1% de las personas padece cierta enfermedad, esa proporción es la creencia inicial sobre la probabilidad de que un individuo cualquiera esté enfermo.

Cuando incorporamos nueva información entramos en el terreno de la **verosimilitud**, que mide hasta qué punto la evidencia es coherente con la hipótesis. Si la enfermedad genera un resultado positivo en una prueba diagnóstica en el 95% de los casos, la presencia de un test positivo resulta altamente compatible con la hipótesis de enfermedad.

El resultado de este proceso es el **posterior**, una probabilidad revisada que surge de combinar el prior con la verosimilitud. Así, después de observar un test positivo, la probabilidad de que la persona esté enferma ya no se mantiene en el 1% inicial, sino que aumenta a un valor mayor, calculado de forma precisa con el Teorema de Bayes.

Este mecanismo no se limita a una sola actualización. Cada vez que aparece nueva evidencia, el posterior pasa a convertirse en el nuevo prior, y el ciclo se repite. De este modo, Bayes formaliza un proceso de aprendizaje progresivo en el que nuestras creencias se ajustan de manera sistemática a medida que la información disponible crece.

## Ejemplo ilustrativo con datos sencillos: detección de spam con palabras clave

Para entender cómo funciona el **Teorema de Bayes** en la práctica, consideremos el caso de un filtro de spam muy simple. Supongamos que en una bandeja de correo, el 20% de los mensajes son spam y el 80% son legítimos. Esa proporción inicial actúa como el **prior**, pues refleja la probabilidad de que un mensaje cualquiera sea spam antes de observar nada más.

Ahora introducimos una evidencia: la palabra “gratis” aparece en el asunto del correo. A partir de observaciones previas, sabemos que el 60% de los correos de spam contienen la palabra “gratis”, mientras que solo el 5% de los correos legítimos la incluyen. Esta es la **verosimilitud**, ya que mide qué tan consistente es la aparición de la palabra “gratis” con la hipótesis de que un mensaje sea spam.

El Teorema de Bayes nos permite calcular la probabilidad **posterior**, es decir, la probabilidad de que el mensaje sea spam dado que contiene la palabra “gratis”. La fórmula se aplica de la siguiente manera:

$$
P(\text{Spam}|\text{Gratis}) = \frac{P(\text{Gratis}|\text{Spam}) \cdot P(\text{Spam})}{P(\text{Gratis})}.
$$

Sabemos que $P(\text{Spam}) = 0.2$ y $P(\text{Gratis}|\text{Spam}) = 0.6$. La probabilidad total de que aparezca la palabra “gratis” se obtiene considerando los dos tipos de correos:

$$
P(\text{Gratis}) = P(\text{Gratis}|\text{Spam}) \cdot P(\text{Spam}) + P(\text{Gratis}|\text{No Spam}) \cdot P(\text{No Spam}).
$$

Reemplazando valores:

$$
P(\text{Gratis}) = (0.6)(0.2) + (0.05)(0.8) = 0.12 + 0.04 = 0.16.
$$

El posterior queda entonces:

$$
P(\text{Spam}|\text{Gratis}) = \frac{0.6 \cdot 0.2}{0.16} = \frac{0.12}{0.16} = 0.75.
$$

El resultado es que un mensaje que contiene la palabra “gratis” tiene un 75% de probabilidad de ser spam, una cifra muy superior al 20% de probabilidad inicial.

Este ejemplo sencillo muestra el poder del Teorema de Bayes: a partir de un conocimiento previo y de la evidencia observada, se logra **actualizar la probabilidad** de forma rigurosa. Así, la información que parecía anecdótica (una sola palabra en un correo) se convierte en un factor decisivo para la clasificación.

## Conexiones con la Inteligencia Artificial: aplicaciones del Teorema de Bayes

El **Teorema de Bayes** es mucho más que una fórmula estadística: constituye la base de un conjunto amplio de métodos en Inteligencia Artificial que se apoyan en la idea de **actualizar probabilidades a medida que se observan nuevas evidencias**.

En el terreno de la clasificación, el ejemplo más conocido es el **clasificador Naive Bayes**, un algoritmo que asume que las características (palabras en un texto, síntomas en un paciente, señales en un sensor) son independientes entre sí. Aunque esta independencia rara vez se cumple de forma exacta, la simplicidad del modelo lo hace sorprendentemente eficaz. Los filtros de spam funcionan bajo esta lógica: cada palabra de un correo contribuye a modificar la probabilidad de que sea spam, y el clasificador combina esas evidencias mediante Bayes para tomar la decisión final.

El teorema también es fundamental en **modelos probabilísticos** más generales, como las **redes bayesianas**, que representan sistemas complejos de variables con dependencias condicionales entre ellas. Estas redes permiten inferir la probabilidad de eventos ocultos a partir de observaciones parciales, una capacidad crucial en diagnóstico médico, visión por computador o sistemas expertos.

Incluso en algoritmos que no se consideran explícitamente bayesianos, la lógica de Bayes aparece en el trasfondo. Los modelos de aprendizaje automático trabajan constantemente con la relación entre datos y parámetros. La probabilidad de observar ciertos datos dado un modelo corresponde a la verosimilitud, mientras que el ajuste de parámetros con regularización puede interpretarse como la incorporación de un prior. Bajo esta óptica, muchos algoritmos de IA pueden verse como aplicaciones específicas del principio bayesiano.

En definitiva, Bayes aporta un marco matemático para **razonar bajo incertidumbre**, lo que lo convierte en una pieza central de la Inteligencia Artificial. Allí donde los datos son incompletos, ambiguos o ruidosos, la actualización de probabilidades que propone el teorema se convierte en la herramienta que da coherencia a las decisiones automáticas.









