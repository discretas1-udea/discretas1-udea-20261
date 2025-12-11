---
layout: default
title: Introducción a la Lógica Proposicional
parent: Lógica Proposicional
nav_order: 1                   
---

# Notas de Clase: Introducción a la Lógica Proposicional

* **Asignatura:** Matemáticas Discretas 1
* **Clase:** 1
* **Tema:** Del Lenguaje Natural al Lenguaje Matemático

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

{: .note }
> **Declaración de uso responsable de IA:**  
>
> * Parte del contenido presente en este documento fue elaborado o refinado con apoyo de herramientas de Inteligencia Artificial.  
> * El profesor realizó revisión, verificación y ajustes para garantizar la precisión, pertinencia académica y alineación con los objetivos del curso.  
> * Esta declaración se incluye para asegurar prácticas de transparencia y uso ético de tecnologías emergentes.
