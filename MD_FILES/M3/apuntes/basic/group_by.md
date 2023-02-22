# GROUP BY

Group by es una cláusura que recopila los datos en varios registros y agrupa los resultados en una o más columnas.

Se utiliza dentro de una consulta de selección de alguna columna y que además haya sido utilizada alguna función de agregación vista anteriormente, la sintaxis es la siguiente:

    SELECT [columna], [función_de_agregación]
    FROM [tabla] GROUP BY [columna]

## Ahora vamos a realizar varios ejemplos

### Función de agregación sum()

    SELECT marca, sum(precio)
    FROM producto
    GROUP BY marca;

    +-------------+-------------+
    | marca       | sum(precio) |
    +-------------+-------------+
    | stk         |        2500 |
    | balay       |       31000 |
    | sansung     |         700 |
    | dako        |        5400 |
    | eletrolux   |        1250 |
    | vidaelect   |        2300 |
    | fell        |        3700 |
    | continental |       16970 |
    | electrolux  |        5500 |
    | oster       |        1250 |
    | bsh         |        7050 |
    +-------------+-------------+
    11 rows in set (0,03 sec)

### Función de agregacion count()

    SELECT marca, COUNT(*)
    FROM producto
    GROUP BY marca;

    +-------------+----------+
    | marca       | count(*) |
    +-------------+----------+
    | stk         |        1 |
    | balay       |        1 |
    | sansung     |        1 |
    | dako        |        2 |
    | eletrolux   |        1 |
    | vidaelect   |        1 |
    | fell        |        2 |
    | continental |        8 |
    | electrolux  |        2 |
    | oster       |        1 |
    | bsh         |        3 |
    +-------------+----------+
    11 rows in set (0,00 sec)

## Función de agregación COUNT() con un WHERE

    SELECT marca, COUNT(*)
    FROM producto
    WHERE color = "negro"
    GROUP BY marca;

    +-------------+----------+
    | marca       | count(*) |
    +-------------+----------+
    | vidaelect   |        1 |
    | continental |        4 |
    | oster       |        1 |
    | bsh         |        1 |
    | electrolux  |        1 |
    +-------------+----------+
    5 rows in set (0,00 sec)

### Función de agregación MIN()

    SELECT color, MIN(precio)
    FROM producto
    GROUP BY color;

    +--------+-------------+
    | color  | MIN(precio) |
    +--------+-------------+
    | blanco |        1250 |
    | gris   |         700 |
    | negro  |        1250 |
    | azul   |        2400 |
    | rojo   |        1250 |
    | verde  |        1300 |
    +--------+-------------+
    6 rows in set (0,00 sec)

### Función de agregación MAX()

    SELECT color, MAX(precio)
    FROM producto
    GROUP BY color;

    +--------+-------------+
    | color  | max(precio) |
    +--------+-------------+
    | blanco |       31000 |
    | gris   |        3000 |
    | negro  |        3000 |
    | azul   |        4000 |
    | rojo   |        1800 |
    | verde  |        2300 |
    +--------+-------------+
    6 rows in set (0,00 sec)
