# Logic

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
   \text{Triangle}(a) \land \text{Triangle}(c) \Leftrightarrow (\text{Big}(a) \lor \text{Big}(c))
   $$
4. a es un triángulo, pero c no es grande.
   $$
   \text{Triangle}(a) \land \neg \text{Big}(c)
   $$
5. Si c es pequeño y d es un pentágono, entonces d no es ni grande ni pequeño.
6. c es mediano solo si ninguno de d, e y f son cuadrados.
7. d es un pentágono pequeño a menos que a sea pequeño.
8. e es grande si es un hecho que d es grande si y sólo si f lo es.
9. d y e son del mismo tamaño.
10. d y e tienen la misma forma.
11. f es un cuadrado o un pentágono, si es grande.
12. c es más grande que e solo si b es más grande que c.
