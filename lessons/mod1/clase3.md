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

Esta sesión marca el avance del cálculo tabular al **cálculo algebraico**. En lugar de usar tablas de verdad (método semántico), empleamos leyes lógicas (método sintáctico) para simplificar, demostrar o transformar proposiciones de manera eficiente.

## Tabla de Contenidos

{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 1. Repaso

{: .no_toc }

Antes de aplicar el Álgebra de Proposiciones, es fundamental recordar las bases de la formalización y los axiomas de verdad de los conectores lógicos.

### 1.1. Lenguaje Natural vs Lenguaje Lógico

El lenguaje natural es el que usamos en la vida cotidiana, mientras que el lenguaje lógico es el que usamos en la formalización de proposiciones. Debido a que el lenguaje natural es impreciso, es necesario usar el lenguaje lógico para formalizar las proposiciones.

* **Proposición:** Enunciado que cumple el **Principio de Bivalencia** ($V$ o $F$, pero no ambos).
* **Formalización:** Proceso de traducción que usa variables ($p, q, r$) y operadores ($\land, \lor, \rightarrow$).

---

### 1.2. Axiomas de Verdad y Tablas de Referencia

Las leyes de equivalencia se basan en el comportamiento de los operadores. Las siguientes tablas resumen los valores de verdad:

#### Tabla A: Negación, Conjunción ($\land$) y Disyunción ($\lor$)

| $p$ | $q$ | **Negación**<br>$\neg p$ | **Conjunción**<br>$p \land q$ | **Disyunción**<br>$p \lor q$ |
| :---: | :---: | :---: | :---: | :---: |
| V | V | F | **V** | V |
| V | F | F | F | V |
| F | V | V | F | V |
| F | F | V | F | **F** |

> **Reglas Clave:**
>
> * $\land$: Solo $V$ si ambas son $V$.
> * $\lor$: Solo $F$ si ambas son $F$.
{: .note }

#### Tabla B: Condicional ($\rightarrow$), Bicondicional ($\leftrightarrow$) y Exclusiva ($\oplus$)

| $p$ | $q$ | **Condicional**<br>$p \rightarrow q$ | **Bicondicional**<br>$p \leftrightarrow q$ | **Exclusiva**<br>$p \oplus q$ |
| :---: | :---: | :---: | :---: | :---: |
| V | V | V | **V** | F |
| V | F | **F** | F | V |
| F | V | V | F | V |
| F | F | V | **V** | F |

> **Caso Crítico del Condicional:**
> El operador $p \rightarrow q$ solo es **Falso** cuando el antecedente ($p$) es $V$ y el consecuente ($q$) es $F$ (un único caso).
{: .important }

### 1.3. Tipos de enunciados declarativos

A continuación se presentan los tipos de enunciados declarativos y su equivalencia con conectores lógicos.

#### 1.3.1. Equivalencia entre enunciados declarativos y conectores lógicos

Sean $P$ y $Q$ dos enunciados declarativos cualesquiera (simples o compuestos).

| Tipo                   | Conector lógico      | Forma simbólica | Enunciados en lenguaje natural |
|------------------------|----------------------|-----------------|--------------------------------|
| Conjuntivo             | Conjunción           | $P \land Q$     | • P y Q<br>• P, pero Q<br>• P aun Q<br>• P también Q<br>• P todavía Q<br>• P, aunque Q<br>• P sin embargo Q<br>• P además Q<br>• P no obstante Q |
| Disyuntivo (inclusivo) | Disyunción           | $P \lor Q$      | • P o Q<br>• P, a menos que Q<br>• Al menos una entre P y Q |
| Disyuntivo exclusivo   | Disyunción exclusiva | $P \oplus Q$    | • P o Q, pero no ambos<br>• O P o Q exclusivamente<br>• Exactamente uno de P y Q |

> ##### Notas clave
>
>* El **“o”** en lenguaje natural se interpreta por defecto como **disyunción inclusiva**.
>* El **“o exclusivo”** indica que **solo una** proposición es verdadera.
>* Expresiones como *pero*, *sin embargo* o *no obstante* no alteran la estructura lógica.
>* La expresión *“a menos que”* se modela como una disyunción inclusiva.
{: .note }

#### 1.3.2. Equivalencia entre enunciados declarativos con condicionales y bicondicionales

Sobre el enunciado declarativo **condicional**: en este caso $P$ representa el **antecedente** y $Q$ el **consecuente**.

| Tipo                         | Conector lógico      | Forma simbólica        | Enunciados en lenguaje natural |
|------------------------------|----------------------|------------------------|--------------------------------|
| Condicional (Hipotético)     | Implicación          | $P \to Q$              | • Si $P$, entonces $Q$<br>• Si $P$, $Q$<br>• $Q$ si $P$<br>• $P$ solo si $Q$<br>• Para $P$, es necesario $Q$<br>• Es suficiente $P$ para $Q$<br>• $Q$ en caso de que $P$<br>• $Q$ siempre que $P$<br>• Como $P$, $Q$<br>• $Q$ cuando $P$<br>• $P$ implica que $Q$<br>• Cuando $P$, $Q$ |
| Bicondicional                | Bicondicional        | $P \leftrightarrow Q$  | • $P$ si, y solo si, $Q$<br>• $P$ es suficiente y necesario para $Q$<br>• $P$ es equivalente a $Q$<br>• $P$ y $Q$ son equivalentes |

> #### Notas clave
>
> * La expresión **“$P$ solo si $Q$”** se formaliza como $P \to Q$.
> * La expresión **“$Q$ si $P$”** también corresponde a $P \to Q$.
> * En el **bicondicional**, ambas proposiciones tienen el mismo valor de verdad.
{: .note }

### 1.4. Traducción de lenguaje natural a lenguaje lógico

Para traducir proposiciones expresadas en lenguaje natural a lenguaje lógico, es necesario identificar los conectivos y variables que representan las proposiciones. Esto se muestra en los siguientes pasos:

1. Leer y comprender el enunciado.
2. Identificar las proposiciones simples (atômicas).
3. Asignar variables a las proposiciones simples.
4. Identificar los conectores lógicos.
5. Construir la proposición lógica completa asociada al enunciado.

### 1.5. Ejemplos de traducción de lenguaje natural a lenguaje lógico

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

## 2. Expresiones condicionales

### 2.1 Tipos de proposiciones condicionales

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

### 2.2. Condiciones de suficiencia y necesidad

To Do...

## 3. Reglas de Prioridad de Operadores

La **Jerarquía de Operadores** es una regla sintáctica que define el orden de aplicación de los conectivos lógicos al evaluar expresiones sin paréntesis, siendo esencial para eliminar la ambigüedad.

| Prioridad        | Símbolo | Asociatividad            | Ejemplo con paréntesis |
|------------------|---------|--------------------------|------------------------|
| 1 (más alta)     | $¬$     | No aplica (unitario)     | $¬p \land q \;\mapsto\; ((¬p) \land q)$ |
| 2                | $\land$ | Izquierda (I → D)        | $p \land q \land r \;\mapsto\; ((p \land q) \land r)$ |
| 3                | $\lor$  | Izquierda (I → D)        | $p \lor q \lor r \;\mapsto\; ((p \lor q) \lor r)$ |
| 4                | $\oplus$| Izquierda (I → D)        | $p \oplus q \oplus r \;\mapsto\; ((p \oplus q) \oplus r)$ |
| 5                | $\to$   | Derecha (I ← D)          | $p \to q \to r \;\mapsto\; (p \to (q \to r))$ |
| 6 (más baja)     | $\leftrightarrow$ | Derecha (I ← D) | $p \leftrightarrow q \leftrightarrow r \;\mapsto\; (p \leftrightarrow (q \leftrightarrow r))$ |

> #### Notas clave
>
> * La **negación** ($¬$) siempre aplica a **una proposición o a una expresión completa**.
> * Los operadores con **igual precedencia** se agrupan según su **asociatividad** (izquierda o derecha).
> * El uso de **paréntesis** permite evitar la ambigüedad en expresiones que usan varios operadores.
> * Cuando una expresión tiene **paréntesis anidados**, la evaluación se realiza **de adentro hacia afuera**.
{: .note }

---
