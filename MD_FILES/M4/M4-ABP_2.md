# ABP_2

---

Considere el siguiente enunciado. Determine las unidades al mínimo nivel de detalle, y expréselas
como un conjunto de expresiones lógicas

*“Una persona debe permanecer 14 días en observación únicamente si ha salido del país. La persona se hará el PCR si quiere volver a la normalidad. Dado que ni la persona ha salido del país ni presenta contagios cercanos, no tendrá que hacer cuarentena ni se le hará el PCR.”*

## Notación Lógica proposicional

    P: Una persona ha salido del país
    Q: La personal presenta contactos cercanos
    R: Una persona debe permanecer 14 dias en observación
    S: La persona se hará el PCR

    (P → R) ^ (┐P v ┐Q) → (┐R ^ ┐S)

.

    si (salida) hacer
        observacion
        hacerPCR
    si no
        si (contactoCercano) entonces
            observacion
            hacer_PCR
        sino
            normalidad
        fin si
    fin si
