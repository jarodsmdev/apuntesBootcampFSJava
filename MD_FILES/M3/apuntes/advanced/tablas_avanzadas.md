# TABLAS AVANZADAS

    CREATE DATABASE PRUEBA;
    USE PRUEBA;

    CREATE TABLE USUARIO(
        ID_USUARIO INT UNSIGNED PRIMARY KEY,
        NOMBRE VARCHAR(50) NOT NULL UNIQUE,
        FECHA_RENOVACION DATE NOT NULL,
        MES_CADUCIDAD TINYINT(2) UNSIGNED ZEROFILL CHECK(MES_CADUCIDAD >= 1 AND MES_CADUCIDAD <=12),
        AGNO_CADUCIDAD YEAR CHECK(AGNO_CADUCIDAD <= 2021),
        GENERO ENUM("MASCULINO", "FEMENINO") NOT NULL,
        TIPO_USUARIO ENUM("GRATIS", "DE_PAGO") NOT NULL DEFAULT "GRATIS"
    );

    DESCRIBE USUARIO;

    +------------------+------------------------------+------+-----+---------+-------+
    | Field            | Type                         | Null | Key | Default | Extra |
    +------------------+------------------------------+------+-----+---------+-------+
    | ID_USUARIO       | int unsigned                 | NO   | PRI | NULL    |       |
    | NOMBRE           | varchar(50)                  | NO   | UNI | NULL    |       |
    | FECHA_RENOVACION | date                         | NO   |     | NULL    |       |
    | MES_CADUCIDAD    | tinyint(2) unsigned zerofill | YES  |     | NULL    |       |
    | AGNO_CADUCIDAD   | year                         | YES  |     | NULL    |       |
    | GENERO           | enum('MASCULINO','FEMENINO') | NO   |     | NULL    |       |
    | TIPO_USUARIO     | enum('GRATIS','DE_PAGO')     | NO   |     | GRATIS  |       |
    +------------------+------------------------------+------+-----+---------+-------+
    7 rows in set (0,00 sec)