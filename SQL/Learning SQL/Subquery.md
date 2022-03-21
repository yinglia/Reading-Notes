# Chapter 9

Two type of subquery:

 - noncorrelated subquery
   - single row/column (<>)
   - multiple-row, signle-column (in, not in, all, any, having
   - multicolumn
 - correlated subquery


## Noncorrelated subquery

Defination: it may be executed alone and does not reference anything from the containing statement

### multiple-row, signle-column

WHERE customer_id <> ALL

 -> (SELECT customer_id
 
 -> FROM payment
 
 -> WHERE amount = 0);
 
 
 WHERE customer_id NOT IN
 
 (SELECT customer_id
 
 FROM payment
 
 WHERE amount = 0)

ensure that the set of values does not contain a null value

### multicolumnn

-without subquery
 > WHERE fa.actor_id IN
 
 > (SELECT actor_id FROM actor WHERE last_name = 'MONROE')
 
 > AND fa.film_id IN
 
 > (SELECT film_id FROM film WHERE rating = 'PG')
 
 -with subquery
 
 > WHERE (actor_id, film_id) IN
 
 > (SELECT a.actor_id, f.film_id
 
 > FROM actor a
 
 > CROSS JOIN film f
 
 > WHERE a.last_name = 'MONROE'
 
 > AND f.rating = 'PG');
 
