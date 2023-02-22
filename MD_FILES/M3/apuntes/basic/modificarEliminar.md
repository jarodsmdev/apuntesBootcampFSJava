# MODIFICAR Y ELIMINAR REGISTROS

## CREAR BD

    CREATE DATABASE prueba_db;

## MOSTRAR BD

    SHOW DATABASES;

## ELIMINAR BD

    DROP DATABASE prueba_db;

## CREAR TABLA USUARIO

    CREATE TABLE USUARIO(
        CI INT(13),
        COD_PRODUCTO INT(13),
        FECHA_COMPRA DATE,
        CANTIDAD INT(15),
        PRIMARY KEY (CI)
    );

## CREAR TABLA PRODUCTO

    CREATE TABLE PRODUCTO(
        COD_PRODUCTO INT(13) PRIMARY KEY,
        NOMBRE VARCHAR(22),
        MARCA VARCHAR(22),
        COLOR VARCHAR(22),
        MODELO VARCHAR(22),
        STOCK INT(100),
        PRECIO INT(100)
    );

## CREAR TABLA SERVICIOS

    CREATE TABLE SERVICIOS(
        CI INT(13),
        COD_PRODUCTO INT(13),
        FEHA_COMPRA DATE,
        CANTIDAD INT(15),
        PRIMARY KEY (CI),
        FOREIGN KEY (COD_PRODUCTO) REFERENCES PRODUCTO (COD_PRODUCTO)
    );

## MOSTRAR TABLAS

    SHOW TABLES;

    +---------------------+
    | Tables_in_prueba_db |
    +---------------------+
    | PRODUCTO            |
    | SERVICIOS           |
    | USUARIO             |
    +---------------------+
    3 rows in set (0,00 sec)

## RENOMBRAR LA TABLA usuario a CLIENTE

    RENAME TABLE usuario TO CLIENTE;

    +---------------------+
    | Tables_in_prueba_db |
    +---------------------+
    | CLIENTE             |
    | PRODUCTO            |
    | SERVICIOS           |
    +---------------------+
    3 rows in set (0,00 sec)

## DESCRIBIR LA TABLA CLIENTE

    DESCRIBE CLIENTE;

    +--------------+------+------+-----+---------+-------+
    | Field        | Type | Null | Key | Default | Extra |
    +--------------+------+------+-----+---------+-------+
    | CI           | int  | NO   | PRI | NULL    |       |
    | COD_PRODUCTO | int  | YES  |     | NULL    |       |
    | FECHA_COMPRA | date | YES  |     | NULL    |       |
    | CANTIDAD     | int  | YES  |     | NULL    |       |
    +--------------+------+------+-----+---------+-------+
    4 rows in set (0,00 sec)

## ELIMINAR COLUMNA CANTIDAD DE LA TABLA CLIENTE

    ALTER TABLE CLIENTE
    DROP COLUMN CANTIDAD;

    +--------------+------+------+-----+---------+-------+
    | Field        | Type | Null | Key | Default | Extra |
    +--------------+------+------+-----+---------+-------+
    | CI           | int  | NO   | PRI | NULL    |       |
    | COD_PRODUCTO | int  | YES  |     | NULL    |       |
    | FECHA_COMPRA | date | YES  |     | NULL    |       |
    +--------------+------+------+-----+---------+-------+
    3 rows in set (0,00 sec)

## ELIMINAR COLUMNAS STOCK Y COLOR DE LA TABLA PRODUCTO

La tabla se encuentra con estas columnas

    +--------------+-------------+------+-----+---------+-------+
    | Field        | Type        | Null | Key | Default | Extra |
    +--------------+-------------+------+-----+---------+-------+
    | COD_PRODUCTO | int         | NO   | PRI | NULL    |       |
    | NOMBRE       | varchar(22) | YES  |     | NULL    |       |
    | MARCA        | varchar(22) | YES  |     | NULL    |       |
    | COLOR        | varchar(22) | YES  |     | NULL    |       |
    | MODELO       | varchar(22) | YES  |     | NULL    |       |
    | STOCK        | int         | YES  |     | NULL    |       |
    | PRECIO       | int         | YES  |     | NULL    |       |
    +--------------+-------------+------+-----+---------+-------+
    7 rows in set (0,01 sec)

    ALTER TABLE PRODUCTO
    DROP COLUMN STOCK,
    DROP COLUMN COLOR;

Luego de ejecutar la sentencia anterior podemos apreciar que las columnas STOCK y COLOR ya no se encuentan

    +--------------+-------------+------+-----+---------+-------+
    | Field        | Type        | Null | Key | Default | Extra |
    +--------------+-------------+------+-----+---------+-------+
    | COD_PRODUCTO | int         | NO   | PRI | NULL    |       |
    | NOMBRE       | varchar(22) | YES  |     | NULL    |       |
    | MARCA        | varchar(22) | YES  |     | NULL    |       |
    | MODELO       | varchar(22) | YES  |     | NULL    |       |
    | PRECIO       | int         | YES  |     | NULL    |       |
    +--------------+-------------+------+-----+---------+-------+
    5 rows in set (0,00 sec)

## ELIMINAR LLAVE PRIMARIA

    ALTER TABLE SERVICIOS
    DROP PRIMARY KEY;

## ELIMINAR LLAVE FORÁNEA

Para esto debemos saber cuál es el nombre interno que tomó nuestra llave foránea

    SHOW CREATE TABLE;

    | SERVICIOS | CREATE TABLE `SERVICIOS` (
      `CI` int NOT NULL,
      `COD_PRODUCTO` int DEFAULT NULL,
      `FEHA_COMPRA` date DEFAULT NULL,
      `CANTIDAD` int DEFAULT NULL,
      KEY `COD_PRODUCTO` (`COD_PRODUCTO`),
      CONSTRAINT `SERVICIOS_ibfk_1` FOREIGN KEY (`COD_PRODUCTO`) REFERENCES `PRODUCTO` (`COD_PRODUCTO`)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |

en la 7ma línea del código anterior aparece el nombre que necesitamos **SERVICIOS_ibfk_1**

    ALTER TABLE SERVICIOS
    DROP FOREIGN KEY SERVICIOS_ibfk_1;

## INSERTAR NUEVA COLUMNA AL FINAL DE UNA TABLA

    ALTER TABLE CLIENTE
    ADD COLUMN TELEFONO INT(10);

    +--------------+------+------+-----+---------+-------+
    | Field        | Type | Null | Key | Default | Extra |
    +--------------+------+------+-----+---------+-------+
    | CI           | int  | NO   | PRI | NULL    |       |
    | COD_PRODUCTO | int  | YES  |     | NULL    |       |
    | FECHA_COMPRA | date | YES  |     | NULL    |       |
    | TELEFONO     | int  | YES  |     | NULL    |       |
    +--------------+------+------+-----+---------+-------+
    4 rows in set (0,00 sec)

## INSERTAR UNA COLUMNA DESPUÉS DE CI EN LA TABLA CLIENTE

    ALTER TABLE CLIENTE
    ADD COLUMN NOMBRE VARCHAR(15)
    AFTER CI;

    +--------------+-------------+------+-----+---------+-------+
    | Field        | Type        | Null | Key | Default | Extra |
    +--------------+-------------+------+-----+---------+-------+
    | CI           | int         | NO   | PRI | NULL    |       |
    | NOMBRE       | varchar(15) | YES  |     | NULL    |       |
    | COD_PRODUCTO | int         | YES  |     | NULL    |       |
    | FECHA_COMPRA | date        | YES  |     | NULL    |       |
    | TELEFONO     | int         | YES  |     | NULL    |       |
    +--------------+-------------+------+-----+---------+-------+
    5 rows in set (0,00 sec)

## INSERTAR UNA COLUMNA AL INICIO EN LA TABLA CLIENTE

    ALTER TABLE CLIENTE
    ADD COLUMN CODIGO INT(5)
    FIRST;

    +--------------+-------------+------+-----+---------+-------+
    | Field        | Type        | Null | Key | Default | Extra |
    +--------------+-------------+------+-----+---------+-------+
    | CODIGO       | int         | YES  |     | NULL    |       |
    | CI           | int         | NO   | PRI | NULL    |       |
    | NOMBRE       | varchar(15) | YES  |     | NULL    |       |
    | COD_PRODUCTO | int         | YES  |     | NULL    |       |
    | FECHA_COMPRA | date        | YES  |     | NULL    |       |
    | TELEFONO     | int         | YES  |     | NULL    |       |
    +--------------+-------------+------+-----+---------+-------+
    6 rows in set (0,00 sec)

## RENOMBRAR UNA COLUMNA DE LA TABLA CLIENTE

    ALTER TABLE CLIENTE
    CHANGE COLUMN TELEFONO CELULAR INT(10);

    +--------------+-------------+------+-----+---------+-------+
    | Field        | Type        | Null | Key | Default | Extra |
    +--------------+-------------+------+-----+---------+-------+
    | CODIGO       | int         | YES  |     | NULL    |       |
    | CI           | int         | NO   | PRI | NULL    |       |
    | NOMBRE       | varchar(15) | YES  |     | NULL    |       |
    | COD_PRODUCTO | int         | YES  |     | NULL    |       |
    | FECHA_COMPRA | date        | YES  |     | NULL    |       |
    | CELULAR      | int         | YES  |     | NULL    |       |
    +--------------+-------------+------+-----+---------+-------+
    6 rows in set (0,00 sec)

## CAMBIAR EL TIPO DE DATO DE UNA COLUMNA

    ALTER TABLE PRODUCTO
    MODIFY MODELO INT(8) NOT NULL;

    +--------------+-------------+------+-----+---------+-------+
    | Field        | Type        | Null | Key | Default | Extra |
    +--------------+-------------+------+-----+---------+-------+
    | COD_PRODUCTO | int         | NO   | PRI | NULL    |       |
    | NOMBRE       | varchar(22) | YES  |     | NULL    |       |
    | MARCA        | varchar(22) | YES  |     | NULL    |       |
    | MODELO       | int         | NO   |     | NULL    |       |
    | PRECIO       | int         | YES  |     | NULL    |       |
    +--------------+-------------+------+-----+---------+-------+
    5 rows in set (0,00 sec)
