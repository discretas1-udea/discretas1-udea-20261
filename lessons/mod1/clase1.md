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

## 1. El Lenguaje y la Necesidad de la Lógica

Cuando nos comunicamos, los seres humanos lo hacemos a traves del lenguaje. Gracias a este, los seres humanos podemos transmitir cualquier cosa como ideas, conceptos y sentimientos por medio de mensajes.

El intercambio de mensajes en el acto comunicativo tiene una intención (o propósito) y es de acuerto a esta que se estructura el mensaje. Por ejemplo, cuando alguien dice "Dino es el perro de los Picapiedra", el mensaje tiene la intención de informar o afirmar un hecho; sin embargo, cuando lo que dice es "¿Dino es el perro de los Picapiedra?" la intención busca preguntar o solicitar información.

Para construir mensajes empleamos oraciones. Una oración es la unidad minima provista de sentido y significado la cual, desde el punto de vista sintactico esta formada por la unión de un sujeto y un predicado (**Oración = Sujeto + Predicado**):

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

Cuando se construyen oraciones como la anteriormente analizada, se deben tener en cuenta un conjunto de reglas que establecen el orden y la forma en que se deben combinar las palabras para construir oraciones correctas, esta reglas se conocen como **Sintaxis**. Comprender la sintaxis es escencial por que define el marco general que determina la validez y el sentido de lo que intentamos decir.

ToDo:
- [ ] Hablar de la sintaxis, semantica y pracmatica.
- [ ] Hablar de la riqueza del lenguaje.
- [ ] Empezar a hablar de la necesidad de restringir.
- [ ] Volver a los enunciados y a sus tipos.
- [ ] Restingir el caso a la parte de las proposiciones.
- [ ] Empezar a hablar de Matematicas como lengua exacta..
- [ ] Terminar hanlando de la logica.
  
  
La comunicación humana utiliza símbolos (alfabeto) para construir enunciados. Sin embargo, el **Lenguaje Natural (Español)** es inherentemente ambiguo (ej. ironía, contexto). La Lógica surge como la disciplina que busca la **exactitud** y la **eliminación de la ambigüedad**.

```mermaid
graph BT
    %% Definición de Nodos
    Sintaxis[("1. Sintaxis<br/>(Estructura / Forma)<br/>¿Es correcto?")]
    Semantica[("2. Semántica<br/>(Significado / Lógica)<br/>¿Tiene sentido?")]
    Pragmatica[("3. Pragmática<br/>(Contexto / Intención)<br/>¿Es adecuado?")]

    %% Relaciones (De abajo hacia arriba: Base -> Abstracción)
    Sintaxis -->|Soporta| Semantica
    Semantica -->|Habilita| Pragmatica

    %% Notas explicativas laterales (Simulando anotaciones)
    Note1[/"Ej: 'int edad = 10;'<br/>Compila bien"/]
    Note2[/"Ej: Asignar número a variable int<br/>Lógica válida"/]
    Note3[/"Ej: Usar esa variable para<br/>calcular descuento<br/>Objetivo real"/]

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

### Estructura del Lenguaje Natural

En gramática, la unidad mínima con sentido es la oración:

* **Sujeto:** Quien ejecuta la acción.
* **Predicado:** La acción (verbo) y su complemento.

> **Ejemplo:** *Dino es el perro de los Picapiedra*
>
> * **Sujeto**: Dino
> * **Predicado**: es el perro de los Picapiedra

### Clasificación de Enunciados

No todos los enunciados son aptos para el análisis lógico. Se clasifican según su intención comunicativa:

| Tipo | Intención Comunicativa | Ejemplo | Propiedad Lógica |
| :--- | :--- | :--- | :---: |
| **Declarativo** | Informar o afirmar un hecho. | "Pedro es el esposo de Vilma." | **Apto** |
| Interrogativo | Preguntar o solicitar información. | "¿Dino es el perro de los Mármol?" | No Apto |
| Imperativo | Ordenar o solicitar una acción. | "¡Estudia para el examen!" | No Apto |
| Exclamativo | Expresar emoción o sorpresa. | "¡Qué día tan caluroso!" | No Apto |

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
