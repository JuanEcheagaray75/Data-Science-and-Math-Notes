# Logical Agents

- The central component of a knowledge based agent is its _knowledge base_
- A knowledge base is a set of _sentences_
- Each sentence is then expressed in a language called a _knowledge representation language_
- We can say a sentence is an _axiom_ when it is given, meaning it did not derive from other sentences

To add new sentences to the KB and to query what is know, we perform 2 operations, commonly referred to as _TELL_ and _ASK_, both operations may involve **inference**. The agent maintains a KB which might initially contain a set of axioms, we call this initial knowledge the _background knowledge_.

## How a logical agent works

Each time the agent program is called it performs 3 actions:

1. Tell the KB what it perceives
2. Ask the KB what action it should perform
   1. To answer this query, some extensive reasoning may occur, ex. understanding the current state of the world, what are the possible outcomes of the available action sequences
3. Tell the KB which action it performed, and then perform said action

The details of the representation language are encapsulated in 3 different functions:

1. MAKE-PERCEPT-SENTENCE: to construct a sentence that asserts what the agent perceived at a certain time
2. MAKE-ACTION-QUERY: to construct a sentence that asks the KB which action should be chosen at the current time
3. MAKE-ACTION-SENTENCE: to construct a sentence that asserts the chosen action was executed

| KB Agent |
| ---- |
| ![[Pasted image 20220517094550.png]] |

> Need further study of knowledge level and implementation level

## Building a KB Agent

There are 2 approaches to building an agent's KB:

- Declarative: the agent designer TELLS sentences one by one until the agent knows how to operate in its environment
- Procedural: the desired behavior (and sentences) are encoded directly as program code

> Note that in each case for which the agent draws a conclusion from the available information, that conclusion is _guaranteed_ to be correct if the available information is correct

## Afterthoughts

1. ¿Qué es un Sistema Basado en
2. ¿Qué componentes tiene un SBC?
3. ¿Cuáles son las fuentes de conocimiento para un SBC?
4. ¿Cuáles son los dominios de aplicación de SBCs?
5. ¿Cuáles son los retos en el diseños de un SBC?
