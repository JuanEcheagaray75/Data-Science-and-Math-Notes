# Logic

- [Logic](#logic)
  - [Model](#model)
  - [Entailment](#entailment)
  - [Inference algorithm](#inference-algorithm)
  - [Examples](#examples)
    - [Propositional Logic](#propositional-logic)
    - [Tarski's World](#tarskis-world)
    - [For Tarski's World](#for-tarskis-world)

> We develop logic as a general class of representations to support knowledge based agents

- The _syntax_ of a language specifies all the sentences that are well formed
- The _semantics_ of a language defines the truth of each sentence with respect to each _possible world_

## Model

When in need of rigor, the term **model** is preferred over _possible world_. Possible worlds might be thought of as potentially real environments that an agent may or may not be in, on the other hand, **models** are mathematical abstractions that determine the truth or falsehood of _every_ relevant sentence.

If a sentence $\alpha$ is true in model $m$, we say that $m$ satisfies $\alpha$, or sometimes, $m$ **is a model of** $\alpha$. To denote the set of all possible models of $\alpha$ we use the notation $M(\alpha)$.

## Entailment

> The idea that a sentence follows logically from another sentence

In mathematical notation, to say that $\alpha$ entails $\beta$ we write:

$$ a \models a $$

The formal definition of entailment is: $a \models b$ if and only if, in every model in which $\alpha$ is true, $\beta$ is also true, in mathematical notation:

$$ a \models b \Leftrightarrow M(a) \subseteq M(b) $$

The definition of entailment can then be applied to carry out _logical inference_. **Model checking** makes reference to enumerating all possible worlds to check if $\alpha$ is true in all models in which the knowledge base is also true, in mathematical notation $M(KB) \subseteq M(A)$

## Inference algorithm

## Examples

### Propositional Logic

1. Juan fue a la escuela y María fue a la escuela.
    $$
    p: \text{Juan fue a la escuela} \\
    q: \text{María fue a la escuela} \\
    p \land q
    $$
2. No es el caso que me guste la mantequilla de cacahuate y la mermelada.
    $$
    p: \text{Me gusta la mantequilla de cacahuate} \\
    q: \text{Me gusta la mermelada} \\
    \neg (p \land q)
    $$
3. No me gusta la mantequilla de cacahuate y no me gusta la mermelada.
    $$
    p: \text{Me gusta la mantequilla de cacahuate} \\
    q: \text{Me gusta la mermelada} \\
    \neg p \land \neg q
    $$
4. Si los impuestos suben, aumentará la inflación.
    $$
    p: \text{Los impuestos suben} \\
    q: \text{Aumentará la inflación} \\
    p \Rightarrow q
    $$
5. Obtener una A en el examen final es una condición necesaria para obtener una A en la clase.
    $$
    p: \text{Obtener una A en el final} \\
    q: \text{Obtener una A en la clase} \\
    p \Rightarrow q
    $$
6. Obtener una B en todos los exámenes es una condición suficiente para obtener una B en la clase.
    $$
    p: \text{Obtener una B en todos los exámenes} \\
    q: \text{Obtener una B en la clase} \\
    p \Leftrightarrow q
    $$
7. No es el caso de que Tomás y Ricardo trabajen hasta tarde o que Enrique llame para reportarse enfermo.
    $$
    p: \text{Tomás trabaja hasta tarde} \\
    q: \text{Ricardo trabaja hasta tarde} \\
    j: \text{Enrique llama para reportarse enfermo} \\
    \neg (p \land q) \land j
    $$
8. Irán suministrará armas a Siria solo si Siria ayuda a Hezbollah.
    $$
    p: \text{Irán suministra armas a Siria} \\
    q: \text{Siria ayuda a Hezbollah} \\
    q \Rightarrow p
    $$
9. Julia necesita un paracaídas si y solo si planea saltar del avión.
    $$
    p: \text{Julia necesita un paracaídas} \\
    q: \text{planea saltar del avión} \\
    p \Leftrightarrow q
    $$
10. Si no tengo suficiente dinero en efectivo, puedo ir al cine o a comer fuera, pero no ambos.
    $$
    p: \text{Tengo suficiente dinero en efectivo} \\
    q: \text{Ir al cine} \\
    j: \text{Comer fuera} \\
    p \Rightarrow (q \oplus j)
    $$

### Tarski's World

1. Si a es un triángulo, entonces b también es un triángulo.
    $$
    \text{Triangle}(a) \Rightarrow \text{Triangle}(b)
    $$
2. c es un triángulo si b lo es.
    $$
    \text{Triangle}(b) \Rightarrow \text{Triangle}(c)
    $$
3. a y c son ambos triángulos solo si al menos uno de ellos es grande.
    $$
    \text{Triangle}(a) \land \text{Triangle}(c) \Leftrightarrow (\text{Large}(a) \lor \text{Large}(c))
    $$
4. a es un triángulo, pero c no es grande.
    $$
    \text{Triangle}(a) \land \neg \text{Large}(c)
    $$
5. Si c es pequeño y d es un pentágono, entonces d no es ni grande ni pequeño.
    $$
    (\text{Small(c)} \land \text{Pentagon(d)}) \Rightarrow (\neg \text{Large(d)} \land \neg \text{Small(d)})
    $$
6. c es mediano solo si ninguno de d, e y f son cuadrados.
    $$
    \text{Medium(c)} \Rightarrow (\neg \text{Square(d)} \land \neg \text{Square(e)} \land \neg \text{Square(f)})
    $$
7. d es un pentágono pequeño a menos que a sea pequeño.
    $$
    (\text{Pentagon(d)} \land \text{Small(d)}) \Rightarrow \neg \text{Small(a)}
    $$
8. e es grande si es un hecho que d es grande si y sólo si f lo es.
    $$
    (\text{Large(d)} \Rightarrow \text{Large(e)}) \Leftrightarrow \text{Large(f)}
    $$
9. d y e son del mismo tamaño.
    $$
    \text{SameSize(d, e)}
    $$
10. d y e tienen la misma forma.
    $$
    (\text{Triangle(d)} \land \text{Triangle(e)}) \lor (\text{Square(d)} \land \text{Square(e)}) \lor (\text{Pentagon(d)} \land \text{Pentagon(e)})
    $$
11. f es un cuadrado o un pentágono, si es grande.
    $$
    \text{Large(f)} \Rightarrow (\text{Square(f)} \lor \text{Pentagon(f)})
    $$
12. c es más grande que e solo si b es más grande que c.
    $$
    \text{Smaller(e,c)} \Rightarrow \text{Smaller(c, b)}
    $$

### For Tarski's World

```text
Triangle(a) => Triangle(b)
Triangle(b) => Triangle(c)
Triangle(a) /\ Triangle(c) <=> (Large(a) \/ Large(c))
Triangle(a) /\ ~Large(c)
(Small(c) /\ Pentagon(d)) => (~Large(d) /\ Small(d))
Medium(c) => (~Square(d) /\ ~Square(e) /\ ~Square(f))
(Pentagon(d) /\ Small(d)) => ~Small(a)
(Large(d) => Large(e)) <=> Large(f)
SameSize(d,e)
(Triangle(d) /\ Triangle(e)) \/ (Square(d) /\ Square(e)) \/ (Pentagon(d) /\ Pentagon(e))
Large(f) => (Square(f) \/ Pentagon(f))
Smaller(e,c) => Smaller(c,b)
```
