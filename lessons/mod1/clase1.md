---
layout: default
title: Clase 01 - Fundamentos de Lógica Proposicional
parent: Lógica Proposicional
nav_order: 1
---

![Built with AI](https://img.shields.io/badge/Built%20with-AI-blue.svg)

# Clase 01 - Fundamentos de Lógica Proposicional
{: .no_toc .text-delta }

Esta sesión introduce el objeto de estudio de la Lógica Proposicional, diferenciando el lenguaje natural de las estructuras formales que rigen el razonamiento matemático.

## Tabla de Contenidos
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## El Lenguaje y su importancia

Cuando nos comunicamos, los seres humanos lo hacemos a **través** del lenguaje. Gracias a este, podemos transmitir cualquier idea, concepto o sentimiento por medio de mensajes.

Para construir mensajes empleamos oraciones. Una oración es una unidad fundamental del lenguaje que expresa un contenido con sentido completo en un contexto. Desde el punto de vista **sintáctico**, está formada por la unión de un sujeto y un predicado (**Oración = Sujeto + Predicado**):

<div style="text-align: center;" markdown="1">

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
    SV --> SN2[SN - Complemento]
    
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
**Figura 1**. Análisis sintáctico de una oración.
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>


Al construir oraciones, se debe tener en cuenta un conjunto de reglas que establecen el orden y la forma en que se combinan las palabras; estas reglas se conocen como **sintaxis**. Comprenderla es esencial porque define el marco general que determina la validez de lo que intentamos expresar.

Además de la sintaxis, todo lo que decimos tiene un significado abordado por la **semántica**. Al escribir, relacionamos un concepto mental con una representación simbólica para que el mensaje sea interpretable por otros.

Por otro lado, el lenguaje posee un sentido práctico que depende del contexto; esto hace que lo dicho no sea siempre literal, sino que contenga significados "entre líneas". Esta dimensión es abordada por la **pragmática**.

<div style="text-align: center;" markdown="1">
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
**Figura 2**. Dimensiones sintáctica, semántica y pragmática.
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>

A pesar de su riqueza, el lenguaje humano es inherentemente **ambiguo**; un mismo mensaje puede admitir múltiples interpretaciones, lo que suele derivar en confusiones. Asimismo, el objetivo de un enunciado puede transformarse según la intención comunicativa, incluso si las palabras son idénticas. Por ejemplo, mientras que la afirmación *"Dino es el perro de los Picapiedra"* cumple una función informativa, la variante *"¿Dino es el perro de los Picapiedra?"* busca solicitar información.

Históricamente, en la antigua Grecia, uno de los mayores usos del lenguaje consistía en la **persuasión** (influir o convencer a una audiencia). Para potenciar esta capacidad surge la **Retórica**, cuyo objetivo es utilizar el lenguaje como herramienta de convencimiento. Los maestros en esta rama eran los sofistas griegos; sin embargo, la retórica anteponía la **efectividad** sobre la **verdad**, explotando la **ambigüedad** propia del lenguaje.

Ante esta instrumentalización, Aristóteles buscó que el pensamiento humano tuviera reglas tan claras como las de las matemáticas. Para ello, **inventó la lógica**, cuyo propósito era formalizar el razonamiento para alcanzar la verdad de manera objetiva.

Teniendo en cuenta la intención comunicativa, la siguiente tabla clasifica los tipos de enunciados:

<div style="text-align: center;" markdown="1">
|Tipo |Intención Comunicativa |Ejemplo | 
|---|---|---|
|Declarativo | Informar o afirmar un hecho. | "Pedro es el esposo de Vilma." |
|Interrogativo | Preguntar o solicitar información. | "¿Dino es el perro de los Mármol?"|
|Imperativo	| Ordenar o solicitar una acción.|"¡Estudia para el examen!"|
|Exclamativo | Expresar emoción o sorpresa.| "¡Qué día tan caluroso!"|

**Tabla 1**. Algunos tipos de enunciados.
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>

De la tabla anterior, no todos los enunciados son aptos para determinar su veracidad. Por lo tanto, una primera restricción en pro de la exactitud consiste en limitar los enunciados válidos a los declarativos, conocidos como **proposiciones**. En las siguientes secciones se **ahondará** en estos enunciados y en la manera en que, tal como planteó Aristóteles, permiten establecer un sistema formal bajo reglas claras expresadas en lenguaje **matemático**.

---

## Conceptos Básicos de Lógica Proposicional

### Proposición

La lógica se enfoca exclusivamente en los **Enunciados Declarativos** ya que al ser oraciones que afirman o niegan algo sobre la realidad pueden tener un valor de verdad asociado. En el campo de la lógica, este tipo de enunciados se conocen como proposiciones.

<div style="background-color: #f0f4f8; border-left: 5px solid #0056b3; padding: 15px; margin: 20px 0;">
  <strong style="color: #0056b3;">Definición: Proposición Lógica</strong>
  <p style="margin-top: 5px;">
    Una <b>Proposición Lógica</b> es todo enunciado declarativo al cual se le puede asignar, sin ambigüedad, un único <b>Valor de Verdad</b> (Axioma de Bivalencia).
  </p>
</div>

<div style="background-color: #f0f4f8; border-left: 5px solid #0056b3; padding: 15px; margin: 20px 0;">
  <strong style="color: #0056b3;">Definición: Axioma de Bivalencia</strong>
  <p style="margin-top: 5px;">
    El <b>Axioma de Bivalencia</b> establece que un enunciado puede ser <b>Verdadero ($V$)</b> o <b>Falso ($F$)</b>, pero nunca ambos a la vez.
  </p>
</div>

### Clasificación de Proposiciones

Según su estructura, existen dos tipos de proposiciones:
1. **Proposición simple o atómica**: No contiene conectores lógicos. 
   * **$P$**: "Hoy hay clase de Discretas 1".
   * **$Q$**: "7 es primo".
2. **Proposición compuesta o molecular**: Contiene conectores lógicos ($\neg$, $\land$, $\lor$, $\oplus$, $\rightarrow$, $\leftrightarrow$).
   * **$\neg P$**: "Hoy no hay clase de Discretas 1".
   * **$P \land Q$**: "Hoy hay clase de Discretas 1 **y** 7 es primo".
   * **$P \rightarrow Q$**: **Si** hoy hay clase de Discretas 1, **entonces** 7 es primo.
   
---

## Introducción a la Formalización

En lógica, la **formalización** es el proceso de traducir enunciados y razonamientos del lenguaje natural (ambiguo y dependiente del contexto) a un lenguaje formal con:
* Símbolos definidos (variables y conectores).
* Reglas sintácticas (qué expresiones están bien formadas)
* Reglas semánticas (cómo asignarles valor de verdad)
* Reglas de inferencia (cómo derivar conclusiones válidas)

> El objetivo central de todo esto consiste en pasar de "frases" a estructuras que puedan ser evaluadas y manipuladas sin ambigüedad.
{: .important }

### Símbolos

En el lenguaje natural podemos decir lo mismo de muchas formas ("si... entonces...", "en caso de que...", "cuando...") y, además, una misma frase puede interpretarse de varias maneras según el contexto. Para evitar esa ambigüedad, la lógica trabaja con un **lenguaje formal**: un conjunto pequeño de **símbolos definidos** con significado fijo. 

#### Variables

Una **variable proposicional** representa una proposición completa (un enunciado declarativo con valor de verdad).
* **$P$**: "Hoy estudio Discretas 1."
* **$Q$**: "Mañana presento el parcial."

Estas letras **no son** números ni cantidades: son "etiquetas" para proposiciones.

#### Operadores Lógicos (Conectores)

Los **conectores** son símbolos que permiten construir proposiciones compuestas a partir de proposiciones simples. La siguiente tabla muestra de manera resumida los operadores lógicos empleados:

<div style="text-align: center;" markdown="1">
| Operador | Nombre | Símbolo | Lectura Común |
| :--- | :--- | :---: | :--- |
| **Negación** | "No" | $\neg$ | "**No** $P$" |
| **Conjunción** | "Y" | $\land$ | "$P$ **y** $Q$" |
| **Disyunción** | "O" (Inclusiva) | $\lor$ | "$P$ **o** $Q$" |
| **O exclusivo** | "O... o..." (Pero no ambos) | $\oplus$ | "**O** $P$ **o** $Q$" |
| **Condicional** | "Si... entonces..." | $\rightarrow$ | "**Si** $P$, **entonces** $Q$" |
| **Bicondicional** | "Si y solo si" | $\leftrightarrow$ | "$P$ **si y solo si** $Q$" |

**Tabla 2**. Operadores lógicos.
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>

> **Nota clave:** en lógica, cada símbolo tiene una definición precisa que luego se formaliza con tablas de verdad.
{: .note }

### Proceso de Traducción

Para formalizar una oración del lenguaje natural se muestra el siguiente método consistente en **tres pasos**. La idea es pasar de una frase (potencialmente ambigua) a una **fórmula** con conectores bien definidos.

<div style="text-align: center;" markdown="1">
```mermaid
graph LR
    A[Texto Natural] --> B{1. Identificar<br/>Conectores}
    B --> C{2. Definir<br/>Variables}
    C --> D{3. Ensamblar<br/>Fórmula}
    D --> E[Lenguaje Formal]
    style A fill:#f9f,stroke:#333
    style E fill:#00ff0022,stroke:#00aa00
```
**Figura 3**. Flujo de trabajo para la traducción de enunciados.
{: .fs-2 .text-grey-dk-000 .d-block .mt-2 }
</div>

A continuación, se describe con más detalle cada uno de los pasos mostrados en la figura anterior.

**Paso 1. Detecte la estructura lógica (conectores)**

1. Subraye las palabras que indiquen relación lógica:  
   **no**, **y**, **o**, **si… entonces…**, **si y solo si**, **a menos que**, **solo si**, etc.
2. Determine cuál es el **conector principal** (el que "manda" en toda la frase).
3. Si hay más de un conector, use **paréntesis** para reflejar la agrupación correcta.

**Paso 2. Defina proposiciones simples asociándolas a variables**

1. Separe la frase en **proposiciones atómicas** (enunciados declarativos sin conectores internos).
2. Asigne una letra a cada una y escriba su significado. Usaremos letras como $p, q, r$ para representar proposiciones; la letra es arbitraria, lo importante es el significado que se le asigna.
3. Verifique que cada proposición atómica tenga **valor de verdad** (sea claramente verdadera o falsa).

**Paso 3. Construya la fórmula y verifique**

1. Sustituya cada proposición atómica por su variable.
2. Reemplace los conectores por sus símbolos:  
   $(\neg, \land, \lor, \oplus, \rightarrow, \leftrightarrow)$
3. Revise que la fórmula sea consistente con el español original:
   - ¿La negación está donde corresponde?
   - ¿Los paréntesis reflejan la intención?
   - ¿"solo si" se tradujo correctamente?

> Nota: Para enunciados como "A María le gusta el café, asumimos que el sujeto, el momento y el contexto están fijos. Bajo esa interpretación, el enunciado puede tratarse como proposición (tendrá valor $V$ o $F$).
{: .note }

---

## Ejemplos resueltos

Traduzca los siguientes enunciados a lenguaje formal:

1. **Enunciado en lenguaje natural**: "La Chimoltrufia es mayor que el Chompiras"
   
   **Solución**: 

   **Enunciado**: 

   "La Chimoltrufia es mayor que el Chompiras"
   {: .text-center }

   1. **Conector principal**: No hay, la proposición es simple.
   2. **Proposiciones atómicas**:
      * **$p$**: "La Chimoltrufia es mayor que el Chompiras"
   3. **Expresión Lógica**: 
      
      $$
      p
      $$

2. Obtenga la negación de la proposición anterior y exprese en lenguaje natural.
   
   **Solución**: 

   1. **Proposiciones Simples**:
     * $p$: "La Chimoltrufia es mayor que el Chompiras"

   2. **Expresión Lógica**: Como se pide la negación de la proposición anterior, el resultado es:

      $$
      \neg p
      $$
   
   3. **Expresión en lenguaje natural**:
  
      "La Chimoltrufia ***no*** es mayor que el Chompiras"
      {: .text-center }

3. **Enunciado en lenguaje natural**: "A María le gusta el café y la torta"
   
   **Solución**: 

   **Enunciado**: 

   "A María le gusta el café y la torta"
   {: .text-center }

   1. **Conector principal**: "y" ($\land$).
   2. **Proposiciones atómicas**:
      * **$p$**: "A María le gusta el cafe"
      * **$q$**: "A María le gusta la torta"
   3. **Expresión Lógica**: 
      
      $$
      p \land q
      $$

4. **Enunciado en lenguaje natural**: "A los estudiantes les gustan los perros o les gustan los gatos"
   
   **Solución**: 

   **Enunciado**: 

   "A los estudiantes les gustan los perros o les gustan los gatos"
   {: .text-center }

   1. **Conector principal**: "o" ($\lor$).
   2. **Proposiciones atómicas**:
      * **$p$**: "A los estudiantes les gustan los perros"
      * **$q$**: "A los estudiantes les gustan los gatos"
   3. **Expresión Lógica**: 
      
      $$
      p \lor q
      $$

5. **Enunciado en lenguaje natural**: "Estudias o trabajas"
   
   **Solución**:

   "Estudias o trabajas"
   {: .text-center }

   1. **Conector principal**: "o" ($\lor$).
   2. **Proposiciones atómicas**:
      * **$P$**: "Estudias"
      * **$Q$**: "Trabajas"
   3. **Expresión Lógica**: 
      
      $$
      P \lor Q
      $$

6. **Enunciado en lenguaje natural**: "El Chapulín es un superhéroe y es Mexicano"
   
   **Solución**:

   "El Chapulín es un superhéroe y es Mexicano"
   {: .text-center }

   1. **Conector principal**: "y" ($\land$).
   2. **Proposiciones atómicas**:
      * **$P$**: "El Chapulín es un superhéroe"
      * **$Q$**: "El Chapulín es Mexicano"
   3. **Expresión Lógica**: 
       
       $$
       P \land Q
       $$

7. **Enunciado en lenguaje natural**: "A los estudiantes les gustan los perros o les gustan los gatos, pero no ambos"
   
   **Solución**:
   
   **Enunciado**:

   "A los estudiantes les gustan los perros o les gustan los gatos, pero no ambos"
   {: .text-center }

   1. **Conector principal**: "o" exclusivo ($\oplus$).
   2. **Proposiciones atómicas**:
      * **$p$**: "A los estudiantes les gustan los perros"
      * **$q$**: "A los estudiantes les gustan los gatos"
   3. **Expresión Lógica**: 
      
      $$
      p \oplus q
      $$

8. **Enunciado en lenguaje natural**: "Si estudias con juicio, ganarás la materia"
   
   **Solución**:

   **Enunciado**:
   
   "Si estudias con juicio, ganarás la materia"
   {: .text-center }

   1. **Conector principal:** "Si... entonces..." ($\rightarrow$).
   2. **Proposiciones atómicas:**
       * **$m$**: "Estudias con juicio" (Antecedente)
       * **$n$**: "Ganarás la materia" (Consecuente)
   3. **Expresión Lógica**:
      
      $$
      m \rightarrow n
      $$

9. **Enunciado en lenguaje natural**: "Si le regalo una rosa, entonces ella irá al baile conmigo"
   
   **Solución**:

   **Enunciado**:

   "Si le regalo una rosa, entonces ella irá al baile conmigo"
   {: .text-center }

   1. **Conector principal:** "Si... entonces..." ($\rightarrow$).
   2. **Proposiciones atómicas:**
       * **$p$**: "Le regalo una rosa"
       * **$q$**: "Ella irá al baile conmigo"
   3. **Expresión Lógica**:
      
      $$
      p \rightarrow q
      $$

10. **Enunciado en lenguaje natural**: "Puedes tomar el vuelo si y solo si compras el tiquete"
   
   **Solución**:

   **Enunciado**:

   "Puedes tomar el vuelo si y solo si compras el tiquete"
   {: .text-center }

   1. **Conector principal:** "Si y solo si..." ($\leftrightarrow$).
   2. **Proposiciones atómicas:**
       * **$p$**: "Puedes tomar el vuelo"
       * **$q$**: "Compras el tiquete"
   3. **Expresión Lógica**:
      
      $$
      p \leftrightarrow q
      $$

11. **Enunciado en lenguaje natural**: "Si apruebo el examen y entrego el proyecto, entonces no tendré que ir a recuperación"
    
    **Solución**:

    **Enunciado**:

    "Si apruebo el examen y entrego el proyecto, entonces no tendré que ir a recuperación"
    {: .text-center }

    1. **Conector principal:** "Si... entonces..." ($\rightarrow$).
    2. **Proposiciones atómicas:**
        * **$p$**: "Apruebo el examen"
        * **$q$**: "Entrego el proyecto"
        * **$r$**: "Tendré que ir a recuperación"
    3. **Expresión Lógica**:
       
       $$
       (p \land q) \rightarrow \neg r
       $$

## Actividad

A continuación, exploraremos la conexión de lo que hemos visto hasta el momento con la cotidianidad y la tecnología.

El objetivo de esta materia, más allá de una comprensión introductoria de la lógica y los números como parte del plan académico del microcurrículo, es fomentar el **pensamiento crítico** y la **curiosidad**.
A continuación, lo invitamos a revisar los siguientes dos videos:

### Video 1 - Esta herramienta te ayudará a mejorar tu pensamiento crítico

Video sobre el **Método Sócratico** el cual es la base fundamental para tener pensamiento crítico.

<div style="text-align: center;">
<iframe width="560" height="315" src="https://www.youtube.com/embed/7C3XUy3BYug?si=-qN2gYdYgYigivOa" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

**Actividad**: Identifique 3 enunciados del video que puedan convertirse en proposiciones y formalícelos.

### Video 2 - Documental The Thinking Game

Este documental muestra el recorrido de **DeepMind** en la creación de sistemas de inteligencia artificial capaces de aprender y razonar. Aquí se exploran los desafíos científicos, éticos y humanos detrás del desarrollo de la IA. A través de ejemplos como AlphaGo, reflexiona sobre qué significa "pensar" para una máquina. Invita a debatir los límites, riesgos y responsabilidades del uso de la inteligencia artificial.

<div style="text-align: center;">
<iframe width="560" height="315" src="https://www.youtube.com/embed/d95J8yzvjbQ?si=E5xCapAN1h-fvTva" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

**Actividad**: Escriba una implicación del tipo "si..., entonces..." que aparezca en el argumento del video.

## Resultados de aprendizaje

Al finalizar esta clase, se espera que usted sea capaz de:
* Identificar correctamente las proposiciones simples (atómicas).
* Diferenciar entre la estructura sintáctica de una oración y su valor semántico (verdad/falsedad).
* Seleccionar el conector lógico adecuado según el enunciado.
* Identificar el conector principal de un enunciado y usar paréntesis para reflejar la agrupación cuando sea necesario.
