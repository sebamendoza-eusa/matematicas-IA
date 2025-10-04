Matrices: Operaciones básicas y tipos especiales
===

Definición
---

Continuamos nuestro recorrido por el **álgebra lineal** orientada al uso en **Inteligencia Artificial**. Si los vectores nos permiten representar datos individuales, las **matrices** nos ofrecen la capacidad de estructurar y manipular grandes colecciones de datos de manera eficiente.

Una matriz no es más que una cuadrícula bidimensional de números. Piensa en ella como una tabla o una hoja de cálculo. Cada fila y cada columna de esta matriz puede representar diferentes aspectos de nuestros datos. Por ejemplo, en un conjunto de datos, las filas podrían ser diferentes instancias de datos (como clientes o imágenes), y las columnas podrían ser las características de cada instancia (edad, ingresos, o píxeles).

La forma de una matriz se describe por sus dimensiones, es decir, el número de filas y columnas que posee. Una matriz con $m$ filas y $n$ columnas se denota como una matriz de $m \times n$.

> **Ejemplo**:
> En un conjunto de datos de un modelo de *machine learning*, podríamos tener una matriz donde cada fila es una casa y cada columna una característica (número de habitaciones, metros cuadrados, etc.). Si tuviéramos 100 casas y 3 características, la matriz de datos tendría un tamaño de $100 \times 3$.

## Principales operaciones con matrices

Las operaciones con matrices nos permiten transformar y combinar datos a gran escala.

**Suma y Resta**: La suma y resta de matrices se realiza elemento a elemento, de manera similar a los vectores. Para que la operación sea posible, ambas matrices deben tener las mismas dimensiones.

$$
\mathbf{A} + \mathbf{B} = \begin{bmatrix} a_{11}+b_{11} & \dots & a_{1n}+b_{1n} \\ \vdots & \ddots & \vdots \\ a_{m1}+b_{m1} & \dots & a_{mn}+b_{mn} \end{bmatrix}
$$

**Multiplicación por un Escalar**: Multiplicar una matriz por un escalar implica multiplicar cada elemento de la matriz por ese escalar. Esta operación es útil para escalar o normalizar todo un conjunto de datos.

$$
c\mathbf{A} = \begin{bmatrix} ca_{11} & \dots & ca_{1n} \\ \vdots & \ddots & \vdots \\ ca_{m1} & \dots & ca_{mn} \end{bmatrix}
$$

**Multiplicación de Matrices**: La multiplicación de matrices es la operación más compleja y, al mismo tiempo, una de las más cruciales en el **Deep Learning**. El resultado de multiplicar una matriz $\mathbf{A}$ de $m \times n$ por una matriz $\mathbf{B}$ de $n \times p$ es una nueva matriz $\mathbf{C}$ de $m \times p$. **La condición es que el número de columnas de la primera matriz ($n$) debe ser igual al número de filas de la segunda matriz ($n$).**

Cada elemento $c_{ij}$ de la matriz resultante se calcula como el producto escalar de la fila $i$ de la primera matriz y la columna $j$ de la segunda.

$$
c_{ij} = \sum_{k=1}^n a_{ik}b_{kj}
$$

Esta operación es fundamental en las **redes neuronales**, donde la información se propaga de una capa a otra a través de multiplicaciones matriciales. Los pesos de la red se organizan en matrices, y la multiplicación matricial permite calcular las activaciones de las neuronas de la siguiente capa de manera eficiente.

> **Ejemplo:  multiplicación de una matriz $3\times 3$ por un vector**
>
> Consideremos la matriz
>
> $$
> \mathbf{A} =
> \begin{bmatrix}
> 1 & 2 & 3 \\
> 0 & 1 & 4 \\
> 5 & 6 & 0
> \end{bmatrix}
> $$
>
> y el vector
>
> $$
> \mathbf{v} =
> \begin{bmatrix}
> 1 \\
> 2 \\
> 3
> \end{bmatrix}.
> $$
>
> La multiplicación $\mathbf{A}\mathbf{v}$ consiste en calcular el producto escalar de cada fila de la matriz con el vector $\mathbf{v}$.
>
> * Primera fila: $1\cdot 1 + 2\cdot 2 + 3\cdot 3 = 1 + 4 + 9 = 14$
> * Segunda fila: $0\cdot 1 + 1\cdot 2 + 4\cdot 3 = 0 + 2 + 12 = 14$
> * Tercera fila: $5\cdot 1 + 6\cdot 2 + 0\cdot 3 = 5 + 12 + 0 = 17$
>
> El resultado es el nuevo vector
>
> $$
> \mathbf{A}\mathbf{v} =
> \begin{bmatrix}
> 14 \\
> 14 \\
> 17
> \end{bmatrix}.
> $$
>
> ---
>
> #### Interpretación
>
> La matriz $\mathbf{A}$ actúa como una transformación sobre el vector $\mathbf{v}$, combinando linealmente sus componentes. Aunque $\mathbf{v}$ tenía coordenadas $(1,2,3)$, después de la transformación pasa a tener coordenadas $(14,14,17)$.
>
> Este ejemplo muestra que una matriz puede verse como una “máquina” que toma un vector y lo convierte en otro, siguiendo reglas de combinación determinadas por sus filas
>



**Matriz Transpuesta**: Es el resultado de intercambiar las filas por las columnas de una matriz. Si una matriz $\mathbf{A}$ tiene dimensiones $m \times n$, su transpuesta $\mathbf{A}^T$ tendrá dimensiones $n \times m$. Esta operación es clave en la optimización de algoritmos.

> El siguiente ejemplo ilustra el concepto de transposición de una matriz, que es un proceso fundamental en el **álgebra lineal** y tiene aplicaciones prácticas en la **IA**. La transpuesta de una matriz se obtiene al intercambiar sus filas por sus columnas. Si una matriz original tiene dimensiones $m \times n$, su transpuesta tendrá dimensiones $n \times m$.
> 
> Consideremos una matriz $\mathbf{A}$ de 3x3:
> 
> $$
> \mathbf{A} = \begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9
\end{bmatrix}
> $$
> 
> Para obtener su matriz transpuesta, denotada como $\mathbf{A}^T$, simplemente convertimos las filas de $\mathbf{A}$ en las columnas de $\mathbf{A}^T$.
> 
> La primera fila de $\mathbf{A}$ (1, 2, 3) se convierte en la primera columna de $\mathbf{A}^T$.
> La segunda fila de $\mathbf{A}$ (4, 5, 6) se convierte en la segunda columna de $\mathbf{A}^T$.
> La tercera fila de $\mathbf{A}$ (7, 8, 9) se convierte en la tercera columna de $\mathbf{A}^T$.
> 
> El resultado es la siguiente matriz transpuesta:
> 
> $$
> \mathbf{A}^T = \begin{bmatrix}
1 & 4 & 7 \\
2 & 5 & 8 \\
3 & 6 & 9
\end{bmatrix}
> $$

---

>**Para reflexionar**
> **¿Por qué la multiplicación de matrices es una operación tan importante en el Deep Learning?**
> *Considera cómo los pesos de una capa neuronal y las entradas de la misma se organizan en matrices y cómo la multiplicación de estas matrices permite calcular de manera paralela y eficiente las activaciones de todas las neuronas de la siguiente capa. Piensa en la diferencia en la complejidad computacional entre realizar los cálculos uno por uno frente a usar una operación matricial única.*

Tipos especiales de matrices
---

Existen matrices con propiedades particulares que son de gran importancia en la IA. Conocerlas y comprender su comportamiento permite simplificar cálculos y entender mejor los algoritmos que dependen de operaciones matriciales.

### **Matriz de Identidad**

Es una matriz cuadrada (mismo número de filas y columnas) con unos en la diagonal principal y ceros en el resto. Es el equivalente matricial del número 1, ya que multiplicar cualquier matriz por la matriz de identidad no la altera. Por ejemplo, una matriz identidad de dimensión tres sería:

$$
\mathbf{I} = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}
$$

### La matriz nula

La **matriz nula** es aquella cuyos elementos son todos iguales a cero. Se denota como $\mathbf{0}$ y actúa como el **elemento neutro de la suma** de matrices: cualquier matriz sumada a la matriz nula permanece inalterada.

Ejemplo en dimensión $3 \times 3$:

$$
\mathbf{0} = \begin{bmatrix}
0 & 0 & 0 \\
0 & 0 & 0 \\
0 & 0 & 0
\end{bmatrix}
$$

En IA, esta matriz aparece de manera natural al inicializar parámetros o al representar la ausencia total de información en un conjunto de características.

---

### Matrices diagonales

Una **matriz diagonal** es aquella en la que todos los elementos fuera de la diagonal principal son cero. Formalmente:

$$
\mathbf{D} = \begin{bmatrix}
d_{11} & 0 & 0 \\
0 & d_{22} & 0 \\
0 & 0 & d_{33}
\end{bmatrix}
$$

El interés de las matrices diagonales reside en que simplifican enormemente las operaciones: multiplicar por una matriz diagonal equivale a escalar cada componente de un vector. Este comportamiento es clave en algoritmos de reducción de dimensionalidad y en transformaciones lineales simples.

---

### Matrices simétricas

Una **matriz simétrica** es una matriz cuadrada que coincide con su transpuesta, es decir:

$$
\mathbf{A} = \mathbf{A}^T
$$

Ejemplo:

$$
\mathbf{S} = \begin{bmatrix}
2 & 3 & 1 \\
3 & 5 & 4 \\
1 & 4 & 6
\end{bmatrix}
$$

Las matrices simétricas tienen propiedades muy importantes:

* Todos sus **autovalores** son reales.
* Se pueden **diagonalizar** mediante una base ortogonal.
* Representan relaciones “equilibradas” entre variables, como ocurre en las matrices de covarianzas.

En IA, aparecen de forma recurrente en estadística y aprendizaje automático, ya que las matrices de covarianzas y correlaciones son siempre simétricas, y constituyen la base de técnicas como el PCA.

> **Para reflexionar…**
> **¿Por qué crees que resulta tan útil que las matrices de covarianzas sean simétricas en algoritmos de aprendizaje? ¿Qué implicaciones tiene que sus autovalores sean siempre reales?**

---

El concepto de rango en matrices
---

El **rango de una matriz** es una medida de la cantidad de información independiente que contiene. Dicho de otra manera, nos dice cuántas filas o columnas de la matriz aportan realmente algo nuevo y cuántas son redundantes.

Formalmente, el rango se define como el **número máximo de filas o columnas que son linealmente independientes entre sí**. En la práctica, esto significa que si alguna fila o columna se puede expresar como combinación de otras, deja de aportar información adicional y no cuenta para el rango.

Imaginemos una tabla de datos con varias columnas, cada una representando una característica. Si una columna es, en realidad, la suma o el doble de otra, entonces no aporta nada nuevo. El rango nos alerta de esta redundancia: si tenemos cinco columnas pero solo tres son realmente independientes, el rango de la matriz será 3.

### Interpretación en el contexto de IA

El rango de una matriz de datos puede verse como una medida de la **información útil** que tenemos disponible. **Cuanto mayor es el rango, más diversidad de características independientes existen, y por tanto más rica es la representación de los datos.**

Cuando el rango es menor que el número total de columnas, significa que algunos de los rasgos que hemos recogido son **repetitivos o redundantes**. Aunque tengamos más columnas, no estamos ganando información nueva. En la práctica, esto puede llevar a modelos confusos o ineficaces, porque resulta difícil distinguir qué variables son realmente las responsables de las diferencias en los datos.

### Ejemplos

#### Ejemplo práctico 1

Consideremos la siguiente matriz de $3 \times 3$:

$$
\mathbf{A} =
\begin{bmatrix}
1 & 2 & 3 \\
2 & 4 & 6 \\
1 & 1 & 1
\end{bmatrix}
$$

A primera vista parece que tiene tres filas “distintas”, pero observemos con calma:

* La **segunda fila** es exactamente el doble de la primera.
* Eso significa que la segunda no aporta información nueva, ya que puede construirse como combinación lineal de otra.

En consecuencia, solo la primera y la tercera fila son independientes.

El rango de $\mathbf{A}$ es, por tanto, **2**.

---

##### Interpretación en términos de datos

Podemos imaginar que esta matriz representa un pequeño conjunto de datos con tres características:

* La primera y la segunda columna no son realmente independientes, porque la segunda es el doble de la primera en todas las filas.
* Solo dos columnas bastan para describir toda la información presente en la matriz.

Esto nos indica que los datos en $\mathbf{A}$ tienen **redundancia** y que, aunque formalmente tengamos tres variables, solo dos son útiles de verdad.

#### Ejemplo práctico 2

Supongamos que en una base de datos de viviendas tenemos las siguientes columnas:

* “Tamaño en metros cuadrados”
* “Número de habitaciones”
* “Tamaño en pies cuadrados”

Aunque parecen tres características, en realidad solo hay dos distintas: los metros cuadrados y el número de habitaciones. La columna de pies cuadrados es solo una versión escalada de los metros cuadrados. El rango de esta matriz de datos sería 2, no 3, porque una de las columnas no aporta información independiente.

> **Para reflexionar…**
> **¿Por qué crees que es problemático almacenar muchas características que en el fondo dicen lo mismo? ¿Qué ventajas tendría identificar estas redundancias antes de trabajar con los datos?**
> **Si quisieras entrenar un modelo con estos datos, ¿qué problemas crees que surgirían al incluir una característica que es exactamente proporcional a otra? ¿Por qué sería más razonable quedarse solo con dos columnas?**

---

## Matrices cuadradas y determinante de una matriz

Una primera condición para avanzar en operaciones más complejas es comprender qué significa que una matriz sea **cuadrada**. Llamamos matriz cuadrada a aquella que tiene el mismo número de filas que de columnas. Ejemplos comunes serían una matriz de $2 \times 2$, de $3 \times 3$ o de $n \times n$ en general. Esta condición es indispensable para ciertas operaciones, como veremos cuando queramos calcular la matriz inversa, ya que el concepto mismo de invertir una matriz exige simetría en sus dimensiones. **Si una matriz no es cuadrada, no podemos hablar de inversa.**

El siguiente paso es introducir el **determinante**, un número único que se asocia a cada matriz cuadrada. Aunque pueda parecer un cálculo técnico más, en realidad el determinante nos ofrece una información profunda sobre la estructura de la matriz. De forma intuitiva, podemos pensar en él como un indicador que nos dice si la matriz está “bien formada” o si, por el contrario, contiene redundancias en sus filas o columnas.

### Interpretación del valor del determinante

En efecto, si el determinante de una matriz es **distinto de cero**, significa que sus columnas (o filas) **son linealmente independientes**. En ese caso, la matriz es invertible, lo cual abre la puerta a resolver sistemas de ecuaciones y a aplicar transformaciones sin perder información.

Si, por el contrario, el determinante es **cero**, la matriz se llama **singular** y no tiene inversa. Esto nos está diciendo que al menos una de sus columnas (o filas) se puede expresar como combinación lineal de las demás. En términos prácticos, parte de la información está repetida y la matriz ha “colapsado” en alguna dirección.

### Relación entre rango y determinante

El **rango** y el **determinante** son dos formas distintas de medir la información contenida en una matriz, pero están estrechamente relacionados. El rango nos indica cuántas filas o columnas son independientes entre sí, mientras que el determinante nos da una medida global de esa independencia en el caso particular de las matrices cuadradas.

Si una matriz cuadrada tiene rango **máximo**, es decir, igual a su número de filas o columnas, entonces su determinante es distinto de cero y la matriz es invertible. Por el contrario, si el rango es menor que el tamaño de la matriz, significa que alguna fila o columna se puede obtener como combinación lineal de otras, y en ese caso el determinante es cero.

En otras palabras:

* **Determinante distinto de cero** ⟶ rango máximo ⟶ columnas independientes ⟶ matriz invertible.
* **Determinante igual a cero** ⟶ rango menor al máximo ⟶ dependencia lineal ⟶ matriz singular.

Esta relación es muy útil en la práctica, porque el rango nos ofrece una medida general de la independencia (aplicable a cualquier matriz, cuadrada o no), mientras que el determinante actúa como un “test rápido” que confirma si una matriz cuadrada tiene independencia completa o si, por el contrario, está degenerada.

---

> **Para reflexionar…**
> **¿Por qué crees que en el análisis de datos resulta más flexible trabajar con el rango que con el determinante? ¿Qué ventaja ofrece el rango cuando tratamos matrices rectangulares que no son cuadradas?**

---

### Relación con la IA

En el análisis de datos, este concepto conecta directamente con la **independencia de las características**. Las columnas de una matriz de datos representan las variables o rasgos que describen a cada instancia. Si alguna columna puede deducirse de otras (por ejemplo, si “tamaño en pies cuadrados” es siempre proporcional a “tamaño en metros cuadrados”), el determinante de la matriz que las contiene será cero.

Esta situación refleja la conocida **multicolinealidad**, un problema serio en algoritmos de aprendizaje automático, porque confunde al modelo e impide determinar la contribución individual de cada característica. El resultado suele ser un rendimiento inestable y una interpretación poco fiable.

---

### Ejemplo sencillo

Consideremos la matriz

$$
\mathbf{A} =
\begin{bmatrix}
1 & 2 \\
2 & 4
\end{bmatrix}
$$

El determinante se calcula como

$$
|\mathbf{A}| = (1)(4) - (2)(2) = 0
$$

El resultado nos indica que las dos columnas de $\mathbf{A}$ son dependientes (la segunda es el doble de la primera). No hay, por tanto, dos direcciones realmente independientes en el espacio, y la matriz no puede invertirse.

---

> **Para reflexionar…**
> **¿Por qué crees que es peligroso entrenar un modelo con variables redundantes? ¿Qué pasaría si intentamos resolver un sistema de ecuaciones con datos que contienen esta dependencia oculta?**

---

## Matriz Inversa: el equivalente a la división en el mundo de las matrices

En el álgebra lineal, la **matriz inversa** ocupa un lugar equivalente al de la división en el mundo de los números. Así como todo número real distinto de cero tiene un inverso multiplicativo —por ejemplo, $5 \cdot \tfrac{1}{5} = 1$—, también ciertas matrices poseen una inversa que, al multiplicarse por la matriz original, da como resultado la **matriz identidad**.

### Definición

Formalmente, una matriz cuadrada $\mathbf{A}$ es **invertible** si existe otra matriz $\mathbf{A}^{-1}$ tal que

$$
\mathbf{A} \cdot \mathbf{A}^{-1} = \mathbf{A}^{-1} \cdot \mathbf{A} = \mathbf{I}.
$$

No todas las matrices tienen inversa. Para que una matriz sea invertible debe cumplir dos condiciones:

1. Ser **cuadrada** (mismo número de filas y columnas).
2. Tener un **determinante distinto de cero** (lo que garantiza que sus filas o columnas son linealmente independientes).

Cuando alguna de estas condiciones no se cumple, hablamos de una matriz **singular**, que no tiene inversa.

> **Ejemplo:**
>
> Consideremos la matriz
>
> $$
> \mathbf{A} = 
> \begin{bmatrix}
> 1 & 2 \\
> 3 & 4
> \end{bmatrix}.
> $$
>
> El determinante de $\mathbf{A}$ es
>
> $$
> |\mathbf{A}| = (1)(4) - (2)(3) = -2 \neq 0.
> $$
>
> Por tanto, $\mathbf{A}$ es invertible. Su inversa puede calcularse con la fórmula para matrices $2 \times 2$:
>
> $$
> \mathbf{A}^{-1} = \frac{1}{|\mathbf{A}|}
> \begin{bmatrix}
> d & -b \\
> -c & a
> \end{bmatrix},
> $$
>
> donde $a, b, c, d$ son los elementos de $\mathbf{A}$. Aplicando la fórmula:
>
> $$
> \mathbf{A}^{-1} = \frac{1}{-2}
> \begin{bmatrix}
> 4 & -2 \\
> -3 & 1
> \end{bmatrix}
> =\\
> \begin{bmatrix}
> -2 & 1 \\
> 1.5 & -0.5
> \end{bmatrix}
> $$
>
> Multiplicar $\mathbf{A}$ por $\mathbf{A}^{-1}$ devuelve la matriz identidad $\mathbf{I}_2$.
>

### Interpretación en de la matriz inversa en el campo de la Inteligencia Artificial

En términos prácticos, la matriz inversa aparece al resolver sistemas de ecuaciones lineales del tipo

$$
\mathbf{A}\mathbf{x} = \mathbf{b},
$$

donde $\mathbf{A}$ es una matriz de coeficientes, $\mathbf{x}$ un vector de incógnitas y $\mathbf{b}$ un vector de resultados. Si $\mathbf{A}$ es invertible, la solución se obtiene directamente como

$$
\mathbf{x} = \mathbf{A}^{-1}\mathbf{b}.
$$

En IA, aunque rara vez se calcula la inversa de manera explícita en la práctica (porque es costoso computacionalmente), el concepto es clave para entender cómo los modelos ajustan parámetros o encuentran soluciones únicas. La existencia o no de inversa nos habla de si los datos contienen suficiente información independiente para llegar a una solución estable.

---

> **Para reflexionar…**
> **¿Por qué crees que en problemas con datos redundantes (donde las características no son independientes) no podemos calcular una solución única usando la matriz inversa? ¿Qué alternativas podrían usarse en esos casos?**

### Cómo calcular la inversa de una matriz: Método formal

Aunque en la práctica utilizamos herramientas computacionales como **NumPy** para obtener la inversa de una matriz de forma automática, es importante conocer los métodos básicos que permiten calcularla. Esto nos ayuda a entender qué significa realmente la operación y por qué no siempre es posible realizarla.

El procedimiento depende del tamaño de la matriz:

**1. Para matrices $2 \times 2$**
Existe una fórmula directa. Si

$$
\mathbf{A} =
\begin{bmatrix}
a & b \\
c & d
\end{bmatrix},
$$

su inversa es

$$
\mathbf{A}^{-1} = \frac{1}{ad - bc}
\begin{bmatrix}
d & -b \\
-c & a
\end{bmatrix},
$$

siempre que $ad - bc \neq 0$.

---

**2. Para matrices de mayor dimensión**
El cálculo requiere un procedimiento más general, basado en tres ideas:

* **Determinante**: asegura si la matriz es invertible (debe ser distinto de cero).
* **Matriz adjunta o de cofactores**: se construye a partir de los determinantes menores de la matriz original.
* **División por el determinante**: la inversa se obtiene como

$$
\mathbf{A}^{-1} = \frac{1}{|\mathbf{A}|} \cdot \text{adj}(\mathbf{A}).
$$

Este método, aunque conceptualmente claro, es laborioso de aplicar manualmente para matrices grandes.

---

**3. Métodos algorítmicos**
En la práctica, cuando se trabaja con matrices de tamaño elevado, se utilizan métodos de cálculo basados en **descomposiciones matriciales** (como la eliminación de Gauss-Jordan o la descomposición LU). Estos procedimientos son más eficientes y estables numéricamente, y son los que implementan las bibliotecas de álgebra lineal que se emplean en IA.

#### La matriz adjunta

La **matriz adjunta** es una construcción que se utiliza para calcular la inversa de una matriz cuadrada.

Para obtenerla, seguimos un procedimiento basado en lo que denominan **cofactores**:

1. Para cada elemento $a_{ij}$ de la matriz original $\mathbf{A}$, se calcula su **menor complementario**, que es el determinante de la submatriz que resulta de eliminar la fila $i$ y la columna $j$ de $\mathbf{A}$.
2. A este menor se le aplica un signo según la posición, siguiendo la regla $(-1)^{i+j}$, obteniendo así el **cofactor** $C_{ij}$.
3. Con todos los cofactores se forma la **matriz de cofactores**.
4. Finalmente, la **matriz adjunta** $\text{adj}(\mathbf{A})$ es la transpuesta de la matriz de cofactores.

En resumen:

$$
\text{adj}(\mathbf{A}) = \text{Cof}(\mathbf{A})^T
$$

donde $\text{Cof}(\mathbf{A})$ es la matriz de cofactores de $\mathbf{A}$.

Una vez construida la matriz adjunta, la inversa de $\mathbf{A}$ se puede calcular mediante la fórmula:

$$
\mathbf{A}^{-1} = \frac{1}{|\mathbf{A}|}\,\text{adj}(\mathbf{A})
$$

siempre que $|\mathbf{A}| \neq 0$.

---

Perfecto 🙌. Entonces preparo un **ejemplo completo con una matriz $3 \times 3$**, para que los alumnos vean cómo se aplica el método de la adjunta al cálculo de la inversa.

---

#### Ejemplo: cálculo de la inversa de una matriz $3 \times 3$ usando la adjunta

Consideremos la matriz

$$
\mathbf{A} =
\begin{bmatrix}
1 & 2 & 3 \\
0 & 1 & 4 \\
5 & 6 & 0
\end{bmatrix}.
$$

**1. Cálculo del determinante**

Para poder calcular la inversa necesitamos que el determinante sea distinto de cero.

$$
|\mathbf{A}| = 1 \cdot (1 \cdot 0 - 4 \cdot 6) - 2 \cdot (0 \cdot 0 - 4 \cdot 5) + 3 \cdot (0 \cdot 6 - 1 \cdot 5)
$$

$$
= 1 \cdot (-24) - 2 \cdot (-20) + 3 \cdot (-5)
= -24 + 40 - 15 = 1
$$

Como $|\mathbf{A}| = 1 \neq 0$, la matriz es invertible.

---

**2. Matriz de cofactores**

Ahora calculamos cada cofactor $C_{ij} = (-1)^{i+j} |M_{ij}|$, donde $M_{ij}$ es la submatriz que se obtiene eliminando la fila $i$ y la columna $j$.

$$
C_{11} = 
\begin{vmatrix} 1 & 4 \\
6 & 0 
\end{vmatrix}
=\\ (1)(0) - (4)(6) = -24
$$

$$
C_{12} = 
-\begin{vmatrix}
 0 & 4 \\
 5 & 0 
 \end{vmatrix} 
= -[(0)(0) - (4)(5)] = -(-20) = 20
$$

$$
C_{13} = 
\begin{vmatrix}
0 & 1 \\
5 & 6
\end{vmatrix}
= (0)(6) - (1)(5) = -5
$$

$$
C_{21} = 
-\begin{vmatrix}
2 & 3 \\
6 & 0
\end{vmatrix}
= -[(2)(0) - (3)(6)] = -(-18) = 18
$$

$$
C_{22} = 
\begin{vmatrix}
1 & 3 \\
5 & 0
\end{vmatrix}
= (1)(0) - (3)(5) = -15
$$

$$
C_{23} = 
-\begin{vmatrix}
1 & 2 \\
5 & 6
\end{vmatrix}
= -[(1)(6) - (2)(5)] = -[6 - 10] = 4
$$

$$
C_{31} = 
\begin{vmatrix}
2 & 3 \\
1 & 4
\end{vmatrix}
= (2)(4) - (3)(1) = 8 - 3 = 5
$$

$$
C_{32} = 
-\begin{vmatrix}
1 & 3 \\
0 & 4
\end{vmatrix}
= -[(1)(4) - (3)(0)] = -4
$$

$$
C_{33} = 
\begin{vmatrix}
1 & 2 \\
0 & 1
\end{vmatrix}
= (1)(1) - (2)(0) = 1
$$

La **matriz de cofactores** es:

$$
\text{Cof}(\mathbf{A}) =
\begin{bmatrix}
-24 & 20 & -5 \\
18 & -15 & 4 \\
5 & -4 & 1
\end{bmatrix}.
$$

---

**3. Matriz adjunta**

La adjunta se obtiene trasponer la matriz de cofactores:

$$
\text{adj}(\mathbf{A}) =
\begin{bmatrix}
-24 & 18 & 5 \\
20 & -15 & -4 \\
-5 & 4 & 1
\end{bmatrix}.
$$

---

**4. Inversa de la matriz**

Finalmente, aplicamos la fórmula:

$$
\mathbf{A}^{-1} = \frac{1}{|\mathbf{A}|} \, \text{adj}(\mathbf{A}).
$$

Como $|\mathbf{A}| = 1$, la inversa coincide con la adjunta:

$$
\mathbf{A}^{-1} =
\begin{bmatrix}
-24 & 18 & 5 \\
20 & -15 & -4 \\
-5 & 4 & 1
\end{bmatrix}.
$$

---

> **Para reflexionar…**
> **Si en este ejemplo el determinante hubiera resultado ser cero, ¿qué habría significado en términos de independencia de las filas y columnas de la matriz? ¿Cómo se relaciona esto con la imposibilidad de calcular la inversa?**

#### Interpretación práctica

Más allá de la técnica concreta, lo importante es comprender que el cálculo de la inversa está íntimamente ligado a la estructura de la matriz:

* Si el determinante es cero, no podremos obtener una inversa, sin importar el método.
* Si el determinante es distinto de cero, siempre existirá una estrategia para calcularla, aunque en la práctica lo haremos con un ordenador.

---

> **Para reflexionar…**
> **Si en un proyecto de IA tuviéramos que invertir una matriz de datos de tamaño muy grande, ¿crees que sería práctico hacerlo a mano con el método de cofactores? ¿Qué ventajas ofrecen entonces las bibliotecas computacionales frente a los métodos teóricos?**

---

### Métodos alternativos para el cálculo de la matriz inversa

El cálculo de la inversa de una matriz puede hacerse de varias maneras. Aunque la definición formal mediante la **matriz adjunta** y el **determinante** es útil para matrices pequeñas, en la práctica existen otros métodos más eficientes y aplicables a matrices de mayor dimensión. Estos métodos son importantes porque, en el contexto de la inteligencia artificial, solemos trabajar con datos de gran tamaño y necesitamos estrategias que sean estables y rápidas.

---

#### El método de Gauss-Jordan

El método de **Gauss-Jordan** es un procedimiento algorítmico que permite calcular la inversa de una matriz aplicando operaciones elementales por filas.

El proceso comienza construyendo una **matriz aumentada** en la que a la derecha de la matriz $\mathbf{A}$ se coloca la matriz identidad $\mathbf{I}$:

$$
[\mathbf{A} \,|\, \mathbf{I}]
$$

El objetivo es aplicar transformaciones por filas que reduzcan la parte izquierda hasta convertirla en la matriz identidad. Cuando esto ocurre, la parte derecha se habrá transformado en la matriz inversa $\mathbf{A}^{-1}$:

$$
[\mathbf{I} \,|\, \mathbf{A}^{-1}]
$$

Este método resulta especialmente útil porque es **mecánico y sistemático**: basta con seguir una secuencia de operaciones sin necesidad de calcular determinantes ni cofactores. Por este motivo es un enfoque mucho más práctico para la enseñanza y la programación de algoritmos.

#### Descomposiciones matriciales LU y QR

En problemas reales de IA, cuando las matrices son muy grandes, se emplean técnicas de **descomposición** que permiten reorganizar la matriz en factores más simples. Estas factorizaciones facilitan la resolución de sistemas lineales sin necesidad de calcular directamente la inversa.

* **Descomposición LU**: toda matriz invertible puede escribirse como el producto de dos matrices, una triangular inferior ($\mathbf{L}$) y otra triangular superior ($\mathbf{U}$). Resolver un sistema de ecuaciones con esta descomposición resulta mucho más rápido que calcular la inversa.

* **Descomposición QR**: la matriz se descompone en una matriz ortogonal $\mathbf{Q}$ y una triangular superior $\mathbf{R}$. Este método es muy útil en problemas de optimización y en el cálculo de autovalores, que son fundamentales para algoritmos de reducción de dimensionalidad.

Estas técnicas muestran que la **inversa no se calcula directamente**, sino que se evita en favor de procedimientos más eficientes y menos sensibles a errores numéricos.

#### Por qué casi nunca se calcula la inversa explícita en IA

En la práctica, calcular la inversa de una matriz de manera explícita es algo excepcional. Existen varias razones para ello:

* **Costo computacional elevado**: calcular la inversa de matrices grandes requiere muchos cálculos, lo que no es eficiente en entornos donde los datos crecen rápidamente.
* **Inestabilidad numérica**: los ordenadores trabajan con números aproximados, y los pequeños errores de redondeo pueden amplificarse al invertir una matriz.
* **Métodos alternativos más fiables**: en la mayoría de los casos, resolver el problema que requiere la inversa puede hacerse directamente con descomposiciones LU, QR o tam bién SVD, sin necesidad de calcular la inversa de forma explícita.

Por esto, aunque el concepto de inversa es crucial desde el punto de vista teórico, los algoritmos prácticos en IA suelen **evitar calcularla directamente**.

---

> **Para reflexionar…**
> **Si las herramientas computacionales modernas nos permiten resolver sistemas lineales sin necesidad de invertir matrices, ¿por qué sigue siendo importante entender qué es la matriz inversa y cuáles son sus propiedades teóricas?**

## Autovalores y autovectores: una nueva forma de ver las matrices

Hemos visto que cuando multiplicamos una matriz por un vector, lo habitual es que el resultado sea un vector distinto: cambia su dirección y también su magnitud. Sin embargo, existen casos especiales en los que un vector **mantiene su dirección** al ser transformado, aunque su tamaño cambie. Estos vectores se llaman **autovectores**, y el factor de escala que los acompaña se llama **autovalor**.

Formalmente, un vector $\mathbf{v}$ es autovector de una matriz cuadrada $\mathbf{A}$ si existe un escalar $\lambda$ tal que

$$
\mathbf{A}\mathbf{v} = \lambda \mathbf{v}
$$

donde $\lambda$ es el **autovalor** asociado a $\mathbf{v}$.

---

### Interpretación geométrica

Podemos imaginar que una matriz representa una transformación en el plano: rotar, estirar o comprimir. La mayoría de los vectores cambian de dirección bajo esa transformación, pero algunos se limitan a cambiar de tamaño sin perder la orientación.

* Si $\lambda > 1$, el vector se estira.
* Si $0 < \lambda < 1$, el vector se encoge.
* Si $\lambda < 0$, el vector también cambia de sentido.
* Si $\lambda = 0$, el vector colapsa en el vector nulo.



> **Ejemplo:**
>
> Consideremos la matriz
>
> $$
> \mathbf{A} =
> \begin{bmatrix}
> 2 & 0 \\
> 0 & 3
> \end{bmatrix}
> $$
>
> Si multiplicamos $\mathbf{A}$ por el vector 
>
>$$\mathbf{v}_1 =
>\begin{bmatrix}1 \ 0
>\end{bmatrix}
>$$
>, obtenemos
>
> $$
> \mathbf{A}\mathbf{v}_1 =
> \begin{bmatrix}
> 2 & 0 \\
> 0 & 3
> \end{bmatrix}
> \begin{bmatrix}
> 1 \\
> 0
> \end{bmatrix}
> = \\
> \begin{bmatrix}
> 2 \\
> 0
> \end{bmatrix}
> = 2\mathbf{v}_1
> $$
>
> Aquí, $\mathbf{v}_1$ es un autovector y su autovalor es $\lambda = 2$.
>
> De manera análoga, para $$\mathbf{v}_2 = \begin{bmatrix}0 \ 1\end{bmatrix}$$:
>
> $$
> \mathbf{A}\mathbf{v}_2 =
> \begin{bmatrix}
> 0 \\
> 3
> \end{bmatrix}
> = 3\mathbf{v}_2
> $$
>
> Por tanto, $\mathbf{v}_2$ es un autovector y $\lambda = 3$ su autovalor.
>

---

### Relevancia en inteligencia artificial

Como en otros elementos del álgebra lineal, aunque autovalores y autovectores puedan parecer un concepto matemático abstracto, en realidad aparecen de forma natural en distintos ámbitos de la inteligencia artificial. No nos interesa en un primer momento saber calcular los mismos, sino comprender su significado y entender cómo permiten simplificar problemas complejos.

#### Análisis de componentes principales (PCA)

En el **Análisis de Componentes Principales (PCA)**, por ejemplo, los datos se organizan a menudo en un espacio con muchas dimensiones. Una matriz de covarianza nos revela cómo se relacionan esas dimensiones entre sí, y sus autovectores nos indican hacia qué direcciones se extienden más los datos. Dicho de otro modo, los autovectores marcan las direcciones privilegiadas en las que la nube de puntos muestra mayor variabilidad, mientras que los autovalores nos dicen con qué intensidad se produce esa variación. Esta idea es la que permite reducir la dimensionalidad de un conjunto de datos sin perder la mayor parte de la información relevante, proyectándolos en menos ejes pero más representativos.

por ejemplo, para describir una casa podrías registrar el número de habitaciones, los metros cuadrados, el precio, la antigüedad, etc. Si representamos estas variables en un espacio de coordenadas, obtenemos una nube de puntos.

Ahora bien, esa nube de datos no se reparte de forma uniforme en todas las direcciones. Habrá ciertas direcciones en las que los datos varíen mucho (por ejemplo, casas más grandes suelen tener más habitaciones), y otras en las que apenas cambien.

Aquí entran en juego los autovectores y autovalores de la **matriz de covarianza**:

- Los **autovectores** señalan esas direcciones privilegiadas donde los datos “se abren más” o presentan mayor variabilidad.
- Los **autovalores** indican cuánto se extienden los datos en cada dirección.

El PCA aprovecha esta idea: en lugar de trabajar con todas las variables originales, proyecta los datos sobre las direcciones más importantes (autovectores con autovalores más grandes). De este modo, se reduce el número de dimensiones, pero conservando casi toda la información esencial.

#### Covarianza y correlación

En el análisis de **covarianza y correlación**, el papel de los autovalores es igualmente revelador. Un autovalor grande significa que hay una dirección en la que los datos se dispersan de forma notable, lo cual refleja un patrón importante. En cambio, autovalores pequeños se asocian a direcciones donde apenas hay variación, lo que suele ser indicio de ruido o de redundancia entre variables. En términos intuitivos, los autovalores actúan como un filtro que nos ayuda a separar lo esencial de lo accesorio.

#### Redes neuronales

En el caso de las **redes neuronales profundas**, los autovalores aparecen en un contexto diferente pero no menos importante. En el entrenamiento de una red neuronal, utilizamos un algoritmo llamado **descenso de gradiente**. Este algoritmo ajusta poco a poco los parámetros del modelo para que la predicción se acerque cada vez más a la realidad.

Pero la “superficie” que describe el error no es plana: es una especie de paisaje con valles y montañas. Los autovalores de la **matriz Hessiana** (que recoge las curvaturas de ese paisaje) nos indican si el terreno es estable o problemático: Si hay autovalores **muy grandes**, significa que en ciertas direcciones el paisaje es demasiado empinado: el algoritmo puede dar pasos demasiado bruscos y volverse inestable. Si hay autovalores **muy pequeños** (cercanos a cero), significa que el paisaje es casi plano en algunas direcciones: el algoritmo avanza con dificultad y el aprendizaje se hace muy lento.

#### Modelos dinámicos

Algo similar ocurre en los **modelos dinámicos**, donde se estudia la evolución de un sistema a lo largo del tiempo. Puede tratarse de cómo se estabiliza la temperatura en una habitación, de cómo se propaga una enfermedad o de cómo evoluciona una población. Los autovalores de las matrices que describen estos procesos nos dicen si el sistema tenderá a equilibrarse, a crecer de manera descontrolada o a entrar en un ciclo de oscilaciones. En este sentido, los autovalores actúan como una especie de termómetro de la estabilidad de un proceso dinámico.

Por ejemplo, imagina el caso concreto de un modelo dinámico que describe cómo evoluciona la temperatura en una sala. Los autovalores de la matriz que describe esa dinámica nos dan información clave:

- Si todos los autovalores están entre 0 y 1, el sistema tiende a estabilizarse (por ejemplo, la temperatura se equilibra).
- Si algún autovalor es mayor que 1, el sistema crece sin control (una epidemia que se expande rápidamente).
- Si los autovalores son negativos o complejos, el sistema puede mostrar oscilaciones o comportamientos más imprevisibles.

------

>**Para reflexionar**
> ¿Por qué es tan útil poder identificar direcciones privilegiadas en un conjunto de datos o en la dinámica de un sistema? ¿Cómo nos ayuda esta visión a simplificar problemas que, a primera vista, parecen demasiado complejos
>
> ¿Por qué es útil identificar vectores que no cambian de orientación bajo la acción de una matriz? ¿Qué nos dice un autovalor grande sobre la importancia de esa dirección en los datos?

### La ecuación característica

Hasta ahora hemos comprendido de manera intuitiva qué significa que un vector sea un autovector y que un número asociado sea su autovalor. El siguiente paso es ver cómo se calculan en la práctica.

Partimos de la definición: un vector $\mathbf{v}$ es autovector de una matriz $\mathbf{A}$ si cumple

$$
\mathbf{A}\mathbf{v} = \lambda \mathbf{v}.
$$

Si pasamos todo al mismo lado, obtenemos

$$
(\mathbf{A} - \lambda \mathbf{I}) \mathbf{v} = \mathbf{0}.
$$

Para que esta ecuación tenga soluciones no triviales (es decir, vectores distintos del vector nulo), la matriz $(\mathbf{A} - \lambda \mathbf{I})$ no debe ser invertible. Esto ocurre precisamente cuando su determinante es igual a cero.

De aquí surge la **ecuación característica**:

$$
|\mathbf{A} - \lambda \mathbf{I}| = 0.
$$

Resolver esta ecuación nos da los posibles valores de $\lambda$, que son los **autovalores** de la matriz. Una vez obtenidos, podemos calcular los **autovectores** resolviendo el sistema lineal $(\mathbf{A} - \lambda \mathbf{I})\mathbf{v} = \mathbf{0}$ para cada autovalor.

> **Ejemplo sencillo en $2\times 2$**
>
> Consideremos la matriz
>
> $$
> \mathbf{A} =
> \begin{bmatrix}
> 2 & 1 \\
> 1 & 2
> \end{bmatrix}.
> $$
>
> La ecuación característica es
>
> $$
> \det \begin{bmatrix}
> 2 - \lambda & 1 \\
> 1 & 2 - \lambda
> \end{bmatrix} = 0.
> $$
>
> El determinante se desarrolla como
>
> $$
> (2 - \lambda)(2 - \lambda) - (1)(1) = (2 - \lambda)^2 - 1 = 0.
> $$
>
> Resolviendo:
>
> $$
> (2 - \lambda)^2 = 1 \quad \Rightarrow \quad 2 - \lambda = \pm 1.
> $$
>
> De aquí obtenemos dos autovalores: $\lambda_1 = 1$ y $\lambda_2 = 3$.
>
> Para $\lambda_1 = 1$, sustituimos en $(\mathbf{A} - \lambda \mathbf{I})\mathbf{v} = 0$:
>
> $$
> \begin{bmatrix}
> 1 & 1 \\
> 1 & 1
> \end{bmatrix}
> \begin{bmatrix}
> x \\
> y
> \end{bmatrix}
> = \\
> \begin{bmatrix}
> 0 \\
> 0
> \end{bmatrix}.
> $$
>
> Esto implica que $x = -y$, así que un autovector es
>
> $$
> \mathbf{v}_1 = \begin{bmatrix}1 \\ -1\end{bmatrix}.
> $$
>
> Para $\lambda_2 = 3$, hacemos lo mismo:
>
> $$
> \begin{bmatrix}
> -1 & 1 \\
> 1 & -1
> \end{bmatrix}
> \begin{bmatrix}
> x \\
> y
> \end{bmatrix}
> = \\
> \begin{bmatrix}
> 0 \\
> 0
> \end{bmatrix}.
> $$
>
> Ahora se cumple $x = y$, y un autovector correspondiente es
>
> $$
> \mathbf{v}_2 = \begin{bmatrix}1 \\ 1\end{bmatrix}.
> $$
>
> ---
>
> **Interpretación del ejemplo**
>
> La matriz $\mathbf{A}$ transforma los vectores del plano de tal manera que los que están alineados con $(1, -1)$ se encogen (autovalor $1$), mientras que los que están alineados con $(1,1)$ se estiran (autovalor $3$). El resto de vectores se transforman en combinaciones de estas dos direcciones principales.
>
> Este ejemplo muestra cómo los autovalores y autovectores revelan las **direcciones privilegiadas de una transformación lineal** y el **factor de escala** aplicado en cada una.
>

---

>**Para reflexionar**
> Si tuviéramos un conjunto de datos que se extiende principalmente a lo largo de la dirección $(1,1)$, ¿qué nos diría que esa dirección tenga un autovalor grande? ¿Cómo podríamos usar esta información para representar los datos de manera más simple?

---

#### Relación entre autovalores, autovectores y la diagonalización de una matriz

Una última propiedad muy interesante de autovalores y autovectores es que, juntos, permiten **reorganizar una matriz** en una forma mucho más simple de interpretar. Esa reorganización recibe el nombre de **diagonalización**.

El punto de partida es que una matriz $\mathbf{A}$ puede escribirse como

$$
\mathbf{A}\mathbf{v} = \lambda \mathbf{v},
$$

donde $\mathbf{v}$ es un autovector y $\lambda$ su autovalor. Si reunimos todos los autovectores de la matriz y los colocamos como columnas en una nueva matriz $\mathbf{P}$, y además ponemos los autovalores en una matriz diagonal $\mathbf{D}$, ocurre algo sorprendente:

$$
\mathbf{A} = \mathbf{P} \mathbf{D} \mathbf{P}^{-1}.
$$

Esta expresión es lo que llamamos **diagonalización**. La matriz $\mathbf{D}$ es diagonal porque en ella solo aparecen los autovalores en la diagonal principal, y la matriz $\mathbf{P}$ contiene los autovectores que “explican” esa transformación.

##### Interpretación e importancia en IA

Diagonalizar una matriz significa “cambiar de perspectiva” para ver el problema en la base formada por los autovectores. En esa nueva base, la transformación que antes era complicada ahora se reduce a algo muy simple: cada autovector se escala por su autovalor, sin mezclarse con los demás.

Lo que antes era una transformación general en el espacio se convierte, tras la diagonalización, en un conjunto de estiramientos y encogimientos independientes, cada uno en su propia dirección.

Aunque no siempre se presenta explícitamente con el nombre de diagonalización, esta idea está detrás de muchos algoritmos:

* En el **PCA**, diagonalizar la matriz de covarianza nos permite encontrar las direcciones independientes de máxima variabilidad. La matriz diagonal contiene la varianza explicada en cada componente, lo que facilita elegir cuáles conservar.
* En el análisis de la matriz **Hessiana** de una función de pérdida, la diagonalización permite descomponer la curvatura en direcciones independientes, mostrando por qué unas direcciones del aprendizaje son más “difíciles” que otras.
* En modelos dinámicos, la diagonalización ayuda a predecir el comportamiento de un sistema descomponiéndolo en evoluciones independientes, cada una gobernada por un autovalor.

> **Ejemplo de diagonalización de una matriz $2\times 2$**
>
> Consideremos la matriz
>
> $$
> \mathbf{A} =
> \begin{bmatrix}
> 2 & 1 \\
> 1 & 2
> \end{bmatrix}.
> $$
>
> Queremos encontrar si es diagonalizable, y en ese caso obtener la descomposición
>
> $$
> \mathbf{A} = \mathbf{P}\mathbf{D}\mathbf{P}^{-1},
> $$
>
> donde $\mathbf{D}$ es diagonal y $\mathbf{P}$ contiene los autovectores.
>
> **Paso 1: cálculo de los autovalores**
>
> Partimos de la ecuación característica:
>
> $$
> |\mathbf{A} - \lambda \mathbf{I}| = 0.
> $$
>
> Es decir:
>
> $$
> \det \begin{bmatrix}
> 2 - \lambda & 1 \\
> 1 & 2 - \lambda
> \end{bmatrix} = (2 - \lambda)(2 - \lambda) - 1 = (2 - \lambda)^2 - 1.
> $$
>
> De aquí obtenemos
>
> $$
> (2 - \lambda)^2 = 1 \quad \Rightarrow \quad \lambda_1 = 1, \ \lambda_2 = 3.
> $$
>
> **Paso 2: cálculo de los autovectores**
>
> Para $\lambda_1 = 1$:
>
> $$
> (\mathbf{A} - \mathbf{I})\mathbf{v} = 
> \begin{bmatrix}
> 1 & 1 \\
> 1 & 1
> \end{bmatrix}
> \begin{bmatrix}
> x \\
> y
> \end{bmatrix}
> = \begin{bmatrix}0 \\ 0\end{bmatrix}.
> $$
>
> Esto implica $x = -y$, por lo que un autovector es
>
> $$
> \mathbf{v}_1 = \begin{bmatrix} 1 \\ -1 \end{bmatrix}.
> $$
>
> Para $\lambda_2 = 3$:
>
> $$
> (\mathbf{A} - 3\mathbf{I})\mathbf{v} =
> \begin{bmatrix}
> -1 & 1 \\
> 1 & -1
> \end{bmatrix}
> \begin{bmatrix}
> x \\
> y
> \end{bmatrix}
> = \begin{bmatrix}0 \\ 0\end{bmatrix}.
> $$
>
> Esto implica $x = y$, por lo que un autovector es
>
> $$
> \mathbf{v}_2 = \begin{bmatrix} 1 \\ 1 \end{bmatrix}.
> $$
>
> **Paso 3: construcción de $\mathbf{P}$ y $\mathbf{D}$**
>
> Colocamos los autovectores como columnas de la matriz $\mathbf{P}$:
>
> $$
> \mathbf{P} =
> \begin{bmatrix}
> 1 & 1 \\
> -1 & 1
> \end{bmatrix}.
> $$
>
> Y construimos la matriz diagonal $\mathbf{D}$ con los autovalores en la diagonal:
>
> $$
> \mathbf{D} =
> \begin{bmatrix}
> 1 & 0 \\
> 0 & 3
> \end{bmatrix}.
> $$
>
> **Paso 4: verificación**
>
> Comprobamos que efectivamente
>
> $$
> \mathbf{A} = \mathbf{P}\mathbf{D}\mathbf{P}^{-1}.
> $$
>
> Es decir, al cambiar la base al sistema definido por los autovectores, la matriz $\mathbf{A}$ se convierte en la matriz diagonal $\mathbf{D}$, mucho más fácil de interpretar: la dirección $(1,-1)$ se escala por $1$ y la dirección $(1,1)$ se escala por $3$.
>
> La diagonalización revela que la transformación definida por $\mathbf{A}$ es, en el fondo, muy simple: en la base original parece mezclar coordenadas, pero en la base de autovectores solo estira en una dirección y encoge en otra. Esto es lo que hace que el análisis de problemas complejos se vuelva más comprensible y manejable.
>

---

>**Para reflexionar...**
> **¿Qué significa, desde un punto de vista práctico, que una matriz se pueda “resumir” como una diagonal en la base de sus autovectores? ¿Cómo facilita esto la interpretación de un conjunto de datos o de un modelo en IA?**

