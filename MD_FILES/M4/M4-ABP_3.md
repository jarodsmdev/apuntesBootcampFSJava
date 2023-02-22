# M4-ABP_3

---

## Planteamiento de Problema

Una compañía de seguros ha elaborado una sesión de lluvia de ideas, en las que se han planteado ciertas observaciones que se desea analizar prontamente. A fin de ordenar las ideas, se ha solicitado:

1. Formalizar la frase.
2. ¿Es posible representar el resultado anterior como un algoritm? De ser posible, transfórmelo a código Java atomizando las frases y asignando un valor de verdad; en caso contrario, justifique por qué no se puede hacer.

**La frase en cuestión es:**
*“Si un trabajador no cuida los procedimientos de seguridad, ocurrirá un accidente. Si el trabajador no lee el manual de seguridad interno sucedería lo mismo. El trabajador no ha sufrido incidentes.*
*De ahí concluimos que ha seguido todos los procedimientos de seguridad, y ha leído el manual de seguridad interno”.*

    P : El trabajador cuida los procedimientos de seguridad
    Q : El trabajador lee el manual de seguridad interno
    R : Ocurre un accidente

    Entonces, la frase se puede expresar como:

    (┐P v ┐Q) → R ^ ┐R → (P ^ Q)

Se interpreta de la siguiente manera:

1. Si el trabajador no cuida los procedimientos de seguridad o no lee el manual de seguridad interno (┐P v ┐Q), entonces ocurrirá un accidente (R).
2. Si el trabajador no ha sufrido incidentes (┐R), entonces ha seguido todos los procedimientos de seguridad y ha leido el manual de seguridad interno (P ^ Q).
