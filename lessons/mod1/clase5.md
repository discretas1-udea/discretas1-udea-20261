---
layout: default
title: Clase 05 - Validez e inferencia (tablas vs reglas)
parent: Lógica Proposicional
nav_order: 5
math: mathjax
---

![Built with AI](https://img.shields.io/badge/Built%20with-AI-blue.svg)
# Clase 05 – Validez e Inferencia: Tablas (Modelos) vs Reglas (Derivación)
{: .no_toc }

En la clase anterior aprendimos a simplificar expresiones usando axiomas de equivalencia ($A \equiv B$). Hoy daremos un paso más allá: no solo queremos saber si dos cosas son iguales, queremos saber si **una conclusión se sigue necesariamente de unas premisas**.

Entramos al corazón de la lógica matemática: la **Argumentación**.

---

## Tabla de contenidos
{: .no_toc .text-delta }
1. TOC
{:toc}

---

## Repaso: Equivalencia Lógica y El Camino hacia la Inferencia

Antes de adentrarnos en el concepto de **Validez** (¿es correcto mi razonamiento?), es fundamental asegurar que dominamos el concepto de **Equivalencia** (¿dicen lo mismo estas dos frases?).

A lo largo del curso, hemos evolucionado desde una perspectiva informal de las proposiciones hacia un enfoque formal apoyado en el **Álgebra Proposicional**. Este cambio nos ha permitido dejar de depender de la intuición lingüística para confiar en reglas matemáticas precisas.

### ¿Qué significa realmente $A \equiv B$?

Diremos que dos expresiones lógicas $A(p,q,\dots)$ y $B(p,q,\dots)$ son **lógicamente equivalentes** ($A \equiv B$) si, y solo si:
> **Al evaluarlas para TODAS las posibles combinaciones de verdad, producen exactamente el mismo resultado.**

En términos prácticos: $A$ y $B$ son "sinónimos matemáticos". Puedo reemplazar uno por otro en cualquier fórmula sin alterar su valor de verdad.

Recordemos las dos herramientas que tenemos para verificar esto:
1.  **Enfoque Semántico (Tablas de Verdad):** Fuerza bruta. Verificamos fila por fila. Es infalible pero lento.
2.  **Enfoque Sintáctico (Axiomático):** Elegancia matemática. Transformamos la expresión usando leyes permitidas hasta que coincida con la otra.
  
### Inventario Rápido de Leyes

Para los ejercicios de demostración que vendrán, mantenga esta tabla a la mano. Estas son sus "herramientas de construcción":

| Nombre | Forma $\land$ / $\to$ | Forma $\lor$ |
| :--- | :--- | :--- |
| **Conmutativa** | $p \land q \equiv q \land p$ | $p \lor q \equiv q \lor p$ |
| **Asociativa** | $(p \land q) \land r \equiv p \land (q \land r)$ | $(p \lor q) \lor r \equiv p \lor (q \lor r)$ |
| **Distributiva** | $p \land (q \lor r) \equiv (p \land q) \lor (p \land r)$ | $p \lor (q \land r) \equiv (p \land q) \land (p \land r)$ |
| **De Morgan** | $\neg(p \land q) \equiv \neg p \lor \neg q$ | $\neg(p \lor q) \equiv \neg p \land \neg q$ |
| **Identidad** | $p \land V \equiv p$ | $p \lor F \equiv p$ |
| **Dominación** | $p \land F \equiv F$ | $p \lor V \equiv V$ |
| **Absorción** | $p \land (p \lor q) \equiv p$ | $p \lor (p \land q) \equiv p$ |
| **Complemento** | $p \land \neg p \equiv F$ | $p \lor \neg p \equiv V$ |
| **Doble Negación** | $\neg(\neg p) \equiv p$ | — |
| **Implicación** | $p \to q \equiv \neg p \lor q$ | — |
| **Contrapositiva** | $p \to q \equiv \neg q \to \neg p$ | *(Muy útil)* |
| **Equivalencia** | $p \leftrightarrow q \equiv (p \to q) \land (q \to p)$ | — |

#### Ejemplo de repaso
{: .no_toc }

Vamos a calentar motores demostrando una propiedad clásica de la lógica: **La contrapositiva del bicondicional**.
Demuestre que:

$$p \leftrightarrow q \equiv \neg p \leftrightarrow \neg q$$

**Solución**: A continuación se muestra la demostración al aplicar ambos metodos.

* **Metodo basado en tablas de verdad**: A continuación se muestra la tabla de verdad evaluada para esta expresión:
 
  | $p$ | $q$ | $\neg p$ | $\neg q$ | **$p \leftrightarrow q$** | **$\neg p \leftrightarrow \neg q$** |  **$p \leftrightarrow q \equiv \neg p \leftrightarrow \neg q$** | ¿Iguales? |
  | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
  | 0 | 0 | 1 | 1 | **1** | **1** | **1** | ✅ |
  | 0 | 1 | 1 | 0 | **0** | **0** | **1** | ✅ |
  | 1 | 0 | 0 | 1 | **0** | **0** | **1** | ✅ |
  | 1 | 1 | 0 | 0 | **1** | **1** | **1** | ✅ |

  Como la proposición $(p \leftrightarrow q) \leftrightarrow (\neg p \leftrightarrow \neg q)$ resulta ser una **tautología**, es válido afirmar que:

  $$
  \therefore\;\; p \leftrightarrow q \equiv \neg p \leftrightarrow \neg q
  $$

* **Metodo axiomático**: Partiendo del lado derecho de la expresión ($\neg p \leftrightarrow \neg q$), aplicamos las leyes del inventario para llegar al lado izquierdo:
  
  Partimos del lado derecho ($\neg p \leftrightarrow \neg q$) e intentaremos transformarlo paso a paso para llegar al lado izquierdo ($p \leftrightarrow q$).

  | Paso | Expresión | Justificación |
  | :---: | :--- | :--- |
  | **1** | $\neg p \leftrightarrow \neg q$ | Expresión original (lado derecho) |
  | **2** | $(\neg p \to \neg q) \land (\neg q \to \neg p)$ | **Definición de Bicondicional** ($A \leftrightarrow B \equiv (A \to B) \land (B \to A)$) |
  | **3** | $(\neg(\neg p) \lor \neg q) \land (\neg(\neg q) \lor \neg p)$ | **Definición de Condicional** ($A \to B \equiv \neg A \lor B$) |
  | **4** | $(p \lor \neg q) \land (q \lor \neg p)$ | **Doble Negación** |
  | **5** | $(\neg q \lor p) \land (\neg p \lor q)$ | **Conmutativa** (Ordenamos para ver el condicional) |
  | **6** | $(q \to p) \land (p \to q)$ | **Definición de Condicional** (Inversa: $\neg A \lor B \equiv A \to B$) |
  | **7** | $(p \to q) \land (q \to p)$ | **Conmutativa** (del operador $\land$) |
  | **8** | $p \leftrightarrow q$ | **Definición de Bicondicional** |

  Por lo tanto,

  $$
  \therefore\;\; p \leftrightarrow q \equiv \neg p \leftrightarrow \neg q
  $$

  > **Reflexión:** Note que en el paso 6 recuperamos dos condicionales. El hecho de que $(q \to p) \land (p \to q)$ sea lo mismo que $p \leftrightarrow q$ nos muestra la simetría perfecta de esta estructura.


## El proceso deductivo

### Contextualización: De la Opinión a la Demostración

Argumentar es una actividad cotidiana. Lo hacemos constantemente al discutir sobre política, religión o fútbol, o cuando intentamos convencer a alguien de nuestro punto de vista. En esos escenarios informales, solemos mezclar hechos con emociones, intuiciones y opiniones.

Sin embargo, en el ámbito académico y científico, "argumentar" tiene un significado mucho más estricto. Seguramente, en el pasado usted ha realizado exámenes de comprensión lectora donde, a partir de un texto, debe responder preguntas lógicas para demostrar que entendió lo leído.

Analicemos esto con el siguiente relato deductivo:

{: .note }
> **El Caso del Zafiro Desaparecido**
>
> El inspector Lestrade irrumpió en la sala, visiblemente frustrado.
> — "Holmes, es imposible. El **Zafiro de Sussex** ha desaparecido de la caja fuerte, pero no hay signos de fuerza bruta. Tenemos tres sospechosos, pero ninguna prueba."
>
> Sherlock Holmes, encendiendo su pipa, respondió con calma:
> — "Lestrade, los hechos hablan por sí solos si se escuchan con lógica. Repasemos lo que sabemos:"
>
> 1. "Sabemos que si el ladrón hubiera forzado la ventana, entonces habría huellas de barro en la alfombra, pues anoche llovió a cántaros."
> 2. "Sin embargo, he revisado la alfombra con mi lupa y no hay ni una sola mancha de barro."
> 3. "Ahora bien, por la naturaleza de la caja fuerte, sabemos que o bien el ladrón forzó la ventana o bien tenía la llave maestra."
> 4. "Y finalmente, un hecho doloroso pero cierto: si el ladrón tenía la llave maestra, entonces el mayordomo es cómplice, pues solo él custodia esa llave."

Ante este escenario, una pregunta natural sería: **¿Quién es el culpable y por qué?**

Nuestra intuición nos grita la respuesta rápidamente ("¡El mayordomo!"). Pero, **¿cómo podemos estar seguros al 100%?** ¿Cómo podemos garantizar que nuestra conclusión no es una corazonada, sino una verdad ineludible?

En esta sección, conectaremos esta narrativa con la **lógica formal**. Veremos cómo transformar estas pistas (premisas) en fórmulas matemáticas y cómo el **proceso deductivo** nos permite "calcular" al culpable sin margen de error, utilizando las reglas de inferencia.

### Sobre la argumentación

**Argumentar** es el proceso de presentar una secuencia de enunciados, denominados **premisas** con el objetivo de demostrar la veracidad de una afirmación final, llamada **conclusión**. 

Retornando a nuestro **El Caso del Zafiro Desaparecido**, las premisas, escritas en un tono mas formal con el fin de hacer mas facil la visualización de las proposiciones (para su posterior traducción a lenguaje simbolico) que hacen parte de la historia:
1. "Si el ladrón hubiera forzado la ventana, entonces habría huellas de barro en la alfombra."
2. "No hay manchas de barro en la alfombra."
3. "El ladron forzo la ventana o bien tenía la llave maestra."
4. "Si el ladrón tenía la llave maestra, entonces el mayordomo es cómplice."

Por otro lado, para responder a la pregunta **¿quién es el culpable?**, la afirmación que se pretende justificar a partir de estas premisas es:

> **"El mayordomo es cómplice."**

Esta afirmación puede verse como una **proposición candidata a conclusión**, cuya veracidad no se asumirá de entrada, sino que deberá derivarse lógicamente a partir de las premisas mediante un proceso deductivo.

Antes de proceder a trabajar la historia dentro del contexto le la logica proposicional debemos traducir las proposiciones y la conclusión anterior a lenguaje formal. Para ello iniciamos definiendo las variables logicas asociadas a las proposiciones atomicas:
* **$p$**: El ladrón forzó la ventana.
* **$q$**: Hay huellas de barro en la alfombra.
* **$r$**: El ladrón tenia llave maestra.
* **$s$**: El mayordomo es complice.

Ahora, expresando las premisas y la conclusion en lenguaje formal tenemos:
* **Premisas**:
  1. "Si el ladrón hubiera forzado la ventana, entonces habría huellas de barro en la alfombra."
     
     $$
     p \to q
     $$
  2. "No hay manchas de barro en la alfombra."
     
     
     $$
     \neg q
     $$

  3. "El ladron forzo la ventana o bien tenía la llave maestra."
     
     $$
     p \lor r
     $$

  4. "Si el ladrón tenía la llave maestra, entonces el mayordomo es cómplice."
     
     $$
     r \to s
     $$
     

* **Conclusión**:
  
  > "El mayordomo es cómplice."
  
  $$
  s
  $$

En, resumen nuestra historia **El Caso del Zafiro Desaparecido** expresada en lenguaje formal, queda de la siguiente manera:

$$
\begin{array}{l}
p \rightarrow q \\
\neg q \\
p \lor r \\
r \rightarrow s \\
\hline
\therefore\ s
\end{array}
$$

Si observamos lo anterior, desde la lógica proposicional, un argumento tiene una estructura lógica definida por:
* **Premisas**: $P_1,P_2,...,P_n$, que representan los hechos, leyes o suposiciones iniciales.
* **Conclusión**: $(Q)$, que es la afirmación que se pretende derivar a partir de las premisas.

De manera general, cualquier argumento puede representarse como:

$$
\begin{array}{l}
P_1 \\
P_2 \\
\vdots \\
P_n \\
\hline
\therefore\ Q
\end{array}
$$

Una vez que el argumento ha sido planteado, el siguiente paso es determinar si este es **válido o no**. Esto se logra mediante un proceso de inferencia lógica, el cual permite establecer si la conclusión se deduce necesariamente de las premisas. En el caso de nuestra historia, ya hemos identificado los indicios y la conclusión esperada; sin embargo, aún no hemos explicado el **porqué**. Antes de demostrarlo, haremos una aclaración sumamente importante en la siguiente sección.

### Representación de Argumentos

Una vez que hemos identificado las premisas y la conclusión en lenguaje natural, es fundamental organizarlas formalmente para evitar ambigüedades. En la lógica matemática y las ciencias de la computación, utilizamos tres notaciones estándar para representar argumentos.

Es importante que se familiarice con ellas, ya que las usaremos indistintamente a lo largo del curso según el contexto (demostración manual, enunciado de examen o validación algorítmica).

#### 1. Forma Estándar (Vertical)
{: .no_toc }

Es la notación clásica utilizada para realizar **demostraciones paso a paso**. Se listan las premisas numeradas una debajo de otra, se traza una línea horizontal (que representa la inferencia) y se escribe la conclusión al final.

**Estructura:**

$$
\begin{array}{ll}
P_1 \\
P_2 \\
\vdots \\
P_n \\
\hline
\therefore & Q
\end{array}
$$

* **$P_1, P_2, \dots, P_n$:** Son las premisas (hipótesis).
* **Línea horizontal:** Delimita el fin de las premisas y el inicio de la deducción.
* **$\therefore$**: Símbolo matemático que se lee *"Por lo tanto"*.
* **$Q$:** Es la conclusión.

#### 2. Forma Horizontal (Notación de Secuente)
{: .no_toc }

Esta notación es muy compacta y se utiliza frecuentemente en libros de texto o para enunciar problemas donde el espacio es limitado. Utiliza el símbolo **$\vdash$** (llamado *deductor* o *turnstile*) para separar el conjunto de premisas de la conclusión.

**Estructura:**

$$
P_1, P_2, \dots, P_n \vdash Q
$$

* **Lectura:** *"Del conjunto de premisas $P_1$ hasta $P_n$ se deduce (es válido inferir) $Q$".*

#### 3. Forma Condicional (La "Gran Implicación")
{: .no_toc }

Esta forma es crucial para verificar la validez mediante **Tablas de Verdad** o métodos computacionales. Convertimos todo el argumento en una única fórmula lógica condicional.

**Estructura:**

$$
(P_1 \land P_2 \land \dots \land P_n) \to Q
$$

* **Interpretación:** *"Si todas las premisas son verdaderas simultáneamente (conjunción), entonces la conclusión debe ser verdadera".*
* **Criterio de Validez:** Para que el argumento sea válido, esta fórmula debe ser una **Tautología** (siempre verdadera).

#### Ejemplo Comparativo
{: .no_toc }

La siguiente tabla retoma nuevamente el argumento previamente obtenido para *El Caso del Zafiro Desaparecido* para el caso estandar y lo compara con las otras .

| Formato | Representación | Uso Principal |
| :--- | :--- | :--- |
| **Estándar** | $\begin{array}{l} p \rightarrow q \\\\ \neg q \\\\ p \lor r \\\\ r \rightarrow s \\\\ \hline \therefore\ s \end{array}$ | Ideal para aplicar reglas de inferencia paso a paso. |
| **Horizontal** | $p \rightarrow q,\ \neg q,\ p \lor r,\ r \rightarrow s \ \vdash\ s$ | Ideal para enunciados compactos. |
| **Condicional** | $\bigl[(p \rightarrow q)\land(\neg q)\land(p \lor r)\land(r \rightarrow s)\bigr] \to s$ | Ideal para validación por **Tabla de Verdad**. |

### Verdad vs validez (sin confundir conceptos)

En el lenguaje cotidiano, solemos usar las palabras *verdadero* y *válido* como si fueran sinónimos. Sin embargo, en **lógica** representan conceptos distintos y no deben confundirse.

#### Sobre la verdad

El concepto de **verdad** se aplica a una **proposición** (un enunciado declarativo) y depende del **contexto** o de la **interpretación** que estemos usando. En particular, una proposición puede ser **verdadera** o **falsa** según si lo que afirma coincide con los hechos (o con el modelo) que estamos tomando como referencia.

Por ejemplo, usando conocimiento básico de geografía (donde \(V\) = verdadero y \(F\) = falso):

| Proposición | Representación | Valor de verdad | Justificación |
|---|---:|:---:|---|
| Medellín está en Colombia | $P_1$ | $V$ | Coincide con la realidad geográfica. |
| Medellín está en Brasil   | $P_2$ | $F$ | No coincide con la realidad. |

> En otras palabras, la **verdad** está relacionada con el **contenido** del enunciado respondiendo, dentro de un contexto, a la pregunta  
**¿Coincide lo que afirma la proposición con los hechos (o el modelo) considerado?**

#### Sobre la validez

A diferencia de la **verdad**, que está relacionada con las proposiciones, la **validez** tiene que ver con los argumentos. Más exactamente, la **validez** es una propiedad de los argumentos que depende exclusivamente de su forma lógica y no de su contenido específico (contexto).


Previamente habiamos dicho que desde el punto de vista de la logica, un argumento esta compuesto por premisas y conclusión. En lo que respecta a la validez como propiedad, un argumento se considera valido si, y solo si, es imposible que su conclusión sea falsa dado que todas sus premisas sean verdaderas. 

**Ejemplos**

Los siguientes ejemplos buscan aclarar el concepto de **validez**.

1. En el argumento mostrado a continuación, la **forma** es válida (Modus Ponens). Además, en el contexto cotidiano, sus premisas y conclusión suelen ser verdaderas.

   $$
   \begin{array}{l}
   \text{Si llueve, la calle se moja.}\\
   \text{Llueve.}\\ \hline
   \therefore\ \text{La calle se moja.}
   \end{array}
   $$

   Del argumento anterior, se puede deducir a partir de los hechos que nos dan que cuando hay lluvia la calle se moja.

2. En el siguiente argumento notese que teniendo en cuenta el contexto (nuestro conocimiento real sobre la luna y los ratones), las premisas son falsas. Sin embargo, la validez no exige que las premisas sean reales, sino que el argumento esta bien construido (tiene una estructura correca) lo cual se cumple en el ejemplo:
  
   $$
   \begin{array}{l}
   \text{Si la Luna es de queso, entonces hay ratones astronautas.}\\
   \text{La Luna es de queso.}\\ \hline
   \therefore\ \text{Hay ratones astronautas.}
   \end{array}
   $$
  
   Si aceptamos que las premisas son ciertas, vemos que *la forma* en que se infiere a la conclusión es correcta por lo tanto el argumento es **valido** aunque desde la realidad, lo que aqui se dice sea un disparate.

   {: .tip }
   > **Validez** no significa que lo que dices sea verdad en la vida real. Significa que, si aceptamos las premisas (aunque sean locas), la conclusión es inevitable.

3. El siguiente argumento es **invalido** y es una tipo de falacia conocida **afirmar el consecuente**.
  
   $$
   \begin{array}{l}
   \text{Si estudio, apruebo.}\\
   \text{Apruebo.}\\ \hline
   \therefore\ \text{Estudio.}
   \end{array}
   $$

   En este caso llegar a la coclusión de que *estudie* para lograr el resultado de *apruebar* no es clara; de hecho hay otras formas de haber *aprobado* sin haber *estudiado* (causa) que pueden ser tenidas en cuenta: hacer trampa, el examen estaba muy facil, etc. Note que la estructura del argumento da lugar a probar las otros posibles antecedentes que hagan que el consecuente sea falso, de modo que reducir la conclusión a solo *estudiar*, como se muestra en el ejemplo, no es valido.

  {: .tip }
  > La falacia de **afirmar el consecuente** consiste en ver el resultado y asumir erróneamente que solo hay una causa posible, ignorando que muchas otras cosas podrían haber provocado ese mismo resultado.
  
Según lo anterior, podemos concluir que:
- **Validez** no es lo mismo que **verdad**
- La lógica se ocupa principalmente de evaluar la **validez de los razonamientos**, no de verificar hechos.

Para construir algumentos validos se utilizan **reglas de inferencia**, mediante estas, es como construimos el camino para llegar de manera logica a una concluión a partir de las premidas.

## Métodos de validación de argumentos

Recordemos que un **argumento** es un razonamiento compuesto por unas **premisas** y una **conclusión**, y que la relación entre ellas puede ser **válida** o **inválida**. Como vimos, la validez depende de la forma lógica del argumento, no del contenido.

Esto abre preguntas naturales:
- Si un argumento es "válido por su estructura", **¿cómo podemos verificar esa validez de manera formal?**
- **¿Existe un procedimiento sistemático** (no solo intuición) para decidir si las premisas obligan a la conclusión?
- Así como para la equivalencia lógica usamos métodos mecánicos (por ejemplo, tablas de verdad o transformaciones), **¿qué métodos existen para validar argumentos?**
- Y cuando el argumento tiene muchas variables (y la tabla de verdad se vuelve enorme), **¿cómo razonamos paso a paso sin perdernos?**

El objetivo de esta sección es responder estas preguntas de forma progresiva: primero veremos un método **semántico** (validación con tablas de verdad) y luego un método **sintáctico** (prueba formal), donde cada paso se justifica mediante **reglas de inferencia**.

### Validación por fuerza bruta (enfoque basado en modelos o tablas de verdad)

Hasta aquí ya sabemos **qué** es un argumento (premisas + conclusión) y **qué** significa que sea válido (no depende del contenido, sino de la forma). La pregunta ahora es:

**¿Cómo determinamos formalmente si un argumento es válido o inválido?**

La primera respuesta es un método directo, mecánico y sin ambigüedades: **las tablas de verdad**.  
A este enfoque lo llamaremos **fuerza bruta**, porque revisa sistemáticamente *todos* los casos posibles.

Recordemos la forma formal de un argumento esta dada por:

$$
\begin{array}{l}
P_1 \\
P_2 \\
\vdots \\
P_n \\
\hline
\therefore\ Q
\end{array}
$$

Teniendo en cuenta que *un argumento es válido si no existe ningún escenario donde las premisas sean verdaderas y la conclusión falsa*, podemos construir una tabla de verdad para la implicación asociada al argumento para evaluarlo mediante la siguiente expresión:

$$
(P_1 \land P_2 \land \dots \land P_n) \to Q
$$

Para determinar si un argumento es valido, una vez que la tabla ha sido construida para todos valores de entrada posibles, debemos restringir el analisis a los **renglones criticos**. Un reglon critico, es una fila de la tabla en la cual todas las premisas $P_1, P_2,\dots, P_n$ son verdaderas simultaneamende. La valides dependiende del valor de la conclusión para los renglones criticos de tal manera que el argumento es:
* **Valido**: si para todos los valores de los renglones criticos la conclusión es verdadera.
* **Invalido**: Si existe al menos un renglón crítico donde la conclusión sea falsa.

El problema de usar tabla de verdad para demostrar la validez (al igual que con las equivalencias) es la **escalabilidad** pues a mas variables proposicionales ($n$) mayor numero de filas ($2^n$) lo cual es impractico para mas de 5 variables en terminos de eficiencia.

{: .note }
> En las tablas de verdad usaremos la codificación: **1 = Verdadero** y **0 = Falso**.


#### Ejemplo
{: .no_toc }

Retomemos nuevamente al **Caso del Zafiro Desaparecido** cuyo argumento expresado en lenguaje formal era el siguiente:

$$
\begin{array}{l}
p \rightarrow q \\
\neg q \\
p \lor r \\
r \rightarrow s \\
\hline
\therefore\ s
\end{array}
$$

Para evaluar la validez por fuerza bruta, seguimos los siguientes pasos:
1. **Identificar las proposiciones atómicas del argumento**: En este caso que estas son $p, q, r$ y $s$.
2. **Construir la tabla de verdad con todas las combinaciones posibles**: El numero de variables es $n = 4$ de modo combinaciones posible es $filas = 2^n = 2 ^ 4 = 16$:
   
    | # | $p$ | $q$ | $r$ | $s$ | $p \to q$ | $\neg q$ | $p \lor r$ | $r \to s$ | Premisas <br> $(p \to q)\land(\neg q)\land(p \lor r)\land(r \to s)$ | Conclusión <br> $s$ |
    |---:|---:|---:|---:|---:|---:|---:|---:|---:|:---:|:---:|
    | 1  | 0 | 0 | 0 | 0 |  |  |  |  |  |  |
    | 2  | 0 | 0 | 0 | 1 |  |  |  |  |  |  |
    | 3  | 0 | 0 | 1 | 0 |  |  |  |  |  |  |
    | 4  | 0 | 0 | 1 | 1 |  |  |  |  |  |  |
    | 5  | 0 | 1 | 0 | 0 |  |  |  |  |  |  |
    | 6  | 0 | 1 | 0 | 1 |  |  |  |  |  |  |
    | 7  | 0 | 1 | 1 | 0 |  |  |  |  |  |  |
    | 8  | 0 | 1 | 1 | 1 |  |  |  |  |  |  |
    | 9  | 1 | 0 | 0 | 0 |  |  |  |  |  |  |
    | 10 | 1 | 0 | 0 | 1 |  |  |  |  |  |  |
    | 11 | 1 | 0 | 1 | 0 |  |  |  |  |  |  |
    | 12 | 1 | 0 | 1 | 1 |  |  |  |  |  |  |
    | 13 | 1 | 1 | 0 | 0 |  |  |  |  |  |  |
    | 14 | 1 | 1 | 0 | 1 |  |  |  |  |  |  |
    | 15 | 1 | 1 | 1 | 0 |  |  |  |  |  |  |
    | 16 | 1 | 1 | 1 | 1 |  |  |  |  |  |  |
    
    
3. **Calcular el valor de cada premisa y de la conclusión en cada fila**:
   
    | # | $p$ | $q$ | $r$ | $s$ | $p \to q$ | $\neg q$ | $p \lor r$ | $r \to s$ | Premisas <br> $(p \to q)\land(\neg q)\land(p \lor r)\land(r \to s)$ | Conclusión <br> $s$ |
    |---:|---:|---:|---:|---:|---:|---:|---:|---:|:---:|:---:|
    | 1  | 0 | 0 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 |
    | 2  | 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 0 | 1 |
    | 3  | 0 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | 0 |
    | **4**  | **0** | **0** | **1** | **1** | **1** | **1** | **1** | **1** | **1** | **1** |
    | 5  | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 |
    | 6  | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1 |
    | 7  | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 0 | 0 | 0 |
    | 8  | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | 0 | 1 |
    | 9  | 1 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 0 | 0 |
    | 10 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 |
    | 11 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | 0 |
    | 12 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 1 | 0 | 1 |
    | 13 | 1 | 1 | 0 | 0 | 1 | 0 | 1 | 1 | 0 | 0 |
    | 14 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 |
    | 15 | 1 | 1 | 1 | 0 | 1 | 0 | 1 | 0 | 0 | 0 |
    | 16 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | 0 | 1 |

4. **Inspeccionar los renglones críticos para determinar la validez del argumento**: En la tabla anterior, la única fila donde la columna **Premisas** vale **1** es la **fila 4** (es decir, todas las premisas son verdaderas simultáneamente). En esa misma fila, la conclusión también vale **1** (es decir, $s$ es verdadera).  

   Por lo tanto, **no existe** un renglón crítico con premisas verdaderas y conclusión falsa, y el argumento es **válido**.  
   
   En términos del caso, Sherlock Holmes concluye que **“el mayordomo es cómplice”**.

En conclusión, validar con tablas de verdad consiste en evaluar **todos** los escenarios posibles para verificar que **no existe** ninguno en el que las premisas se cumplan y la conclusión falle. Por eso decimos que este método **no apela a la intuición**, sino a un criterio **formal, mecánico y verificable**.

### Validación mediante reglas de inferencia (enfoque axiomatico o sintactico)

La validación con tablas de verdad es un método **infalible**: revisa todos los escenarios posibles y comprueba que no existan renglones críticos donde la conclusión falle. Sin embargo, su principal desventaja es la **escalabilidad**: con $n$ variables proposicionales, la tabla tiene $2^n$ filas.

En otras palabras, el método semántico (basado en modelos) responde la pregunta:

> "¿El argumento es válido en **todos** los escenarios posibles?"

Debido al alto costo de emplear tablas de verdad, existe un método alternativo cuyo enfoque es el **sintáctico**. En este, en vez de evaluar el argumento en todos los modelos, construimos una **demostración** donde cada línea está justificada por una **regla válida**.

De manera similar a como empleamos **leyes de equivalencia** para transformar (y simplificar) expresiones lógicas, para **validar argumentos** de manera eficiente empleamos **reglas de inferencia**.


{: .def }
> **Definición**: Una **regla de inferencia** es un esquema de razonamiento **válido** que nos permite pasar de unas premisas a una conclusión de forma segura.

El uso de las **reglas de inferencia** (moldes) para *"construir un camino"* desde las Premisas hasta la Conclusión es conocido como **Prueba Formal** o **Demostración Deductiva**. Estas reglas no dicen *qué es verdadero en el mundo*, simplemente dicen qué pasos están **permitidos** para que una conclusión se siga **necesariamente** de lo anterior.

A continuación, se presentan las **reglas de inferencia** que vamos a usar. Asuma que todo lo que está sobre la línea son verdades que usted ya posee, y lo que está debajo es lo que tiene permiso de escribir como nueva verdad.

| Nombre | Regla (Esquema) | Descripción Intuitiva |
| :--- | :---: | :--- |
| **Modus Ponens (MP)** | $\begin{array}{l} p \to q \\\\ p \\\\ \hline \therefore\ q \end{array}$ | **Causa-Efecto:** Si se da la causa, ocurre el efecto. |
| **Modus Tollens (MT)** | $\begin{array}{l} p \to q \\\\ \neg q \\\\ \hline \therefore\ \neg p \end{array}$ | **Descarte:** Si no veo el efecto, no pudo haber ocurrido la causa. |
| **Silogismo Hipotético (SH)** | $\begin{array}{l} p \to q \\\\ q \to r \\\\ \hline \therefore\ p \to r \end{array}$ | **Cadena:** Si $p$ lleva a $q$ y $q$ lleva a $r$, entonces $p$ lleva a $r$. |
| **Silogismo Disyuntivo (SD)** | $\begin{array}{l} p \lor q \\\\ \neg p \\\\ \hline \therefore\ q \end{array}$ | **Eliminación:** Si tengo dos opciones y descarto una, me toca la otra. |
| **Simplificación (Simp)** | $\begin{array}{l} p \land q \\\\ \hline \therefore\ p \end{array}$ | **Extracción:** Si tengo todo, tengo una parte. |
| **Adición (Ad)** | $\begin{array}{l} p \\\\ \hline \therefore\ p \lor q \end{array}$ | **Generalización:** Si algo es verdad, esa cosa "o cualquier otra" también lo es. |
| **Conjunción (Conj)** | $\begin{array}{l} p \\\\ q \\\\ \hline \therefore\ p \land q \end{array}$ | **Fusión:** Puedo unir dos verdades independientes. |
| **Resolución (Res)** | $\begin{array}{l} p \lor q \\\\ \neg p \lor r \\\\ \hline \therefore\ q \lor r \end{array}$ | **Eliminación de una opción:** una cláusula contiene $p$ y otra contiene $\neg p$; al combinarse, "se elimina" esa variable y quedan las alternativas restantes ($q \lor r$). |
| **División por Casos** | $\begin{array}{l} p \lor q \\\\ p \to r \\\\ q \to r \\\\ \hline \therefore\ r \end{array}$ | **Todos los caminos llevan a Roma:** Si mis opciones son A o B, y ambas llevan al mismo resultado, el resultado es seguro. |

Para validar un argumento mediante reglas de inferencia listadas anteriormente se sugiere aplicar los siguientes pasos:
1. **Listar las Premisas**: Escriba numeradas todas las afirmaciones iniciales que le da el problema.
2. **Identificar la Meta**: Tenga clara cuál es la proposición conclusión a la que debe llegar.
3. **Reconocimiento de Patrones**: Busque entre sus premisas dos (o una) que encajen visualmente con alguna de las reglas de la tabla anterior.
4. **Derivación**: Aplique la regla y escriba la nueva proposición resultante en un nuevo renglón, indicando qué regla y qué líneas usó (Ej: "Modus Ponens en 1 y 3").
5. **Iteración**: Repita el proceso usando las nuevas líneas generadas hasta que obtenga la conclusión deseada (meta).

#### Ejemplo
{: .no_toc }

Retomemos nuevamente al **Caso del Zafiro Desaparecido**:

$$
\begin{array}{l}
p \rightarrow q \\
\neg q \\
p \lor r \\
r \rightarrow s \\
\hline
\therefore\ s
\end{array}
$$

La meta es derivar la conclusión $s$ (el mayordomo es cómplice) a partir de las premisas, justificando cada paso con una **regla de inferencia**.

A continuación se realiza a cabo la deducción formal (derivación paso a paso):

| # | Proposición | Justificación |
|---:|---|---|
| 1 | $p \to q$ | Premisa |
| 2 | $\neg q$ | Premisa |
| 3 | $p \lor r$ | Premisa |
| 4 | $r \to s$ | Premisa |
| 5 | $\neg p$ | **Modus Tollens (MT)** en 1 y 2 |
| 6 | $r$ | **Silogismo Disyuntivo (SD)** en 3 y 5 |
| 7 | $s$ | **Modus Ponens (MP)** en 4 y 6 |

Hemos obtenido $s$ a partir de las premisas aplicando únicamente reglas de inferencia válidas.  
Por tanto, el argumento es **válido**.

{: .note }
> Observe que esta demostración evita construir la tabla de verdad completa: en lugar de revisar $2^n$ escenarios, construimos una cadena corta de pasos justificados.

---

## Ejemplos de repaso

1. Dado el siguiente argumento:
   
    $$
    \begin{array}{l}
    p \rightarrow q \lor r \\
    q \rightarrow p \land r \\
    \hline
    \therefore\ p \rightarrow r
    \end{array}
    $$
    
    Determine la validez empleando el metodo basado en modelos (tablas de verdad).

2. Empleando el enfoque axiomatico, demuestre que el siguiente argumendo es valido:

    $$
    \bigl[p \land (p \to q) \land (s \lor r) \land (r \to \neg q)\bigr] \to (s \lor t)
    $$   

3. Demuestre que el siguiente argumento lógico es valido:
   
   $$
   \begin{array}{l}
   (\neg p \lor q) \to r \\
   r \to (s \lor t) \\
   \neg s \land \neg u \\
   \neg u \to \neg t \\
   \hline
   \therefore\ p
   \end{array}
   $$

4. Dado el siguiente argumento:

   > "Si la ley no fue aprobada, entonces la constitución del país queda sin modificaciones. Si la constitución del país queda sin modificaciones no se puede elegir nuevos diputados. O se eligen nuevos diputados o el informe del presidente del país se retrasará. El informe no se retrasó un mes. Por lo que la ley fue aprobada".

   Expresarlo en lenguaje formal y determinar su validez.

5. Dada la siguiente información que:
   
   > Milhouse estaba a punto de salir para la escuela en la mañana y descubrió que no tenia puestas sus gafas. Si se sabe que los siguientes enunciados son verdaderos:
   > * Si Milhouse estaba leyendo el periódico en la cocina, entonces, las gafas estaban sobre la mesa de la cocina.
   > * Si las gafas estaban sobre la mesa de la cocina, entonces los Milhouse los vio al desayunar.
   > * Milhouse no ha visto las gafas en el desayuno.
   > * Milhouse estaba leyendo el periódico en la sala o estaba leyendo el periódico en la cocina.
   > * Si Milhouse estaba leyendo el periódico en la sala entonces, sus gafas estaban sobre la mesa del café.

   A partir de la información anterior: ¿Dónde estaban los lentes de Milhouse?
   
**Solución**:

1. Recordemos el argumento sobre el cual debemos demostrar validez:

    $$
    \begin{array}{l}
    p \rightarrow q \lor \neg r \\
    q \rightarrow p \land r \\
    \hline
    \therefore\ p \rightarrow r
    \end{array}
    $$
   
    **Solución empleando tablas de verdad**:
   
    | # | $p$ | $q$ | $r$ | $\neg r$ | $q \lor \neg r$ | $p \to (q \lor \neg r)$ | $p \land r$ | $q \to (p \land r)$ | Premisas <br> $(p \to (q \lor \neg r))\land(q \to (p \land r))$ | Conclusión <br> $p \to r$ |
    |---:|---:|---:|---:|---:|---:|---:|---:|---:|:---:|:---:|
    | **1** | **0** | **0** | **0** | **1** | **1** | **1** | **0** | **1** | **1** | **1** |
    | **2** | **0** | **0** | **1** | **0** | **0** | **1** | **0** | **1** | **1** | **1** |
    | 3 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 |
    | 4 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | 1 |
    | **5** | **1** | **0** | **0** | **1** | **1** | **1** | **0** | **1** | **1** | **0** |
    | 6 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | 1 |
    | 7 | 1 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 |
    | **8** | **1** | **1** | **1** | **0** | **1** | **1** | **1** | **1** | **1** | **1** |
     
     > **Conclusión**: el argumento es **inválido**, porque existe un renglón crítico para el cual las premisas arrojan una conclución cuyo valor es falso (fila 5).

2. Para resolver este ejercicio primero expresemos el argumento en notación estandar:
   
   $$
   \begin{array}{l}
   p\\
   p \to q\\
   s \lor r\\
   r \to \neg q\\
   \hline
   \therefore\ s \lor t
   \end{array}
   $$
   
   A continuación se demuestra la validez del argumento mediante el uso de reglas de inferencia:

   | Paso | Proposición | Justificación |
   | :---: | :--- | :--- |
   | **1** | $p$ | Premisa |
   | **2** | $p \to q$ | Premisa |
   | **3** | $s \lor r$ | Premisa |
   | **4** | $r \to \neg q$ | Premisa |
   | **5** | **$q$** | **Modus Ponens** en 1 y 2. |
   | **6** | **$\neg r$** | **Modus Tollens** en 4 y 5. |
   | **7** | **$s$** | **Silogismo Disyuntivo** en 3 y 6. |
   | **8** | **$s \lor t$** | **Adición** en 7. |

3. Recordemos nuevamente el argumento a demostrar:

   $$
   \begin{array}{l}
   (\neg p \lor q) \to r \\
   r \to (s \lor t) \\
   \neg s \land \neg u \\
   \neg u \to \neg t \\
   \hline
   \therefore\ p
   \end{array}
   $$

   A continuación, se muestra el procedimiento de deducción logica paso a paso:

   | Paso | Proposición | Justificación |
   | :---: | :--- | :--- |
   | **1** | $(\neg p \lor q) \to r$ | Premisa |
   | **2** | $r \to (s \lor t)$ | Premisa |
   | **3** | $\neg s \land \neg u$ | Premisa |
   | **4** | $\neg u \to \neg t$ | Premisa |
   | **5** | **$\neg u$** | **Simplificación** en 3. |
   | **6** | **$\neg t$** | **Modus Ponens** en 4 y 5. |
   | **7** | **$\neg s$** | **Simplificación** en 3. |
   | **8** | **$\neg s \land \neg t$** | **Conjunción** en 7 y 6. |
   | **9** | **$\neg (s \lor t)$** | **Ley de De Morgan** en 8. |
   | **10** | **$\neg r$** | **Modus Tollens** en 2 y 9. |
   | **11** | **$\neg (\neg p \lor q)$** | **Modus Tollens** en 1 y 10. |   
   | **12** | **$\neg( \neg p) \land \neg q$** | **Ley de De Morgan** en 11. |
   | **13** | **$p \land \neg q$** | **Doble negación** en 12. |
   | **14** | **$p$** | **Simplificación** en 13. |   

4. Retomemos el enunciado del argumento del problema dado en lenguaje natural:
   
   > "Si la ley no fue aprobada, entonces la constitución del país queda sin modificaciones. Si la constitución del país queda sin modificaciones no se puede elegir nuevos diputados. O se eligen nuevos diputados o el informe del presidente del país se retrasará. El informe no se retrasó un mes. **<u>Por lo que</u>** la ley fue aprobada".

   Si observamos el enunciado, la secuencia de palabras **Por lo que** como un conector que une dos oraciones, donde la segunda es una consecuencia. De modo que este nos permite separar las premisas de la conclución:
   * **Premisas**:
     *  ***Si*** la ley ***<u>no</u>*** fue aprobada, ***entonces*** la constitución del país queda sin modificaciones.
     *  ***Si*** la constitución del país queda sin modificaciones ***,*** ***<u>no</u>*** se puede elegir nuevos diputados.
     *  ***O*** se eligen nuevos diputados ***o*** el informe del presidente del país se retrasará.
     *  El informe ***<u>no</u>*** se retrasó un mes.
   * **Conclusión**:
     *  La ley fue aprobada.
   
   Una vez identificados los elementos del argumento, procedemos a identificar las proposiciones simples analizando cada uno de los enunciados anteriores (en los cuales se resaltaron los conectores)
   * **Proposiciones simples**:
     *  **$l$**: La ley fue aprobada.
     *  **$c$**: La constitución del país quedará sin modificaciones.
     *  **$p$**: Se pueden elegir nuevos diputados.
     *  **$i$**: El informe del presidente se retrasará un mes.
   
   Ahora, al traducir las premisas y la conclusión del lenguaje natural, al lenguaje formal tenemos:

   $$
   \begin{array}{l}
   \neg l \to c \\
   c \to \neg d \\
   d \lor i \\
   \neg i \\
   \hline
   \therefore\ l
   \end{array}
   $$
   
   A continuación, muestra el proceso deductivo para comprobar la validez del argumento:

   | Paso | Proposición | Justificación |
   | :---: | :--- | :--- |
   | **1** | $\neg l \to c$ | Premisa |
   | **2** | $c \to \neg d$ | Premisa |
   | **3** | $d \lor i$ | Premisa |
   | **4** | $\neg i$ | Premisa |
   | **5** | **$d$** | **Silogismo Disyuntivo** en 3 y 4. |
   | **6** | **$\neg c$** | **Modus Tollens** en 2 y 5. |
   | **7** | **$\neg (\neg l)$** | **Modus Tollens** en 1 y 6. |
   | **8** | **$l$** | **Doble Negación** en 7. |

5. Retomemos nuevamente las premisas del enunciado:
   * ***Si*** Milhouse estaba leyendo el periódico en la cocina, ***entonces***, las gafas estaban sobre la mesa de la cocina.
   * ***Si*** las gafas estaban sobre la mesa de la cocina, ***entonces*** los Milhouse los vio al desayunar.
   * Milhouse ***<u>no</u>*** ha visto las gafas en el desayuno.
   * Milhouse estaba leyendo el periódico en la sala ***o*** estaba leyendo el periódico en la cocina.
   * ***Si*** Milhouse estaba leyendo el periódico en la sala ***entonces***, sus gafas estaban sobre la mesa de café.
   
   A partir de las premisas anteriores podemos obtener las **proposiciones simples** las cuales definimos a continuación:
   * **$RK$**: Milhouse estaba leyendo el periódico en la cocina.
   * **$GK$**: Las gafas de Milhouse estaban sobre la mesa de la cocina.
   * **$SB$**: Milhouse vio las gafas en el desayuno
   * **$LR$**: Milhouse estaba leyendo el periódico en la sala.
   * **$GC$**: Las gafas de Milhouse estaban sobre la mesa de café.
   
   El argumento en lenguaje formal queda de la siguiente manera:

   $$
   \begin{array}{l}
   RK \to GK \\
   GK \to SB \\
   \neg SB \\
   LR \lor RK \\
   LR \to GC \\
   \hline
   \therefore\ ?
   \end{array}
   $$

   Donde la respuesta a la pregunta ¿Dónde estaban los lentes de Milhouse? teniendo en cuenta las premisas puede ser que las gafas esten sobre la mesa de la cocina ($GK$) o sobre la mesa de cafe ($GC$). A continuación se muestra la deducción realizada:

   | Paso | Proposición | Justificación |
   | :---: | :--- | :--- |
   | **1** | $RK \to GK$ | Premisa |
   | **2** | $GK \to SB$ | Premisa |
   | **3** | $\neg SB$ | Premisa |
   | **4** | $LR \lor RK$ | Premisa |
   | **5** | $LR \to GC$ | Premisa |
   | **6** | **$\neg GK$** | **Modus Tollens** en 2 y 3. |
   | **7** | **$\neg RK$** | **Modus Tollens** en 1 y 6. |
   | **8** | **$LR$** | **Silogismo Disyuntivo** en 4 y 7. |
   | **9** | **$GC$** | **Modus Ponens** en 5 y 8. |
    
   De modo que la respuesta a la pregunta era que las gafas de Millhouse estaban sobre la mesa de café.

---

## Resultados de aprendizaje

Al finalizar esta clase, usted será capaz de:
* Distinguir sin ambigüedades entre la verdad de una proposición y la validez de un argumento.
* Formalizar argumentos en lenguaje natural traduciéndolos a notación lógica estándar.
* Demostrar la validez de un argumento utilizando reglas de inferencia paso a paso.
* Identificar cuándo utilizar un enfoque semántico (tablas de verdad) frente a un enfoque sintáctico (reglas de inferencia).

---

## Ejercicios de autoevaluación (Retos)

Ponga a prueba sus habilidades de detective lógico. Intente resolverlos antes de desplegar las respuestas.

### Reto 1: ¿Válido o Inválido? (Método de Tablas)
Analice el siguiente argumento pequeño. Construya su tabla de verdad, identifique las **filas críticas** y determine si es válido.

> **Argumento:**
> 1. $p \to q$
> 2. $q$
> 3. $\therefore p$

### Reto 2: Derivación Formal (Método de Reglas)
Demuestre paso a paso que el siguiente argumento es válido llegando a la conclusión $t$.

**Premisas:**
1. $r \to s$
2. $r \land q$
3. $s \to t$

**Conclusión a demostrar:** $\vdash t$

### Reto 3: El misterio del servidor caído
Traduzca y demuestre la validez del siguiente argumento técnico:
* "Si el tráfico es alto ($A$), entonces el servidor se calienta ($C$)."
* "El servidor no se calienta ($\neg C$) o se activa la alarma ($L$)."
* "El tráfico es alto ($A$)."
* **Conclusión:** ¿Se activa la alarma ($L$)?

---

## Sección de Respuestas
{: .no_toc }

<details markdown="1">
  <summary><b>Haga clic aquí para ver las soluciones y justificaciones</b></summary>
<br>

### Solución Reto 1: La Falacia de Afirmación del Consecuente
Construimos la tabla de verdad:

| $p$ | $q$ | $p \to q$ (P1) | $q$ (P2) | $p$ (Concl) | Análisis |
| :-: | :-: | :-: | :-: | :-: | :--- |
| V | V | **V** | **V** | **V** | Fila Crítica (Todo OK) |
| V | F | F | F | V | No es fila crítica |
| F | V | **V** | **V** | **F** | **¡Fila Crítica con Conclusión Falsa!** |
| F | F | V | F | F | No es fila crítica |

**Veredicto:** El argumento es **INVÁLIDO**. Note la tercera fila: las premisas son verdaderas, pero la conclusión es falsa. Esto se conoce como la *Falacia de afirmación del consecuente*.

### Solución Reto 2: Derivación Formal
| Paso | Proposición | Justificación |
| :---: | :--- | :--- |
| 1 | $r \to s$ | Premisa |
| 2 | $r \land q$ | Premisa |
| 3 | $s \to t$ | Premisa |
| 4 | $r$ | **Simplificación** en 2 |
| 5 | $s$ | **Modus Ponens** en 1 y 4 |
| 6 | $t$ | **Modus Ponens** en 3 y 5 |

### Solución Reto 3: El servidor caído
**Formalización:**
1. $A \to C$
2. $\neg C \lor L$
3. $A$
**Conclusión:** $L$

**Demostración:**
| Paso | Proposición | Justificación |
| :---: | :--- | :--- |
| 1 | $A \to C$ | Premisa 1 |
| 2 | $A$ | Premisa 3 |
| 3 | $C$ | **Modus Ponens** en 1 y 2 |
| 4 | $\neg(\neg C)$ | **Doble Negación** en 3 (Truco para ver el silogismo) |
| 5 | $\neg C \lor L$ | Premisa 2 |
| 6 | $L$ | **Silogismo Disyuntivo** en 5 y 4 |

</details>