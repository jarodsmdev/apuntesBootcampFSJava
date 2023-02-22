# CONSULTAS SQL

Una consulta SQL básica puede constar con un máximo de seis cláusulas;

- SELECT
- FROM
- WHERE
- GROUP BY
- HAVING
- ORDER BY

## ¿Qué hacen estas cláusulas?

- SELECT: Lista los atributos
- FROM: Lista las tablas
- WHERE: Agrega la condición
- HAVING: Agrega la condición de Agrupación
- GROUP BY: Agrega atributos de Agrupación
- ORDER BY: Lista de atributos y los ordena (ASC, DESC)

## SELECT y FROM

SELECT indica los atributos a seleccionar
FROM Especifica la tabla que se necesita consultar

    SELECT A FROM B;

    A: SON LOS DATOS QUE REQUIERO (COLUMNAS)
    B: DE DÓNDE VOY A OBTENER LOS DATOS (COLUMNAS)

Veamos un ejemplo

    SELECT *
    FROM cliente;

    TABLA CLIENTE:
    +---------+----------+----------+-----------------------+----------+
    | CI      | nombre   | apellido | direccion             | telefono |
    +---------+----------+----------+-----------------------+----------+
    | 1830258 | SOLEDAD  | FLORES   | CALLE 4 z olivos      |  6654812 |
    | 1834505 | DELICIA  | CORTEZ   | CALLE 56 z green      |  7254872 |
    | 1880804 | RAMIRO   | BENITEZ  | CALLE 2 z golveta     |  2579457 |
    | 1892870 | LAURA    | CRUZ     | plaza avaroa          |  1235798 |
    | 2233046 | MERCEDES | MIRANDA  | CALLE f z leon        |  7112081 |
    | 5008608 | EDWIN    | RAMIREZ  | CALLE 12 z fuel       |  7888021 |
    | 5543170 | EDDIE    | PERALTA  | CALLE 67 z golketa    |  7985412 |
    | 5785085 | JAIME    | CRUZ     | CALLE 80 z miraflores |  7548352 |
    | 5798046 | WILDER   | ARMELLA  | CALLE R z pinos       |  7885428 |
    | 7193156 | LUCERO   | RAMIEZZ  | CALLE 5 z golbert     | 12374387 |
    +---------+----------+----------+-----------------------+----------+
    10 rows in set (0,00 sec)

La consulta anterior usa el caracter '*' el cual indica que traerá **TODOS** los registros, de la tabla **cliente**.

## WHERE

Quiere decir que especificaremos una o más condiciones, para que funcione correctamente debe trabajar con operadores matemáticos (>, >=, <, <=, =, !=) y/o operadores lógicos (AND, OR).

    SELECT *
    FROM cliente
    WHERE apellido = 'CRUZ';

    +---------+--------+----------+-----------------------+----------+
    | CI      | nombre | apellido | direccion             | telefono |
    +---------+--------+----------+-----------------------+----------+
    | 1892870 | LAURA  | CRUZ     | plaza avaroa          |  1235798 |
    | 5785085 | JAIME  | CRUZ     | CALLE 80 z miraflores |  7548352 |
    +---------+--------+----------+-----------------------+----------+
    2 rows in set (0,06 sec)

    ----------------------

    SELECT * 
    FROM producto
    WHERE marca = 'continental'
    AND precio > 1000;

    +--------------+-----------+-------------+-------+--------+-------+--------+
    | COD_PRODUCTO | NOMBRE    | MARCA       | COLOR | MODELO | STOCK | PRECIO |
    +--------------+-----------+-------------+-------+--------+-------+--------+
    |          107 | horno     | continental | negro | 12-fr  |    20 |   2120 |
    |          108 | lavadora  | continental | negro | 23-ip  |    24 |   3000 |
    |          113 | tostadora | continental | negro | 13-am  |    30 |   2400 |
    |          114 | cocina    | continental | verde | 70-dm  |    34 |   2300 |
    |          117 | cafetera  | continental | gris  | ev-20  |    24 |   2300 |
    +--------------+-----------+-------------+-------+--------+-------+--------+
    5 rows in set (0,00 sec)

## WHERE LIKE

Al usar la condición **LIKE** debe recibir un simbolo que puede ser de 2 tipos:

- **%** : Al usar el símbolo de porcentaje, quiere decir que en su lugar puede ir cualquier **cadena de caracteres.**
  
- **_** : Al usar el símbolo de barra baja, quiere decir que en su lugar puede ir cualquier **caracter individual.**

Ejemplo:

    SELECT nombre, apellido
    FROM cliente
    WHERE apellido LIKE 'C%';

    +---------+----------+
    | nombre  | apellido |
    +---------+----------+
    | DELICIA | CORTEZ   |
    | LAURA   | CRUZ     |
    | JAIME   | CRUZ     |
    +---------+----------+
    3 rows in set (0,00 sec)

    -----

    SELECT *
    FROM proveedor
    WHERE id_proveedor LIKE '%0%';

    +--------------+------------+-------------------+----------+
    | ID_PROVEEDOR | NOMBRE     | DIRECCION         | TELEFONO |
    +--------------+------------+-------------------+----------+
    |         1201 | DISMAC     | CALLE 32 Z. SEYA  |  1279432 |
    |         2015 | LA PRIMERA | CALLE A Z. KOLVER |  2256788 |
    |         2018 | DORADO     | CALLE 4 Z. OLIVOS |  1694328 |
    +--------------+------------+-------------------+----------+
    3 rows in set (0,03 sec)

    ------
    SELECT *
    FROM salvadora.cliente
    WHERE CI NOT LIKE '18%';

    +---------+----------+----------+-----------------------+----------+
    | CI      | nombre   | apellido | direccion             | telefono |
    +---------+----------+----------+-----------------------+----------+
    | 2233046 | MERCEDES | MIRANDA  | CALLE f z leon        |  7112081 |
    | 5008608 | EDWIN    | RAMIREZ  | CALLE 12 z fuel       |  7888021 |
    | 5543170 | EDDIE    | PERALTA  | CALLE 67 z golketa    |  7985412 |
    | 5785085 | JAIME    | CRUZ     | CALLE 80 z miraflores |  7548352 |
    | 5798046 | WILDER   | ARMELLA  | CALLE R z pinos       |  7885428 |
    | 7193156 | LUCERO   | RAMIEZZ  | CALLE 5 z golbert     | 12374387 |
    +---------+----------+----------+-----------------------+----------+
    6 rows in set (0,00 sec)

    -----

    SELECT *
    FROM producto
    WHERE COD_PRODUCTO LIKE '10_';

    +--------------+-----------+-------------+--------+---------+-------+--------+
    | COD_PRODUCTO | NOMBRE    | MARCA       | COLOR  | MODELO  | STOCK | PRECIO |
    +--------------+-----------+-------------+--------+---------+-------+--------+
    |          100 | licuadora | stk         | blanco | jty-371 |    10 |   2500 |
    |          101 | lavajilla | balay       | blanco | ju-301  |    15 |  31000 |
    |          102 | lavadora  | sansung     | gris   | ity-65  |    15 |    700 |
    |          103 | cocina    | dako        | blanco | wqe-34  |    30 |   2400 |
    |          104 | Cafetera  | eletrolux   | blanco | ui-95   |    34 |   1250 |
    |          105 | tostadora | vidaelect   | negro  | ewq-65  |    15 |   2300 |
    |          106 | secadora  | fell        | azul   | 32-uy   |    34 |   2400 |
    |          107 | horno     | continental | negro  | 12-fr   |    20 |   2120 |
    |          108 | lavadora  | continental | negro  | 23-ip   |    24 |   3000 |
    |          109 | horno     | continental | negro  | 81-th   |    10 |   1800 |
    +--------------+-----------+-------------+--------+---------+-------+--------+
    10 rows in set (0,00 sec)

## WHERE BETWEEN

La condición **BETWEEN** selecciona y retorna un rango de la columna indicada, se debe utilizar operadores lógicos (Ej.: AND, OR, NOT)

Además es posible utilizar **IN()**, aquí se puede especificar una relación de valores

    SELECT nombre, marca, color, precio
    FROM producto
    WHERE precio BETWEEN 1500 AND 3000;

    +--------------+-------------+--------+--------+
    | nombre       | marca       | color  | precio |
    +--------------+-------------+--------+--------+
    | licuadora    | stk         | blanco |   2500 |
    | cocina       | dako        | blanco |   2400 |
    | tostadora    | vidaelect   | negro  |   2300 |
    | secadora     | fell        | azul   |   2400 |
    | horno        | continental | negro  |   2120 |
    | lavadora     | continental | negro  |   3000 |
    | horno        | continental | negro  |   1800 |
    | tostadora    | continental | negro  |   2400 |
    | cocina       | continental | verde  |   2300 |
    | refrigerador | dako        | gris   |   3000 |
    | batidora     | bsh         | negro  |   1800 |
    | cafetera     | continental | gris   |   2300 |
    | refrigerador | continental | rojo   |   1800 |
    | cocina       | electrolux  | negro  |   1500 |
    +--------------+-------------+--------+--------+
    14 rows in set (0,00 sec)

    ---


    SELECT nombre, marca, color, precio
    FROM producto
    WHERE precio NOT BETWEEN 1500 AND 3000;

    +-----------+-------------+--------+--------+
    | nombre    | marca       | color  | precio |
    +-----------+-------------+--------+--------+
    | lavajilla | balay       | blanco |  31000 |
    | lavadora  | sansung     | gris   |    700 |
    | Cafetera  | eletrolux   | blanco |   1250 |
    | licuadora | electrolux  | azul   |   4000 |
    | lavadora  | oster       | negro  |   1250 |
    | sumidora  | bsh         | rojo   |   1250 |
    | tostadora | bsh         | blanco |   4000 |
    | sumidora  | continental | rojo   |   1250 |
    | licuadora | fell        | verde  |   1300 |
    +-----------+-------------+--------+--------+
    9 rows in set (0,00 sec)

    ---

    SELECT *
    FROM producto
    WHERE precio in (1800, 2300, 3000);

    +--------------+--------------+-------------+-------+--------+-------+--------+
    | COD_PRODUCTO | NOMBRE       | MARCA       | COLOR | MODELO | STOCK | PRECIO |
    +--------------+--------------+-------------+-------+--------+-------+--------+
    |          105 | tostadora    | vidaelect   | negro | ewq-65 |    15 |   2300 |
    |          108 | lavadora     | continental | negro | 23-ip  |    24 |   3000 |
    |          109 | horno        | continental | negro | 81-th  |    10 |   1800 |
    |          114 | cocina       | continental | verde | 70-dm  |    34 |   2300 |
    |          115 | refrigerador | dako        | gris  | 19-bf  |    20 |   3000 |
    |          116 | batidora     | bsh         | negro | 96-za  |    10 |   1800 |
    |          117 | cafetera     | continental | gris  | ev-20  |    24 |   2300 |
    |          118 | refrigerador | continental | rojo  | ay-90  |    15 |   1800 |
    +--------------+--------------+-------------+-------+--------+-------+--------+
    8 rows in set (0,00 sec)

    ---

    SELECT nombre, marca, color
    FROM color IN ('gris', 'rojo', 'verde')

    +--------------+-------------+-------+
    | nombre       | marca       | color |
    +--------------+-------------+-------+
    | lavadora     | sansung     | gris  |
    | sumidora     | bsh         | rojo  |
    | cocina       | continental | verde |
    | refrigerador | dako        | gris  |
    | cafetera     | continental | gris  |
    | refrigerador | continental | rojo  |
    | sumidora     | continental | rojo  |
    | licuadora    | fell        | verde |
    +--------------+-------------+-------+
    8 rows in set (0,00 sec)
