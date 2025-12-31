---
layout: default
title: Clase 03 - Equivalencias y Álgebra de Proposiciones
parent: Lógica Proposicional
nav_order: 3
math: mathjax
---

![Built with AI](https://img.shields.io/badge/Built%20with-AI-blue.svg)

# Clase 03 - Equivalencias Lógicas y Álgebra de Proposiciones
{: .no_toc }

Teniendo en cuenta los conceptos iniciales vistos en las secciones anteriores, ya estamos listos para abordar con un poco mas de profundidad algunos aspectos relacionados con la traducción de lenguaje natural a expresiones logica proposicional. Una vez visto esto, vamos a tratar con un poco mas de profundidad aspectos relacionados con los conectores de implicación y equivalencia cuya comprensión es util para analizar relaciones de dependencia y equivalencia dentro de la logica formal.

## Tabla de Contenidos
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Repaso: El Kit del Traductor Lógico

Para lograr traducir correctamente del español (ambiguo) al lenguaje matemático (preciso), necesitamos tener a mano las herramientas que definimos en las clases 1 y 2.

Antes de comenzar, verifique que tiene claros estos tres componentes:

### 1. La Materia Prima: Proposiciones Atómicas

Recuerde el **Axioma de Bivalencia**: Solo nos interesan oraciones que puedan ser **Verdaderas (1)** o **Falsas (0)**.
* *En el código:* Estas serán nuestras variables booleanas (`p`, `q`, `r`, `isUserLoggedIn`).

### 2. El Pegamento: Operadores Lógicos

Estos símbolos son la estructura sintáctica que une las ideas.

<div style="text-align: center;" markdown="1">
| Nombre | Símbolo | Rol Gramatical (Aprox.) |
| :--- | :---: | :--- |
| Negación | $\neg$ | Modificador del verbo ("No") |
| Conjunción | $\land$ | Unión ("Y", "Pero") |
| Disyunción | $\lor$ | Alternativa ("O") |
| Condicional | $\to$ | Relación Causa-Efecto ("Si... entonces") |
| Bicondicional| $\leftrightarrow$ | Equivalencia ("Si y solo si") |

**Tabla 1**. Operadores lógicos fundamentales.
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>

### 3. Las Reglas de Puntuación: Jerarquía
Al igual que en la aritmética ($\times$ antes que $+$), en lógica el orden importa para evitar ambigüedades.
1.  **Paréntesis** `()` (Máxima prioridad)
2.  **Negación** $\neg$
3.  **Conjunción** $\land$ y **Disyunción** $\lor$
4.  **Condicional** $\to$ y **Bicondicional** $\leftrightarrow$ (Menor prioridad)

---

## Traducción: De Palabras a Fórmulas (y Viceversa)

Traducir de lenguaje natural a lógico es similar a "compilar" código: buscamos eliminar la ambigüedad humana para dejar instrucciones precisas. Para realizar esto con éxito, seguiremos un proceso estructurado.

### Dirección 1: Lenguaje Natural $\to$ Lógica Formal

Para evitar errores comunes, recomendamos seguir un algoritmo de 3 pasos:

1.  **Atomización:** Identifique las oraciones simples y asígneles una variable ($P, Q, R...$).
2.  **Identificación de Conectores:** Busque las "palabras clave" y elija el símbolo correspondiente apoyándose en las siguientes tablas de referencia:
    
    <div markdown="1">
    | Tipo | Conector lógico | Forma simbólica | Enunciados en lenguaje natural |
    |---|---|---|---|
    | Conjuntivo | Conjunción | $P \land Q$ | • P y Q<br>• P, pero Q<br>• P aun Q<br>• P también Q<br>• P todavía Q<br>• P, aunque Q<br>• P sin embargo Q<br>• P además Q<br>• P no obstante Q |
    | Disyuntivo (inclusivo) | Disyunción | $P \lor Q$ | • P o Q<br>• P, a menos que Q<br>• Al menos una entre P y Q |
    | Disyuntivo exclusivo | Disyunción exclusiva | $P \oplus Q$ | • P o Q, pero no ambos<br>• O P o Q exclusivamente<br>• Exactamente uno de P y Q |
    
    **Tabla 2**. Operadores $\land$, $\lor$ y $\oplus$ y palabras claves relacionadas.
    {: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
    </div>

    > **Notas clave**
    >
    >* El **"o"** en lenguaje natural se interpreta por defecto como **disyunción inclusiva**.
    >* El **"o exclusivo"** indica que **solo una** proposición es verdadera.
    >* Expresiones como *pero*, *sin embargo* o *no obstante* no alteran la estructura lógica (son conjunciones).
    >* La expresión *“a menos que”* se modela usualmente como una disyunción inclusiva ($P \lor Q$) o una implicación ($\neg Q \to P$).
    {: .note }

    El caso del condicional requiere especial atención. En la siguiente tabla, asuma que $P$ representa el **antecedente** y $Q$ el **consecuente**.
    
    <div markdown="1">
    | Tipo | Conector lógico | Forma simbólica | Enunciados en lenguaje natural |
    |---|---|---|---|
    | Condicional (Hipotético) | Implicación | $P \to Q$ | • Si $P$, entonces $Q$<br>• Si $P$, $Q$<br>• $Q$ si $P$<br>• $P$ solo si $Q$<br>• Para $P$, es necesario $Q$<br>• Es suficiente $P$ para $Q$<br>• $Q$ en caso de que $P$<br>• $Q$ siempre que $P$<br>• Como $P$, $Q$<br>• $Q$ cuando $P$<br>• $P$ implica que $Q$<br>• Cuando $P$, $Q$ |
    | Bicondicional | Bicondicional | $P \leftrightarrow Q$ | • $P$ si, y solo si, $Q$<br>• $P$ es suficiente y necesario para $Q$<br>• $P$ es equivalente a $Q$<br>• $P$ y $Q$ son equivalentes |
    
    **Tabla 3**. Operadores $\leftarrow$ y $\leftrightarrow$ y palabras claves relacionadas.
    {: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
    </div>
    
    > **Notas clave sobre la Implicación**
    >
    > * La expresión **“$P$ solo si $Q$”** se formaliza como $P \to Q$. (El "solo si" introduce la condición necesaria/consecuente).
    > * La expresión **“$Q$ si $P$”** también corresponde a $P \to Q$. (El "si" introduce la condición suficiente/antecedente).
    > * En el **bicondicional**, ambas proposiciones tienen el mismo valor de verdad.
    {: .note }
    
3.  **Estructuración:** Use paréntesis para agrupar las ideas y definir la jerarquía.

#### Ejemplo Guiado: Reglas de Red

Analicemos el siguiente enunciado de política de seguridad para aplicar el algoritmo:

> "Puedes acceder a internet desde el campus **solo si** estudias ciencias de la computación **o** **no** eres estudiante de primer año."

* **Paso 1: Definir Átomos (Variables)**
  * $P$: Puedes acceder a internet desde el campus.
  * $Q$: Estudias ciencias de la computación.
  * $R$: Eres estudiante de primer año.

* **Paso 2: Traducir Conectores**
  * "o" $\to \lor$ (Disyunción entre la carrera y el año).
  * "no" $\to \neg$ (Negación de ser de primer año: $\neg R$).
  * "solo si" $\to \to$ (Condicional).
      * **Atención:** Como vimos en la tabla anterior, "$P$ solo si..." indica que lo que sigue es el consecuente.

* **Paso 3: Formalizar**
  El antecedente es el acceso ($P$) y el consecuente es la condición compuesta ($Q$ o no $R$).


**Resultado Final**:

$$
P \to (Q \lor \neg R)
$$

### Dirección 2: Lógica Formal $\to$ Lenguaje Natural

Esta habilidad es vital para leer código ajeno, documentación o especificaciones técnicas. El objetivo es convertir una fórmula abstracta en una oración coherente en español.

**Ejercicio:**
Dadas las proposiciones:
* $S$: El sistema tiene memoria disponible.
* $E$: Se ejecuta el proceso.

Interprete la fórmula: 

$$
\neg S \to \neg E
$$

* **Traducción Literal (Robótica):**
  
  > "Si no es cierto que el sistema tiene memoria disponible, entonces no es cierto que se ejecuta el proceso".

* **Traducción Natural (Profesional):**
  
  > "Si el sistema no tiene memoria, el proceso no se ejecuta".

> **Nota para programadores:** Esta estructura lógica es el fundamento de las *Cláusulas de Guardia* ([Guard Clauses](https://en.wikipedia.org/wiki/Guard_(computer_science))) en programación: verificar primero las condiciones de fallo para detener la ejecución antes de continuar.

### Ejemplos de traducción de lenguaje natural a lenguaje lógico

Traducir de lenguaje natural a lenguaje lógico los siguientes enunciados:

1. "El automovil arranca si y solo si el tanque tiene gasolina y la bateria esta cargada".

   **Solución**:
   El enunciado es un bicondicional, por lo que se puede formalizar como $P \leftrightarrow Q$.

   Donde:
   * $P$: El automovil arranca.
   * $Q$: El tanque tiene gasolina y la bateria esta cargada.

   Sin embargo, podemos descomponer cada parte del bicondicional mediante proposiciones simples de la siguiente manera:
   * Para $P$ tenemos la siguiente proposición simple:
     * $ON$: El automovil arranca.
   * Para $Q$ tenemos las siguiente proposiciones simples unidas mediante la conjunción ($\land$):
     * $GAS$: El tanque tiene gasolina.
     * $CHARGED$: La bateria esta cargada.

   De modo que $P = ON$ y $Q = (GAS \land CHARGED)$. Por lo que $P \leftrightarrow Q$ se puede formalizar como:

   $$
   ON \leftrightarrow (GAS \land CHARGED)
   $$

2. "Saldras a jugar solo si terminas la tarea".

   **Solución**:
   El enunciado es un condicional, por lo que se puede formalizar como $J \to T$.

   Donde:
   * $J$: Saldras a jugar.
   * $T$: Terminas la tarea.

   Por lo que el enunciado se puede formalizar como:

   $$
   J \to T
   $$

3. "Si no estudio Matematicas Discretas 1 y no hago la tarea de Logica y Representación 1, entonces no podre cursar Matematicas Discretas 2 ni Logica y Representación 2".

   **Solución**:
   El enunciado es una proposicion condicional de la forma $P \to Q$, donde el antecedente y el consecuente son proposiciones compuestas tal y como se muestra a continuación:
   * $P$: No estudio Matematicas Discretas 1 y no hago la tarea de Logica y Representación 1.
   * $Q$: No podre cursar Matematicas Discretas 2 ni Logica y Representación 2.

   En lo que respecta al antecedente $P$, tenemos las siguientes proposiciones simples:
   * $M1$: Estudio Matematicas Discretas 1.
   * $T$: Hago la tarea de Logica y Representación 1.

   Estas proposiciones estan negadas y unidas por una conjunción ($\land$). Por lo que:

    $$
    P = \neg M1 \land \neg T
    $$

   Por otro lado, en lo que respecta al consecuente $Q$, tenemos las siguientes proposiciones simples:
   * $M2$: Podré cursar Matematicas Discretas 2.
   * $T2$: Podré cursar Logica y Representación 2.

   Estas proposiciones estan negadas y unidas por una conjunción ($\land$). Por lo que:

    $$
    Q = \neg M2 \land \neg T2
    $$

   Finalmente el enunciado se puede formalizar como:

   $$P \to Q = (\neg M1 \land \neg T) \to (\neg M2 \land \neg T2)$$

4. "No puedes subir la montaña rusa si mides menos de 1.2, a menos que tengas mas de 16 años".

   **Solución**:
   Antes de empezar la traducción tratemos de entender el enunciado llevandolo a una forma que diga lo mismo pero que sea mas facil de traducir: "Si mides menos de 1.2 y no tienes mas de 16 años, entonces no puedes subir a la montaña rusa".

   Este enunciado es mas facil de traducir ya que facilmente se puede indentificar que es una proposicion condicional de la forma $P \to Q$ donde el antecedente y el consecuente son:
   * $P$: Mides menos de 1.2 y no tienes mas de 16 años.
   * $Q$: No puedes subir a la montaña rusa.

   Sin embargo, las proposiciones anteriores son compuestas de modo que el siguiente paso consiste obtener las proposiciones simples que las componen.

   En lo que respecta al antecedente $P$, tenemos las siguientes proposiciones simples:
   * $Age$: Tienes mas de 16 años.
   * $Height$: Mides menos de 1.2.

   De modo que el antecedente $P$ es $P = Height \land \neg Age$.

   Por otro lado, el consecuente $Q$ se puede expresar en terminos de una unica proposicion simple:
   * $RolerCoaster$: Puedes subir a la montaña rusa.

   Por lo que $Q = \neg RolerCoaster$.

   Finalmente el enunciado se puede formalizar como:

   $$P \to Q = (Height \land \neg Age) \to \neg RolerCoaster$$

5. "Puedes acceder a internet desde el campus solo si estudias ciencias de la computacion o no eres estudiante de primer año".

    **Solución**:
    Este enunciado tiene la forma "P solo si Q", por lo que es una proposicion condicional de la forma $P \to Q$:
    * $P$: Puedes acceder a internet desde el campus.
    * $Q$: Estudias ciencias de la computacion o no eres estudiante de primer año.

    El antecedente es una proposición simple la cual llamaremos $Internet$:
    * $Internet$: Puedes acceder a internet desde el campus.

    El consecuente es una proposición compuesta la cual llamaremos la cual se forma de dos proposiciones simples las cuales son:
    * $ComputerScience$: Estudias ciencias de la computacion.
    * $Freshman$: Eres estudiante de primer año.

    Por lo que $Q = ComputerScience \lor \neg Freshman$.

    Finalmente el enunciado se puede formalizar como:

    $$P \to Q = Internet \to (ComputerScience \lor \neg Freshman)$$

---

## Expresiones condicionales

### Tipos de proposiciones condicionales

A partir de una proposición condicional original (o Directa):

$$
P \to Q
$$

Se pueden generar tres proposiciones relacionadas, que tienen relaciones específicas de equivalencia:

* **Reciproco (Converse)**: Se forma al intercambiar el antecedente y el consecuente de la proposición original.

$$
Q \to P
$$

* **Contrareciproco (Contrapositive)**: Se forma al negar el antecedente y el consecuente de la proposición original y luego intercambiarlos.

$$
\neg Q \to \neg P
$$

* **Contrario (Inverse)**: Se forma al negar el antecedente de la proposición original.

$$
\neg P \to \neg Q
$$

### Condiciones de suficiencia y necesidad

To Do...

### Ejemplos

To do...
---
