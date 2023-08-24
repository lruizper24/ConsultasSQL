
# Ejercicio 5

**A continuación se relaciona la pregunta seguida de la respectiva respuesta con el Query y su resultado.**

1. Selecciona las columnas film_id y title de la tabla film.

~~~
SELECT film_id, title FROM film;
~~~

![ resultado punto 1](Image/Exercise%201.png)

2. Selecciona 5 filas de la tabla film, obteniendo todas las columnas.

~~~
SELECT * FROM film LIMIT 5;
~~~

![ resultado punto 2](Image/Exercise%202.png)

3. Selecciona filas de la tabla film donde film_id sea menor que 4.

~~~
SELECT * FROM film WHERE film_id < 4;
~~~

![ resultado punto 3](Image/Exercise%203.png)

4. Selecciona filas de la tabla film donde el rating sea PG o G.

~~~
SELECT * FROM film WHERE rating = 'PG' OR rating = 'G';
~~~

![ resultado punto 4](Image/Exercise%204.png)

5. Selecciona filas de la tabla actor donde el nombre sea Angela, Angelina o Audrey usando IN.

~~~
SELECT * FROM actor WHERE first_name IN ('Angela','Angelina','Audrey');
~~~

![ resultado punto 5](Image/Exercise%205.png)

6. Obtén una lista de actores con el nombre Julia.

~~~
SELECT * FROM actor WHERE LOWER (first_name) = 'julia';
~~~

![ resultado punto 6](Image/Exercise%206.png)

7. Obtén una lista de actores con los nombres Chris, Cameron o Cuba.

~~~
SELECT * FROM actor WHERE LOWER (first_name) = 'chris' OR 
LOWER (first_name) = 'cameron' OR LOWER (first_name) = 'cuba';
~~~

![ resultado punto 7](Image/Exercise%207.png)

8. Selecciona la fila de la tabla customer para el cliente con el nombre Jamie Rice.

~~~
SELECT * FROM customer WHERE LOWER (first_name) = 'jamie' 
AND LOWER (last_name) = 'rice';
~~~

![ resultado punto 8](Image/Exercise%208.png)

9. Selecciona el monto y la fecha de pago de la tabla payment donde el monto pagado sea menor a $1.

~~~
SELECT amount, payment_date FROM payment WHERE amount < 1;
~~~

![ resultado punto 9](Image/Exercise%209.png)

10.  ¿Cuáles son las diferentes duraciones de alquiler permitidas por la tienda?

~~~
SELECT DISTINCT rental_duration FROM film; 
~~~

![ resultado punto 10](Image/Exercise%2010.png)

11. Ordena las filas en la tabla city por country_id y luego por city.

~~~
SELECT * FROM city ORDER BY country_id, city; 
~~~

![ resultado punto 11](Image/Exercise%2011.png)

12. ¿Cuáles son los ID de los últimos 3 clientes que devolvieron un alquiler?

~~~
SELECT rental_id, return_date FROM rental ORDER BY return_date LIMIT 3; 
~~~

![ resultado punto 12](Image/Exercise%2012.png)

13. ¿Cuántas películas tienen clasificación NC-17? ¿Cuántas tienen clasificación PG o PG-13?

~~~
SELECT COUNT (rating) FROM film WHERE rating ='NC-17'; 
~~~

![ resultado punto 13.1](Image/Exercise%2013.1.png)

~~~
SELECT COUNT (rating) FROM film WHERE rating = 'PG' OR rating = 'PG-13'; 
~~~

![ resultado punto 13.2](Image/Exercise%2013.2.png)

~~~
SELECT rating, COUNT (rating) FROM film WHERE rating ='NC-17' OR rating = 'PG' OR rating = 'PG-13' GROUP BY rating; 
~~~

![ resultado punto 13.3](Image/Exercise%2013.3.png)

14. ¿Cuántos clientes diferentes tienen registros en la tabla rental?

~~~
SELECT COUNT (DISTINCT customer_id) FROM rental; 
~~~

![ resultado punto 14](Image/Exercise%2014.png)

15. ¿Hay algún cliente con el mismo apellido? 

Respuesta: NO

~~~
SELECT COUNT (last_name) AS numer_of_last_name_items FROM customer; 
~~~

![ resultado punto 15.1](Image/Exercise%2015.1.png)

~~~
SELECT COUNT (DISTINCT last_name) AS unique_number_of_last_name FROM customer; 
~~~

![ resultado punto 15.2](Image/Exercise%2015.2.png)

16. ¿Qué película (id) tiene la mayor cantidad de actores?

~~~
SELECT film_id, COUNT (actor_id) AS actor_amount FROM film_actor GROUP BY film_id ORDER BY actor_amount DESC LIMIT 1;
~~~

![ resultado punto 16](Image/Exercise%2016.png)

17. ¿Qué actor (id) aparece en la mayor cantidad de películas?

~~~
SELECT actor_id, COUNT (film_id) AS actor_most_movies FROM film_actor GROUP BY actor_id ORDER BY actor_most_movies DESC LIMIT 1;
~~~

![ resultado punto 17](Image/Exercise%2017.png)

18. Cuenta el número de ciudades para cada country_id en la tabla city. Ordena los resultados por count(*).

~~~
SELECT country_id, COUNT (city) AS number_of_cities FROM city GROUP BY country_id ORDER BY number_of_cities;
~~~

![ resultado punto 18](Image/Exercise%2018.png)

19. ¿Cuál es la tarifa de alquiler promedio de las películas? ¿Puedes redondear el resultado a 2 decimales?

~~~
SELECT AVG(rental_rate) AS rental_rate_avg FROM film;
~~~

![ resultado punto 19.1](Image/Exercise%2019.1.png)

~~~
SELECT ROUND(AVG(rental_rate),2) AS rental_rate_avg FROM film;
~~~

![ resultado punto 19.2](Image/Exercise%2019.2.png)

20. Selecciona los 10 actores que tienen los nombres más largos (nombre y apellido combinados).

~~~
SELECT first_name, last_name, LENGTH(first_name || last_name) 
AS length_full_name FROM actor ORDER BY length_full_name DESC LIMIT 10;
~~~

![ resultado punto 20](Image/Exercise%2020.png)

