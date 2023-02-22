# Foreign Keys (Llaves Foráneas)

¿Qué es una Foreign key en SQL y para qué se utiliza?

Una **Foreign Key** en SQL, es una **clave** (campo de una columna) que sirve para relacionar dos tablas.  El campo **FOREIGN KEY** se relaciona o vincula con la **PRIMARY KEY** de otra tabla de la BBDD.

> La tabla secundaria es la que contiene la FOREIGN KEY y la tabla principal contiene la PRIMARY KEY.

La Foreign Key es una restricción que no permite que se agreguen o inserten datos que no son válidos en la columna foreign key, ya que los valores que se van a insertar deben ser valores que se encuentren o **o ya estén en la tabla principal** que se quiere relacionar.

## Crear Base de datos

    CREATE DATABASE NEGOCIO;

## Seleccionar base de datos a utilizar

    USE NEGOCIO;

## Crear tablas

Para comenzar debemos tener estas tablas creadas

En la imagen las primeras 3 tablas son tablas principales y las 2 restantes que se encuentran en la segunda línea son tablas secundarias ya que dependen de datos que contienen las tablas principales.
![tablas.png](./tablas.png)

## Creando la tabla 'CLIENTE'

    CREATE TABLE CLIENTE(
        CI INT(10) NOT NULL,
        NOMBRE VARCHAR(20),
        APELLIDO VARCHAR(20),
        DIRECCION VARCHAR(50),
        TELEFONO INT(8),
        PRIMARY KEY (CI)
    );

## En caso de haber cometido un error y desees eliminar una tabla

    DROP TABLE [NOMBRE_DE_LA_TABLA];

## Creando la tabla 'PROVEEDOR'

    CREATE TABLE PROVEEDOR(
        ID_PROVEEDOR INT NOT NULL,
        NOMBRE VARCHAR(45),
        DIRECCION VARCHAR(45),
        TELEFONO INT(10),
        PRIMARY KEY (ID_PROVEEDOR)
    );

## Creando la tabla 'PRODUCTO'

    CREATE TABLE PRODUCTO(
        COD_PRODUCTO INT(15) PRIMARY KEY AUTO_INCREMENT,
        NOMBRE VARCHAR(22),
        MARCA VARCHAR(22),
        COLOR VARCHAR(22),
        MODELO VARCHAR(22),
        STOCK INT(100),
        PRECIO INT(100)
    )AUTO_INCREMENT = 100;

## De cometer un error en el nombre de un campo se puede modificar

    ALTER TABLE PRODUCTO CHANGE COLUMN MODEL MODELO VARCHAR(22);

## Creando la tabla 'COMPRA'

    CREATE TABLE COMPRA(
    CI INT(13),
    COD_PRODUCTO INT(13),
    FECHA_COMPRA DATE,
    CANTIDAD INT (100),
    PRIMARY KEY (CI, COD_PRODUCTO)
    );

    TIP: RECORDAR QUE LAS PRIMARY KEY VIENEN DE OTRAS TABLAS
    (CI, COD_PRODUCTO) QUE LUEGO SE TRANSFORMARAN EN FOREIGN KEYS

## Creando la table 'PROVEE'

    CREATE TABLE PROVEE(
        ID_PROVEEDOR INT(10),
        COD_PRODUCTO INT(8),
        FECHA DATE,
        CANTIDAD INT(10),
        PRIMARY KEY(ID_PROVEEDOR, COD_PRODUCTO)
    );

## Ver tablas dentro de la BBDD

    SHOW TABLES;

    +-------------------+
    | Tables_in_NEGOCIO |
    +-------------------+
    | CLIENTE           |
    | COMPRA            |
    | PRODUCTO          |
    | PROVEE            |
    | PROVEEDOR         |
    +-------------------+
    5 rows in set (0,00 sec)

## Ver cómo fue creada la tabla 'PRODUCTO'

Puedes usar el comando 'DESCRIBE [NOMBRE_DE_LA_TABLA];'
para detallar cualquier tabla y ver nombre de campo, pk, etc.

    DESCRIBE PRODUCTO;

    +--------------+-------------+------+-----+---------+----------------+
    | Field        | Type        | Null | Key | Default | Extra          |
    +--------------+-------------+------+-----+---------+----------------+
    | COD_PRODUCTO | int         | NO   | PRI | NULL    | auto_increment |
    | NOMBRE       | varchar(22) | YES  |     | NULL    |                |
    | MARCA        | varchar(22) | YES  |     | NULL    |                |
    | COLOR        | varchar(22) | YES  |     | NULL    |                |
    | MODEL        | varchar(22) | YES  |     | NULL    |                |
    | STOCK        | int         | YES  |     | NULL    |                |
    | PRECIO       | int         | YES  |     | NULL    |                |
    +--------------+-------------+------+-----+---------+----------------+
    7 rows in set (0,00 sec)

## Insertar Datos en la tabla 'CLIENTE'

    INSERT INTO CLIENTE
    (CI, NOMBRE, APELLIDO, DIRECCION, TELEFONO)
    VALUE
    ("335287", "Victor", "Cruz", "Calle 4 Z. Miraflores", "77850451");

## Mostrar registros de la tabla 'CLIENTE'

    SELECT * FROM CLIENTE;

    +--------+--------+----------+-----------------------+----------+
    | CI     | NOMBRE | APELLIDO | DIRECCION             | TELEFONO |
    +--------+--------+----------+-----------------------+----------+
    | 335287 | Victor | Cruz     | Calle 4 Z. Miraflores | 77850451 |
    +--------+--------+----------+-----------------------+----------+
    1 row in set (0,00 sec)

## Si deseas ELIMINAR REGISTROS DE LA TABLA CLIENTE

    DELETE FROM CLIENTE;

>ATENCIÓN: EN ESTE CASO SÓLO ELIMINARÁ 01 REGISTRO PORQUE
>EN ESTA TABLA EXISTE NADA MÁS QUE 01 REGISTRO, PERO LA SENTENCIA ANTERIOR
>ELIMINARÁ TODOS LOS REGISTROS EXISTENTES EN LA TABLA.

## Insertar datos en la tabla 'PRODUCTO'

    INSERT INTO PRODUCTO
    (COD_PRODUCTO, NOMBRE, MARCA, COLOR, MODEL, STOCK, PRECIO)
    VALUES
    (100, "TOSTADORA", "OSTER", "ROJO", "RT-8", "34", "1200"),
    (NULL, "LAVADORA", "LG", "GRIS", "RT-7", "20", "23000" );

## Mostrar los registros de la tabla 'PRODUCTO'

    SELECT * FROM PRODUCTO;

    +--------------+-----------+-------+-------+--------+-------+--------+
    | COD_PRODUCTO | NOMBRE    | MARCA | COLOR | MODELO | STOCK | PRECIO |
    +--------------+-----------+-------+-------+--------+-------+--------+
    |          100 | TOSTADORA | OSTER | ROJO  | RT-8   |    34 |   1200 |
    |          101 | LAVADORA  | LG    | GRIS  | RT-7   |    20 |  23000 |
    +--------------+-----------+-------+-------+--------+-------+--------+
    2 rows in set (0,00 sec)

## Insertar datos en la tabla 'PROVEEDOR'

    INSERT INTO PROVEEDOR
    (ID_PROVEEDOR, NOMBRE, DIRECCION, TELEFONO)
    VALUE
    ("123", "JUJU", "CALLE 4", 123456);

    SELECT * FROM PROVEEDOR;

    +--------------+--------+-----------+----------+
    | ID_PROVEEDOR | NOMBRE | DIRECCION | TELEFONO |
    +--------------+--------+-----------+----------+
    |          123 | JUJU   | CALLE 4   |   123456 |
    +--------------+--------+-----------+----------+
    1 row in set (0,00 sec)

## POR FIN!!! VAMOS A TRABAJAR CON LLAVES FORÁNEAS

Las tablas 'COMPRAS' y 'PROVEE' las hemos creado como todas las demás sin embargo, estas tablas son algo 'especiales' ya que son tablas 'intermedias'.

**¿Qué significa que sean tablas intermedias?**

Signica que tienen campos que dependen de otras tablas y que **NO** aceptarán ingreso de datos en dichos campos que **NO EXISTAN EN LAS TABLAS PRINCIPALES.** 

Por ejemplo la tabla 'COMPRAS' tiene 2 campos que están declarados como PRIMARY KEY (CI y COD_PRODUCTO) que dependen de 'CI de la tabla 'CLIENTE' y COD_PRODUCTO de la tabla 'PRODUCTO' respectivamente.

**AVISO:** Todo lo dicho anteriormente es sobre 'PAPEL' porque **aún** no se encuentran **'RELACIONADAS'** y esto lo veremos a continuación.

## Definiendo la primera llave foránea

La primera tabla en que realizaremos la primera relación será 'COMPRA':

    ALTER TABLE COMPRA
    ADD FOREIGN KEY (CI) REFERENCES CLIENTE(CI);

Esto significa que estamos realizando la relación de llave foránea del campo CI de la tabla COMPRA con el campo CI de la tabla CLIENTE.

Recordemos que la tabla COMPRA tiene 2 campos que deben relacionarse con 2 tablas distintas, ya tenemos 1 relación vamos a realizar la siguente:

    ALTER TABLE COMPRA
    ADD FOREIGN KEY (COD_PRODUCTO) REFERENCES PRODUCTO(COD_PRODUCTO);

Listo, ya tenemos realizadas las 2 relaciones que debe tener esta tabla.

## Definiendo llave foranea en la tabla 'PROVEE'

Relación ID_PROVEEDOR con el campo ID_PROVEEDOR de la tabla PROVEEDOR

    ALTER TABLE PROVEE
    ADD FOREIGN KEY (ID_PROVEEDOR) REFERENCES PROVEEDOR(ID_PROVEEDOR);

Relación COD_PRODUCTO con el campo COD_PRODUCTO de la tabla PRODUCTO

    ALTER TABLE PROVEE
    ADD FOREIGN KEY (COD_PRODUCTO) REFERENCES PRODUCTO (COD_PRODUCTO);

## Borrar una relación de llave foránea

**¿Cómo puedo borrar una relación de llave foránea en caso que la haya realizado por error?**

Primero debe ingresar la sentencia para revisar los nombres asignados a las llaves foráneas

    SHOW CREATE TABLE [NOMBRE_DE_LA_TABLA];

    SHOW CREATE TABLE PROVEE;

    | PROVEE | CREATE TABLE `PROVEE` (
      `ID_PROVEEDOR` int NOT NULL,
      `COD_PRODUCTO` int NOT NULL,
      `FECHA` date DEFAULT NULL,
      `CANTIDAD` int DEFAULT NULL,
      PRIMARY KEY (`ID_PROVEEDOR`,`COD_PRODUCTO`),
      KEY `COD_PRODUCTO` (`COD_PRODUCTO`),
      CONSTRAINT `PROVEE_ibfk_1` FOREIGN KEY (`ID_PROVEEDOR`) REFERENCES `PROVEEDOR` (`ID_PROVEEDOR`),
      CONSTRAINT `PROVEE_ibfk_2` FOREIGN KEY (`COD_PRODUCTO`) REFERENCES `PRODUCTO` (`COD_PRODUCTO`)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |

luego debemos ejecutar las sentencias:

    ALTER TABLE [NOMBRE_DE_LA_TABLA]
    DROP FOREIGN KEY [NOMBRE_DE_LA_CLAVE_FORÁNEA];

Dado los datos obtenidos anteriormente debemos fijarnos en 'CONSTRAINT' que es el nombre de la llave foránea que fue asignada de manera automática y quedaría de esta manera las sentencias anteriores:

    ALTER TABLE PROVEE
    DROP FOREIGN KEY PROVEE_ibfk_1,
    DROP FOREIGN KEY PROVEE_ibkf_2;

**¿Puedo asignar un nombre de llave foránea personalizada?**
Sí, debe añadir la cláusula ADD CONSTRAINT seguido del nombre a darle entre comillas, al momento de definir las llave foráneas. Ejemplo:

    ALTER TABLE PROVEE
    ADD CONSTRAINT 'NOMBRE_LLAVE_FORANEA'
    FOREIGN KEY (COD_PRODUCTO) REFERENCES PRODUCTO (COD_PRODUCTO);

## Ingresar datos en las tablas con relación de llaves foráneas

El ingreso de datos en estas tablas son idénticos que introducir datos en tablas comunes, solo se debe tener en cuenta que en los campos que tiene la llave foránea **DEBEN EXISTIR** en las tablas relacionadas.

    INSERT INTO COMPRA
    (CI, COD_PRODUCTO, FECHA_COMPRA, CANTIDAD)
    VALUES
    ("335287", "100", "2019-03-07", "20");

    +--------+--------------+--------------+----------+
    | CI     | COD_PRODUCTO | FECHA_COMPRA | CANTIDAD |
    +--------+--------------+--------------+----------+
    | 335287 |          100 | 2019-03-07   |       20 |
    +--------+--------------+--------------+----------+
    1 row in set (0,00 sec)

Debe poner atención que el primer campo llamado CI con el dato "335287" **existe** en la tabla de CLIENTE:

    +--------+--------+----------+-----------------------+----------+
    | CI     | NOMBRE | APELLIDO | DIRECCION             | TELEFONO |
    +--------+--------+----------+-----------------------+----------+
    | 335287 | Victor | Cruz     | Calle 4 Z. Miraflores | 77850451 |
    +--------+--------+----------+-----------------------+----------+
    1 row in set (0,00 sec)

y el segundo campo que hace referencia al código de producto "100" **también existe** en la tabla PRODUCTO:

    +--------------+-----------+-------+-------+--------+-------+--------+
    | COD_PRODUCTO | NOMBRE    | MARCA | COLOR | MODELO | STOCK | PRECIO |
    +--------------+-----------+-------+-------+--------+-------+--------+
    |          100 | TOSTADORA | OSTER | ROJO  | RT-8   |    34 |   1200 |
    |          101 | LAVADORA  | LG    | GRIS  | RT-7   |    20 |  23000 |
    +--------------+-----------+-------+-------+--------+-------+--------+
    2 rows in set (0,00 sec)

Cabe resaltar que en caso de querer ingresar un registro con un dato que **NO** exista  en una tabla con una relación de llave foránea simplemente el gestor de BBDD arrojará un error y no permitirá la inserción de dicho registro.

y esto es lo que significa "BASES DE DATOS RELACIONALES", WELCOME!!!