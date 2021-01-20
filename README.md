**SAKILA Task**

1.

	SELECT first_name, last_name FROM actor;

2.

	SELECT last_name FROM actor WHERE first_name='John';

3.

	SELECT first_name, last_name FROM actor WHERE last_name='Neeson';

4.

	SELECT first_name, last_name, actor_id/10 FROM actor WHERE actor_id%10=0;

5.

	SELECT title, description FROM film WHERE film_id=100;

6.

	SELECT title FROM film WHERE rating='R';

7.

	SELECT title FROM film WHERE rating!='R';

8.

	SELECT title, length FROM film ORDER BY length ASC LIMIT 10;

9.

	SELECT title, length FROM film ORDER BY length DESC;

10.

	SELECT title FROM film WHERE special_features='Deleted Scenes';

11.

	SELECT last_name, count(\*) FROM actor GROUP BY last_name HAVING count(\*)=1 ORDER BY last_name DESC;

12.

	SELECT last_name, count(\*) FROM actor GROUP BY last_name HAVING count(\*)>1 ORDER BY count(\*) DESC;

13.

	SELECT count(\*), (SELECT first_name FROM actor WHERE actor.actor_id=film_actor.actor_id) AS first,
		(SELECT last_name FROM actor WHERE actor.actor_id=film_actor.actor_id) AS last 
			FROM film_actor GROUP BY actor_id ORDER BY count(\*) DESC;

14.

	SELECT film.title, rental.rental_date, film.rental_duration, DATE_ADD(rental.rental_date, INTERVAL film.rental_duration DAY) 
		FROM film 
			JOIN inventory ON film.film_id=inventory.film_id 
			JOIN rental ON inventory.inventory_id=rental.inventory_id 
				WHERE film.title='Academy Dinosaur' AND rental.return_date IS NULL;

15.

	SELECT SUM(length)/COUNT(\*) FROM film;

16.

	SELECT category, SUM(length)/COUNT(\*) AS average FROM film_list GROUP BY category;

17.

	SELECT title, description FROM film_list WHERE description LIKE '%robot%';

18.

	SELECT title FROM film WHERE release_year='2010';

19.

	select title, category FROM film_list WHERE category LIKE '%horror%';

20.

	SELECT name FROM staff_list WHERE SID=2;

21.

#EASY WAY

	SELECT title FROM film_list WHERE actors LIKE '%Fred Costner%';

22.

	SELECT count(\*) FROM (SELECT DISTINCT country FROM country) distinct_country;

23.

	SELECT name FROM language ORDER BY name DESC;

24.

	SELECT first_name, last_name FROM actor WHERE last_name LIKE '%son' ORDER BY first_name ASC;

25.

	SELECT category, COUNT(\*) FROM 
		film_list fl JOIN film_category fc ON fl.FID=fc.film_id 
			GROUP BY category ORDER BY COUNT(\*) DESC LIMIT 1;

