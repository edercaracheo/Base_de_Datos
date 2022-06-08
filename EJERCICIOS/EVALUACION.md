## Práctica 1.

1. Introducción a base de datos

Objetivo: Identificar el nivel de comprensión de los conceptos de base de datos,
mediante preguntas abiertas.
 
Preguntas:

1. ¿Cuáles son las cinco funciones principales del administrador de bases de datos?
(valor 1.5)

-Asegurar el buen funcionamiento de las BD
-Retención de información de las BD
-Evitar pérdida de datos
-Solucionar incidencias y pérdidas de datos
-Asegurar la seguridad de los datos

2. Indíque cinco responsabilidades del sistema gestor de bases de datos (valor 1.5)

-Instalar, configurar y gestionar bases de datos.
-Dar soporte al equipo de desarrollo, seguridad informática y redes.
-Definir el esquema del diccionario de datos.
-Especificar restricciones de integridad para asegurar los datos.
-Garantizar la alta disponibilidad de la base de datos.


3. En una BD al usuario del sistema se le brindarán recursos para realizar diversas
operaciones sobre estos archivos, tales como: (valor 1.5)

La supervisión del rendimiento, el ajuste, la copia de seguridad y la recuperación.

4. ¿Qué es un Sistema de Información? (valor 1.5)

Conjunto de elementos orientados al tratamiento y administración de datos e información, organizados y listos para su posterior uso, generados para cubrir necesidad.



## Práctica 2.

2. Diseño de un modelo relacional

Objetivo: Representar desde un modelo entidad relación un problema


Ejercicio:

Tenemos que diseñar una base de datos sobre proveedores y disponemos de la siguiente
información:

Realiza el modelo entidad relación. (valor 6)

Tenemos esta información sobre una cadena editorial:

● La editorial tiene varias sucursales, con su domicilio, teléfono y un código de
sucursal.

● Cada sucursal tiene varios empleados, de los cuales tendremos su nombre,
apellidos, NIF y teléfono. Un empleado trabaja en una única sucursal.

● En cada sucursal se publican varias revistas, de las que almacenaremos su título,
número de registro, periodicidad y tipo.

● Una revista puede ser publicada por varias sucursales.

● La editorial tiene periodistas (que no trabajan en las sucursales) que pueden
escribir artículos para varias revistas. Almacenaremos los mismos datos que para
los empleados, añadiendo su especialidad.

● También es necesario guardar las secciones fijas que tiene cada revista, que
constan de un título y una extensión.

● Para cada revista, almacenaremos información de cada ejemplar, que incluirá la
fecha, número de páginas y el número de ejemplares vendidos.

![image](https://user-images.githubusercontent.com/101481181/172019421-e09b7ccc-4ad0-45e0-91c5-c3a8545c0586.png)

codigo

CREATE DATABASE PROVEEDORES;
USE PROVEEDORES;

CREATE TABLE SUCURSAL (
  cod_suc varchar(50) PRIMARY KEY,
  DIR_SUR varchar(200) NOT NULL,
  TEL_SUC bigint unsigned not null unique,
  CIUDAD varchar(100),
  PROVINCIA_SUC varchar(100) not null
  );
  
  
  create table revista (
    numero_registro varchar(100) primary key,
    titulo varchar (100) not null unique,
    tipo_rev varchar(100) unique,
    periodicidad varchar(100)
    );
    
    
    create table periodista(
      id_per varchar(50) primary key,
      nom_per varchar(100) unique not null,
      apellido1_per varchar(100) not null,
      apellido2_per varchar(100) not null,
     tel_per bigint unique not null, 
     especialidad varchar(100) not null
     );
     
     create table empleado(
       nif varchar(50) primary key,
       nom_emp varchar(100) not null,
       apellido1_emp varchar(100) not null,
       apellido2_emp varchar(100) not null,
       tel_emp bigint unique not null,
       cod_suc1 varchar(50),
       foreign key(cod_suc1) references SUCURSAL(cod_suc)
       
       );
