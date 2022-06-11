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
CREATE DATABASE editorial;
USE editorial;

--CREANOS LA TABLA SUCURSAL
CREATE TABLE sucursal(
    codigo_de_sucursal INT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    domicilio CHAR(100) NOT NULL,
    telefono BIGINT UNSIGNED NOT NULL
);

INSERT INTO sucursal VALUES(01,'Tenayuca 15, Colonia Porvenir',5573485948);
INSERT INTO sucursal VALUES(02,'Ahuehuetes 24, Colona Reynosa',3395847649);
INSERT INTO sucursal VALUES(03,'	San Juan 12, Colonia Electricistas',7293840947);
INSERT INTO sucursal VALUES(04,'Manuel Buendía 948, Colonia Reforma',8293459375);
INSERT INTO sucursal VALUES(05,'Petroleos 12, Cpolonia Alabama',7394850983);
INSERT INTO sucursal VALUES(06,'Petén 1209, Roma Norte',5587394785);
INSERT INTO sucursal VALUES(07,'Tlahuac 10, Colonia Reyes',4593849058);
INSERT INTO sucursal VALUES(08,'Anaxagoras 15, Polanco',3384909859);
INSERT INTO sucursal VALUES(09,'Miguel Hidalgo 98, Colonia Angustura',3338930403);
INSERT INTO sucursal VALUES(10,'Cervantes 56, Colonia Juárez',2288473845);


--CREAMOS LA TABLA REVISTA
 CREATE TABLE revista(
   numero_de_registro INT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
   titulo VARCHAR(100) NOT NULL,
   tipo VARCHAR(100) NOT NULL,
   periodicidad VARCHAR(100)
 );
 
 INSERT INTO revista VALUES(098,'POLITICA HOY','POLITICA','SEMANAL');
 INSERT INTO revista VALUES(099,'EMOCION 			   DEPORTIVA','DEPORTIVA','QUINCENAL');
 INSERT INTO revista VALUES(100,'MUNDO ROSA','ESPECTACULOS','SEMANAL');
 INSERT INTO revista VALUES(101,'VIDEOGAMER','VIDEOJUEGOS','MENSUAL');
 INSERT INTO revista VALUES(102,'CINE HOY','CINE','	SEMANAL');
 INSERT INTO revista VALUES(103,'TODO EN CULTURA','CULTURAL','MENSUAL');


--CREAMOS TABLA PERIODISTAS 
 CREATE TABLE periodistas(
   nif INT UNSIGNED PRIMARY KEY,
   nombre_periodista VARCHAR(50) NOT NULL,
   apellidos_periodista VARCHAR (50) NOT NULL,
   telefono_periodista BIGINT UNSIGNED NOT NULL,
   especialidad VARCHAR (70) NOT NULL
 );
 
 INSERT INTO periodistas VALUES(01,'KARLA','JUAREZ PEREZ',5534563748,'DEPORTES');
 INSERT INTO periodistas VALUES(02,'BEATRIZ','LOPEZ ANGELES	',7289467349,'POLITICA');
 INSERT INTO periodistas VALUES(03,'TITO','MARQUEZ GALINDO',8203978465,'ESPECTACULOS');
 INSERT INTO periodistas VALUES(04,'ISABEL','SUAREZ	JIMENEZ',8263748987,'VIDEOJUEGOS');
 INSERT INTO periodistas VALUES(05,'PABLO','FERNANDEZ DUARTE',5523784938,'CINE');
 INSERT INTO periodistas VALUES(06,'SERGIO','INFANTE MORALES',7238946574,'CINE');
 INSERT INTO periodistas VALUES(07,'CARLOS','GUIZAR	CISNEROS',3398475840,'CULTURA');
 INSERT INTO periodistas VALUES(08,'JUAN','SALAS MACIAS',5682394848,'DEPORTES');
 INSERT INTO periodistas VALUES(09,'PEDRO','RICO GARAY',5548738495,'POLITICA');
 INSERT INTO periodistas VALUES(10,'ANGEL','HERAS FUENTES',8236475894,'VIDEOJUEGOS');
 INSERT INTO periodistas VALUES(11,'CESAR','SAN PEDRO RODRIGUEZ',4585968495,'CINE');
 INSERT INTO periodistas VALUES(12,'MAGDA','LIRA SANCHEZ',7683749504,'POLITICA');

 
 --CREAMOS TABLA EMPLEADOS
 CREATE TABLE empleados(
   nif INT UNSIGNED PRIMARY KEY,
   nombre_empleado VARCHAR(50) NOT NULL,
   apellidos_empleado VARCHAR (50) NOT NULL,
   telefono_empleado BIGINT UNSIGNED NOT NULL,
   codigo_de_sucursal1 INT UNSIGNED,
   FOREIGN KEY (codigo_de_sucursal1) REFERENCES sucursal (codigo_de_sucursal)
    
 );
 
 INSERT INTO empleados VALUES(01,'ANGELICA','BLANCAS MIRANDA',5534563748,01);
 INSERT INTO empleados VALUES(02,'DAVID','ASPEITIA ESCOBEDO', 7289467349,02);
 INSERT INTO empleados VALUES(03,'ANGEL','GALINDO HERAS',8203978465,03);
 INSERT INTO empleados VALUES(04,'ISMAEL','FERNANDEZ HERNADEZ',8263748987,04);
 INSERT INTO empleados VALUES(05,'MAURICIO','ANDA JUAREZ',5523784938,05);
 INSERT INTO empleados VALUES(06,'ALONSO','BLANCO ANGELES',7238946574,06);
 INSERT INTO empleados VALUES(07,'ALMA','SALAZAR HUERTA',3398475840,07);
 INSERT INTO empleados VALUES(08,'BLANCA','SANTOS SANTIAGO',5682394848,08);
 INSERT INTO empleados VALUES(09,'IGNACIO','HERNANDEZ HERNNDEZ',5548738495,09);
 INSERT INTO empleados VALUES(10,'MAURICIO','MARQUEZ CHAVEZ',8236475894,10);
  INSERT INTO empleados VALUES(11,'ANGEL','JUAREZ LEON',7658495857,01);
   INSERT INTO empleados VALUES(12,'DANIEL','FRI LUCAS',5564738943,01);
  CREATE TABLE secciones(
   id INT UNSIGNED PRIMARY KEY, 
   extension VARCHAR(30) NOT NULL,
   titulo VARCHAR(30) NOT NULL,
   numero_de_registro3 INT UNSIGNED ,
  FOREIGN KEY (numero_de_registro3) REFERENCES revista(numero_de_registro)
 );
 

  INSERT INTO secciones VALUES(1,'esp','espectaculos',100); 
 INSERT INTO secciones VALUES(2,'dep','deportes',099);
 INSERT INTO secciones VALUES(3,'pol','politica',098);
 INSERT INTO secciones VALUES(4,'cin','cine',103);
 INSERT INTO secciones VALUES(5,'hog','hogar',103);
 INSERT INTO secciones VALUES(6,'esp','cultura',103);
 INSERT INTO secciones VALUES(7,'vid','videojuegos',101);
 

 --CREAMOS LA TABLA ejemplares
 CREATE TABLE ejemplares(
   ID INT UNSIGNED PRIMARY KEY,
   numero_de_paginas INT UNSIGNED,
   ejemplares_vendidos INT UNSIGNED,
   fecha DATE NOT NULL,
   numero_de_registro4 INT UNSIGNED ,
  FOREIGN KEY (numero_de_registro4) REFERENCES revista(numero_de_registro)
 );
 

 INSERT INTO ejemplares VALUES(01,'56','4855','2021-09-23',098);
 INSERT INTO ejemplares VALUES(02,'89','1234','2021-09-30',099);
 INSERT INTO ejemplares VALUES(03,'78','5343','2021-10-09',100);
 INSERT INTO ejemplares VALUES(04,'90','5654','2022-04-06',101);
 INSERT INTO ejemplares VALUES(05,'100','3434','2022-03-15',102);
 INSERT INTO ejemplares VALUES(06,'100','6546','2021-06-01',103);
 INSERT INTO ejemplares VALUES(07,'56','4534','2022-05-15',103);
 
 --CREAMOS LA TABLA INTERMEDIA
 CREATE TABLE publican(
   codigo_de_sucursal2 INT UNSIGNED,
  FOREIGN KEY (codigo_de_sucursal2) REFERENCES sucursal(codigo_de_sucursal),
   numero_de_registro1 INT UNSIGNED,
   FOREIGN KEY (numero_de_registro1) REFERENCES revista(numero_de_registro)
 );
 
 
INSERT INTO publican VALUES(01,098); 
INSERT INTO publican VALUES(02,099); 
INSERT INTO publican VALUES(03,100); 
INSERT INTO publican VALUES(04,101);
INSERT INTO publican VALUES(05,102);
INSERT INTO publican VALUES(06,103);
INSERT INTO publican VALUES(07,098);
INSERT INTO publican VALUES(08,099);
INSERT INTO publican VALUES(09,100);
INSERT INTO publican VALUES(10,101);
 
 --CREAMOS LA OTRA TABLA INTERMEDIA
 CREATE TABLE trabajan(
   numero_de_registro2 INT UNSIGNED,
   FOREIGN KEY (numero_de_registro2) REFERENCES revista(numero_de_registro),
   nif1 INT UNSIGNED,
   FOREIGN KEY ( nif1 ) REFERENCES periodistas(nif)
 );
 
 INSERT INTO trabajan VALUES(099,01);
 INSERT INTO trabajan VALUES(098,02);
 INSERT INTO trabajan VALUES(100,03);
 INSERT INTO trabajan VALUES(101,04);
 INSERT INTO trabajan VALUES(102,05);
 INSERT INTO trabajan VALUES(102,06);
 INSERT INTO trabajan VALUES(098,07);
 INSERT INTO trabajan VALUES(099,08);
 INSERT INTO trabajan VALUES(103,09);
 INSERT INTO trabajan VALUES(101,10);
 INSERT INTO trabajan VALUES(102,11);
 INSERT INTO trabajan VALUES(098,12);
 
 
 
 
 
