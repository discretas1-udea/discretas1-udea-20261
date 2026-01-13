---
layout: default
title: Clase 04 - Enfoque axiomático
parent: Lógica Proposicional
nav_order: 4
math: mathjax
---

![Built with AI](https://img.shields.io/badge/Built%20with-AI-blue.svg)
# Clase 04 – Enfoque axiomático
{: .no_toc }

## Introducción: Del Álgebra Escolar a la Lógica Formal
{: .no_toc }

Seguramente, durante sus estudios de Álgebra en el colegio se topó con ejercicios de **simplificación** como el siguiente:

> **Ejercicio:** Simplificar la expresión racional:
>
> $$\frac{x^2-9}{x^2+4x+3}$$

Para resolverlo, usted no probaba números al azar hasta que funcionara. Usted aplicaba reglas estructurales (casos de factorización):

$$
\begin{aligned}
  \frac{x^2-9}{x^2+4x+3} &= \frac{(x-3)(x+3)}{(x+3)(x+1)} & \quad \text{(Diferencia de cuadrados y Trinomio)} \\
                         &= \frac{x-3}{x+1} & \quad \text{(Cancelación de términos semejantes)}
\end{aligned}
$$

**Nótese algo crucial:** Mediante la aplicación de reglas que asumimos como verdaderas (teoremas matemáticos), transformamos una expresión compleja en una **equivalente más simple** sin necesidad de evaluar el valor de $x$.

En la **Lógica Proposicional**, el juego es el mismo, solo cambian las fichas:
* Ya no operamos con variables numéricas reales ($x, y, \pi$), sino con variables proposicionales ($p, q, r$).
* Nuestras operaciones no son suma y resta, sino conjunciones ($\land$), disyunciones ($\lor$) e implicaciones ($\to$).

### ¿Por qué necesitamos un nuevo enfoque?
{: .no_toc }

En la clase anterior utilizamos **Tablas de Verdad** (Enfoque basado en Modelos) para verificar equivalencias. Si bien este método es infalible, se vuelve inmanejable rápidamente: una tabla con 5 variables requiere 32 filas; una con 10 variables, ¡1024 filas!

Aquí entra el **Enfoque Axiomático**. Al igual que en el álgebra, utilizaremos un conjunto de "Leyes" o "Axiomas Lógicos" para manipular, simplificar y demostrar equivalencias de forma elegante y eficiente, sin necesidad de construir tablas gigantescas.

## Objetivos de la Clase
{: .no_toc }

En esta sesión:
1.  Repasaremos brevemente la diferencia entre el enfoque semántico (tablas) y el sintáctico (axiomas).
2.  Presentaremos las **Leyes de la Lógica** (sus nuevas "reglas de factorización").
3.  Realizaremos ejercicios de **simplificación** paso a paso.
4.  Aprenderemos a validar argumentos lógicos mediante derivación formal.

## Tabla de Contenidos
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Repaso: Equivalencia Lógica y el Enfoque Basado en Modelos

Antes de comenzar a operar con axiomas, es fundamental tener claro qué estamos buscando. En la **Clase 03**, definimos el concepto central de nuestra álgebra: la **Equivalencia Lógica**.

### ¿Qué significa que dos proposiciones sean equivalentes?

Dos proposiciones compuestas $P$ y $Q$ son lógicamente equivalentes (se denota $P \equiv Q$ o $P \iff Q$) si tienen **exactamente el mismo valor de verdad** para todas las posibles combinaciones de verdad de sus variables atómicas.

En términos sencillos: semánticamente, $P$ y $Q$ dicen lo mismo, aunque su estructura gramatical (sintaxis) sea diferente.

### El Enfoque Basado en Modelos (Tablas de Verdad)

Hasta ahora, nuestra herramienta principal para verificar si dos expresiones eran equivalentes ha sido el **Enfoque basado en Modelos**. Este método consiste en construir una tabla de verdad exhaustiva ("fuerza bruta") para inspeccionar cada escenario posible.

**Ejemplo de la clase anterior:**
Recordemos cómo demostramos que negar una condicional *no* implica negar sus partes, sino afirmar el antecedente y negar el consecuente:

$$\neg(p \to q) \equiv p \land \neg q$$

Construyendo la tabla de verdad (el modelo):

| $p$ | $q$ | $p \to q$ | $\mathbf{\neg(p \to q)}$ | $\neg q$ | $\mathbf{p \land \neg q}$ |
|:---:|:---:|:---:|:---:|:---:|:---:|
| 1 | 1 | 1 | **0** | 0 | **0** |
| 1 | 0 | 0 | **1** | 1 | **1** |
| 0 | 1 | 1 | **0** | 0 | **0** |
| 0 | 0 | 1 | **0** | 1 | **0** |

Al observar que la columna de $\neg(p \to q)$ es idéntica a la de $p \land \neg q$ en todas las filas, concluimos que la equivalencia es válida.

> **El problema de este enfoque:**
> Como mencionamos en la introducción, este método es perfecto para verificar, pero ineficiente para *descubrir* o simplificar. Si nos piden simplificar una expresión de 4 variables, ¿realmente queremos dibujar una tabla de 16 filas?
>
> Para evitar esto, cambiamos de estrategia: del **enfoque semántico** (tablas) al **enfoque sintáctico** (axiomas).

