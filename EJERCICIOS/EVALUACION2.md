## Práctica 3.
### Introducción a SQL
Objetivo: Demostrar la correcta identificación de los conceptos del lenguaje SQL
Ejercicio:

1. Menciona los comandos DMl: (valor .85)

SELECT: Encargado de consultar registros de la base de datos que satisfagan un criterio determinado.

INSERT: Encargado de cargar lotes de datos en la base de datos en una única operacion.

UPDATE: Encargado de modificar los valores de los campos y registros especificados.

DELETE: Encargado de eliminar registros de una tabla.

2. Menciona 3 tipos de datos que existen: (valor .85)

VARCHAR(X): Define una cadena de longitud variable, con una longitud maxima especificada por el usuario. La forma completa, character varying. 

BIGINT: Un entero grande (numeros).

FLOAT: UN NUMERO DE COMA FLOTANTE CUYA PRECISION ES, AL MENOS, DE N DIGITO
3. ¿Qué diferencia existe entre TRUNCATE y DELETE?(valor .85)

truncate elimina el contenido pero sin borrar la tabla, asimismo los contadores los resetea a 0, al contrario delete elimina de forma selectiva elementos de la tabla, sin embargo, truncate es la forma mas rapida de eliminar el contenido de una tabla.

4. ¿Para qué se utiliza el atributo UNIQUE?(valor .85)

Nos permite establecer este atributo a los campos que requerimos tengan datos que no se puedan repetir.


5. ¿Qué diferencia hay entre los tipos de datos VARCHAR y CHAR? (valor .85)

En VARCHAR los caracteres son variables, con una longitud maxima, pero puede ser menos, al contrario el char, es fija y necesita que la longitud completa sea ocupada. Como dato, el char al ser fijo ocupa memoria estatica y el varchar ocupa memoria dinamica, siendo esta ultima mas lenta que char.

6. Defina brevemente el significado de las siglas SQL(valor .85)

Lenguaje de consulta estructurado. Brinda la posibilidad de realizar consultas con el objetivo de recuperar informacion de las bases de datos de manera sencilla.

7. Defina brevemente qué es MySQL WorkBench (valor .85)
Es un editor de base de datos pero grafico.

## Práctica 5.
### Gestores de base de datos

Objetivo: Categorizar los distintos gestores de base de datos que existen y señalar las
ventajas y desventajas

Evaluación: Conoce los tipos de gestores de base de datos 3 puntos.

Domina sus diferencias de los gestores de base de datos mencionados 3 puntos

Ejercicio:

En un mapa conceptual presenta 3 gestores de bases de datos, sus características
principales, las ventajas y desventajas. (valor 6)

![image](https://user-images.githubusercontent.com/91554777/170415427-e2b7321b-a97f-43b0-ac24-6e506c307e6b.png)

![image](https://user-images.githubusercontent.com/101481181/173198192-6752d257-313f-46b8-906e-b19d893cb131.png)


## Práctica 6.
### Herramienta en línea y ejercicio necesarios para realizar las prácticas

Creación de base de datos.

Objetivo: Demostrar mediante la creación de una base de datos el uso y la aplicación de
las funciones

Ejercicio: Creación de la base de datos (valor 18 puntos)

Tienda de informática

![image](https://user-images.githubusercontent.com/91554777/170415101-717bca19-3644-46a9-8a57-8d5940c5d283.png)




Modelo entidad/relación

![image](https://user-images.githubusercontent.com/101481181/173207910-f7bcfef4-702c-43b8-9c63-e497f62997d7.png)

Base de datos para MySQL

CREATE DATABASE Tienda;

USE Tienda;


CREATE TABLE producto(

  id_prod VARCHAR(10) PRIMARY KEY,
  
  nom_prod VARCHAR(50) NOT NULL,
  
  precio FLOAT NOT NULL,
  
  nom_fab VARCHAR(50) NOT NULL
  
  );
  
  INSERT INTO producto VALUES ('DD-23','Disco Duro SATA3 1 TB',86.99,'SEAGATE');
  
  INSERT INTO producto VALUES ('MM-34','MEMORIA RAM DDR4 8GB',120.6,'CRUCIAL');
  
  INSERT INTO producto VALUES ('DD-98','DISCO SSD 1 TB',150.99,'SAMSUNG');
  
  INSERT INTO producto VALUES ('MM-98','GEFORCE GTX 1050TI',185.7,'GIGABYTE');
  
  INSERT INTO producto VALUES ('MM-23','GEFORCE GTX 1080 EXTREME',755.6,'CRUCIAL');
  
  INSERT INTO producto VALUES ('MT-12','MONITOR 24 LED FULL HD',202.1,'ASUS');
  
  INSERT INTO producto VALUES ('MT-08','MONITOR 27 LED FULL HD',245.99,'ASUS');
  
  INSERT INTO producto VALUES ('LP-19','PORTATIL YOGA 520',559.2,'LENOVO');
  
  INSERT INTO producto VALUES ('LP-11','PORTATIL IDEAPAD 320',444.2,'LENOVO');
  
  INSERT INTO producto VALUES ('IM-56','IMPRESORA HP DESKJET 3720',59.99,'HP');
  
  INSERT INTO producto VALUES ('IP-54','IMPRESORA HP LASERJET PRO M26NW',180.3,'HP');
  
  



