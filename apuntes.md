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
 	~~~
