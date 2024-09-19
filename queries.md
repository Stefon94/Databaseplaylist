Make sure you download the starter code and run the following:

psql < movies.sql
psql movies_db
In markdown, you can place a code block inside of three backticks (```) followed by the syntax highlighting you want, for example

```sql

SELECT * FROM users;

```

Using the movies_db database, write the correct SQL queries for each of these tasks:

The title of every movie.
SELECT title FROM movies;

All information on the G-rated movies.
SELECT \* FROM movies WHERE ratings='G';

The title and release year of every movie, ordered with the oldest movie first.
SELECT title, release_year FROM movies ORDER BY release_year;

All information on the 5 longest movies.
SELECT \* FROM movies ORDER BY runtime DESC LIMIT 5;

A query that returns the columns of rating and total, tabulating the total number of G, PG, PG-13, and R-rated movies.
SELECT rating, COUNT(rating) as total FROM movies GROUP BY rating;

A table with columns of release_year and average_runtime, tabulating the average runtime by year for every movie in the database. The data should be in reverse chronological order (i.e. the most recent year should be first).
SELECT release_year, AVG(runtime) as average_runtime FROM movies GROUP BY release_year ORDER BY release_year DESC;

The movie title and studio name for every movie in the database.
SELECT title, name FROM movies JOIN studios ON movies.studios_id = studios.id;

The star first name, star last name, and movie title for every matching movie and star pair in the database.
SELECT first_name, last_name, title FROM stars JOIN roles ON stars.id=star_id JOIN movies ON movies.id = roles.movie_id;

The first and last names of every star who has been in a G-rated movie. The first and last name should appear only once for each star, even if they are in several G-rated movies. IMPORTANT NOTE: it's possible that there can be two different actors with the same name, so make sure your solution accounts for that.
SELECT first_name, last_name, rating FROM stars join roles ON stars.id = star_id JOIN movies ON movies.id=roles.movie_id WHERE rating = 'G';

The first and last names of every star along with the number of movies they have been in, in descending order by the number of movies. (Similar to #9, make sure that two different actors with the same name are considered separately).
SELECT first_name, last_name, COUNT(\*) as total_movies FROM stars JOIN roles ON stars.id=roles.star_id GROUP BY first_name, last_name ORDER BY total_movies DESC;

The rest of these are bonuses

The title of every movie along with the number of stars in that movie, in descending order by the number of stars.

The first name, last name, and average runtime of the five stars whose movies have the longest average.

The first name, last name, and average runtime of the five stars whose movies have the longest average, among stars who have more than one movie in the database.

The titles of all movies that don't feature any stars in our database.

The first and last names of all stars that don't appear in any movies in our database.

The first names, last names, and titles corresponding to every role in the database, along with every movie title that doesn't have a star, and the first and last names of every star not in a movie.