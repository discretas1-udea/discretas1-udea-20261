![Built with AI](https://img.shields.io/badge/Built%20with-AI-blue.svg)

# Clase 01 - Introducción a la Lógica Proposicional

{: .no_toc }

## 1. Introducción: Comunicación y Lenguaje

La comunicación humana se basa en la intención y el uso de símbolos (alfabeto) para construir enunciados.

### Estructura Básica (Lenguaje Natural)

En español, la unidad mínima con sentido es la oración, compuesta por:

* **Sujeto:** Quien realiza la acción.
* **Predicado:** La acción (verbo) y complemento.

**Ejemplo:** *Dino es el perro de los Picapiedra*

* **Sujeto**: Dino
* **Predicado**: es el perro de los Picapiedra

### Clasificación de los Enunciados

No todo lo que decimos sirve para las matemáticas. Los enunciados se clasifican según su intención comunicativa:

|Tipo| Inteción |Ejemplo|
|---|---|---|
|Enunciado declarativo| Informar o afirmar algo| <ul><li>Pedro es el esposo de Vilma</li><li>Dino no es el perro de los Marmol</li></ul> |
|Enunciado interrogativo| Preguntar o solicitar información| <ul><li>¿Dino es el perro de los Picapiedra?</li><li>¿Que hora es?</li></ul>|
|Enunciado exclamativo| Expresar una emoción o sentitimiento intenso| <ul><li>¡Qué linda mujer!</li><li>¡Eres un angel!</li></ul>|
|Enunciado imperativo| Dar ordener, insistir, ruegos| <ul><li>Por favor, limpia tu habitacion</li><li>Tomate la colada</li></ul>|
|Enunciado dudativo| Expresar duda o posibilidad| <ul><li>Quizas llueva en la noche</li><li>Puede que la misión tenga exito</li></ul>|
|Enunciado desiderativo| Expresar deseos| <ul><li>Ojala haya paz en el mundo</li><li>Ojalá que nadie muera de hambre</li></ul>|

El mayor problema del Lenguaje Natural es que es **ambiguo*

## 2. Lógica Matemática

Las matemáticas son una ciencia exacta que busca argumentar y demostrar hechos sin ambigüedad mediante el uso de un lenguaje simbólico.

### La Proposición

Es la unidad mínima del lenguaje matemático.

{: .highlight }
> **Definición:**  
> Una **Proposición** es enunciado declarativo que puede ser **Falso (F)** o **Verdadero (V)**, pero no ambos a la vez.

El **valor de verdad** de una proposición es el valor que se le asigna a ella, es decir, si es verdadera ($V$, $1$, True) o falsa ($F$, $0$, False).

Para la representación de proposiciones se usan variables proposionales, generalmente $p$, $q$, $r$, $s$, etc.

**Ejemplos:**

* Sea $p$ la proposición "Dino es el perro de los Picapiedra". Entonces $p$ es una proposición.
* Sea $P$ la proposición "Hoy amaneció lloviendo". Si es cierto decirmos que el valor de verdad de $P$ es $V$, es decir, $P=V$.
* Sea $Q$ la proposición "Nacional le ganó a Sao Pablo". Si Nacional perdió con Sao Pablo decimos que el valor de verdad de $Q$ es $F$, es decir, $Q=F$.

## 3. Tipos de Proposiciones y Operadores

La lógica utiliza un razonamiento formal, es decir, a partir de hechos (premisas) se argumenta y se llega a conclusiones.

### Clasificación de las proposiciones

Según su forma, las proposiciones se clasifican en:

|Tipo| Inteción |Ejemplo|
|---|---|---|
|Proposición simple| Son proposiciones que no se pueden descomponer en otras proposiciones| Sea $p$ la proposición "Dino es el perro de los Picapiedra". Entonces $p$ es una proposición simple.|
|Proposición compuesta| Son proposiciones que se pueden descomponer en otras proposiciones| Sea $p$ la proposición "Hoy estudio Discretas" y $q$ la proposición "hago deporte", entonces "Hoy estudio Discretas **y** hago deporte" es una proposición compuesta la cual se denota como $p \land q$.|

### Operadores Lógicos (Conectores)

Así como en aritmética usamos $+$, $-$, $\times$, en lógica usamos conectores para operar con valores de verdad.

| Operación | Símbolo | Significado | Lógica |
| :--- | :---: | :--- | :--- |
| **Negación** | $\neg$ (o $\sim$) | No | Invierte el valor |
| **Conjunción** | $\land$ | Y | $P \land Q$ |
| **Disyunción** | $\lor$ | O | $P \lor Q$ |
| **O Exclusivo** | $\oplus$ | O ... o... | Uno u otro, no ambos |
| **Condicional** | $\to$ | Si ... entonces ... | Causa y efecto |
| **Bicondicional**| $\leftrightarrow$ | ... si y solo si... | Equivalencia |

## 4. Formalización (Traducción)

### Traducción de Lenguaje Natural a Expresión Lógica

A continuación se presentan los pasos para convertir Lenguaje Natural a Expresión Lógica:

1. **Identificación de Conectores Lógicos** El primer paso consiste en analizar el enunciado para detectar los operadores que vinculan las ideas. Es necesario distinguir las partículas gramaticales que funcionan como operadores lógicos (negación, conjunción, disyunción, condicional, bicondicional).
   * *Referencia*: Se deben buscar términos como "y", "o", "si... entonces", "no".
2. **Identificación y Simbolización de Proposiciones Simples**: Se deben aislar las unidades mínimas de sentido (proposiciones atómicas) que componen el enunciado complejo. A cada proposición simple se le asigna una variable proposicional, usualmente denotada con letras minúsculas o mayúsculas del alfabeto (ej. $p$, $q$, $r$, $m$, $n$).
3. **Construcción de la Expresión Lógica**: Finalmente, se procede a construir la fórmula matemática. Esto implica reescribir el enunciado original sustituyendo el texto por las variables asignadas y los símbolos lógicos correspondientes, respetando la jerarquía y estructura sintáctica del argumento.

### Ejemplos

Obtenga las expresiones lógicas de los siguientes enunciados:

1. "Estudias o trabajas"
2. "El Chapulín es un superhéroe y es Mexicano"
3. "Si estudias con juicio, ganarás la materia"
4. "Dino no es el perro de los Picapiedra"

### Solución

#### Ejercicio 1

Aplicando los pasos anteriores, obtenemos:

<p align="center">
  "Estudias <b>o</b> trabajas"
</p>

1. **Identificación de conectores**: Tenemos el "o" que es equivalente a la disyunción ($\lor$).
2. **Proposiciones simple**:
   * **$P$**: "Estudias"
   * **$Q$**: "Trabajas"
3. **Expresión lógica**:

<p align="center">
  $$ P \lor Q $$
</p>

#### Ejercicio 2

A partir de la siguiente proposición:

<p align="center">
  "El Chapulín es un superhéroe y es Mexicano"
</p>

1. **Identificación de conectores**: Tenemos el "y" que es equivalente a la conjunción ($\land$).
2. **Proposiciones simple**:
   * **$P$**: "El Chapulín es un superhéroe"
   * **$Q$**: "El Chapulín es Mexicano"
3. **Expresión lógica**:

<p align="center">
  $$ P \land Q $$
</p>

#### Ejercicio 3

Para este ejercicio, tenemos la siguiente proposición:

<p align="center">
  "Si estudias con juicio, ganarás la materia"
</p>

1. **Identificación de conectores**: Tenemos el "si... entonces..." que es equivalente a la conjunción ($\to$).
2. **Proposiciones simple**:
   * **$m$**: "Estudias con juicio"
   * **$n$**: "Ganarás la materia"
3. **Expresión lógica**:

<p align="center">
  $$ m \to n $$
</p>

#### Ejercicio 4

Finalmente, tenemos la siguiente proposición:

<p align="center">
  "Dino no es el perro de los Picapiedra"
</p>

1. **Identificación de conectores**: Tenemos el "no" que es equivalente a la negación ($\neg$).
2. **Proposiciones simple**:
   * **$D$**: "Dino es el perro de los Picapiedra"
3. **Expresión lógica**:

<p align="center">
  $$ \neg D $$
</p>

***********************************
***********************************

## 2. Definición de Equivalencia Lógica

### 2.1 Concepto de Equivalencia

Dos proposiciones, $P$ y $Q$, son **lógicamente equivalentes** si poseen la misma tabla de verdad. En otras palabras, sin importar el valor de verdad de sus variables componentes, siempre tienen el mismo resultado final.

**Notación:**
$$P \equiv Q$$
o
$$P \Leftrightarrow Q$$

> **Principio de Sustitución:** Una vez que se establece una equivalencia, una proposición puede ser sustituida por su equivalente en cualquier fórmula lógica sin alterar la validez del argumento.
{: .note }

---

## 3. Leyes Fundamentales del Álgebra de Proposiciones

Este conjunto de axiomas rige la simplificación lógica y es análogo a las propiedades algebraicas (conmutativa, asociativa, distributiva).

### 3.1 Leyes de Dominación y de Identidad

Estas leyes definen el comportamiento de las constantes $V$ (Verdadero) y $F$ (Falso).

| Nombre de la Ley | Conjunción ($\land$) | Disyunción ($\lor$) |
| :--- | :---: | :---: |
| **Dominación** | $$p \land F \equiv F$$|$$p \lor V \equiv V$$ |
| **Identidad** | $$p \land V \equiv p$$|$$p \lor F \equiv p$$ |
| **Idempotencia** | $$p \land p \equiv p$$|$$p \lor p \equiv p$$ |

### 3.2 Leyes de De Morgan (Negación de Compuestos)

Estas leyes son esenciales para negar proposiciones moleculares, transformando las conjunciones en disyunciones (y viceversa) e invirtiendo el valor de las variables.

1. **Negación de Conjunción:**
    $$\neg(p \land q) \equiv \neg p \lor \neg q$$
2. **Negación de Disyunción:**
    $$\neg(p \lor q) \equiv \neg p \land \neg q$$

### 3.3 Leyes de Absorción

Permiten simplificar expresiones donde una proposición se relaciona con una expresión que la contiene.

1. $$p \lor (p \land q) \equiv p$$
2. $$p \land (p \lor q) \equiv p$$

### 3.4 Leyes Asociativas y Conmutativas

Al igual que en álgebra, permiten reordenar o reagrupar proposiciones si se usa el mismo operador.

* **Conmutativa:** $$p \lor q \equiv q \lor p$$y$$p \land q \equiv q \land p$$
* **Asociativa:** $$(p \land q) \land r \equiv p \land (q \land r)$$

---

## 4. Leyes de Transformación de Operadores

Estas leyes son las "reglas de traducción" que nos permiten eliminar el condicional y el bicondicional, facilitando su manipulación con el álgebra.

### 4.1 Ley del Condicional

Permite expresar la implicación ($\rightarrow$) solo con negación ($\neg$) y disyunción ($\lor$).

$$p \rightarrow q \equiv \neg p \lor q$$

### 4.2 Ley del Bicondicional

Permite descomponer la equivalencia ($\leftrightarrow$) en dos condicionales interconectados.

$$p \leftrightarrow q \equiv (p \rightarrow q) \land (q \rightarrow p)$$

---

## 5. Ejercicio Resuelto de Simplificación

**Problema:** Simplificar la expresión lógica $$\neg(p \lor \neg q) \lor (\neg p \land q)$$

**Desarrollo Paso a Paso:**

1. **Expresión Original:**
    $$\neg(p \lor \neg q) \lor (\neg p \land q)$$

2. **Aplicar De Morgan (al primer paréntesis):**
    $$\neg p \land \neg(\neg q) \lor (\neg p \land q)$$

3. **Aplicar Doble Negación:** $\neg(\neg q) \equiv q$
    $$(\neg p \land q) \lor (\neg p \land q)$$

4. **Aplicar Idempotencia:** $A \lor A \equiv A$ (donde $A = \neg p \land q$)
    $$\neg p \land q$$

**Resultado Final:** La expresión simplificada es $$\neg p \land q$$

---
