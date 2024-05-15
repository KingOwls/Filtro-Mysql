Presentacion de resultados Jorge Osorio y Bryan  Martines Santo

Genere repositorio con la solucion
Genere README el cual debe tener la siguiente informacion:
\- Enunciado de la consulta
\- Solucion de la consulta
\- Resultado de la consulta



1. Obtener los nombres de todos los actores y las películas en las
   que han actuado.

   ```mysql
   SELECT a.nombre,a.apellidos,p.titulo FROM actor a
   
   INNER JOIN pelicula_actor pa ON a.id_actor = pa.id_actor
   
   INNER JOIN pelicula p ON pa.id_pelicula = p.id_pelicula;
   
   +----------+-----------+-----------------------+
   | nombre   | apellidos | titulo                |
   +----------+-----------+-----------------------+
   | PENELOPE | GUINESS   | ACADEMY DINOSAUR      |
   | PENELOPE | GUINESS   | ANACONDA CONFESSIONS  |
   | PENELOPE | GUINESS   | ANGELS LIFE           |
   | PENELOPE | GUINESS   | BULWORTH COMMANDMENTS |
   | PENELOPE | GUINESS   | CHEAPER CLYDE         |
   | PENELOPE | GUINESS   | COLOR PHILADELPHIA    |
   | PENELOPE | GUINESS   | ELEPHANT TROJAN       |
   | PENELOPE | GUINESS   | GLEAMING JAWBREAKER   |
   | PENELOPE | GUINESS   | HUMAN GRAFFITI        |
   | PENELOPE | GUINESS   | KING EVOLUTION        |
   | PENELOPE | GUINESS   | LADY STAGE            |
   | PENELOPE | GUINESS   | LANGUAGE COWBOY       |
   | PENELOPE | GUINESS   | MULHOLLAND BEAST      |
   | PENELOPE | GUINESS   | OKLAHOMA JUMANJI      |
   | PENELOPE | GUINESS   | RULES HUMAN           |
   +----------+-----------+-----------------------+
   5462 rows in set (0,01 sec)
   
   ```



2. Listar todos los clientes y los almacenes donde están
   registrados.

   ```mysql
   SELECT c.nombre, c.apellidos,al.id_almacen FROM cliente c
   
   INNER JOIN almacen al ON c.id_almacen = al.id_almacen;
   
   +----------+-----------+------------+
   | nombre   | apellidos | id_almacen |
   +----------+-----------+------------+
   | BARBARA  | JONES     |          2 |
   | JENNIFER | DAVIS     |          2 |
   | SUSAN    | WILSON    |          2 |
   | MARGARET | MOORE     |          2 |
   | LISA     | ANDERSON  |          2 |
   | KAREN    | JACKSON   |          2 |
   | BETTY    | WHITE     |          2 |
   | SANDRA   | MARTIN    |          2 |
   | CAROL    | GARCIA    |          2 |
   | SHARON   | ROBINSON  |          2 |
   | SARAH    | LEWIS     |          2 |
   | KIMBERLY | LEE       |          2 |
   | JESSICA  | HALL      |          2 |
   | SHIRLEY  | ALLEN     |          2 |
   | ANGELA   | HERNANDEZ |          2 |
   +----------+-----------+------------+
   601 rows in set (0,00 sec)
   
   ```

   



3. Encontrar todas las películas y sus respectivas categorías.

   ```mysql
   SELECT p.titulo, c.nombre as Categoria FROM pelicula p
   
   INNER JOIN pelicula_categoria pc ON pc.id_pelicula = p.id_pelicula
   
   INNER JOIN categoria c ON c.id_categoria = pc.id_categoria;
   
   +---------------------+-----------+
   | titulo              | Categoria |
   +---------------------+-----------+
   | AMADEUS HOLY        | Action    |
   | AMERICAN CIRCUS     | Action    |
   | ANTITRUST TOMATOES  | Action    |
   | ARK RIDGEMONT       | Action    |
   | BAREFOOT MANCHURIAN | Action    |
   | BERETS AGENT        | Action    |
   | BRIDE INTRIGUE      | Action    |
   | BULL SHAWSHANK      | Action    |
   | CADDYSHACK JEDI     | Action    |
   | CAMPUS REMEMBER     | Action    |
   | CASUALTIES ENCINO   | Action    |
   | CELEBRITY HORN      | Action    |
   | CLUELESS BUCKET     | Action    |
   | CROW GREASE         | Action    |
   | DANCES NONE         | Action    |
   +---------------------+-----------+
   1000 rows in set (0,00 sec)
   
   ```

   LIMIT 15

4. Listar los nombres de las ciudades junto con sus países.

   ```mysql
   SELECT c.nombre, p.nombre FROM ciudad c
   
   INNER JOIN pais p ON p.id_pais = c.id_pais;
   
   | Valle de la Pascua         | Venezuela                             |
   | Cam Ranh                   | Vietnam                               |
   | Haiphong                   | Vietnam                               |
   | Hanoi                      | Vietnam                               |
   | Nam Dinh                   | Vietnam                               |
   | Nha Trang                  | Vietnam                               |
   | Vinh                       | Vietnam                               |
   | Charlotte Amalie           | Virgin Islands, U.S.                  |
   | Aden                       | Yemen                                 |
   | Hodeida                    | Yemen                                 |
   | Sanaa                      | Yemen                                 |
   | Taizz                      | Yemen                                 |
   | Kragujevac                 | Yugoslavia                            |
   | Novi Sad                   | Yugoslavia                            |
   | Kitwe                      | Zambia                                |
   +----------------------------+---------------------------------------+
   600 rows in set (0,01 sec)
   
   ```

   



5. Obtener los detalles de los alquileres, incluyendo el cliente y el
   empleado que gestionó el alquiler.

   ```mysql
   SELECT cl.nombre, cl.apellidos, em.nombre , em.apellidos, pa.total,pl.titulo FROM alquiler al
   
   INNER JOIN pago pa ON al.id_alquiler = pa.id_alquiler
   
   INNER JOIN empleado em ON em.id_empleado = pa.id_empleado
   
   INNER JOIN cliente cl ON cl.id_cliente = pa.id_cliente
   
   INNER JOIN inventario i ON i.id_pelicula = al.id_inventario
   
   INNER JOIN pelicula pl ON pl.id_pelicula = i.id_pelicula;
   
   
   ```

   

6. Encontrar todas las películas que se encuentran en un almacén
   específico.

   ```mysql
   SELECT pl.titulo,alm.id_almacen FROM pelicula pl
   
   INNER JOIN inventario inv ON inv.id_pelicula = pl.id_pelicula
   
   INNER JOIN almacen alm ON alm.id_almacen = inv.id_almacen ORDER BY alm.id_almacen;
   
   | JEREMY      | HURTADO      | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | IRMA        | PEARSON      | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | CLIFFORD    | BOWENS       | Jon    | Stephens  |  2.99 | ZORRO ARK                   |
   | KARL        | SEAL         | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | JEREMY      | HURTADO      | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | IRMA        | PEARSON      | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | CLIFFORD    | BOWENS       | Jon    | Stephens  |  2.99 | ZORRO ARK                   |
   | KARL        | SEAL         | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | JEREMY      | HURTADO      | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | IRMA        | PEARSON      | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | CLIFFORD    | BOWENS       | Jon    | Stephens  |  2.99 | ZORRO ARK                   |
   | KARL        | SEAL         | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | JEREMY      | HURTADO      | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | IRMA        | PEARSON      | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | CLIFFORD    | BOWENS       | Jon    | Stephens  |  2.99 | ZORRO ARK                   |
   | KARL        | SEAL         | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | JEREMY      | HURTADO      | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | IRMA        | PEARSON      | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | CLIFFORD    | BOWENS       | Jon    | Stephens  |  2.99 | ZORRO ARK                   |
   | KARL        | SEAL         | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | JEREMY      | HURTADO      | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | IRMA        | PEARSON      | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | CLIFFORD    | BOWENS       | Jon    | Stephens  |  2.99 | ZORRO ARK                   |
   | KARL        | SEAL         | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   | JEREMY      | HURTADO      | Mike   | Hillyer   |  2.99 | ZORRO ARK                   |
   +-------------+--------------+--------+-----------+-------+-----------------------------+
   15895 rows in set (0,08 sec)
   
   ```

   

7. Listar los nombres y apellidos de los empleados junto con las
   direcciones de los almacenes en los que trabajan.

   ```mysql
   SELECT em.nombre, em.apellidos, dr.direccion,alm.id_almacen FROM direccion dr
   
   INNER JOIN almacen alm ON alm.id_direccion = dr.id_direccion
   
   INNER JOIN empleado em ON em.id_almacen = alm.id_almacen;
   
   +--------+-----------+--------------------+------------+
   | nombre | apellidos | direccion          | id_almacen |
   +--------+-----------+--------------------+------------+
   | Mike   | Hillyer   | 28 MySQL Boulevard |          2 |
   | Jon    | Stephens  | 28 MySQL Boulevard |          2 |
   | Pepe   | Spilberg  | 28 MySQL Boulevard |          2 |
   | Ada    | Byron     | 47 MySakila Drive  |          1 |
   | Ringo  | Rooksby   | 47 MySakila Drive  |          1 |
   +--------+-----------+--------------------+------------+
   5 rows in set (0,00 sec)
   
   ```

   



8. Obtener una lista de pagos realizados, incluyendo el cliente, el
   empleado que registró el pago y el alquiler correspondiente.

   ```mysql
   SELECT cl.nombre, cl.apellidos, em.nombre,em.apellidos, alq.id_alquiler FROM pago pa
   
   INNER JOIN cliente cl ON cl.id_cliente = pa.id_cliente
   
   INNER JOIN empleado em ON em.id_empleado = pa.id_empleado
   
   INNER JOIN alquiler alq ON alq.id_alquiler = pa.id_alquiler;
   
   | WADE        | DELVALLE     | Mike   | Hillyer   |       10054 |
   | WADE        | DELVALLE     | Jon    | Stephens  |       11350 |
   | WADE        | DELVALLE     | Jon    | Stephens  |       12601 |
   | WADE        | DELVALLE     | Jon    | Stephens  |       14345 |
   | WADE        | DELVALLE     | Jon    | Stephens  |       15307 |
   | WADE        | DELVALLE     | Mike   | Hillyer   |       15443 |
   | AUSTIN      | CINTRON      | Jon    | Stephens  |        1008 |
   | AUSTIN      | CINTRON      | Mike   | Hillyer   |        2272 |
   | AUSTIN      | CINTRON      | Jon    | Stephens  |        3043 |
   | AUSTIN      | CINTRON      | Jon    | Stephens  |        3398 |
   | AUSTIN      | CINTRON      | Mike   | Hillyer   |        3429 |
   | AUSTIN      | CINTRON      | Mike   | Hillyer   |        5065 |
   | AUSTIN      | CINTRON      | Mike   | Hillyer   |        5843 |
   | AUSTIN      | CINTRON      | Jon    | Stephens  |        6800 |
   | AUSTIN      | CINTRON      | Jon    | Stephens  |        6895 |
   | AUSTIN      | CINTRON      | Mike   | Hillyer   |        8965 |
   | AUSTIN      | CINTRON      | Jon    | Stephens  |        9630 |
   | AUSTIN      | CINTRON      | Jon    | Stephens  |        9679 |
   | AUSTIN      | CINTRON      | Jon    | Stephens  |       11522 |
   | AUSTIN      | CINTRON      | Mike   | Hillyer   |       14233 |
   | AUSTIN      | CINTRON      | Mike   | Hillyer   |       14599 |
   | AUSTIN      | CINTRON      | Mike   | Hillyer   |       14719 |
   | AUSTIN      | CINTRON      | Jon    | Stephens  |       15590 |
   | AUSTIN      | CINTRON      | Jon    | Stephens  |       15719 |
   | AUSTIN      | CINTRON      | Jon    | Stephens  |       15725 |
   +-------------+--------------+--------+-----------+-------------+
   16044 rows in set (0,04 sec)
   
   
   ```

   

9. Listar las películas y los idiomas en los que están disponibles.

   ```mysql
   SELECT pl.titulo, idi.nombre FROM pelicula pl
   
   INNER JOIN idioma idi ON idi.id_idioma = pl.id_idioma;
   
   | WISDOM WORKER               | English |
   | WITCHES PANIC               | English |
   | WIZARD COLDBLOODED          | English |
   | WOLVES DESIRE               | English |
   | WOMEN DORADO                | English |
   | WON DARES                   | English |
   | WONDERFUL DROP              | English |
   | WONDERLAND CHRISTMAS        | English |
   | WONKA SEA                   | English |
   | WORDS HUNTER                | English |
   | WORKER TARZAN               | English |
   | WORKING MICROCOSMOS         | English |
   | WORLD LEATHERNECKS          | English |
   | WORST BANGER                | English |
   | WRATH MILE                  | English |
   | WRONG BEHAVIOR              | English |
   | WYOMING STORM               | English |
   | YENTL IDAHO                 | English |
   | YOUNG LANGUAGE              | English |
   | YOUTH KICK                  | English |
   | ZHIVAGO CORE                | English |
   | ZOOLANDER FICTION           | English |
   | ZORRO ARK                   | English |
   +-----------------------------+---------+
   1000 rows in set (0,00 sec)
   
   ```

   



10. Encontrar todos los empleados y los almacenes que gestionan.

    ```mysql
    SELECT em.nombre,em.apellidos,alm.id_almacen FROM almacen alm
    
    INNER JOIN empleado em ON alm.id_empleado_jefe = em.id_empleado;
    
    +--------+-----------+------------+
    | nombre | apellidos | id_almacen |
    +--------+-----------+------------+
    | Jon    | Stephens  |          2 |
    | Ringo  | Rooksby   |          1 |
    +--------+-----------+------------+
    2 rows in set (0,00 sec)
    
    ```

    

11. Obtener los títulos de las películas que nunca han sido
    alquiladas.

    ```mysql
    SELECT pl.titulo as peliculas_no_alquiladas_nunca FROM inventario inv
    
     RIGHT JOIN pelicula pl ON inv.id_pelicula = pl.id_pelicula
     
     WHERE inv.id_pelicula IS NULL;
    
    +-------------------------------+
    | peliculas_no_alquiladas_nunca |
    +-------------------------------+
    | ALICE FANTASIA                |
    | APOLLO TEEN                   |
    | ARGONAUTS TOWN                |
    | ARK RIDGEMONT                 |
    | ARSENIC INDEPENDENCE          |
    | BOONDOCK BALLROOM             |
    | BUTCH PANTHER                 |
    | CATCH AMISTAD                 |
    | PSYCHO SHRUNK                 |
    | RAIDERS ANTITRUST             |
    | RAINBOW SHOCK                 |
    | ROOF CHAMPION                 |
    | SISTER FREDDY                 |
    | SKY MIRACLE                   |
    | SUICIDES SILENCE              |
    | TADPOLE PARK                  |
    | TREASURE COMMAND              |
    | VILLAIN DESPERATE             |
    | VOLUME HOUSE                  |
    | WAKE JAWS                     |
    | WALLS ARTIST                  |
    +-------------------------------+
    42 rows in set (0,00 sec)
    
    ```

    

12. Listar los empleados que trabajan en el mismo almacén que el
    empleado con id_empleado = 1.

    ```mysql
    SELECT em2.nombre,em2.apellidos FROM empleado em2
    
    INNER JOIN (SELECT em.id_empleado,em.nombre,em.apellidos,em.id_almacen FROM empleado em
    INNER JOIN almacen alm ON alm.id_almacen = em.id_almacen
    WHERE em.id_empleado = 1) subc ON subc.id_almacen = em2.id_almacen;
                
    +--------+-----------+
    | nombre | apellidos |
    +--------+-----------+
    | Mike   | Hillyer   |
    | Jon    | Stephens  |
    | Pepe   | Spilberg  |
    +--------+-----------+
    3 rows in set (0,00 sec)
    
    ```

13. Encontrar el nombre de las ciudades que no tienen ningún
    cliente registrado.

    ```mysql
    SELECT ciu.nombre FROM cliente cli
    
    INNER JOIN direccion dr ON dr.id_direccion = cli.id_direccion
    
    RIGHT JOIN ciudad ciu ON ciu.id_ciudad = dr.id_ciudad
    
    WHERE cli.id_direccion IS NULL;
    
    | Xinxiang                   |
    | Yangor                     |
    | Yantai                     |
    | Yaound                     |
    | Yerevan                    |
    | Yinchuan                   |
    | Yingkou                    |
    | York                       |
    | Yuncheng                   |
    | Yuzhou                     |
    | Zalantun                   |
    | Zanzibar                   |
    | Zaoyang                    |
    | Zapopan                    |
    | Zaria                      |
    | Zeleznogorsk               |
    | Zhezqazghan                |
    | Zhoushan                   |
    | Ziguinchor                 |
    +----------------------------+
    560 rows in set (0,00 sec)
    ```

    

14. Obtener los nombres y apellidos de los actores que han
    participado en más de 10 películas.(having)

    ```mysql
    SELECT act.nombre, act.apellidos, COUNT(pla.id_pelicula) as participaciones FROM actor act
    
    INNER JOIN pelicula_actor pla ON act.id_actor = pla.id_actor
    
    INNER JOIN pelicula pl ON pl.id_pelicula = pla.id_pelicula GROUP BY act.id_actor
    
    HAVING participaciones > 10;
    
    | OLYMPIA     | PFEIFFER     |              28 |
    | GROUCHO     | WILLIAMS     |              25 |
    | ALAN        | DREYFUSS     |              27 |
    | MICHAEL     | BENING       |              24 |
    | WILLIAM     | HACKMAN      |              27 |
    | JON         | CHASE        |              29 |
    | GENE        | MCKELLEN     |              27 |
    | LISA        | MONROE       |              23 |
    | ED          | GUINESS      |              29 |
    | JEFF        | SILVERSTONE  |              25 |
    | MATTHEW     | CARREY       |              39 |
    | DEBBIE      | AKROYD       |              24 |
    | RUSSELL     | CLOSE        |              19 |
    | HUMPHREY    | GARLAND      |              29 |
    | MICHAEL     | BOLGER       |              30 |
    | JULIA       | ZELLWEGER    |              16 |
    | RENEE       | BALL         |              33 |
    | ROCK        | DUKAKIS      |              30 |
    | CUBA        | BIRCH        |              24 |
    | AUDREY      | BAILEY       |              27 |
    | GREGORY     | GOODING      |              30 |
    | JOHN        | SUVARI       |              29 |
    | BURT        | TEMPLE       |              23 |
    | MERYL       | ALLEN        |              22 |
    | JAYNE       | SILVERSTONE  |              27 |
    | BELA        | WALKEN       |              30 |
    | REESE       | WEST         |              33 |
    | MARY        | KEITEL       |              40 |
    | JULIA       | FAWCETT      |              15 |
    | THORA       | TEMPLE       |              20 |
    +-------------+--------------+-----------------+
    200 rows in set (0,01 sec)
    
    ```

    

15. Encontrar los nombres y apellidos de los clientes que han
    realizado un pago mayor a 100.

    ```mysql
    SELECT cli.nombre, cli.apellidos, SUM(pa.total) AS totalGastado FROM cliente cli
    
    INNER JOIN pago pa ON pa.id_cliente = cli.id_cliente
    
    GROUP BY cli.id_cliente HAVING totalGastado > 100 ;
    
    | SERGIO      | STANFIELD    |       108.74 |
    | MARION      | OCAMPO       |       115.71 |
    | TRACY       | HERRMANN     |       129.72 |
    | SETH        | HANNON       |       112.75 |
    | KENT        | ARSENAULT    |       134.73 |
    | TERRANCE    | ROUSH        |       111.71 |
    | RENE        | MCALISTER    |       113.74 |
    | EDUARDO     | HIATT        |       130.73 |
    | TERRENCE    | GUNDERSON    |       117.70 |
    +-------------+--------------+--------------+
    395 rows in set (0,02 sec)
    
    ```

    

16. Listar los títulos de las películas lanzadas en el mismo año que
    la película con id_pelicula = 2.

    ```mysql
    SELECT peli.id_pelicula, peli.titulo FROM pelicula peli
    
    INNER JOIN(SELECT pl.id_pelicula, pl.anyo_lanzamiento FROM pelicula pl WHERE pl.id_pelicula = 2) subcpl ON subcpl.anyo_lanzamiento = peli.anyo_lanzamiento;
    
    |         960 | WARS PLUTO                  |
    |         961 | WASH HEAVENLY               |
    |         962 | WASTELAND DIVINE            |
    |         963 | WATCH TRACY                 |
    |         964 | WATERFRONT DELIVERANCE      |
    |         965 | WATERSHIP FRONTIER          |
    |         966 | WEDDING APOLLO              |
    |         967 | WEEKEND PERSONAL            |
    |         968 | WEREWOLF LOLA               |
    |         969 | WEST LION                   |
    |         970 | WESTWARD SEABISCUIT         |
    |         971 | WHALE BIKINI                |
    |         972 | WHISPERER GIANT             |
    |         973 | WIFE TURN                   |
    |         974 | WILD APOLLO                 |
    |         975 | WILLOW TRACY                |
    |         976 | WIND PHANTOM                |
    |         977 | WINDOW SIDE                 |
    |         978 | WISDOM WORKER               |
    |         979 | WITCHES PANIC               |
    |         980 | WIZARD COLDBLOODED          |
    |         981 | WOLVES DESIRE               |
    |         982 | WOMEN DORADO                |
    |         983 | WON DARES                   |
    |         984 | WONDERFUL DROP              |
    |         985 | WONDERLAND CHRISTMAS        |
    |         986 | WONKA SEA                   |
    |         987 | WORDS HUNTER                |
    |         988 | WORKER TARZAN               |
    |         989 | WORKING MICROCOSMOS         |
    |         990 | WORLD LEATHERNECKS          |
    |         991 | WORST BANGER                |
    |         992 | WRATH MILE                  |
    |         993 | WRONG BEHAVIOR              |
    |         994 | WYOMING STORM               |
    |         995 | YENTL IDAHO                 |
    |         996 | YOUNG LANGUAGE              |
    |         997 | YOUTH KICK                  |
    |         998 | ZHIVAGO CORE                |
    |         999 | ZOOLANDER FICTION           |
    |        1000 | ZORRO ARK                   |
    +-------------+-----------------------------+
    1000 rows in set (0,00 sec)
    
    ```

    