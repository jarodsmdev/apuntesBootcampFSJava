# ORDER BY

La cláusula order by se usa para **ordenar** los registros en un conjunto de resultados.
Se puede ordenar de manera **ascendente (menor a mayor) o descendente (mayor a menor)**

## SINTAXIS

    SELECT [columna]
    FROM [tabla]
    WHERE [condición]
    ORDER BY [columna] [[ASC] O [DESC]];

## EJEMPLOS

1.- Visualiza todos los productos de la marca contiental, ordenados por código de producto

    SELECT *
    FROM producto
    WHERE marca = "continental"
    ORDER BY COD_PRODUCTO;

    +--------------+--------------+-------------+-------+--------+-------+--------+
    | COD_PRODUCTO | NOMBRE       | MARCA       | COLOR | MODELO | STOCK | PRECIO |
    +--------------+--------------+-------------+-------+--------+-------+--------+
    |          107 | horno        | continental | negro | 12-fr  |    20 |   2120 |
    |          108 | lavadora     | continental | negro | 23-ip  |    24 |   3000 |
    |          109 | horno        | continental | negro | 81-th  |    10 |   1800 |
    |          113 | tostadora    | continental | negro | 13-am  |    30 |   2400 |
    |          114 | cocina       | continental | verde | 70-dm  |    34 |   2300 |
    |          117 | cafetera     | continental | gris  | ev-20  |    24 |   2300 |
    |          118 | refrigerador | continental | rojo  | ay-90  |    15 |   1800 |
    |          120 | sumidora     | continental | rojo  | 34-tb  |    16 |   1250 |
    +--------------+--------------+-------------+-------+--------+-------+--------+
    8 rows in set (0,00 sec)
*En caso de no especificar el tipo de orden, de manera predeterminada se ordena de manera ascendente*

2.- Haz la misma consulta del punto 1, pero ordénalos de manera descendente

    SELECT *
    FROM producto
    WHERE marca = "contiental"
    ORDER BY cod_producto DESC;

    +--------------+--------------+-------------+-------+--------+-------+--------+
    | COD_PRODUCTO | NOMBRE       | MARCA       | COLOR | MODELO | STOCK | PRECIO |
    +--------------+--------------+-------------+-------+--------+-------+--------+
    |          120 | sumidora     | continental | rojo  | 34-tb  |    16 |   1250 |
    |          118 | refrigerador | continental | rojo  | ay-90  |    15 |   1800 |
    |          117 | cafetera     | continental | gris  | ev-20  |    24 |   2300 |
    |          114 | cocina       | continental | verde | 70-dm  |    34 |   2300 |
    |          113 | tostadora    | continental | negro | 13-am  |    30 |   2400 |
    |          109 | horno        | continental | negro | 81-th  |    10 |   1800 |
    |          108 | lavadora     | continental | negro | 23-ip  |    24 |   3000 |
    |          107 | horno        | continental | negro | 12-fr  |    20 |   2120 |
    +--------------+--------------+-------------+-------+--------+-------+--------+
    8 rows in set (0,00 sec)

3.- Visualiza el nombre del producto solamente de la marca 'continental', ordenados de manera ascendente.

    SELECT nombre
    FROM producto
    WHERE marca = "continental"
    ORDER BY nombre;

    +--------------+
    | nombre       |
    +--------------+
    | cafetera     |
    | cocina       |
    | horno        |
    | horno        |
    | lavadora     |
    | refrigerador |
    | sumidora     |
    | tostadora    |
    +--------------+
    8 rows in set (0,00 sec)

4.- Haz la misma consulta del punto 3, ordenados de manera descendente.

    SELECT nombre
    FROM producto
    WHERE marca = "continental"
    ORDER BY nombre DESC;

    +--------------+
    | nombre       |
    +--------------+
    | tostadora    |
    | sumidora     |
    | refrigerador |
    | lavadora     |
    | horno        |
    | horno        |
    | cocina       |
    | cafetera     |
    +--------------+
    8 rows in set (0,00 sec)

5.- Visualiza código del producto, su nombre, su marca y precio de la marca continental ordenados por precio de manera descendiente.

    SELECT cod_producto, nombre, marca, precio
    FROM producto
    WHERE marca = "continental"
    ORDER BY precio DESC;

    +--------------+--------------+-------------+--------+
    | cod_producto | nombre       | marca       | precio |
    +--------------+--------------+-------------+--------+
    |          108 | lavadora     | continental |   3000 |
    |          113 | tostadora    | continental |   2400 |
    |          114 | cocina       | continental |   2300 |
    |          117 | cafetera     | continental |   2300 |
    |          107 | horno        | continental |   2120 |
    |          109 | horno        | continental |   1800 |
    |          118 | refrigerador | continental |   1800 |
    |          120 | sumidora     | continental |   1250 |
    +--------------+--------------+-------------+--------+
    8 rows in set (0,00 sec)
