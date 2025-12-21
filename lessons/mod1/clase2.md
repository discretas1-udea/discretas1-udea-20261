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

> **Conexión con programación**: en lógica proposicional trabajamos con valores $V/F$, que en programación suelen representarse como booleanos `true/false` (o incluso `1/0`).
{: .important }

### Elementos de la Formalización

La lógica proposicional opera mediante la **formalización**, un proceso que traduce el lenguaje natural (intrínsecamente ambiguo y semántico) a un lenguaje simbólico (exacto y sintáctico).

<div style="text-align: center;" markdown="1">
| Elemento | Representación Simbólica | Función |
| :--- | :---: | :--- |
| **Variables** | $p, q, r, ...$ | Representar hechos o afirmaciones simples. |
| **Operadores** | $\neg, \land, \lor, \oplus, \rightarrow, \leftrightarrow$ | Establecer relaciones lógicas entre variables. |
| **Signos de Agrupación** | $( ), [ ]$ | Determinar la jerarquía y el orden de evaluación. |

**Tabla 1**. Elementos para formalizar enunciados.
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>

---

## Sistematización de Operadores Lógicos

Los conectores lógicos son las herramientas fundamentales que nos permiten construir proposiciones complejas a partir de proposiciones simples.

<div style="text-align: center;" markdown="1">
| Operador | Nombre Técnico | Notación | Expresión Natural |
| :--- | :--- | :---: | :--- |
| **Negación** | Negación | $\neg p$ | "No p", "Es falso que p" |
| **Conjunción** | Conjunción | $p \land q$ | "p y q" |
| **Disyunción** | Disyunción Inclusiva | $p \lor q$ | "p o q" |
| **Disyunción Exc.**| Disyunción Exclusiva | $p \oplus q$ | "o p o q" (pero no ambas) |
| **Condicional** | Implicación | $p \rightarrow q$ | "Si p, entonces q" |
| **Bicondicional**| Equivalencia | $p \leftrightarrow q$ | "p si y solo si q" |

**Tabla 2**. Operadores lógicos.
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>

---

## Axiomas de Verdad

Para operar lógicamente, debemos conocer cómo se comporta cada operador frente a los valores de verdad: Verdadero ($V$) y Falso ($F$). Estas reglas se especifican mediante **tablas de verdad**, que constituyen la base semántica de la lógica proposicional.

> **Nota**: En ingeniería también es común $1/0$ (Verdadero = $1$, Falso = $0$).
{: .note }

### Negación ($\neg p$)

Invierte el valor de verdad de una proposición.

<div style="text-align: center;" markdown="1">
| $p$ | $\neg p$ |
| :---: | :---: |
| V | **F** |
| F | **V** |

**Tabla 3**. Negación.
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>

### Conjunción ($p \land q$)

Es un operador restrictivo. La proposición compuesta solo es verdadera cuando **ambas componentes son verdaderas**.

<div style="text-align: center;" markdown="1">
| $p$ | $q$ | $p \land q$ |
| :---: | :---: | :---: |
| V | V | **V** |
| V | F | **F** |
| F | V | **F** |
| F | F | **F** |

**Tabla 4**. Conjunción.
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>

> **Regla corta**: basta una falsedad para que toda la conjunción sea $F$.
{: .important }

### Disyunción ($p \lor q$)

Es un operador inclusivo. La proposición es verdadera si **al menos una** de las componentes es verdadera.

<div style="text-align: center;" markdown="1">
| $p$ | $q$ | $p \lor q$ |
| :---: | :---: | :---: |
| V | V | **V** |
| V | F | **V** |
| F | V | **V** |
| F | F | **F** |

**Tabla 5**. Disyunción
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>

> **Regla corta**: basta una verdad para que toda la disyunción sea $V$.
{: .important }

### Disyunción Exclusiva ($p \oplus q$)

Es verdadera cuando exactamente una de las proposiciones es verdadera (no ambas).

<div style="text-align: center;" markdown="1">
| $p$ | $q$ | $p \oplus q$ |
| :---: | :---: | :---: |
| V | V | **F** |
| V | F | **V** |
| F | V | **V** |
| F | F | **F** |

**Tabla 6**. Disyunción Exclusiva
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>

> **Regla de oro**: Valores **diferentes** dan verdadero $V$.
{: .important }

### Condicional ($p \rightarrow q$)

Se interpreta como **Antecedente $\rightarrow$ Consecuente**. Define una relación de compromiso o contrato. La única forma de romper el contrato es que el antecedente se cumpla ($V$) y el consecuente no ($F$).

<div style="text-align: center;" markdown="1">
| $p$ | $q$ | $p \rightarrow q$ |
| :---: | :---: | :---: |
| V | V | **V** |
| V | F | **F** |
| F | V | **V** |
| F | F | **V** |

**Tabla 7**. Condicional
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>    

> **Regla de Oro:** Una implicación solo es FALSA cuando se parte de una verdad y se llega a una falsedad.
> $$V \rightarrow F = F$$
{: .important }

*En todos los demás casos ($V \to V$, $F \to V$, $F \to F$), la implicación es Verdadera.*

Hay varias formas para hacer referencia a una relación condicional, a continuación se muestran algunas:
* "$p$ implica $q$"
* "$p$ es suficiente para $q$"
* "$q$ es necesario para $p$"

### El Bicondicional ($p \leftrightarrow q$)

Representa una equivalencia de valores. Es verdadera cuando ambas proposiciones comparten el mismo valor de verdad.

<div style="text-align: center;" markdown="1">
| $p$ | $q$ | $p \leftrightarrow q$ |
| :---: | :---: | :---: |
| V | V | **V** |
| V | F | **F** |
| F | V | **F** |
| F | F | **V** |

**Tabla 8**. Bicondicional
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>

---

## Jerarquía de Operadores

Cuando nos enfrentamos a una expresión compuesta sin suficientes signos de agrupación, debemos respetar un **orden de precedencia** para evitar ambigüedades. Para ello usamos la tabla de **Jerarquía de operadores**, que establece el orden en que se aplican los conectivos lógicos al interpretar o evaluar expresiones **sin paréntesis**. Esta convención es esencial para asignar una lectura única a la expresión.

<div style="text-align: center;" markdown="1">
| Prioridad        | Símbolo | Asociatividad            | Ejemplo con paréntesis |
|------------------|---------|--------------------------|------------------------|
| 1 (más alta)     | $¬$     | No aplica (unitario)     | $¬p \land q \;\mapsto\; ((¬p) \land q)$ |
| 2                | $\land$ | Izquierda (I → D)        | $p \land q \land r \;\mapsto\; ((p \land q) \land r)$ |
| 3                | $\lor$  | Izquierda (I → D)        | $p \lor q \lor r \;\mapsto\; ((p \lor q) \lor r)$ |
| 4                | $\oplus$| Izquierda (I → D)        | $p \oplus q \oplus r \;\mapsto\; ((p \oplus q) \oplus r)$ |
| 5                | $\to$   | Derecha (I ← D)          | $p \to q \to r \;\mapsto\; (p \to (q \to r))$ |
| 6 (más baja)     | $\leftrightarrow$ | Derecha (I ← D) | $p \leftrightarrow q \leftrightarrow r \;\mapsto\; (p \leftrightarrow (q \leftrightarrow r))$ |

**Tabla 9**. Jerarquía de Operadores.
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>

> **Notas clave**:
> * La **negación** ($¬$) siempre aplica a **una proposición o a una expresión completa**.
> * Los operadores con **igual precedencia** se agrupan según su **asociatividad** (izquierda o derecha).
> * El uso de **paréntesis** permite evitar la ambigüedad en expresiones que usan varios operadores.
> * Cuando una expresión tiene **paréntesis anidados**, la evaluación se realiza **de adentro hacia afuera**.
> * si aparecen operadores con la **misma precedencia**, la expresión se agrupa según su **asociatividad** (por ejemplo, $\land$, $\lor$ y $\oplus$ se asocian a la izquierda; $\to$ y $\leftrightarrow$ a la derecha), salvo que los paréntesis indiquen lo contrario.
{: .note }

### Ejemplos resueltos

1. Sean las proposiciones $P=V$, $Q=F$ y $R=F$. Determine el valor de la verdad de cada una de las siguientes expresiones:
   * $P \rightarrow (Q \lor R)$
   * $Q \rightarrow [P \rightarrow (R \land Q)]$
   * $\neg(\neg P \rightarrow Q) \lor \neg R$

   **Solución**:

   * $P\rightarrow(Q \lor R)$
     
     Se reemplazan los valores de verdad de cada proposición en la expresión original y se procede a realizar la evaluación empleando la jerarquía de operadores:

     $$
     \begin{aligned}
     P \rightarrow (Q \lor R) &\equiv V \rightarrow (F \lor F)\\
                              &\equiv V \rightarrow F\\
                              &\equiv F
     \end{aligned}
     $$

   * $Q \rightarrow [P \rightarrow (R \land Q)]$
    
     Procediendo de manera similar, al reemplazar $P=V$, $Q=F$ y $R=F$ tenemos:

     $$
     \begin{aligned}
     Q \rightarrow [P \rightarrow (R \land Q)] &\equiv F \rightarrow [V \rightarrow (F \land F)]\\
                                               &\equiv F \rightarrow [V \rightarrow F]\\
                                               &\equiv F \rightarrow F \\
                                               &\equiv V 
     \end{aligned}
     $$
   
   * $\neg(\neg P \rightarrow Q) \lor \neg R$
     
     Al reemplazar $P=V$, $Q=F$ y $R=F$ tenemos la siguiente solución paso a paso siguiendo la jerarquía de operadores:

     $$
     \begin{aligned}
     \neg(\neg P \rightarrow Q) \lor \neg R &\equiv \neg(\neg V \rightarrow F) \lor \neg F \\
                                            &\equiv \neg(F \rightarrow F) \lor \neg F \\
                                            &\equiv \neg V \lor \neg F \\
                                            &\equiv F \lor \neg F \\
                                            &\equiv F \lor V \\
                                            &\equiv V
     \end{aligned}
     $$

     Si se procede a evaluar con cualquier otra combinación el resultado será falso, sin embargo, al ser el procedimiento similar, este se omite.

2. Encuentre una proposición compuesta que involucre las variables proposicionales $P$, $Q$ y $R$, que sea verdadera cuando $P$ y $Q$ son verdaderas y $R$ es falsa, pero falsa en caso contrario. 
   
   (**Pista**: Use una conjunción de cada variable proposicional o su negación).

   **Solución**: Para el caso tenemos que hayar una expresión compuesta $f(P,Q,R)$ la cual se caracteriza por ser $f=V$ si $P=V$ y $Q=V$ y $R=F$ y $f=F$ en caso contrario. Si empleamos una conjunción entre las variables tenemos que la unica forma de lograr esto es que $f = P\land Q\land \neg R$. Para comprobar, procedemos a evaluar, paso a paso, la expresión para $f$ para los valores que la hacen verdadera:

   $$
   \begin{aligned}
   P\land Q\land \neg R &\equiv V\land V\land \neg F \\
                        &\equiv V\land V\land V \\
                        &\equiv V\land V \\
                        &\equiv V
   \end{aligned}
   $$

---

## Construcción de Tablas de Verdad

Una tabla de verdad es una herramienta gráfica que se utiliza para analizar todos los posibles valores de verdad de los enunciados lógicos que la componen, a fin de determinar el valor de verdad final de una expresión.

### Tabla de verdad para los operadores lógicos fundamentales

A continuación, se presenta la tabla de verdad unificada para dos proposiciones cualesquiera $p$ y $q$, mostrando el comportamiento de todos los operadores lógicos fundamentales vistos en esta sesión:

<div style="text-align: center;" markdown="1">
| $p$ | $q$ | **Negación**<br>$\neg p$ | **Conjunción**<br>$p \land q$ | **Disyunción**<br>$p \lor q$ | **O Exclusivo**<br>$p \oplus q$ | **Condicional**<br>$p \rightarrow q$ | **Bicondicional**<br>$p \leftrightarrow q$ |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **V** | **V** | F | **V** | V | F | V | V |
| **V** | **F** | F | F | V | **V** | **F** | F |
| **F** | **V** | V | F | V | **V** | V | F |
| **F** | **F** | V | F | **F** | F | V | V |

**Tabla 10**. Tabla de verdad para los operadores lógicos fundamentales.
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>

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
    
    > **Nota**: Para trabajar las tablas de verdad usaremos la notación binaria empleada ingeniería.
    {: .note }

4. **Agregar columnas auxiliares**
    Desglosa la fórmula compleja en operaciones más pequeñas. No intentes resolver todo en una sola columna mentalmente.

    > **Tip de Legibilidad:**
    > Cuando la expresión es muy extensa o tiene muchos anidamientos, es útil sustituir una sub-expresión (letras minúsculas) por una **Variable Mayúscula ($A, B...$)**.
    >
    > *Ejemplo:* En lugar de operar $(p \land q) \to (r \lor s)$, puedes hacer $A \to B$, donde $A = (p \land q)$ y $B = (r \lor s)$.
    {: .note }

5. **Evaluar la expresión lógica paso a paso**
    Llena las columnas auxiliares de izquierda a derecha, respetando la [jerarquía de operadores](#jerarquía-de-operadores).

6. **Revisar y validar la tabla**
    Verifica que no existan inconsistencias y clasifica el resultado final (Tautología, Contradicción o Contingencia).

El número de filas ($N$) de la tabla depende del número de variables proposicionales distintas ($n$) según la fórmula:

$$
N = 2^n
$$

### Errores típicos al construir tablas de verdad (y cómo evitarlos)

1. **Número de filas incorrecto**: si hay $n$ variables, deben ser exactamente $2^n$ filas.  
2. **Patrón $V/F$ mal distribuido**: la primera variable alterna cada $2^{n-1}$ filas, la segunda cada $2^{n-2}$, etc.  
3. **No crear columnas auxiliares**: intentar resolver todo "de cabeza" aumenta errores; descomponga la expresión en subexpresiones.  
4. **Alcance incorrecto de la negación**: $\neg(p \land q) \neq (\neg p \land q)$. Use paréntesis para evitar confusión.  
5. **Confundir $\lor$ con $\oplus$**: $\lor$ permite "ambas", $\oplus$ no.  
6. **Malinterpretar el condicional**: $p \rightarrow q$ solo es falsa cuando $p=V$ y $q=F$.  
7. **Ignorar jerarquía**: si no hay paréntesis, se debe aplicar precedencia y asociatividad (ver Tabla 9).  
8. **Errores de copia en la última columna**: si una columna auxiliar está mal, el resultado final también. Revise hacia atrás.  

> **Recomendación práctica**: si al final el resultado es "raro", revise primero la columna del conector principal y luego las subexpresiones.
{: .note }

### Ejemplos resueltos

1. Construya una tabla de verdad para analizar todos los resultados posibles para la  proposición para la expresión:

    $$
    \neg (p \land q) \lor \neg r
    $$
    
    **Análisis:**
    
    * **Variables**: $p, q, r$ ($n=3$).
    * **Filas**: $2^3 = 8$ filas.
    
    **Tabla de Verdad Paso a Paso**
    
    <div style="text-align: center;" markdown="1">
    | Fila | $p$ | $q$ | $r$ | $(p \land q)$ | $\neg(p \land q)$ | $\neg r$ | **Resultado Final** <br> $\neg(p \land q) \lor \neg r$ |
    | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
    | 1 | 0 | 0 | 0 | 0 | 1 | 1 | **1** |
    | 2 | 0 | 0 | 1 | 0 | 1 | 0 | **1** |
    | 3 | 0 | 1 | 0 | 0 | 1 | 1 | **1** |
    | 4 | 0 | 1 | 1 | 0 | 1 | 0 | **1** |
    | 5 | 1 | 0 | 0 | 0 | 1 | 1 | **1** |
    | 6 | 1 | 0 | 1 | 0 | 1 | 0 | **1** |
    | 7 | 1 | 1 | 0 | 1 | 0 | 1 | **1** |
    | 8 | 1 | 1 | 1 | 1 | 0 | 0 | **0** |
    
    **Tabla 11**. Tabla de verdad de $\neg (p \land q) \lor \neg r$.
    {: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
    </div>
    
2. Construya la tabla de verdad la siguiente expresión:

    $$
    (P \leftrightarrow Q) \oplus (P \leftrightarrow \neg Q)
    $$
    
    **Análisis:**
    
    * **Variables**: $P, Q$ ($n=2$).
    * **Filas**: $2^2 = 4$ filas.
    
    **Tabla de Verdad Paso a Paso**
    
    <div style="text-align: center;" markdown="1">
    | Fila | $P$ | $Q$ | $\neg Q$ | $(P \leftrightarrow Q)$ | $(P \leftrightarrow \neg Q)$ |**Resultado Final** <br> $(P \leftrightarrow Q) \oplus (P \leftrightarrow \neg Q)$ |
    | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
    | 1 | 0 | 0 | 1 | 1 | 0 | **1** |
    | 2 | 0 | 1 | 0 | 0 | 1 | **1** |
    | 3 | 1 | 0 | 1 | 0 | 1 | **1** |
    | 4 | 1 | 1 | 0 | 1 | 0 | **1** |
    
    **Tabla 12**. Tabla de verdad de $(P \leftrightarrow Q) \oplus (P \leftrightarrow \neg Q)$.
    {: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
    </div>

---

## Clasificación de las proposiciones

Las proposiciones pueden clasificarse en tres tipos:

1. **Tautología**: Es una proposición que es verdadera en todos los casos posibles.
   
   Por ejemplo la proposición $p \lor \neg p$ es una tautología.

   <div style="text-align: center;" markdown="1">
    | Fila | $p$ | $\neg p$ | $(p \lor \neg p)$ |
    | :---: | :---: | :---: | :---: |
    | 1 | 0 | 1 | **1** |
    | 2 | 1 | 0 | **1** |   
        
    **Tabla 13**. Tabla de verdad para una tautología.
    {: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
    </div>

2. **Contradicción**: Es una proposición que es falsa en todos los casos posibles.
   
   Por ejemplo la proposición $p \land \neg p$ es una contradicción.

   <div style="text-align: center;" markdown="1">
    | Fila | $p$ | $\neg p$ | $(p \land \neg p)$ |
    | :---: | :---: | :---: | :---: |
    | 1 | 0 | 1 | **0** |
    | 2 | 1 | 0 | **0** |

    **Tabla 14**. Tabla de verdad para una contradicción.
    {: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
    </div>

3. **Contingencia**: Es una proposición que puede ser verdadera o falsa dependiendo de los valores de verdad de las proposiciones simples que la componen.

   Por ejemplo, la proposición $\neg (p \land q) \lor \neg r$ (previamente analizada) es una contingencia. Note que la proposición tiene valores falsos y verdaderos para diferentes entradas.

   <div style="text-align: center;" markdown="1">
    | Fila | $p$ | $q$ | $r$ | $\neg(p \land q) \lor \neg r$ |
    | :---: | :---: | :---: | :---: | :---: |
    | 1 | 0 | 0 | 0 | **1** |
    | 2 | 0 | 0 | 1 | **1** |
    | 3 | 0 | 1 | 0 | **1** |
    | 4 | 0 | 1 | 1 | **1** |
    | 5 | 1 | 0 | 0 | **1** |
    | 6 | 1 | 0 | 1 | **1** |
    | 7 | 1 | 1 | 0 | **1** |
    | 8 | 1 | 1 | 1 | **0** |
    
    **Tabla 15**. Tabla de verdad para una contingencia.
    {: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
    </div>

## Actividad

### Identificación de proposiciones

Identifique cuáles de los siguientes enunciados son proposiciones. Justifica tu respuesta basándote en el **Principio de Bivalencia**.
1.  $x + 5 = 10$
2.  "La suma de los ángulos internos de un triángulo plano es 180°."
3.  "Por favor, compila el código antes de enviarlo a producción."
4.  "Esta frase es falsa."

### Evaluación Directa (Sustitución)

Determine el valor de verdad final realizando la sustitución paso a paso. **Valores**: $A = 1$ (V), $B = 0$ (F), $C = 0$ (F).
1.  $(A \lor B) \to C$
2.  $\neg B \leftrightarrow (A \land \neg C)$
3.  $B \to (C \to A)$


### Tablas de verdad

Construya la tabla de verdad y clasifique el resultado como **Tautología, Contradicción o Contingencia**.

$$\neg [(p \lor q) \to (p \land q)]$$

### Desafío de Ingeniería (Equivalencia XOR)

Demuestre mediante tablas de verdad si la siguiente estructura lógica es una equivalencia válida (si ambas columnas finales son idénticas):

$$(p \oplus q) \equiv (p \lor q) \land \neg (p \land q)$$


### Modelado de Sistemas

Traduzca y evalúe la siguiente expresión:
  
**Requerimiento:** *"Si el usuario tiene privilegios de administrador o el archivo no está bloqueado por el sistema, entonces el acceso es permitido ($r$)."*

1.  **Formulación:** Determine la expresión lógica resultante.
2.  **Caso de prueba:** Si un usuario **no** es administrador, el archivo **está** bloqueado, pero el sistema otorga acceso, ¿es la afirmación del requerimiento verdadera o falsa? Justifique usando la tabla del condicional.

> **Nota importante:** En lógica, la precisión es binaria. Un solo error en un bit de la tabla de verdad invalida todo el sistema. ¡Revisa tus resultados!
{: .note } 

---

## Resultados de aprendizaje

Al finalizar esta clase se espera que el estudiante sea capaz de:
* Traducir enunciados de lenguaje natural a lenguaje lógico.
* Evaluar expresiones logicas compuestas empleando los axiomas de verdad, los operadores logicos y las reglas de jerarquia.
* Construir tablas de verdad para la evalución de proposiciones.
* Clasificar los diferentes tipos de proposiciones.

---

## Solucionario de Autoevaluación

Utilice esta sección para validar sus resultados después de completar la actividad.

<details>
<summary><b>Presione aquí para ver las respuestas</b></summary>
<br>

### Diagnóstico de Bivalencia

1. **No** (Enunciado abierto / Variable $x$ no definida).
2. **Sí** (Proposición atómica / Hecho matemático).
3. **No** (Enunciado imperativo / Orden).
4. **No** (Paradoja / Autoreferencia).

### Evaluación Directa

1. **F** (0)
2. **V** (1)
3. **V** (1)

### Tablas de verdad

* **Columna de salida:** 0, 1, 1, 0
* **Clasificación:** **Contingencia**

### Desafío XOR

* **Resultado:** **Equivalencia Válida**. La tabla resultante para $(p \lor q) \land \neg (p \land q)$ coincide con la definición del XOR ($0, 1, 1, 0$).

### Modelado de Sistemas

1. **Fórmula:** $(p \lor \neg q) \to r$
2. **Evaluación:** **Verdadero (V)**. (Explicación: El antecedente resulta falso $0 \to 1$, lo cual es verdadero por definición del condicional).

</details>

