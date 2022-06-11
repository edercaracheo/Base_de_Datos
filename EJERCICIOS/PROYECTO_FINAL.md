# Proyecto Final de base de datos.
### Indicaciones de lo que se debe realizar

● Diseña el modelo entidad-relación del siguiente problema.

● Crea el script para la base de datos.
Proveedores

Tenemos que diseñar una base de datos sobre proveedores y disponemos de
la siguiente información:

● De cada proveedor conocemos su nombre, dirección, ciudad, provincia y
un código de proveedor que será único para cada uno de ellos.

● Nos interesa llevar un control de las piezas que nos suministra cada
proveedor. Es importante conocer la cantidad de las diferentes piezas
que nos suministra y en qué fecha lo hace. Tenga en cuenta que un
mismo proveedor nos puede suministrar una pieza con el mismo código
en diferentes fechas. El diseño de la base de datos debe permitir
almacenar un histórico con todas las fechas y las cantidades que nos ha
proporcionado un proveedor.

● Una misma pieza puede ser suministrada por diferentes proveedores.

● De cada pieza conocemos un código que será único, nombre, color,
precio y categoría.

● Pueden existir varias categorías y para cada categoría hay un nombre y
un código de categoría único.

● Una pieza sólo puede pertenecer a una categoría.

![image](https://user-images.githubusercontent.com/101481181/173206498-7725ac7d-cf6d-48f2-aac4-38192f89f751.png)

CREATE DATABASE Compras;
USE Compras;

CREATE TABLE Proveedor(
  id_prov VARCHAR(20) PRIMARY KEY,
  nom_prov VARCHAR(100) NOT NULL,
  direccion_prov VARCHAR(200) NOT NULL,
  provincia VARCHAR(30),
  ciudad VARCHAR(30)
  );
  
 CREATE TABLE Pieza(
   id_pieza INT UNSIGNED PRIMARY KEY,
   fecha_sum DATE NOT NULL,
   cantidad INT NOT NULL,
   nom_pieza VARCHAR(100),
   color VARCHAR(15),
   Precio FLOAT
      
    );
    
  CREATE TABLE Categoria(
    Id_cat INT PRIMARY KEY,
    nom_cat VARCHAR(20),
    id_pieza2 INT UNSIGNED,
    FOREIGN KEY (id_pieza2) REFERENCES Pieza(id_pieza)
    );
    
    CREATE TABLE Suministra(
    id_prov1 VARCHAR(20),
    FOREIGN KEY (id_prov1) REFERENCES Proveedor(id_prov),
    id_pieza1 INT UNSIGNED,
    FOREIGN KEY (id_pieza1) REFERENCES Pieza(id_pieza)
    );  
    
