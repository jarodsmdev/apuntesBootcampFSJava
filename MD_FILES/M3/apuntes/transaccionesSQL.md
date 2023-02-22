# Transacciones SQL

## ¿Qué es una transacción y porqué son importantes?

Una transacción es una unidad de trabajo que se realiza en una base de datos.  Las transacciones son unidades o secuencias de trabajo realizadas en un órden lógico, ya sea de forma manual por un usuario o automáticamente por algún tipo de programa de base de datos.

Una transacción es la propagación de uno o más cambios a la base de datos.  Por ejemplo, si está creando, actualizando o eliminando un registro de una tabla, entonces se está realizando una transacción en la tabla.  Es importante controlar las transacciiones para garantizar la integridad de los datos y manejar los errores de la base de datos.

En la práctica, se usa para agrupar múltiples consultas y ejecutarlas todas juntas como parte de una transacción.  A fin de entender la importancia de este concepto, se explicará en primer lugar la diferencia entre las tablas MyISAM e innoDB.

## Características de MyISAM

- Se establece por defecto cuando se crea una tabla, salvo que se indique lo contrario
- Soporta transacciones
- Realiza bloqueo de registros
- Soporta un gran número de consultas SQL, lo que se refleja en una velociadad de carga muy rápida para nuestra web

Como desventaja, señalamos que no realiza bloqueo de tablas, esto puede ser un problema si como se ha mencionado anteriormente hay un acceso simultáneo al mantenimiento de registros por parte de varios usuarios.

## Características de innoDB

- Bloqueo de registros, importante para accesos múltiples al mantenmiento de tablas, es decir, ejecuciones de sentencias tipo INSERT o UPDATE, éstas ejecuciones tienen una velociadad optimizada
- Capacidad para soportar transacciones e integridad de datos, es decir previene el alta de datos no adecuados
- Aplica las caracteristicas propias ACID (Atomicity, Consistency, Isolation and Durability), consistentes en garantizar la integridad de las tablas.

Como desventaja, marcamos que al ser un tipo de motor que define un sistema más complejo de diseño de tablas, reduce el rendimiento en velocidad para desarrollo que requieren de un elevado número de consultas.

## ¿Qué tipo de tablas usar?

Se pueden dar las siguientes situaciones:

- Un solo gestor de mantenimiento para una plataforma que requerirá muchas consultas o visitas: **MyISAM**
- Necesitas velocidad y mínimo consumo de recursos en servidor, espacio, RAM, etc: **MyISAM**
- Varios o muchos gestores de mantenimiento: **InnoDB**
- Desarrollo dónde se prioriza el diseño relacional de bases de datos: **InnoDB**

Independientemente del sistema que se elija, hay que hacer un buen diseño de la estructura y funcionalidad de la base de datos.  Al mismo tiempo, la información o datos no deben almacenarse de cualquier manera.  Hay que buscar el mayor aprovechamiento de los recursos que que tenemos a nuestra disposición, tanto a nivel de almacenamiento como de rendimiento.

Además, hay que mantener la consistencia de la información durante todo el ciclo de vida de la base de datos, más aún si los datos que se manejan son críticos; por ejemplo, los salarios de una organización.

Los primeros factores que realizará el analista serán el análisis del sistema, que servirá de modelo, la observación de los elementos que lo componen y la descomposición en partes mucho más pequeñas.
Las tablas de tipo innoDB están estructuradas en dorma distinta que MyISAM, ya que se almacenan en un sólo archivo en lugar de tres, y sus principales características son que permite trabajar con transacciones, y definir reglas de integridad referencial.

El soporte de transaccones que provee MySQL, no es algo nuevo en él, ya que desde la versión 3.23 se podía hacer uso de las tablas innoDB; la única diferencia es que con la llegada de la versión 4.0 de MySQL, el soporte para este tipo de tablas es habilitado por default.

Las transacciones aportan una fiabilidad superior a las bases de datos.  Si disponemos de una serie de consultas SQL que deben ejecutarse en conjunto, con el uso de transaccones podemos tener la certeza de que nunca nos quedaremos a medio camino de su ejecución.  De hecho, podríamos decir que las transacciones aportan una característica de "deshacer" a las aplicaciones de bases de datos.

Para este fin, las tablas que soportan transacciones, como es el caso de InnoDB, son mucho más seguras y fáciles de recuperar si se produce algún fallo en el servidor, ya que las consultas **se ejecutan** o **no en su totalidad**.  Por otra parte, las transacciones pueden hacer que las consultas tarden más tiempo en ejecutarse.

## Propiedades de las transacciones

Las transacciones tienen las siguientes cuatro propiedades estándar, a las que generalmente hace referencia con el acrónimo **ACID** (Atomicity, Coherence, Isolation, Durability):

- **Atomicidad:** Garantiza que todas las operaciones dentro de la unidad de trabajo se completen con éxito; de lo contrario, la transacción se aborta en el punto de fall y las operaciones anteriores se revierten a su estado anterior.
- **Coherencia:** Garantiza que la base de datos cambie correctamente de estado tras una transacción confirmada con éxito.
- **Aislamiento:** Permite que las transacciiones funcionen de forma independiente y transparente entre sí.
- **Durabilidad:** Asegura que el resultado o efecto de una transacción comprometida persista en caso de falla de sistema.

## Confirmación de una transacción

Los comandos de control transaccional se utilizan con los comandos **DML (Data Manipulation Language)** **INSERT, UPDATE, y DELETE** únicamente. No se pueden usar al crear o descartarlas porque estas operaciones se confirman automáticamente en la base de datos.

Las transacciones se pueden iniciar usando **START**.  Estas transacciones generalmente persisten hasta que se encuentra el siguiente comando **COMMIT O ROLLBACK**.  Una transacción también hara ROLLBACK si la base de datos se cierra o si ocurre un error.

La siguiente es la sintaxis simple para iniciar una transacción:

    BEGIN TRANSACTION;

El comando COMMIT es el comando transaccional que se utiliza para guardar los cambios invocados por una transaccion en la base de datos.  Este comando guarda todas las transacciones en la base de datos desde el último comando COMMIT o ROLLBACK.

La sintaxis del comando COMMIT es la siguiente:

    COMMIT;

## Vuelta atrás de una transacción

El comando ROLLBACK es el comando transaccional que se utiliza para deshacer transacciones que aún no se han guardado en la base de datos.  El comando ROLLBACK sólo se puede utilizar para deshacer transacciones desde que se emitió el último comando COMMIT o ROLLBACK.

La sintaxis del comando ROLLBACK es la siguiente:

    ROLLBACK;

## El autocommit

El modo autocommit indica si los resultados de las consultas DML realizadas serán almacenadas directamente en la base de datos.  Por defecto este dato es igual a VERDADERO, lo que significa que , por defecto, las transacciones se reflejarán inmediatamente.
Sin embargo, este modo se puede desactivar, al fin de poder confirmar o deshacer el resultado de una transacción.  Después de deshabilitar el modo de confirmación automática, estableciendo la variable de confirmación automática en cero, los cambios en las tablas de transacciones seguras (como las de innoDB o NDB) no se hacen permanente de inmediato.  Debe utilizar COMMIT para almacenar sus cambios en el disco o ROLLBACK para ignorar los cambios.

El **autocommit** es una variable de sesión y debe configurarse para cada sesión.  Para entender mejor este punto, haremos un ejemplo:

En primer lugar, iniciamos la transacción
Desactiva el autocommit
Inserta dos registros en la tabla profesor
Muestra los registros existentes
Usa un comando para deshacer la acción
Muestra los registros existentes
Activa el autocommit

    START TRANSACTION;
    SET autocommit = 0;
    INSERT INTO profesor VALUES (10,'Alfonsina', 'Araya', 'Escuela D-255', '2021-01-01', 600000);
    INSERT INTO profesor VALUES (11, 'Bernardo', 'Bustos', 'Escuela Z-001', '2021-02-02', 850000);
    SELECT * FROM profesor;
    ROLLBACK;
    SELECT * FROM profesor;
    SET autocommit = 1;

La primera consulta de selección mostrará la misma data que la segunda consulta de selección ya que al hacer ROLLBACK de deshacen los cambios.