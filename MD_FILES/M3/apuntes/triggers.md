# Triggers

Es un objeto de una tabla 

Un trigger se puede desencadenar cuando en la tabla ocurra cualquiera de los siguientes eventos:

- INSERT (INSERTAR)
- UPDATE (ACTUALIZAR)
- ELIMINAR (ELIMINAR)

## Cuando se detecta cualquiera de los eventos ¿cuándo específicamente se ejecutan los triggers?

Se pueden ejecutar tanto antes (BEFORE) o después (AFTER) del evento, esto de determina dependiendo de la situación en la que se desee.

    CREATE TABLE REG_PRODUCTOS(
        CODIGOARTICULO VARCHAR(25),
        NOMBREARTICULO PRECIO INT(4),
        INSERTADO DATETIME
    );

