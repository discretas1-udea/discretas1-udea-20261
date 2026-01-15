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

**ESTAS SON LAS NOTAS DE CLASE ORIGINALES**

En la clase anterior aprendimos a simplificar expresiones usando axiomas de equivalencia ($A \equiv B$). Hoy daremos un paso más allá: no solo queremos saber si dos cosas son iguales, queremos saber si **una conclusión se sigue necesariamente de unas premisas**.

Entramos al corazón de la lógica matemática: la **Argumentación**.


## Hook: En seguridad, “casi siempre” es lo mismo que “inseguro”
{: .no_toc }

En ciberseguridad no existe la frase “es seguro en el 99% de los casos”.  
Si existe **un solo escenario** en el que un atacante entra, el sistema es vulnerable.

Ese es exactamente el corazón de la **validez** en lógica:

- Un argumento es **inválido** si existe **un solo caso** donde las premisas son verdaderas y la conclusión es falsa.
- Un argumento es **válido** si **no existe** ese caso.

> Hoy veremos dos formas de manejar esa garantía:
> - **Tablas/modelos:** buscar sistemáticamente ese “caso atacante” (contraejemplo).
> - **Reglas de inferencia:** construir una prueba paso a paso donde la conclusión queda asegurada.

---

## Objetivos de la clase
{: .no_toc }

Al finalizar esta sesión usted será capaz de:

1. Distinguir **verdad**, **tautología** y **validez**.
2. Formalizar un **argumento** (premisas/conclusión) en notación simbólica.
3. Probar validez por dos rutas:
   - (A) **Enfoque semántico:** tablas de verdad (modelos).
   - (B) **Enfoque sintáctico:** reglas de inferencia (derivación).
4. Comparar métodos y concluir **cuándo conviene usar cada uno**.

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







En la **Clase 04** aprendimos a transformar proposiciones usando equivalencias (sin evaluar casos),
como se simplifica un polinomio sin reemplazar $x$ por números.

Hoy aprovechamos esa idea, pero el objeto cambia:

- En Clase 04 el foco era una **proposición** ($P \equiv Q$).
- Hoy el foco es un **argumento** (premisas $\Rightarrow$ conclusión).



---

## 2. Verdad vs validez (sin confundir conceptos)

### 2.1 Verdad (depende del caso)
Una proposición puede ser verdadera o falsa **según el escenario** (asignación de valores).

### 2.2 Tautología (verdadera en todos los casos)
Una proposición $P$ es una tautología si $P \equiv V$.

### 2.3 Validez (propiedad de argumentos)
Un argumento:

- Premisas: $P_1, P_2, \dots, P_n$
- Conclusión: $C$

es **válido** si es imposible que todas las premisas sean verdaderas y la conclusión sea falsa.

---

## 3. Vocabulario operativo (lo usaremos todo el tiempo)
{: .no_toc }

- **Caso/Escenario:** una asignación de valores a las variables ($p=V$, $q=F$, ...).
- **Fila crítica:** un caso (fila de tabla) donde **todas las premisas** valen $V$.
- **Contraejemplo:** una fila crítica donde la **conclusión** vale $F$.

> **Regla de oro:**  
> Un argumento es **inválido** si existe al menos un **contraejemplo**.  
> Un argumento es **válido** si **no existe** ningún contraejemplo.

**Chequeo rápido:**  
¿Qué debe cumplirse para que una fila sea “crítica”?  
*(Respuesta esperada: premisas = V.)*

---

## 4. Dos caminos para una misma garantía

| Enfoque | ¿Qué hace? | ¿Qué intenta encontrar? | Resultado típico |
|---|---|---|---|
| **Tablas (modelos)** | Explora escenarios | Un **contraejemplo** | Si lo encuentra ⇒ inválido |
| **Reglas (derivación)** | Encadena pasos válidos | Una **prueba** hacia $C$ | Si la construye ⇒ válido |

---

## 4.5 De argumento a una sola fórmula (el puente con Clase 04)
{: .no_toc }

En Clase 04 trabajamos con equivalencias del tipo $P \equiv Q$ (reescritura sin cambiar significado).
Hoy vamos a usar esa misma idea para transformar un **argumento** en una **fórmula única**.

Sea un argumento con premisas $P_1, P_2, \dots, P_n$ y conclusión $C$:

$$
P_1,\ P_2,\ \dots,\ P_n \ \therefore\ C
$$

### Forma 1: Condicional del argumento

Agrupamos premisas con $\land$ y construimos un condicional:

$$
(P_1 \land P_2 \land \cdots \land P_n) \to C
$$

**Criterio:**  
El argumento es **válido** si y solo si esa fórmula es una **tautología**.

> Intuición: si todas las premisas son verdaderas, entonces la conclusión no puede fallar.

### Forma 2: Búsqueda de contraejemplo (fila crítica)

La forma anterior se conecta con el método de tablas así:

- Una **fila crítica** es una fila donde $(P_1 \land \cdots \land P_n)=V$.
- Un **contraejemplo** ocurre si además $C=F$.
- Equivalentemente, un contraejemplo es una fila donde
  $(P_1 \land \cdots \land P_n)\to C = F$.

**Chequeo rápido:**  
¿Cuándo un condicional $A \to B$ es falso?  
*(Respuesta esperada: cuando $A=V$ y $B=F$.)*

---

## 5. Ruta A: Validez con tablas (enfoque basado en modelos)

### Procedimiento (búsqueda de fila crítica)

1. Identifique las variables atómicas.
2. Construya la tabla (o columnas mínimas necesarias).
3. Evalúe premisas y conclusión.
4. Marque filas críticas: $(P_1 \land \cdots \land P_n)=V$.
5. Si alguna fila crítica tiene $C=F$, hay contraejemplo ⇒ argumento inválido.

---

## 6. Ruta B: Validez con reglas (enfoque sintáctico)

### Plantilla de demostración (estándar)

| Línea | Enunciado | Regla | Referencias |
|---:|---|---|---|
| 1 | (premisa) | Premisa | — |
| 2 | (premisa) | Premisa | — |
| ... | ... | ... | ... |
| k | $C$ | (regla) | (líneas usadas) |

> Idea clave: si cada paso es correcto, toda la cadena lo es.

---

## 7. Kit mínimo de reglas de inferencia (las más productivas)

| Regla | Esquema |
|---|---|
| Modus Ponens (MP) | $p \to q,\ p \ \therefore q$ |
| Modus Tollens (MT) | $p \to q,\ \neg q \ \therefore \neg p$ |
| Silogismo disyuntivo (SD) | $p \lor q,\ \neg p\ \therefore q$ |
| Simplificación (Simp) | $p \land q\ \therefore p$ |
| Conjunción (Conj) | $p,\ q\ \therefore p \land q$ |

---

## 8. Un mismo argumento, dos métodos (comparación directa)

Usaremos este argumento:

1. $p \lor q$
2. $\neg p$
∴ $q$

### 8.1 Método A: tablas (buscando contraejemplo)

**Pregunta guía:**  
¿Puede existir un escenario donde $(p \lor q)=V$ y $\neg p=V$, pero $q=F$?

- Si $q=F$, para que $(p \lor q)=V$ tendría que ocurrir $p=V$.
- Pero $\neg p=V$ exige $p=F$.

Contradicción en el escenario: no puede existir ese caso.  
**No hay contraejemplo ⇒ el argumento es válido.**

*(En clase puedes mostrar la mini-tabla de 2 variables solo para confirmar.)*

### 8.2 Método B: derivación (reglas)

| Línea | Enunciado | Regla | Referencias |
|---:|---|---|---|
| 1 | $p \lor q$ | Premisa | — |
| 2 | $\neg p$ | Premisa | — |
| 3 | $q$ | SD | (1,2) |

**Conclusión:** el argumento es válido (hay derivación).

---

## 9. Conclusiones prácticas: ¿cuándo usar cada enfoque?
- **Tablas**: pocas variables, quiero detectar contraejemplos rápido.
- **Derivación**: muchas variables, quiero una prueba formal clara.
- **Equivalencias (Clase 04)**: me ayudan a *reescribir* premisas/conclusión para que el argumento sea más manejable.

---

## 10. Puente a la Clase 06: demostración directa
Hoy demostramos **validez de argumentos**.

En la **Clase 06** cambia el objeto:
- ya no probaremos “premisas ⇒ conclusión”,
- sino **enunciados matemáticos** del tipo “Si ..., entonces ...”.

La herramienta mental que se mantiene es:

> Una demostración es una secuencia de pasos justificados.  
> En la demostración directa, partimos de las **hipótesis** y llegamos a la **tesis**.

---

## Ejercicios de autoevaluación (Retos)

### Reto 1 (Tablas / contraejemplo)

Determine si el argumento es válido:
1. $p \to q$
2. $q$
∴ $p$

### Reto 2 (Derivación)

Demuestre validez:
1. $p \to q$
2. $\neg q$
∴ $\neg p$

### Reto 3 (Comparación)

Para cada caso, indique qué método usaría y por qué:
- (a) 2 variables.
- (b) 6 variables.

---

## Sección de respuestas
{: .no_toc }

<details markdown="1">
  <summary><b>Haga clic aquí para ver una guía (sin el desarrollo completo)</b></summary>
<br>

- **Reto 1:** intente encontrar un escenario con $p=F$ y $q=V$. Si las premisas quedan V y la conclusión F, hay contraejemplo ⇒ inválido.
- **Reto 2:** patrón de **Modus Tollens (MT)**.
- **Reto 3:** compare costo $2^n$ vs número de pasos de una derivación.

</details>
