# Agentes inteligentes

- Un agente es toda cosa que puede ser vista como algo que percibe el *ambiente* a través de _sensores_ y realiza acciones a través de _actuadores_.
- El término ==percepción== (_percept_) es usado para referirse al estado en el que se encuentren todas las entradas de un agente en un momento determinado, y la ==secuencia de percepción== (_percept sequence_) es todo el conjunto de información que el agente ha recabado desde el momento en que comenzó a funcionar.
	> Las decisiones de un agente generalemente solo pueden depender de la información que este ya dispone
- La ==función del agente== es la abstracción matemática que describe perfectamente el comportamiento de un agente, es decir, esta función mapea cualquier información de entrada que el agente tenga a una acción apropiada.
- El ==programa del agente== hace alusión a la implementación que un desarrollador codifica en el hardware del agente.

## Racionalidad

### Agentes racionales

En palabras generales, podríamos decir que un agente racional es aquel siempre hace las cosas bien. ¿Cómo es que podemos decidir si el comportamiento de este es bueno? Midiendo las consecuencias de las acciones que el agente realice. Si las consecuencias fueron bajas (_maximizing utility function_) [ver video](https://www.youtube.com/watch?v=3TYT1QfdfsM&t=960s) se dice que el desempeño del agente fue bueno.

> Para cada posible secuencia de percepciones, un agente racional deberá siempre escoger la acción (o el conjunto de estas) que maximicen la medición de su desempeño, dada la evidencia que tiene de sus percepciones y del conocimiento base que su desarrollador le haya dado.

Leerlo en la semana: AI: A modern approach

Algoritmos de búsqueda

Agentes racionales: entidad que percibe y actua en un medio

$f: P^{*} \rightarrow L$

army of none

