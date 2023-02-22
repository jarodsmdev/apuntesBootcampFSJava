# ACTIVIDADES

1.- Obtener los nombres de los clientes de la empresa salvadora

    SELECT nombre
    FROM cliente;

    +----------+
    | nombre   |
    +----------+
    | SOLEDAD  |
    | DELICIA  |
    | RAMIRO   |
    | LAURA    |
    | MERCEDES |
    | EDWIN    |
    | EDDIE    |
    | JAIME    |
    | WILDER   |
    | LUCERO   |
    +----------+
    10 rows in set (0,00 sec)

2.- Obtener los nombres, marcas y precios de los productos de la empresa salvadora

    SELECT nombre, marca, precio
    FROM producto;

    +--------------+-------------+--------+
    | nombre       | marca       | precio |
    +--------------+-------------+--------+
    | licuadora    | stk         |   2500 |
    | lavajilla    | balay       |  31000 |
    | lavadora     | sansung     |    700 |
    | cocina       | dako        |   2400 |
    | Cafetera     | eletrolux   |   1250 |
    | tostadora    | vidaelect   |   2300 |
    | secadora     | fell        |   2400 |
    | horno        | continental |   2120 |
    | lavadora     | continental |   3000 |
    | horno        | continental |   1800 |
    | licuadora    | electrolux  |   4000 |
    | lavadora     | oster       |   1250 |
    | sumidora     | bsh         |   1250 |
    | tostadora    | continental |   2400 |
    | cocina       | continental |   2300 |
    | refrigerador | dako        |   3000 |
    | batidora     | bsh         |   1800 |
    | cafetera     | continental |   2300 |
    | refrigerador | continental |   1800 |
    | tostadora    | bsh         |   4000 |
    | sumidora     | continental |   1250 |
    | licuadora    | fell        |   1300 |
    | cocina       | electrolux  |   1500 |
    +--------------+-------------+--------+
    23 rows in set (0,00 sec)

3.- Obtener todos los datos de los productos cuyo precio esté entre 2000 y 3000

    SELECT *
    FROM producto
    WHERE precio BETWEEN 2000 AND 3000;

    +--------------+--------------+-------------+--------+---------+-------+--------+
    | COD_PRODUCTO | NOMBRE       | MARCA       | COLOR  | MODELO  | STOCK | PRECIO |
    +--------------+--------------+-------------+--------+---------+-------+--------+
    |          100 | licuadora    | stk         | blanco | jty-371 |    10 |   2500 |
    |          103 | cocina       | dako        | blanco | wqe-34  |    30 |   2400 |
    |          105 | tostadora    | vidaelect   | negro  | ewq-65  |    15 |   2300 |
    |          106 | secadora     | fell        | azul   | 32-uy   |    34 |   2400 |
    |          107 | horno        | continental | negro  | 12-fr   |    20 |   2120 |
    |          108 | lavadora     | continental | negro  | 23-ip   |    24 |   3000 |
    |          113 | tostadora    | continental | negro  | 13-am   |    30 |   2400 |
    |          114 | cocina       | continental | verde  | 70-dm   |    34 |   2300 |
    |          115 | refrigerador | dako        | gris   | 19-bf   |    20 |   3000 |
    |          117 | cafetera     | continental | gris   | ev-20   |    24 |   2300 |
    +--------------+--------------+-------------+--------+---------+-------+--------+
    10 rows in set (0,05 sec)

4.- Obtener el número de productos cuyo precio sea igual a 1250.

    SELECT COUNT(*)
    FROM producto
    WHERE precio = 1250;

    +----------+
    | count(*) |
    +----------+
    |        4 |
    +----------+
    1 row in set (0,00 sec)

5.- Obtener el nombre, marca y precio del producto más barato

OPCION A:

    SELECT nombre, marca, precio, min(precio)
    FROM producto
    GROUP BY nombre, marca, precio
    ORDER BY precio
    LIMIT  1;

    +----------+---------+--------+
    | nombre   | marca   | precio |
    +----------+---------+--------+
    | lavadora | sansung |    700 |
    +----------+---------+--------+
    1 row in set (0,00 sec)

OPCION B:

    SELECT nombre, marca, precio
    FROM producto
    WHERE precio = (SELECT MIN(precio) FROM producto);

    +----------+---------+--------+
    | nombre   | marca   | precio |
    +----------+---------+--------+
    | lavadora | sansung |    700 |
    +----------+---------+--------+
    1 row in set (0,00 sec)

6.- Seleccionar todos los clientes que no tengan celular
(Para este ejercicio asuma que cualquier número telefónico inciado en 6 o 7 es un número de celular)

    SELECT nombre, apellido, telefono
    FROM cliente
    WHERE telefono NOT LIKE '6%' AND telefono NOT LIKE '7%';

    +--------+----------+----------+
    | nombre | apellido | telefono |
    +--------+----------+----------+
    | RAMIRO | BENITEZ  |  2579457 |
    | LAURA  | CRUZ     |  1235798 |
    | LUCERO | RAMIEZZ  | 12374387 |
    +--------+----------+----------+
    3 rows in set (0,00 sec)
