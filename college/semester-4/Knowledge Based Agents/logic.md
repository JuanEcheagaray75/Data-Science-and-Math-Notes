# Logic

- [Logic](#logic)
  - [Model](#model)
  - [Entailment](#entailment)
  - [Inference algorithm](#inference-algorithm)
    - [Sound](#sound)
    - [Completeness](#completeness)
    - [Grounding](#grounding)

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

A good inference algorithm must possess certain properties:

### Sound

> An inference algorithm that derives only entailed sentences

Often referred to as _truth preserving_. An unsound inference procedure makes things up as it goes along, it announces the discovery of nonexistent needles

### Completeness

> An inference algorithm is complete if it can derive any sentence that is entailed

For finite knowledge bases it may seem pretty easy to define a procedure that systematically examines the database to decide whether a sentence is entailed or not, but for some applications, the knowledge base may be infinite, and there is no easy way to perform the afore mentioned procedure. However, there exist some inference algorithms that are expressive enough to handle large knowledge bases.

### Grounding

> The connection between logical reasoning processes and the real environment in which the agent exists

How can we know that the knowledge base holds true in the real world? Such a philosophical question is far beyond the reach of this chapter, but a simple answer could be that the agent's sensors perform the needed connection. If we have an agent with a well performing light sensor, we know that there is light in the real world whenever this sensor fires.
