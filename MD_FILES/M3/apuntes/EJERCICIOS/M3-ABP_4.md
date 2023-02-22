# ABP_4 (IND)

## CREAR BD

    CREATE DATABASE MINORISTA;

## SELECCIONAR BD

    USE MINORISTA;

## CREAR TABLA VENTAS

    CREATE TABLE ventas(
    idVenta INT NOT NULL PRIMARY KEY,
    vendedor VARCHAR(50) NULL,
    cantArticulos INT NOT NULL,
    subTotal INT NOT NULL,
    impuesto INT NOT NULL,
    total INT NOT NULL,
    clientes_idCliente INT
    );

## CREAR TABLA CLIENTES

    CREATE TABLE clientes(
    idCliente INT NOT NULL PRIMARY KEY,
    nombres VARCHAR(50) NOT NULL,
    apellidos VARCHAR(50) NOT NULL,
    direccion VARCHAR(70),
    telefono INT
    );

## CREAR LLAVE FORÁNEA A LA TABLA ventas

    ALTER TABLE ventas
    ADD FOREIGN KEY (clientes_idCliente)
    REFERENCES clientes (idCliente);

## ACTIVIDADES

1.- Genere tres consultas de inserción de clientes; en las primeras dos deben ir incorporados todos los datos, mientras que la restante debe estar considerado solo el identificador de cliente, nombres y apellidos.

    INSERT INTO clientes
    (idCliente, nombres, apellidos, direccion, telefono)
    values
    (1, 'Frijolito', 'Chupito', 'En mi casa', 555555),
    (2, 'Garbancito','Firulais', 'En su casa', 6666666)
    ;

    INSERT INTO clientes
    (idCliente, nombres, apellidos)
    values
    (3, 'Chuletas', 'Dinamita')
    ;

2.- Genere cinco consultas de inserción de registros en la tabla ventas. No se pide un formato específico de consulta de inserción. Estas ventas deben estar asociadas lógicamente a alguno de los clientes antes creados.

    INSERT INTO ventas
    (idVenta, vendedor, cantArticulos, subTotal, impuesto, total, clientes_idCliente)
    values
    (1, 'Aitor Tilla', 5, 4500, 41, 78522, 1 ),
    (2, 'Alan Brito Delgado', 7, 78421, 9855, 987986, 2),
    (3, 'Aitor Tilla', 60, 96599, 25698, 102354, 3),
    (4, 'Alan Brito Delgado', 9, 87798, 36297, 362541,1),
    (5, 'Evita Dolores', 20, 45656, 85, 999877,2)
    ;

3.- Genere una consulta que permita actualizar el campo total de la tabla ventas, igualándolo a la suma del subtotal y el impuesto.

    UPDATE ventas
    SET total = subTotal + impuesto
    ;

4.- Finalmente, genere una consulta en la que se elimine un cliente a través de su identificador (idcliente), y posterior a eso otra consulta que elimine todas las ventas asociadas a dicho cliente (siempre de acuerdo con el campo idcliente).
**PRIMERO PARA ASEGURARSE DE BORRAR LOS DATOS CORRECTOS EJECUTAREMOS UNA CONSULTA SELECT**

    SELECT *
    FROM clientes
    WHERE idCliente = 2
    ;

    SELECT *
    FROM ventas
    WHERE clientes_idCliente = 2
    ;

En este punto tendremos un problema:
No podemos borrar un cliente directamente porque la tabla de ventas, depende del idCliente através de la llave foránea (FOREIGN KEY)
Para solucionar este inconveniente podríamos tener 2 opciones (talvez más):

**OPCIÓN A:**
Cambiar el orden de las sentencias, esto es:

Ejecutar primero el borrado de los clientes que existen en la tabla **ventas** y luego ejecutar el borrado del cliente en la tabla **clientes**.

    DELETE FROM clientes WHERE idCliente = 2;
    DELETE FROM ventas WHERE clientes_idCliente = 2;

**OPCION B:**
Deshabilitar de manera temporal mientras se ejecuta la consulta la comprobación que hace el gestor de BBDD de integridad de datos a través de la llave foránea, ejecutar las sentencias de borrado y luego volverlas a activar.

    SET FOREIGN_KEY_CHECKS = 0;
    DELETE FROM ventas WHERE clientes_idCliente = 2;
    DELETE FROM clientes WHERE idCliente = 2;
    SET FOREIGN_KEY_CHECKS = 1;

    **créditos: Esta solución fue cedida por Benjamín Pavéz**
