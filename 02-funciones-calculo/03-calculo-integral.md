# Cálculo integral y acumulación de información

Si la derivada mide el cambio puntual, la integral hace lo contrario: mide la **acumulación**. Una forma sencilla de verlo es pensar en la integral como una **suma continua**. Si tenemos una función $f(x)$, su integral entre $a$ y $b$ representa la suma de todos los valores de $f(x)$ en ese intervalo, multiplicados por incrementos diminutos de $x$. En términos geométricos, la integral es el **área bajo la curva** de $f(x)$ entre dos puntos.

Un ejemplo cotidiano es la relación entre velocidad y distancia. La velocidad varía a cada instante, pero si integramos la velocidad a lo largo del tiempo, obtenemos la distancia total recorrida. Así, la integral convierte una información local (qué tan rápido va un objeto en cada momento) en una información acumulada (cuánto camino ha recorrido en total).

Esta idea conecta directamente con la **probabilidad**. Una función de densidad de probabilidad, como la de la distribución normal, asigna un valor a cada punto posible. La integral de esa función en un intervalo nos da la probabilidad de que un evento caiga en ese rango. En otras palabras, la probabilidad es un área bajo la curva de la densidad. Además, la integral nos permite calcular **valores esperados** o medias ponderadas: en probabilidad, la esperanza matemática de una variable aleatoria $X$ se expresa como
$$
\mathbb{E}[X] = \int_{-\infty}^{\infty} x\,p(x)\,dx
$$
donde $p(x)$ es la función de densidad.

En inteligencia artificial, estas ideas aparecen de forma natural. El cálculo de **expectativas** es fundamental, por ejemplo, en el entrenamiento de modelos probabilísticos, donde se busca minimizar el error esperado en lugar del error de un solo caso. También interviene en métricas de evaluación: la media del error cuadrático sobre un conjunto de ejemplos se interpreta como una integral discreta, una suma sobre los datos. Incluso algoritmos avanzados como los basados en inferencia bayesiana formulan el aprendizaje como un problema de integración de probabilidades sobre espacios de parámetros.

Un aspecto importante es que, en la mayoría de los contextos reales, estas integrales no se pueden calcular de manera exacta. En vez de fórmulas cerradas, recurrimos a **métodos numéricos**: aproximar el área bajo la curva con rectángulos (regla del trapecio), sumar valores en puntos seleccionados (cuadraturas) o simular muestras aleatorias (métodos de Monte Carlo). En IA esto es especialmente relevante, porque las funciones que aparecen suelen tener miles de variables, y la integración exacta se vuelve imposible. Los algoritmos aprenden, entonces, a **aproximar** esas integrales con técnicas computacionales eficientes.

> **Para reflexionar…**
> ¿Por qué crees que en IA, donde los modelos pueden tener millones de parámetros, resulta más útil aproximar integrales mediante muestras o simulaciones que intentar resolverlas de forma exacta?

## 
