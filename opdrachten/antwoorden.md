# Antwoorden

1. Welke acteurs hebben de voornaam 'Scarlett'?
```sql
SELECT *
FROM actor
WHERE first_name = 'Scarlett';
```
2. Welke acteurs hebben de achternaam 'Johansson'?
```sql
SELECT *
FROM actor
WHERE last_name = 'Johansson';
```
3. Hoeveel unieke acteur-achternamen zijn er?
```sql
SELECT COUNT(DISTINCT last_name)
FROM actor;
```
4. Welke achternamen zijn uniek? (niet repeterend)?
```sql
SELECT last_name
FROM actor
GROUP BY last_name
    HAVING COUNT(*) = 1;
```
5. Welke achternamen komen vaker dan 1x voor?
```sql
SELECT last_name
FROM actor
GROUP BY last_name
    HAVING COUNT(*) > 1;
```
6. Welke acteur heeft gespeeld in de meeste films?
```sql
SELECT actor.actor_id, actor.first_name, actor.last_name,
       count(actor_id) AS film_count
FROM actor 
    JOIN film_actor USING (actor_id)
GROUP BY actor_id
ORDER BY film_count DESC
LIMIT 1;
```
7. Wat is de gemiddelde lengte van alle films in de database?
```sql
SELECT AVG(length)
FROM film;
```
8. Wat is de gemiddelde lengte van alle films op categorie?
```sql
SELECT category.name, AVG(length)
FROM film 
    JOIN film_category USING (film_id) 
    JOIN category USING (category_id)
GROUP BY category.name
ORDER BY AVG(length) DESC;
```
