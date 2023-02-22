# HAVING

La Cláusula HAVING se usa en la combinación con la cláusula **GROUP BY**, para restringir los grupos de filas retornadas (filtrar), sólo a aquellos registros cuya condición es **VERDADERA**.

## SINTAXIS

    SELECT [columna][función_de_agregación]
    FROM [tabla]
    GROUP BY [columna]
    HAVING [función_agregación o condición a aplicar sobre la función_de_agregación]

## EJEMPLOS

1.- Visualizar columna marca y su stock sea mayor a 30

    SELECT marca, sum(stock)
    FROM producto
    GROUP BY marca
    HAVING SUM(stock) > 30;

    +-------------+------------+
    | marca       | sum(stock) |
    +-------------+------------+
    | dako        |         50 |
    | eletrolux   |         34 |
    | fell        |         50 |
    | continental |        173 |
    | electrolux  |         52 |
    | bsh         |         43 |
    +-------------+------------+
    6 rows in set (0,00 sec)

2.- Mostrar y agrupar por color que no exedan a 4

    SELECT color, COUNT(*)
    FROM producto
    GROUP BY color
    HAVING COUNT(*) < 4;

    +-------+----------+
    | color | count(*) |
    +-------+----------+
    | gris  |        3 |
    | azul  |        2 |
    | rojo  |        3 |
    | verde |        2 |
    +-------+----------+
    4 rows in set (0,00 sec)

3.- Mostrar y agrupar por color y que su precio sea el minimo por color menor a su precio a 2000

    SELECT color, MIN(precio)
    FROM producto
    GROUP BY color
    HAVING MIN(precio) < 2000;

    +-------+----------+
    | color | count(*) |
    +-------+----------+
    | gris  |        3 |
    | azul  |        2 |
    | rojo  |        3 |
    | verde |        2 |
    +-------+----------+
    4 rows in set (0,00 sec)

