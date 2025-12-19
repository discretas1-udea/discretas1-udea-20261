---
layout: default
title: Clase 01 - Fundamentos de Lógica Proposicional
parent: Lógica Proposicional
nav_order: 1
---

![Built with AI](https://img.shields.io/badge/Built%20with-AI-blue.svg)

# Clase 01 - Fundamentos de Lógica Proposicional

{: .no_toc }

Esta sesión introduce el objeto de estudio de la Lógica Proposicional, diferenciando el lenguaje natural de las estructuras formales que rigen el razonamiento matemático.

## Tabla de Contenidos

{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 1. El Lenguaje y su importancia

Cuando nos comunicamos, los seres humanos lo hacemos a **través** del lenguaje. Gracias a este, podemos transmitir cualquier **cosa**, como ideas, conceptos y sentimientos, por medio de mensajes.

Para construir mensajes empleamos oraciones. Una oración es la unidad **mínima** provista de significado y sentido. Desde el punto de vista **sintáctico**, está formada por la unión de un sujeto y un predicado (**Oración = Sujeto + Predicado**):

```mermaid
graph TD
    %% Nivel Superior: Oración
    O[O - Oración] --> SN1[SN - Sujeto]
    O --> SV[SV - Predicado]

    %% Sujeto
    SN1 --> N1[N - Núcleo]
    N1 --> w1("Dino")

    %% Predicado
    SV --> V[V - Verbo]
    SV --> SN2[SN - Atributo]
    
    V --> w2("es")

    %% Atributo (el perro de los Picapiedra)
    SN2 --> Det1[Det]
    SN2 --> N2[N - Núcleo]
    SN2 --> SPrep[SPrep - Compl. Nombre]
    
    Det1 --> w3("el")
    N2 --> w4("perro")

    %% Complemento (de los Picapiedra)
    SPrep --> Prep[Prep]
    SPrep --> SN3[SN - Término]
    
    Prep --> w5("de")
    
    SN3 --> Det2[Det]
    SN3 --> N3[N - Núcleo]
    
    Det2 --> w6("los")
    N3 --> w7("Picapiedra")

    %% Estilos (Cajas punteadas para las palabras)
    style w1 fill:#fff,stroke:#333,stroke-dasharray: 5 5
    style w2 fill:#fff,stroke:#333,stroke-dasharray: 5 5
    style w3 fill:#fff,stroke:#333,stroke-dasharray: 5 5
    style w4 fill:#fff,stroke:#333,stroke-dasharray: 5 5
    style w5 fill:#fff,stroke:#333,stroke-dasharray: 5 5
    style w6 fill:#fff,stroke:#333,stroke-dasharray: 5 5
    style w7 fill:#fff,stroke:#333,stroke-dasharray: 5 5
```

Al construir oraciones, se debe tener en cuenta un conjunto de reglas que establecen el orden y la forma en que se combinan las palabras; estas reglas se conocen como **sintaxis**. Comprenderla es esencial porque define el marco general que determina la validez de lo que intentamos expresar.

Además de la sintaxis, todo lo que decimos tiene un significado abordado por la **semántica**. Al escribir, relacionamos un concepto mental con una representación simbólica para que el mensaje sea interpretable por otros.

Por otro lado, el lenguaje posee un sentido práctico que va más allá del diccionario y depende del contexto; esto hace que lo dicho no sea siempre literal, sino que contenga significados "entre líneas". Esta dimensión es abordada por la **pragmática**.

```mermaid
graph BT
    %% Definición de Nodos
    Sintaxis[("1. Sintaxis<br/>(Estructura / Gramática)<br/>¿Está bien construida?")]
    Semantica[("2. Semántica<br/>(Significado literal)<br/>¿Qué significan las palabras?")]
    Pragmatica[("3. Pragmática<br/>(Uso / Contexto)<br/>¿Cuál es la intención?")]

    %% Relaciones (Base -> Abstracción)
    Sintaxis -->|Organiza la| Semantica
    Semantica -->|Se adapta a la| Pragmatica

    %% Notas explicativas (Ejemplo lingüístico: "Hace frío aquí")
    Note1[/"Ej: 'Hace frío aquí'<br/>Sujeto impersonal + Verbo + Adv.<br/>Gramática correcta."/]
    Note2[/"Ej: La temperatura en este<br/>lugar es baja.<br/>Significado del diccionario."/]
    Note3[/"Ej: 'Cierra la ventana'<br/>o 'Préstame un abrigo'.<br/>Intención del mensaje."/]

    %% Conexiones con las notas
    Sintaxis -.- Note1
    Semantica -.- Note2
    Pragmatica -.- Note3

    %% Estilos
    style Sintaxis fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    style Semantica fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px
    style Pragmatica fill:#fff3e0,stroke:#ef6c00,stroke-width:2px
    
    %% Estilo de las notas
    style Note1 fill:#fff,stroke:#999,stroke-dasharray: 5 5
    style Note2 fill:#fff,stroke:#999,stroke-dasharray: 5 5
    style Note3 fill:#fff,stroke:#999,stroke-dasharray: 5 5
```

A pesar de su riqueza, el lenguaje humano es inherentemente ambiguo; un mismo mensaje puede admitir múltiples interpretaciones, lo que suele derivar en confusiones. Asimismo, el objetivo de un enunciado puede transformarse radicalmente según la intención comunicativa, incluso si las palabras empleadas son idénticas. Por ejemplo, mientras que la afirmación "Dino es el perro de los Picapiedra" cumple una función informativa, la variante "¿Dino es el perro de los Picapiedra?" desplaza el propósito hacia una solicitud de información.

En la antigua Grecia, uno de los usos mayores usos del lenguaje consistia en la **persuación** (influir, convencer o conmover a una audiencia). Para poder aprovechar el lenguaje de la mejor manera posible, esta la **Retorica** cuyo objetivo es estudiar y utilizar el lenguaje como una herramienta para la **persuación** y los maestros en esta rama eran los sofistas griegos. Sin embargo, para el objetivo de la retorica anteponia la **efectividad** sobre la **verdad** gracias al uso de recursos cuyo fin era explotar la ambiguedad propia del lenguaje. Por lo tanto, el lenguaje se volvio una herramienta de poder instrumentalizada al servicio del mejor postor. Aristóteles quería que el pensamiento humano tuviera reglas tan claras como las de las matemáticas para lo cual invento la lógica cuyo objetivo era formalizar el pensamiento para llegar a la verdad.

Teniendo en cuenta la intención comunicativa, la siguiente tabla muestra algunos tipos de enunciados:

|Tipo |Intención Comunicativa |Ejemplo | 
|---|---|---|
|Declarativo | Informar o afirmar un hecho. | "Pedro es el esposo de Vilma." |
|Interrogativo | Preguntar o solicitar información. | "¿Dino es el perro de los Mármol?"|
|Imperativo	| Ordenar o solicitar una acción.|"¡Estudia para el examen!"|
|Exclamativo | Expresar emoción o sorpresa.| "¡Qué día tan caluroso!"|

De la tabla anterior, no todos los enunciados pueden son aptos para determinar son verdaderos o no, por lo tanto una primera restricción que debe ser realizada en pro de la exactitud consiste en restringir los enunciados validos a los declarativos los cuales son conocidos como **proposiciones**. En las siguientes secciones se ahondaran en estos enunciados y en la manera como, tal y como tenia en mente Aristoteles, mediante el uso de los enunciados declarativos se puede establecer un sistema formal siguiendo unas reglas claras las cuales pueden ser expresadas empleando el lenguaje Matematico. 

---

## 2. El Concepto Fundamental: La Proposición

La lógica se enfoca exclusivamente en los **Enunciados Declarativos** que cumplen una condición estricta.

### 2.1 Definición y Principio de Bivalencia

Una **Proposición Lógica** es todo enunciado declarativo al cual se le puede asignar, sin ambigüedad, un único **Valor de Verdad** (Axioma de Bivalencia).

> **Axioma de Bivalencia:** Un enunciado debe ser **Verdadero ($V$)** o **Falso ($F$)**, pero nunca ambos a la vez, ni ninguno.
{: .important }

### 2.2 Clasificación de Proposiciones

| Tipo | Descripción | Ejemplo |
| :--- | :--- | :--- |
| **Simple (Atómica)** | Es la unidad mínima. No tiene conectores lógicos internos. | $P$: "Hoy estudio Discretas 1." |
| **Compuesta (Molecular)** | Formada por dos o más proposiciones simples unidas por **Operadores Lógicos**. | $R$: "Hoy estudio Discretas 1 **y** hago deporte." |

---

## 3. Introducción a la Formalización

El objetivo de la lógica es transformar frases del lenguaje natural en **Expresiones Lógicas** mediante un proceso de traducción.

### 3.1 Los Operadores Lógicos (Conectores)

Los operadores son los símbolos que establecen la relación entre las proposiciones simples. Se presentan aquí de forma preliminar:

| Operador | Nombre | Símbolo | Lectura Común |
| :--- | :--- | :---: | :--- |
| **Negación** | No | $\neg$ | "No $P$" |
| **Conjunción** | Y | $\land$ | "$P$ y $Q$" |
| **Disyunción** | O Inclusiva | $\lor$ | "$P$ o $Q$" |
| **O exclusivo** | O exclusivo | $\oplus$ | "$P$ o $Q$" |
| **Condicional** | Si... entonces... | $\rightarrow$ | "Si $P$, entonces $Q$" |
| **Bicondicional** | Si y solo si | $\leftrightarrow$ | "$P$ si y solo si $Q$" |

### 3.2 Proceso de Traducción

Para formalizar una oración, se sigue este método de tres pasos:

1. **Identificar conectores lógicos** (ej. "o", "y", "si... entonces...").
2. **Identificar y asignar variables** a las proposiciones simples.
3. **Armar la expresión lógica** según la estructura gramatical.

---

## 4. Ejercicios Resueltos de Formalización

A continuación, se aplican los pasos de formalización a enunciados comunes:

#### Ejercicio 1: Disyunción

**Enunciado:** "Estudias o trabajas"

1. **Conector:** "o" ($\lor$).
2. **Variables:**
    * $P$: "Estudias"
    * $Q$: "Trabajas"
3. **Expresión Lógica:** $$P \lor Q$$

#### Ejercicio 2: Conjunción

**Enunciado:** "El Chapulín es un superhéroe y es Mexicano"

1. **Conector:** "y" ($\land$).
2. **Variables:**
    * $P$: "El Chapulín es un superhéroe"
    * $Q$: "El Chapulín es Mexicano"
3. **Expresión Lógica:** $$P \land Q$$

#### Ejercicio 3: Condicional (Implicación)

**Enunciado:** "Si estudias con juicio, ganarás la materia"

1. **Conector:** "Si... entonces..." ($\rightarrow$).
2. **Variables:**
    * $m$: "Estudias con juicio" (Antecedente)
    * $n$: "Ganarás la materia" (Consecuente)
3. **Expresión Lógica:** $$m \rightarrow n$$
