# AE1-ABP

## CREAR BD

    CREATE DATABASE NEGOCIO;

## USAR BASE DE DATOS

    USE NEGOCIO;

## CREAR TABLA

    CREATE TABLE NEGOCIO.ventas (
        idventa INT NOT NULL AUTO_INCREMENT,
        comprador VARCHAR(30) NOT NULL,
        vendedor VARCHAR(30) NOT NULL,
        cantarticulos INT NOT NULL,
        subtotal INT NOT NULL,
        impuesto INT NOT NULL,
        total INT NOT NULL,
        PRIMARY KEY (idventa)
    );

## POBLANDO LA BD

    INSERT INTO NEGOCIO.ventas
    (comprador, vendedor, cantarticulos, subtotal, impuesto, total)
    VALUES
    ('LUCAS','MARIA', 1, 15441, 254,8898944),
    ('CLIENTE 9','MARIA', 2, 122441, 224,555444),
    ('LUCAS','SONIA GARRIDO', 5, 15441, 254, 5944),
    ('LUCAS','SONIA GARRIDO', 20, 15441, 254, 8844),
    ('MARIA','LUCAS', 121, 15441, 254, 66444),
    ('LUCAS','SONIA GARRIDO', 54, 3441, 254, 4555),
    ('LUCAS','MARIA', 21, 151, 254, 44),
    ('CLIENTE 3','SONIA GARRIDO', 12, 15441, 284, 26444),
    ('CLIENTE 2','MARIA', 221, 15641, 234, 56444),
    ('CLIENTE 1','SONIA GARRIDO', 145, 154441, 954, 5444);

## JUGANDO CON LA BD

Crear una consulta que permita obtener todos los registros de la tabla tales que la cantidad de artículos sea mayor que 2, devolviendo todos sus campos.

    SELECT * FROM NEGOCIO.ventas
    WHERE cantarticulos > 2;

    +---------+-----------+---------------+---------------+----------+----------+-------+
    | idventa | comprador | vendedor      | cantarticulos | subtotal | impuesto | total |
    +---------+-----------+---------------+---------------+----------+----------+-------+
    |       3 | LUCAS     | SONIA GARRIDO |             5 |    15441 |      254 |  5944 |
    |       4 | LUCAS     | SONIA GARRIDO |            20 |    15441 |      254 |  8844 |
    |       5 | MARIA     | LUCAS         |           121 |    15441 |      254 | 66444 |
    |       6 | LUCAS     | SONIA GARRIDO |            54 |     3441 |      254 |  4555 |
    |       7 | LUCAS     | MARIA         |            21 |      151 |      254 |    44 |
    |       8 | CLIENTE 3 | SONIA GARRIDO |            12 |    15441 |      284 | 26444 |
    |       9 | CLIENTE 2 | MARIA         |           221 |    15641 |      234 | 56444 |
    |      10 | CLIENTE 1 | SONIA GARRIDO |           145 |   154441 |      954 |  5444 |
    +---------+-----------+---------------+---------------+----------+----------+-------+
    8 rows in set (0,00 sec)

Crear una consulta que permita obtener todos los registros de la tabla tales que el subtotal sea menor que 1000, desplegando solo el ID de venta, el comprador y la cantidad de artículos

    SELECT IDVENTA, COMPRADOR, CANTARTICULOS
    FROM NEGOCIO.ventas
    WHERE SUBTOTAL < 1000;

    +---------+-----------+---------------+
    | IDVENTA | COMPRADOR | CANTARTICULOS |
    +---------+-----------+---------------+
    |       7 | LUCAS     |            21 |
    +---------+-----------+---------------+
    1 row in set (0,00 sec)

Crear una consulta que permite obtener los registros tales que el vendedor tiene el nombre "SONIA GARRIDO", y que el valor total de la venta es mayor o igual a 5000.  Debe indicar todos los campos de la tabla, pero en orden inverso al que se indica la figura.

    SELECT TOTAL, IMPUESTO, SUBTOTAL, CANTARTICULOS, VENDEDOR, COMPRADOR, IDVENTA
    FROM NEGOCIO.ventas
    WHERE VENDEDOR = 'SONIA GARRIDO'
    AND TOTAL >= 5000;

    +-------+----------+----------+---------------+---------------+-----------+---------+
    | TOTAL | IMPUESTO | SUBTOTAL | CANTARTICULOS | VENDEDOR      | COMPRADOR | IDVENTA |
    +-------+----------+----------+---------------+---------------+-----------+---------+
    |  5944 |      254 |    15441 |             5 | SONIA GARRIDO | LUCAS     |       3 |
    |  8844 |      254 |    15441 |            20 | SONIA GARRIDO | LUCAS     |       4 |
    | 26444 |      284 |    15441 |            12 | SONIA GARRIDO | CLIENTE 3 |       8 |
    |  5444 |      954 |   154441 |           145 | SONIA GARRIDO | CLIENTE 1 |      10 |
    +-------+----------+----------+---------------+---------------+-----------+---------+
    4 rows in set (0,00 sec)

Crear una consulta que retorne los registros de la tabla tales que el comprador es "LUCAS", o bien que el vendedor es "MARIA".  Despliegue solo los campos vendedor, comprador y total, en ese orden.

    SELECT VENDEDOR, COMPRADOR, TOTAL
    FROM NEGOCIO.ventas
    WHERE COMPRADOR = "LUCAS" OR COMPRADOR = "MARIA";

    +---------------+-----------+---------+
    | VENDEDOR      | COMPRADOR | TOTAL   |
    +---------------+-----------+---------+
    | MARIA         | LUCAS     | 8898944 |
    | SONIA GARRIDO | LUCAS     |    5944 |
    | SONIA GARRIDO | LUCAS     |    8844 |
    | LUCAS         | MARIA     |   66444 |
    | SONIA GARRIDO | LUCAS     |    4555 |
    | MARIA         | LUCAS     |      44 |
    +---------------+-----------+---------+
    6 rows in set (0,00 sec)

Crear una consulta que despliegue todos los campos de todos los registros tales que el identificador está en el siguiente conjunto 2,5,6 y 9.

    SELECT * FROM NEGOCIO.ventas
    WHERE IDVENTA IN (2,5,6,9);

    +---------+-----------+---------------+---------------+----------+----------+--------+
    | idventa | comprador | vendedor      | cantarticulos | subtotal | impuesto | total  |
    +---------+-----------+---------------+---------------+----------+----------+--------+
    |       2 | CLIENTE 9 | MARIA         |             2 |   122441 |      224 | 555444 |
    |       5 | MARIA     | LUCAS         |           121 |    15441 |      254 |  66444 |
    |       6 | LUCAS     | SONIA GARRIDO |            54 |     3441 |      254 |   4555 |
    |       9 | CLIENTE 2 | MARIA         |           221 |    15641 |      234 |  56444 |
    +---------+-----------+---------------+---------------+----------+----------+--------+
    4 rows in set (0,04 sec)
