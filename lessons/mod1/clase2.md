---
layout: default
title: Clase 02 - Operadores Lógicos y Tablas de Verdad
parent: Lógica Proposicional
nav_order: 2                   
---

![Built with AI](https://img.shields.io/badge/Built%20with-AI-blue.svg)

# Clase 02 - Operadores Lógicos y Tablas de Verdad
{: .no_toc }

Esta sesión profundiza en la semántica de los operadores lógicos, estableciendo las reglas para determinar el valor de verdad de proposiciones compuestas y la construcción de tablas de verdad.

## Tabla de Contenidos
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Repaso Clase Anterior
{: .no_toc }

Para entender los operadores de hoy, necesitamos tener frescos tres conceptos fundamentales de la clase pasada. Utiliza este cuadro para recordar:

### La Regla de Oro de la Proposición

Una **Proposición** no es cualquier frase. Para serlo, debe cumplir estrictamente el **Principio de Bivalencia**:
> "Debe poder clasificarse como **Verdadera** ($V$) o **Falsa** ($F$), pero nunca ambas a la vez, ni ninguna."

No todos los enunciados son proposiciones. Veamos:
* **No son proposiciones:** Preguntas ("¿Qué hora es?"), Órdenes ("¡Siéntese!"), Exclamaciones o Deseos ("Ojalá llueva").
* **Sí son proposiciones:** Afirmaciones sobre hechos ("Hoy es martes", "Dino es un perro").

### El Objetivo del Curso

**¿Por qué nos complicamos con símbolos?**: La transición del lenguaje cotidiano al lógico es necesaria por una razón fundamental: la precisión.
1. **El lenguaje natural es ambiguo**: Palabras como "vela" ("vela" puede ser de barco o de cera). cambian su significado según el contexto, lo que puede generar errores de interpretación. 
2. **El lenguaje lógico es exacto**: Elimina la duda al traducir ideas en fórmulas matemáticas como $p \land q$.

Gracias a esta abstracción, es posible representar y operar sobre problemas reales de forma estructurada. Al aplicar el rigor de las matemáticas, dejamos de lado las interpretaciones subjetivas para enfocarnos en la verificación lógica de la verdad.

### Elementos de la Formalización

La lógica proposicional opera mediante la **formalización**, un proceso que traduce el lenguaje natural (intrínsecamente ambiguo y semántico) a un lenguaje simbólico (exacto y sintáctico).

| Elemento | Representación Simbólica | Función |
| :--- | :---: | :--- |
| **Variables** | $p, q, r, ...$ | Representar hechos o afirmaciones simples. |
| **Operadores** | $\neg, \land, \lor, \rightarrow$ | Establecer relaciones lógicas entre variables. |
| **Signos de Agrupación** | $( ), [ ]$ | Determinar la jerarquía y el orden de evaluación. |

---

## Sistematización de Operadores Lógicos

Los conectores lógicos son las herramientas fundamentales que nos permiten construir proposiciones complejas a partir de proposiciones simples.

| Operador | Nombre Técnico | Notación | Expresión Natural |
| :--- | :--- | :---: | :--- |
| **Negación** | Negación | $\neg p$ | "No p", "Es falso que p" |
| **Conjunción** | Conjunción | $p \land q$ | "p y q" |
| **Disyunción** | Disyunción Inclusiva | $p \lor q$ | "p o q" |
| **Disyunción Exc.**| Disyunción Exclusiva | $p \oplus q$ | "o p o q" (pero no ambas) |
| **Condicional** | Implicación | $p \rightarrow q$ | "Si p, entonces q" |
| **Bicondicional**| Equivalencia | $p \leftrightarrow q$ | "p si y solo si q" |

---

## Axiomas de Verdad

Para operar lógicamente, debemos conocer cómo se comporta cada operador frente a los valores de verdad: Verdadero ($V$) y Falso ($F$).

### La Conjunción ($p \land q$)

Es un operador restrictivo. La proposición compuesta solo es verdadera cuando **ambas componentes son verdaderas**.

$$V \land V = V$$

*En cualquier otro caso (si hay al menos una falsedad), el resultado es $F$.*

### La Disyunción ($p \lor q$)

Es un operador inclusivo. La proposición es verdadera si **al menos una** de las componentes es verdadera.

$$F \lor F = F$$

*Solo es falsa cuando ambas proposiciones son falsas.*

### El Condicional ($p \rightarrow q$)

Es fundamental comprender la relación de **Antecedente $\to$ Consecuente**.

> **Regla de Oro:** Una implicación solo es FALSA cuando se parte de una verdad y se llega a una falsedad.

$$V \rightarrow F = F$$

*En todos los demás casos ($V \to V$, $F \to V$, $F \to F$), la implicación es Verdadera.*

**Lecturas equivalentes:**

* "$p$ implica $q$"
* "$p$ es suficiente para $q$"
* "$q$ es necesario para $p$"

### El Bicondicional ($p \leftrightarrow q$)

Representa una equivalencia de valores. Es verdadera cuando ambas proposiciones comparten el mismo valor de verdad.

$$V \leftrightarrow V = V$$
$$F \leftrightarrow F = V$$

### Ejemplos de repaso

Teniendo en cuenta la teoria anterior, resuelva los siguientes ejemplos:

1. Exprese el siguiente enunciado en lenguaje natural a expresiones lógicas: "La Chimoltrufia es mayor que el Chompiras"

   **Solución**:

   * **Proposiciones Simples**:
     * $p$: "La Chimoltrufia es mayor que el Chompiras"

   * **Expresión Lógica**:

     $$
     p
     $$
2. Obtenga la negación de la proposición anterior y exprese en lenguaje natural.

   **Solución**:

   * **Proposiciones Simples**:
     * $p$: "La Chimoltrufia es mayor que el Chompiras"

   * **Expresión Lógica**:

     $$
     \neg p
     $$

   * **Expresión en lenguaje natural**:
     "La Chimoltrufia ***no*** es mayor que el Chompiras"

3. Dado el enunciado: "Me gusta el cafe y la torta", obtenga las proposiciones simples y exprese la proposición compuesta en lenguaje formal

   **Solución**:

   * **Proposiciones Simples**:
     * $p$: "Me gusta el cafe"
     * $q$: "Me gusta la torta"

   * **Expresión Lógica**:

     $$
     p \land q
     $$

4. Proceda de manera similar al ejercicio anterior para el enunciado: "Me gustan los perros o me gustan los gatos".

   **Solución**:

   * **Proposiciones Simples**:
     * $p$: "Me gusta el cafe"
     * $q$: "Me gusta la torta"

   * **Expresión Lógica**:

     $${
     p \land q
     }$$

5. Dado el enunciado: "Me gustan los perros o me gustan los gatos, pero no ambos", obtenga las proposiciones simples y exprese la proposición compuesta en lenguaje formal.

   **Solución**:

   * **Proposiciones Simples**:
     * $p$: "Me gustan los perros"
     * $q$: "Me gustan los gatos"

   * **Expresión Lógica**:

     $$
     p \oplus q
     $$

6. Dado el enunciado: "Si le regalo una rosa, entonces ella irá al baile conmigo", obtenga las proposiciones simples y exprese la proposición compuesta en lenguaje formal.

   **Solución**:

   * **Proposiciones Simples**:
     * $p$: "Le regalo una rosa"
     * $q$: "Ella irá al baile conmigo"

   * **Expresión Lógica**:

     $${
     p \rightarrow q
     }$$

7. Proceda igual para el enunciado: "Puedes tomar el vuelo si y solo si compras el tiquete".

   **Solución**:

   * **Proposiciones Simples**:
     * $p$: "Puedes tomar el vuelo"
     * $q$: "Compras el tiquete"

   * **Expresión Lógica**:

     $$
     p \leftrightarrow q
     $$

---

## Jerarquía de Operadores

Cuando nos enfrentamos a una expresión compleja sin signos de agrupación suficientes, debemos respetar el siguiente orden de precedencia para evitar ambigüedades:

1. **Signos de agrupación:** $( ), [ ], \{ \}$
2. **Negación:** $\neg$
3. **Conjunción y Disyunción:** $\land, \lor$
4. **Condicional:** $\rightarrow$
5. **Bicondicional:** $\leftrightarrow$

---

## Construcción de Tablas de Verdad

Una tabla de verdad es una herramienta gráfica que se utiliza para analizar todos los posibles valores de verdad de los enunciados lógicos que la componen, a fin de determinar la validez de un enunciado o argumento junto con todos sus posibles resultados.

### Tabla de verdad para los operadores lógicos fundamentales

A continuación, se presenta la tabla de verdad unificada para dos proposiciones cualesquiera $p$ y $q$, mostrando el comportamiento de todos los operadores lógicos fundamentales vistos en esta sesión:

| $p$ | $q$ | **Negación**<br>$\neg p$ | **Conjunción**<br>$p \land q$ | **Disyunción**<br>$p \lor q$ | **O Exclusivo**<br>$p \oplus q$ | **Condicional**<br>$p \rightarrow q$ | **Bicondicional**<br>$p \leftrightarrow q$ |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **V** | **V** | F | **V** | V | F | V | V |
| **V** | **F** | F | F | V | **V** | **F** | F |
| **F** | **V** | V | F | V | **V** | V | F |
| **F** | **F** | V | F | **F** | F | V | V |

### Metodología: Construcción de Tablas de Verdad

Para construir una tabla de verdad de manera sistemática y minimizar errores, se recomienda seguir estrictamente este algoritmo de 6 pasos:

1. **Identificar las variables proposicionales**
    Determinar cuántas letras distintas ($n$) componen la expresión (ej. $p, q, r$).

2. **Determinar el número de filas necesarias**
    Se utiliza la fórmula exponencial base 2:
    $$N_{filas} = 2^n$$

3. **Construir las columnas de las variables**
    Se asignan los valores de verdad iniciales distribuyéndolos sistemáticamente (mitad y mitad, luego de dos en dos, etc.).
    * **Notación:** Se puede utilizar $V/F$ o notación binaria para ingeniería ($1/0$).
        * Verdadero = $1$
        * Falso = $0$

4. **Agregar columnas auxiliares**
    Desglosa la fórmula compleja en operaciones más pequeñas. No intentes resolver todo en una sola columna mentalmente.

    > **Tip de Legibilidad:**
    > Cuando la expresión es muy extensa o tiene muchos anidamientos, es útil sustituir una sub-expresión (letras minúsculas) por una **Variable Mayúscula ($A, B...$)**.
    >
    > *Ejemplo:* En lugar de operar $(p \land q) \to (r \lor s)$, puedes hacer $A \to B$, donde $A = (p \land q)$ y $B = (r \lor s)$.
    {: .note }

5. **Evaluar la expresión lógica paso a paso**
    Llena las columnas auxiliares de izquierda a derecha, respetando la [jerarquía de operadores](#4-jerarquía-de-operadores).

6. **Revisar y validar la tabla**
    Verifica que no existan inconsistencias y clasifica el resultado final (Tautología, Contradicción o Contingencia).

El número de filas ($N$) de la tabla depende del número de variables proposicionales distintas ($n$) según la fórmula:

$$N = 2^n$$

### Ejemplo resuelto

Construya una tabla de verdad para analizar todos los resultados posibles para la  proposición para la expresión:

$$
\neg (p \land q) \lor \neg r
$$

**Análisis:**

* **Variables**: $p, q, r$ ($n=3$).
* **Filas**: $2^3 = 8$ filas.

**Tabla de Verdad Paso a Paso**

| Fila | $p$ | $q$ | $r$ | $(p \land q)$ | $\neg(p \land q)$ | $\neg r$ | **Resultado Final** <br> $\neg(p \land q) \lor \neg r$ |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 1 | F | F | F | F | V | V | **V** |
| 2 | F | F | V | F | V | F | **V** |
| 3 | F | V | F | F | V | V | **V** |
| 4 | F | V | V | F | V | F | **V** |
| 5 | V | F | F | F | V | V | **V** |
| 6 | V | F | V | F | V | F | **V** |
| 7 | V | V | F | V | F | V | **V** |
| 8 | V | V | V | V | F | F | **F** |

---

## Clasificación de las proposiciones

Las proposiciones pueden clasificarse en tres tipos:

1. **Tautología**: Es una proposición que es verdadera en todos los casos posibles.
2. **Contradicción**: Es una proposición que es falsa en todos los casos posibles.
3. **Contingencia**: Es una proposición que puede ser verdadera o falsa dependiendo de los valores de verdad de las proposiciones simples que la componen.

**Ejemplo**: Para el ejemplo anterior, la proposición $\neg (p \land q) \lor \neg r$ es una contigencia, ya que es verdadera en ciertos casos y falsa en otros.
