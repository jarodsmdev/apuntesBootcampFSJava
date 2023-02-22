# AE1-ABRPO

## CREAR BASE DE DATOS 'Capacitacion'

    CREATE DATABASE Capacitacion;

## DEBE CONTENER LOS SIGUIENTES CAMPOS

- [x] Identificador: obligatorio, número interno de la capacitación manejado por la empresa
- [x] RUT cliente: obligatorio, tipo texto largo máximo 15 caracteres.
- [x] Día: texto, día de la semana.
- [x] Hora: texto, largo máximo 5. Debe tener formato HH:MM.
- [x] Lugar: obligatorio, máximo 50 caracteres.
- [x] Duración: obligatorio, número; el valor representa minutos
- [x] Cantidad de asistentes: número

## CÓDIGO SQL PARA CREAR LA BD

    CREATE TABLE Capacitacion.REGISTRO_CAPACITACION (
    ID INT NOT NULL,
    RUT_CLIENTE VARCHAR(15) NOT NULL,
    DIA VARCHAR(10) NULL,
    HORA VARCHAR(5) NULL,
    LUGAR VARCHAR(50) NOT NULL,
    DURACION VARCHAR(10) NOT NULL,
    Q_ASISTENTES VARCHAR(45) NULL,
    PRIMARY KEY (ID));

## MODIFICAR UNA COLUMNA

    ALTER TABLE Capacitacion.REGISTRO_CAPACITACION
    CHANGE COLUMN HORA HORA VARCHAR(5) NULL DEFAULT NULL;

## CAMBIAR A AUTOINCREMENTO LA COLUMNA ID

    ALTER TABLE Capacitacion.Capacitacion`
    CHANGE COLUMN ID ID INT NOT NULL AUTO_INCREMENT ;

## CAMBIA EL NOMBRE DE LA TABLA

    ALTER TABLE Capacitacion.REGISTRO_CAPACITACION
    RENAME TO  Capacitacion.Capacitacion ;

## INSERTAR UN REGISTRO

    INSERT INTO Capacitacion (RUT_CLIENTE, DIA, HORA, LUGAR, DURACION, Q_ASISTENTES) VALUES
    ('159', 'Domingo', '21:00', 'Salón Secundario', 30, 45);

## INSERTAR MÚLTIPLES REGISTROS

    INSERT INTO Capacitacion (RUT_CLIENTE, DIA, HORA, LUGAR, DURACION, Q_ASISTENTES) VALUES
    ('1-9','Lunes','14:00','Salón Principal',30,90),
    ('2-7','Martes','15:00','Salón Secundario',100,45),
    ('3-8','Miércoles','09:00','La Florida',205,100),
    ('1-9','Jueves','11:00','Peñablanca',41,14),
    ('2-7','Viernes','13:00','La Florida',83,74),
    ('7-6','Lunes','15:00','Viña del Mar',94,82),
    ('1-9','Martes','17:00','La Florida',43,14),
    ('2-7','Miércoles','08:30','La Florida',76,45),
    ('8-9','Jueves','19:15','Viña del Mar',99,8),
    ('9-4','Viernes','09:35','Peñablanca',105,70);

    SELECT * FROM Capacitacion;

    +----+-------------+------------+-------+-------------------+----------+--------------+
    | ID | RUT_CLIENTE | DIA        | HORA  | LUGAR             | DURACION | Q_ASISTENTES |
    +----+-------------+------------+-------+-------------------+----------+--------------+
    |  1 | 1-9         | Lunes      | 14:00 | Salón Principal   |       30 |           90 |
    |  2 | 2-7         | Martes     | 15:00 | Salón Secundario  |      100 |           45 |
    |  3 | 3-8         | Miércoles  | 09:00 | La Florida        |      205 |          100 |
    |  4 | 1-9         | Jueves     | 11:00 | Peñablanca        |       41 |           14 |
    |  5 | 2-7         | Viernes    | 13:00 | La Florida        |       83 |           74 |
    |  6 | 7-6         | Lunes      | 15:00 | Viña del Mar      |       94 |           82 |
    |  7 | 1-9         | Martes     | 17:00 | La Florida        |       43 |           14 |
    |  8 | 2-7         | Miércoles  | 08:30 | La Florida        |       76 |           45 |
    |  9 | 8-9         | Jueves     | 19:15 | Viña del Mar      |       99 |            8 |
    | 10 | 9-4         | Viernes    | 09:35 | Peñablanca        |      105 |           70 |
    +----+-------------+------------+-------+-------------------+----------+--------------+
    10 rows in set (0,00 sec)

## MODIFICANDO DATOS DE LOS REGISTROS

    UPDATE Capacitacion SET Q_ASISTENTES = 90 WHERE ID = 1;

## JUGANDO CON LOS REGISTROS

> 1. Cree una consulta que obtenga todos los registros de la tabla sin filtro alguno, mostrando las columnas identificador, hora, dia y rut de cliente (en ese orden).

    SELECT ID, HORA, DIA, RUT_CLIENTE FROM Capacitacion;

    +----+-------------+------------+-------+-------------------+----------+--------------+
    | ID | RUT_CLIENTE | DIA        | HORA  | LUGAR             | DURACION | Q_ASISTENTES |
    +----+-------------+------------+-------+-------------------+----------+--------------+
    |  1 | 1-9         | Lunes      | 14:00 | Salón Principal   |       30 |           90 |
    |  2 | 2-7         | Martes     | 15:00 | Salón Secundario  |      100 |           45 |
    |  3 | 3-8         | Miércoles  | 09:00 | La Florida        |      205 |          100 |
    |  4 | 1-9         | Jueves     | 11:00 | Peñablanca        |       41 |           14 |
    |  5 | 2-7         | Viernes    | 13:00 | La Florida        |       83 |           74 |
    |  6 | 7-6         | Lunes      | 15:00 | Viña del Mar      |       94 |           82 |
    |  7 | 1-9         | Martes     | 17:00 | La Florida        |       43 |           14 |
    |  8 | 2-7         | Miércoles  | 08:30 | La Florida        |       76 |           45 |
    |  9 | 8-9         | Jueves     | 19:15 | Viña del Mar      |       99 |            8 |
    | 10 | 9-4         | Viernes    | 09:35 | Peñablanca        |      105 |           70 |
    +----+-------------+------------+-------+-------------------+----------+--------------+
    10 rows in set (0,00 sec)

>1. Cree una consulta que obtenga todas las capacitaciones que duran una hora, y que tuvieron más de 30 asistentes. Debe desplegar todas las columnas sin un orden solicitado.

    zzSELECT * FROM Capacitacion WHERE DURACION = 60 AND Q_ASISTENTES >30;

    +----+-------------+------------+-------+-------------------+----------+--------------+
    | ID | RUT_CLIENTE | DIA        | HORA  | LUGAR             | DURACION | Q_ASISTENTES |
    +----+-------------+------------+-------+-------------------+----------+--------------+
    |  2 | 2-7         | Martes     | 15:00 | Salón Secundario  |      100 |           45 |
    |  3 | 3-8         | Miércoles  | 09:00 | La Florida        |      205 |          100 |
    |  5 | 2-7         | Viernes    | 13:00 | La Florida        |       83 |           74 |
    |  6 | 7-6         | Lunes      | 15:00 | Viña del Mar      |       94 |           82 |
    |  8 | 2-7         | Miércoles  | 08:30 | La Florida        |       76 |           45 |
    | 10 | 9-4         | Viernes    | 09:35 | Peñablanca        |      105 |           70 |
    +----+-------------+------------+-------+-------------------+----------+--------------+
    6 rows in set (0,00 sec)

> 3. Cree una consulta que obtenga las capacitaciones realizadas por el cliente de RUT 1-9 o 2-7, y que el lugar es “La Florida”. Despliegue todas las columnas en el orden contrario a su definición original.

    SELECT Q_ASISTENTES, DURACION, LUGAR, HORA, DIA, RUT_CLIENTE, ID
    FROM Capacitacion
    WHERE LUGAR = 'La Florida'
    AND (RUT_CLIENTE = '1-9' OR RUT_CLIENTE='2-7');

    +--------------+----------+------------+-------+------------+-------------+----+
    | Q_ASISTENTES | DURACION | LUGAR      | HORA  | DIA        | RUT_CLIENTE | ID |
    +--------------+----------+------------+-------+------------+-------------+----+
    |           74 |       83 | La Florida | 13:00 | Viernes    | 2-7         |  5 |
    |           14 |       43 | La Florida | 17:00 | Martes     | 1-9         |  7 |
    |           45 |       76 | La Florida | 08:30 | Miércoles  | 2-7         |  8 |
    +--------------+----------+------------+-------+------------+-------------+----+
    3 rows in set (0,00 sec)

> 4. Cree una consulta que obtenga todas las capacitaciones que han durado más de media hora, pero menos de una hora y media, o bien que sus asistentes es menos que 10 personas. Se pide mostrar el identificador de una tabla, y los campos indicados en la consulta.

    OPCION A:
        SELECT ID, DURACION, Q_ASISTENTES
        FROM Capacitacion
        WHERE (DURACION > 30 AND DURACION < 90) 
        OR Q_ASISTENTES < 10;

    +----+----------+--------------+
    | ID | DURACION | Q_ASISTENTES |
    +----+----------+--------------+
    |  4 |       41 |           14 |
    |  5 |       83 |           74 |
    |  7 |       43 |           14 |
    |  8 |       76 |           45 |
    |  9 |       99 |            8 |
    +----+----------+--------------+
    5 rows in set (0,00 sec)

    OPCION B:
        SELECT ID, DURACION, Q_ASISTENTES
        FROM Capacitacion
        WHERE (DURACION BETWEEN 30 AND 90) 
        OR Q_ASISTENTES < 10;
        
        TIP: BETWEEN HACE UN CORTE EN EL RANGO CONSULTADO (INCLUYENDO EL NÚMERO CONSULTADO)

    +----+----------+--------------+
    | ID | DURACION | Q_ASISTENTES |
    +----+----------+--------------+
    |  1 |       30 |           90 |
    |  4 |       41 |           14 |
    |  5 |       83 |           74 |
    |  7 |       43 |           14 |
    |  8 |       76 |           45 |
    |  9 |       99 |            8 |
    +----+----------+--------------+
    6 rows in set (0,00 sec)

> 5. Una consulta que obtenga las capacitaciones de los lunes, miércoles y viernes, que tengan más de 50 asistentes y que hayan durado menos de media hora. Debe desplegar los campos que estime prudente.

    SELECT ID, DIA, LUGAR, Q_ASISTENTES
    FROM CAPACITACION
    WHERE (DIA = 'Lunes' OR DIA = 'Miércoles' OR DIA = 'Viernes')
    AND DURACION < 30 
    AND Q_ASISTENTES > 50;

    +----+------------+------------------+--------------+
    | ID | DIA        | LUGAR            | Q_ASISTENTES |
    +----+------------+------------------+--------------+
    |  1 | Lunes      | Salón Principal  |           90 |
    |  3 | Miércoles  | La Florida       |          100 |
    |  6 | Lunes      | Viña del Mar     |           82 |
    |  8 | Miércoles  | La Florida       |           45 |
    +----+------------+------------------+--------------+
    4 rows in set (0,00 sec)
