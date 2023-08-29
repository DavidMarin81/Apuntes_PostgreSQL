- [COMENTARIOS]()
	~~~
 	-- SELECT * FROM alumnos;
	/*
  	CREATE TABLE Alumno (
		idAlumno INT NOT NULL,
		nombre VARCHAR(20),
		apellido VARCHAR(50)
	);
	*/
   	~~~
   	
- [CREAR BBDD]()
	~~~
	CREATE DATABASE MiBaseDeDatos;
	~~~
- [BORRAR BBDD]()
	~~~
	DROP DATABASE IF EXISTS MiBaseDeDatos;
	~~~

 - [CREAR TABLA]()
	~~~
	CREATE TABLE Alumno (
		idAlumno INT NOT NULL,
		nombre VARCHAR(20),
		apellido VARCHAR(50)
	);
	~~~
 	~~~
  	-- Creando tabla con PK y AUTOINCREMENT
	-- Serial = tipo de dato para autoincrementales
	CREATE TABLE alumno2 (
		idAlumno SERIAL PRIMARY KEY NOT NULL,
		nombre VARCHAR(20),
		apellido VARCHAR(50)
	);
  	~~~
  	~~~
   	-- Crear tabla con valores por defecto
	CREATE TABLE alumno3 (
	idAlumno SERIAL PRIMARY KEY NOT NULL,
	nombre VARCHAR(20),
	apellido VARCHAR(50),
	telefono varchar(9) DEFAULT 'X'
	);
	~~~
   	- *Para ver la tabla en PostgreSQL -> MiBaseDeDatos / Schemas / public / Tables / Alumno*
- [INSERTAR DATOS]()
	~~~
	INSERT INTO alumno values ('1', 'Patricia', 'Cid');
	INSERT INTO alumno (nombre, idAlumno) values ('Xian', '2');
	~~~
- [MODIFICAR DATOS]()
	~~~
	UPDATE alumno SET apellido = 'Marin' WHERE idAlumno = '3';
	UPDATE alumno SET apellido = 'En blanco' WHERE apellido IS NULL;
	UPDATE alumno SET nombre = 'Lara', apellido = 'Martinez' WHERE idAlumno = '4';
	~~~
- [TIPOS DE DATOS]()
  	- Boolean = true or false;
 	- Varchar(n) = cadena de caracteres de tamaño variable
  	- Character(n) = cadena de caracteres de tamaño fijo
  	- date = fecha (sin hora)
  	- Float = flotante
  	- Int, Integer = numero entero
  	- Decimal = numero exacto
  	- time = horas, minutos, segundos, etc
- [CONSULTAS DE DATOS]()
	~~~
	SELECT * FROM alumno;
	SELECT idAlumno as ID, nombre as NAME FROM alumno;
	SELECT * FROM alumno WHERE nombre = 'David';
	SELECT * FROM alumno WHERE nombre != 'David';
	SELECT * FROM alumno WHERE idAlumno > '1';
	SELECT * FROM alumno WHERE idAlumno > '1' AND apellido = 'Marin';
 	SELECT * FROM MOVIES WHERE ID (SELECT ID FROM MOVIES WHERE "YEAR" > 1995);
	~~~
 - [SUBCONSULTAS DE DATOS]()
	~~~
 	-- Para cuando la consulta devuelve un valor
 	SELECT * FROM MOVIES WHERE ID = (SELECT ID FROM MOVIES WHERE "YEAR" = 2008;
 	-- Para cuando la consulta devuelve un grupo de valores
 	SELECT * FROM MOVIES WHERE ID IN (SELECT ID FROM MOVIES WHERE "YEAR" > 1995);
	~~~
- [ELIMINAR DATOS]()
	~~~
	DELETE FROM alumno WHERE idAlumno = '5';
	~~~
- [MODIFICAR COLUMNAS]()
	~~~
	-- Añadir columna
	ALTER TABLE alumno ADD COLUMN dni varchar(20);
	~~~
 
 	~~~
	-- Modificar nombre de la columna
	ALTER TABLE alumno RENAME COLUMN dni to pasaporte;
	~~~
  
  	~~~
	-- Eliminar columna
	ALTER TABLE alumno DROP COLUMN pasaporte;
	~~~
   
   	~~~
	-- Modificar la columna para que no acepte valores nulos
	-- Para hacer esto, no puede haber datos "not null" en la tabla
	UPDATE alumno SET dni = 'Sin introducir';
	-- Ahora ya se puede estableces que no acepte valores nulos
	ALTER TABLE alumno ALTER COLUMN dni SET NOT NULL;
   	~~~
    
  	~~~
	-- Quitarle el valor NOT NULL, para que acepte valores nulos
	ALTER TABLE alumno ALTER COLUMN dni DROP NOT NULL;
	~~~

 	~~~
	-- Modificar el tipo de dato de la columna
	-- Hay que tener cuidado si ya hay datos introducidos
	ALTER TABLE alumno ALTER COLUMN dni TYPE VARCHAR(50);
  	~~~
  
	~~~
 	-- Modificando la tabla para añadirle un PK
	ALTER TABLE alumno ADD PRIMARY KEY (idAlumno);
	~~~
 - [ORDER BY]()
	~~~
	SELECT * FROM alumno ORDER BY idAlumno DESC;
	~~~
 - [LIKE, ILIKE, NOT LIKE, NOT ILIKE]()
   	- ILIKE = no tiene en cuanta mayúsculas ni minúsculas
   	- % = cero o más caracteres
   	- _ = un solo caracter
	~~~
	-- Que empiece por 0 o + caracteres, que contenga la 'i' y que termine por un caracter cualquiera
 	SELECT * FROM alumno WHERE nombre LIKE '%i_';
	~~~
 - [COUNT]()
	~~~
	SELECT COUNT(*) from alumno WHERE nombre LIKE '%i_';
	~~~
 	~~~
	SELECT COUNT(DISTINCT DIRECTORID) FROM MOVIES; /* Cuenta los ids de los directores sin repetrilos */
	~~~
 - [SUM]()
	~~~
	SELECT SUM(salario) from alumno WHERE nombre LIKE '%I_';
	~~~
- [MAX(), MIN(), GROUP BY]()
  	- MAX()
	~~~
	SELECT MAX(idAlumno) from alumno;
	~~~
 	- MIN()
	~~~
	SELECT MIN(idAlumno) from alumno;
	~~~
 	- GROUP BY
	~~~
	-- agrupa todos los apellidos, los muestra y, de cada apellido, muestra el valor más pequeño
	SELECT apellido, MIN(salario) FROM alumno GROUP BY apellido;
	~~~
 	- HAVING
	~~~
	SELECT DIRECTORID, COUNT(ID) FROM MOVIES GROUP BY DIRECTORID HAVING COUNT(ID) > 1;
	~~~
 - [AVG]()
	~~~
	SELECT AVG(Salario) FROM alumno;
	~~~
