# M3-ABPRO_7 (MER)

![M3-ABPRO_7[MER]](./assets/img/M3-ABPRO_7%5BMER%5D.png)

## ACTIVIDAD

Una empresa de asesorías en prevención de riesgos necesita contar con un sistema de información
que le permita administrar los principales procesos que se llevan a cabo en ella día a día.
Esta empresa entrega asesoría a diversos clientes. De cada uno de ellos se necesita saber su RUT de la empresa, el nombre y apellido del representante legal, nombre de la empresa y el teléfono de la empresa cliente. A cada uno de estos clientes se le realizan visitas de forma regular; a cada visita en terreno se le asigna un número único de identificación, y se registra la fecha que se hace, la hora, el nombre del lugar que se analizó y comentarios relacionados con la visita.

En cada visita en terreno, la empresa de asesoría tiene un conjunto de chequeos que debe realizar, y por cada visita se debe registrar si ese chequeo se cumple, si se cumple con observaciones, o bien si no se cumple.

Además, la empresa de asesoría realiza capacitaciones a sus clientes, eventos de los que interesa saber el día, hora y lugar. Al mismo tiempo, se requiere saber que personas asistieron a dicha capacitación, almacenando su nombre completo, su edad, correo electrónico y teléfono.
Finalmente, a cada cliente se le ha habilitado un usuario de sistema, el cual será el medio para que la empresa cliente pueda acceder a la plataforma. Cada cliente tiene solo un usuario en sistema, y del usuario se almacena su nombre, apellido, la fecha de nacimiento y el RUN.
Con la información anterior debe crear un modelo entidad relación, estableciendo claramente:

- Entidades (considerar los diversos tipos de entidades)
- Relaciones
- Atributos (destaque atributos primarios, e indique la forma correcta según el tipo de
atributo)

## CÓDIGO MYSQL

### CREAR BASE DE DATOS

    DROP DATABASE IF EXISTS ABPRO_7_PREV_RIESGOS;
    CREATE DATABASE ABPRO_7_PREV_RIESGOS;

### SELECCIONAR BD

    USE ABPRO_7_PREV_RIESGOS;

### CREAR TABLAS

    CREATE TABLE CLIENTE(
        rutCliente INT NOT NULL PRIMARY KEY,
        nombre VARCHAR(50) NOT NULL,
        repLegal VARCHAR(50) NULL,
        telefono INT NULL
    );

    CREATE TABLE VISITAS(
        idVisita INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
        fecha DATE NOT NULL,
        hora TIME NOT NULL,
        lugar VARCHAR(20) NULL,
        comentarios VARCHAR(200) NULL,
        visita_rutCliente INT NOT NULL
    );

    CREATE TABLE RESULTADOVISITA(
        idResultado INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
        resultado_idVisita INT NOT NULL,
        resultado ENUM('CUMPLE','CUMPLE C/OBS','NO CUMPLE') NOT NULL
    );

    CREATE TABLE CAPACITACION(
        idCapacitacion INT NOT NULL PRIMARY KEY,
        dia DATE,
        hora TIME,
        lugar VARCHAR(20),
        capacitacion_idCliente INT NOT NULL
    );

### CREAR FK ENTRE VISITAS Y CLIENTES

    ALTER TABLE VISITAS
    ADD CONSTRAINT visitas_clientes_FK
    FOREIGN KEY (visita_rutCliente) REFERENCES CLIENTE(rutCliente);

### CREAR FK ENTRE RESULTADOVISITA Y VISITAS

    ALTER TABLE RESULTADOVISITA
    ADD CONSTRAINT resultadoVisita_visita_FK
    FOREIGN KEY (resultado_idVisita) REFERENCES VISITAS(idVisita);

### CREAR FK ENTRE CAPACITACION Y CLIENTES

    ALTER TABLE CAPACITACION
    ADD CONSTRAINT capacitacion_clientes_FK
    FOREIGN KEY (capacitacion_idCliente) REFERENCES CLIENTE(rutCliente);

    CREATE TABLE ASISTENTES(
        idAsistente INT NOT NULL PRIMARY KEY,
        nombreCompleto VARCHAR(100) NOT NULL,
        edad INT NOT NULL,
        email VARCHAR(30),
        telefono INT,
        asistentes_idCapacitacion INT NOT NULL
    );

### CREAR FK ENTRE ASISTENTES Y CAPACITACION

    ALTER TABLE ASISTENTES
    ADD CONSTRAINT asistentes_capacitacion_FK
    FOREIGN KEY (asistentes_idCapacitacion) REFERENCES CAPACITACION(idCapacitacion);

    CREATE TABLE USUARIOS(
        idUsuario INT NOT NULL,
        rutCliente INT NOT NULL UNIQUE,
        nombre VARCHAR(20) NULL,
        apellido VARCHAR(20) NULL,
        fechaNac DATE NOT NULL,
        PRIMARY KEY(idUsuario, rutCliente)
    );

### CREAR FK ENTRE USUARIOS Y CLIENTES

    ALTER TABLE USUARIOS
    ADD CONSTRAINT usuarios_clientes_FK
    FOREIGN KEY (rutCliente) REFERENCES CLIENTE(rutCliente);
