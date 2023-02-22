# Funciones Agregadas SQL

En esta sección veremos las funciones agregadas: SUM, MIN, COUNT, MAX

- **SUM()** : Vamos a sumar los valores.
- **MIN()** : Nos devolverá el valor minimo de un registro asociado a la columna de la consulta.
- **MAX()** : Nos devolverá el valor máximo de un registro asociado a la columna de la consulta.
- **COUNT** : Esta función lo que hará, será un conteo de registros asociados a la columna de la consulta.
- **AVG()**   : Retorna el promedio en los registros asociados a la columna de la consulta.

## Ejemplos

### SUMAR

    SELECT SUM(precio)
    FROM producto;

    +-------------+
    | sum(precio) |
    +-------------+
    |       77620 |
    +-------------+
    1 row in set (0,02 sec)

### MÍNIMO

    SELECT MIN(precio)
    FROM producto

    +-------------+
    | MIN(precio) |
    +-------------+
    |         700 |
    +-------------+
    1 row in set (0,03 sec)

### MÁXIMO

    SELECT MAX(precio)
    FROM producto;

    +-------------+
    | max(precio) |
    +-------------+
    |       31000 |
    +-------------+
    1 row in set (0,01 sec)

### CONTAR

    SELECT COUNT(id_proveedor)
    FROM proveedor;

    +---------------------+
    | count(id_proveedor) |
    +---------------------+
    |                   5 |
    +---------------------+
    1 row in set (0,01 sec)

### PROMEDIO

    SELECT AVG(precio)
    FROM producto;

    +-------------+
    | AVG(precio) |
    +-------------+
    |   3374.7826 |
    +-------------+
    1 row in set (0,00 sec)
