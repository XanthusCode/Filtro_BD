# Examen Bases de datos

Natalia Giraldo

Johan ALexander Garcia Campos



1. Obtener los nombres de todos los actores y las películas en las que han actuado.

```sql
SELECT  actor.nombre, pelicula.titulo
FROM pelicula_actor
INNER JOIN actor ON pelicula_actor.id_actor = actor.id_actor
INNER JOIN pelicula  ON pelicula_actor.id_pelicula = pelicula.id_pelicula;

+-------------+-----------------------------+
| nombre      | titulo                      |
+-------------+-----------------------------+
| PENELOPE    | ACADEMY DINOSAUR            |
| PENELOPE    | ANACONDA CONFESSIONS        |
| PENELOPE    | ANGELS LIFE                 |
| PENELOPE    | BULWORTH COMMANDMENTS       |
| PENELOPE    | CHEAPER CLYDE               |
| PENELOPE    | COLOR PHILADELPHIA          |
| PENELOPE    | ELEPHANT TROJAN             |
| PENELOPE    | GLEAMING JAWBREAKER         |
| PENELOPE    | HUMAN GRAFFITI              |
| PENELOPE    | KING EVOLUTION              |
| PENELOPE    | LADY STAGE                  |
| PENELOPE    | LANGUAGE COWBOY             |
| PENELOPE    | MULHOLLAND BEAST            |
| PENELOPE    | OKLAHOMA JUMANJI            |
| PENELOPE    | RULES HUMAN                 |
| PENELOPE    | SPLASH GUMP                 |
| PENELOPE    | VERTIGO NORTHWEST           |
| PENELOPE    | WESTWARD SEABISCUIT         |
| PENELOPE    | WIZARD COLDBLOODED          |
| NICK        | ADAPTATION HOLES            |
| ALAN        | CRAZY HOME                  |
+-------------+-----------------------------+
5462 rows in set (0,01 sec)
```

2. Listar todos los clientes y los almacenes donde están registrados.

```sql
SELECT c.nombre, c.apellidos, almacen.id_almacen
FROM cliente AS c
JOIN almacen ON c.id_almacen = almacen.id_almacen;

+-------------+--------------+-----------------+
| nombre      | apellidos    | id_almacen      |
+-------------+--------------+-----------------+
| PEPE        | LÓPEZ        | 2               |
| MARÍA       | SÁNCHEZ      | 2               |
+-------------+--------------+-----------------+
601 rows in set (0,00 sec)
```

3. Encontrar todas las películas y sus respectivas categorías.

```sql
SELECT pelicula.titulo, categoria.nombre
FROM pelicula
JOIN pelicula_categoria  ON pelicula.id_pelicula = pelicula_categoria.id_pelicula
JOIN categoria ON pelicula_categoria.id_categoria = categoria.id_categoria;

+-----------------------------+-------------+
| titulo                      | nombre      |
+-----------------------------+-------------+
| AMADEUS HOLY                | Action      |
| AMERICAN CIRCUS             | Action      |
| ANTITRUST TOMATOES          | Action      |
| ARK RIDGEMONT               | Action      |
| BAREFOOT MANCHURIAN         | Action      |
| BERETS AGENT                | Action      |
| BRIDE INTRIGUE              | Action      |
| BULL SHAWSHANK              | Action      |
| CADDYSHACK JEDI             | Action      |
| CAMPUS REMEMBER             | Action      |
| CASUALTIES ENCINO           | Action      |
| LABYRINTH LEAGUE            | Children    |
| LANGUAGE COWBOY             | Children    |
| LEGALLY SECRETARY           | Children    |
| MAGIC MALLRATS              | Children    |
| MAKER GABLES                | Children    |
| MICROCOSMOS PARADISE        | Children    |
| MODEL FISH                  | Children    |
| MURDER ANTITRUST            | Children    |
| NOON PAPI                   | Children    |
| POLISH BROOKLYN             | Children    |
| ROBBERS JOON                | Children    |
| SABRINA MIDNIGHT            | Children    |
+-----------------------------+-------------+
1000 rows in set (0,01 sec)
```

4. Listar los nombres de las ciudades junto con sus países.

```sql
SELECT ciudad.nombre, pais.nombre
FROM ciudad
JOIN pais ON ciudad.id_pais = pais.id_pais;

+----------------------------+---------------------------------------+
| nombre                     | nombre                                |
+----------------------------+---------------------------------------+
| Kabul                      | Afghanistan                           |
| Batna                      | Algeria                               |
| Bchar                      | Algeria                               |
| Skikda                     | Algeria                               |
| Tafuna                     | American Samoa                        |
| Nagaon                     | India                                 |
| Palghat (Palakkad)         | India                                 |
| Parbhani                   | India                                 |
| Pathankot                  | India                                 |
| Patiala                    | India                                 |
| Pudukkottai                | India                                 |
| Pune                       | India                                 |
| Purnea (Purnia)            | India                                 |
| Rae Bareli                 | India                                 |
| Rajkot                     | India                                 |
| Rampur                     | India                                 |
| Ranchi                     | India                                 |
| Sambhal                    | India                                 |
| Satna                      | India                                 |
| Shimoga                    | India                                 |
| Shivapuri                  | India                                 |
| Siliguri (Shiliguri)       | India                                 |
| Tambaram                   | India                                 |
| Udaipur                    | India                                 |
| Uluberia                   | India                                 |
+----------------------------+---------------------------------------+
600 rows in set (0,01 sec)
```

5. Obtener los detalles de los alquileres, incluyendo el cliente y el empleado que gestionó el alquiler.

```sql
SELECT a.id_alquiler, c.nombre, e.nombre 
FROM alquiler AS a 
JOIN cliente AS c ON c.id_cliente = a.id_cliente 
JOIN empleado AS e ON e.id_empleado = a.id_empleado ;

+-------------+-------------+--------+
| id_alquiler | nombre      | nombre |
+-------------+-------------+--------+
|       15719 | AUSTIN      | Mike   |
|       15725 | AUSTIN      | Mike   |
+-------------+-------------+--------+
16045 rows in set (0,04 sec)
```

6. Encontrar todas las películas que se encuentran en un almacén específico.

```sql
SELECT pelicula.titulo, almacen.id_almacen
FROM almacen
JOIN inventario ON almacen.id_almacen = inventario.id_almacen
JOIN pelicula ON inventario.id_pelicula = pelicula.id_pelicula;

+-----------------------------+------------+
| titulo                      | id_almacen |
+-----------------------------+------------+
| ACADEMY DINOSAUR            |          2 |
| ACADEMY DINOSAUR            |          2 |
| ACADEMY DINOSAUR            |          2 |
| ACADEMY DINOSAUR            |          2 |
| ACE GOLDFINGER              |          2 |
| ACE GOLDFINGER              |          2 |
| ACE GOLDFINGER              |          2 |
| ADAPTATION HOLES            |          2 |
| ADAPTATION HOLES            |          2 |
| ADAPTATION HOLES            |          2 |
| ADAPTATION HOLES            |          2 |
| AFFAIR PREJUDICE            |          2 |
| AFFAIR PREJUDICE            |          2 |
| AFFAIR PREJUDICE            |          2 |
| AFRICAN EGG                 |          2 |
| AFRICAN EGG                 |          2 |
| AFRICAN EGG                 |          2 |
| AGENT TRUMAN                |          2 |
| AGENT TRUMAN                |          2 |
| AGENT TRUMAN                |          2 |
| AIRPLANE SIERRA             |          2 |
| AIRPLANE SIERRA             |          2 |
| AIRPLANE SIERRA             |          2 |
| AIRPORT POLLOCK             |          2 |
| AIRPORT POLLOCK             |          2 |
| BANGER PINOCCHIO            |          2 |
| BARBARELLA STREETCAR        |          2 |
| BARBARELLA STREETCAR        |          2 |
| BAREFOOT MANCHURIAN         |          2 |
| BAREFOOT MANCHURIAN         |          2 |
| BASIC EASY                  |          2 |
| BOOGIE AMELIE               |          2 |
| BORN SPINAL                 |          2 |
| BORN SPINAL                 |          2 |
| BORN SPINAL                 |          2 |
| BORN SPINAL                 |          2 |
| BORROWERS BEDAZZLED         |          2 |
| BORROWERS BEDAZZLED         |          2 |
| BORROWERS BEDAZZLED         |          2 |
+-----------------------------+------------+
4581 rows in set (0,01 sec)
```

7. Listar los nombres y apellidos de los empleados junto con las direcciones de los almacenes en los que trabajan.

```sql
SELECT e.nombre, e.apellidos, d.direccion
FROM empleado AS e
JOIN almacen AS a On e.id_almacen = a.id_almacen
JOIN direccion AS d ON a.id_direccion = d.id_direccion;

+--------+-----------+--------------------+
| nombre | apellidos | direccion          |
+--------+-----------+--------------------+
| Ada    | Byron     | 47 MySakila Drive  |
| Ringo  | Rooksby   | 47 MySakila Drive  |
| Mike   | Hillyer   | 28 MySQL Boulevard |
| Jon    | Stephens  | 28 MySQL Boulevard |
| Pepe   | Spilberg  | 28 MySQL Boulevard |
+--------+-----------+--------------------+
5 rows in set (0,00 sec)
```

8. Obtener una lista de pagos realizados, incluyendo el cliente, el empleado que registró el pago y el alquiler correspondiente.

```sql
SELECT  p.id_pago, c.nombre, e.nombre
FROM pago AS p
JOIN cliente AS c ON c.id_cliente = p.id_cliente 
JOIN empleado AS e ON e.id_empleado = p.id_empleado;

+-------------+--------------+-----------------+
| id_pago     | nombre       | nombre          |
+-------------+--------------+-----------------+
| 16048       | AUSTIN       | Jon             |
| 16049       | AUSTIN       | Jon             |
+-------------+--------------+-----------------+


16049 rows in set (0,03 sec)
```

9. Listar las películas y los idiomas en los que están disponibles.

```sql
SELECT p.titulo, i.nombre
FROM pelicula AS p
JOIN idioma AS i ON p.id_idioma = i.id_idioma;

+-----------------------------+---------+
| titulo                      | nombre  |
+-----------------------------+---------+
| ACADEMY DINOSAUR            | English |
| ACE GOLDFINGER              | English |
| ADAPTATION HOLES            | English |
| AFFAIR PREJUDICE            | English |
| AFRICAN EGG                 | English |
| AGENT TRUMAN                | English |
| AIRPLANE SIERRA             | English |
| AIRPORT POLLOCK             | English |
| ALABAMA DEVIL               | English |
| ALADDIN CALENDAR            | English |
| ALAMO VIDEOTAPE             | English |
| ALASKA PHANTOM              | English |
| ALI FOREVER                 | English |
| ALICE FANTASIA              | English |
| ALIEN CENTER                | English |
| CHAMBER ITALIAN             | English |
| CHAMPION FLATLINERS         | English |
| CHANCE RESURRECTION         | English |
| CHAPLIN LICENSE             | English |
| CHARADE DUFFEL              | English |
| CHARIOTS CONSPIRACY         | English |
| CHASING FIGHT               | English |
| CHEAPER CLYDE               | English |
+-----------------------------+---------+
1000 rows in set (0,01 sec)
```

10. Encontrar todos los empleados y los almacenes que gestionan.

```sql
SELECT e.nombre,a.id_almacen
FROM empleado AS e
JOIN almacen AS a ON a.id_empleado_jefe = e.id_empleado;
	
+----------+------------+
| nombre   | id_almacen |
+----------+------------+
| Jon      |          2 |
| Ringo    |          1 |
+----------+------------+
2 rows in set (0,00 sec)
```

11. Obtener los títulos de las películas que nunca han sido alquiladas.

```sql
SELECT 	p.titulo
FROM 	pelicula AS p
LEFT JOIN	inventario AS i ON i.id_pelicula  = p.id_pelicula  
LEFT JOIN 	alquiler AS a ON a.id_inventario = i.id_inventario 
WHERE 	a.id_inventario IS NULL;
	
+------------------------+
| titulo                 | 
+------------------------+
| ACADEMY DINOSAUR       |
| ALICE FANTASIA         |
| APOLLO TEEN            |
| ARGONAUTS TOWN         |
| VILLAIN DESPERATE      |
| VOLUME HOUSE           |
| WAKE JAWS              |
| WALLS ARTIST           |
+------------------------+
43 rows in set (0,01 sec)
```

12. Listar los empleados que trabajan en el mismo almacén que el empleado con id_empleado = 1.

```sql
SELECT 	e2.nombre,	e2.id_almacen
FROM 	empleado AS e
JOIN	empleado AS e2 ON e2.id_almacen = e.id_almacen
WHERE 	e.id_empleado = 1;

+--------+------------+
| nombre | id_almacen |
+--------+------------+
| Mike   |          2 |
| Jon    |          2 |
| Pepe   |          2 |
+--------+------------+
3 rows in set (0,00 sec)

```

13. Encontrar el nombre de las ciudades que no tienen ningún cliente registrado.

```sql
SELECT 	c.nombre 
FROM 	ciudad AS c
LEFT JOIN	direccion AS d ON d.id_ciudad = c.id_ciudad
LEFT JOIN 	cliente AS c2 ON c2.id_direccion = d.id_direccion  
WHERE 	d.id_ciudad IS NULL	AND 	c2.id_direccion IS NULL	;
	
+----------------------------+
| nombre                     |
+----------------------------+
| Zhoushan                   |
| Ziguinchor                 |
+----------------------------+
558 rows in set (0,00 sec)
```

14. Obtener los nombres y apellidos de los actores que han participado en más de 10 películas.(having)

```sql
SELECT a.nombre, a.apellidos
FROM actor AS a
INNER JOIN pelicula_actor AS pa ON a.id_actor = pa.id_actor
GROUP BY a.id_actor
HAVING COUNT(*) > 10;

+-------------+--------------+
| nombre      | apellidos    |
+-------------+--------------+
| PENELOPE    | GUINESS      |
| NICK        | WAHLBERG     |
| ED          | CHASE        |
| JENNIFER    | DAVIS        |
| JOHNNY      | LOLLOBRIGIDA |
| BETTE       | NICHOLSON    |
| GRACE       | MOSTEL       |
| MATTHEW     | JOHANSSON    |
| RENEE       | BALL         |
| ROCK        | DUKAKIS      |
| CUBA        | BIRCH        |
| AUDREY      | BAILEY       |
| GREGORY     | GOODING      |
| JOHN        | SUVARI       |
| BURT        | TEMPLE       |
| MERYL       | ALLEN        |
| JAYNE       | SILVERSTONE  |
| BELA        | WALKEN       |
| REESE       | WEST         |
| MARY        | KEITEL       |
| JULIA       | FAWCETT      |
| THORA       | TEMPLE       |
+-------------+--------------+
200 rows in set (0,00 sec)
```

15. Encontrar los nombres y apellidos de los clientes que han realizado un pago mayor a 100.

```sql
SELECT c.nombre, c.apellidos
FROM cliente AS c
INNER JOIN pago AS p ON c.id_cliente = p.id_cliente
WHERE p.total > 100;

Empty set (0,00 sec)
```

16. Listar los títulos de las películas lanzadas en el mismo año que la película con id_pelicula = 2.

```sql
SELECT  distinct p.titulo
FROM pelicula AS p
JOIN pelicula AS p2 ON p2.anyo_lanzamiento = p.anyo_lanzamiento
WHERE p.id_pelicula = 2;

+----------------+
| titulo         |
+----------------+
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
| ACE GOLDFINGER |
+----------------+
1000 rows in set (0,00 sec)
```

