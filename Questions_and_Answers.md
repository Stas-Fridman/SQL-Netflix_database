# Questions and Answers 

#### Question 1: Can you get all data about Netflix.
````sql
SELECT * FROM netflix;
````


#### Question 2: Check how many movies are present in Netflix?
````sql
SELECT COUNT(type) AS total_sum_movies FROM netflix
WHERE type = 'Movie';
````
**Results:**
total_sum_movie|
-----------|
6131|



#### Question 3: list all movies that directored by Steven Spilberg.
````sql
SELECT title AS Spilberg_film FROM netflix
WHERE director ILIKE 'Steven spielberg';
````
**Results:**
Spilberg_film|
-----------|
Jaws     |
Catch Me If You Can    |
The BFG       |
Indiana Jones and the Kingdom of the Crystal Skull  |
Indiana Jones and the Last Crusade     |
Indiana Jones and the Raiders of the Lost Ark     |
Indiana Jones and the Temple of Doom    |
Lincoln      |
Schindler's List  |
The Adventures of Tintin     |
War Horse     |


#### Question 4: What is the most common rating category for movies available on Netflix?
````sql
SELECT rating, COUNT(rating) AS rating_count FROM netflix
WHERE type = 'Movie'
GROUP BY rating
ORDER BY rating_count DESC;
````
**Results:**
rating|rating_count|
-----------|--------------|
TV-MA     |           2062|
TV-14    |           1427|
R       |            797|
TV-PG  |           540|
PG-13     |            490|
PG     |           287|
TV-Y7    |           139|
TV-Y       |            131|
TV-G  |           126|
NR     |            75|
G     |           41|
TV-Y7-FV    |           5|
UR       |            3|
NC-17  |           3|
84 min     |            1|
66 min       |            1|
74 min  |           1|
null     |            0|


#### Question 5: What is the average release year of TV shows available on Netflix?
````sql
SELECT ROUND(AVG(release_year),2) AS average_release_year FROM netflix
WHERE type = 'TV Show';
````
**Results:**
average_release_year|
-----------|
2016.61|


#### Question 6: What are the top 5 most common directors for movies available on Netflix?
````sql
SELECT director, COUNT(director) AS movie_count
FROM netflix
WHERE type = 'Movie'
GROUP BY director
ORDER BY movie_count DESC
LIMIT 5;
````
**Results:**
director|movie_count|
-----------|--------------|
Rajiv Chilaka     |           19|
Raúl Campos, Jan Suter    |           18|
Suhas Kadav      |            16|
Marcus Raboy  |           15|
Jay Karas     |            14|


#### Question 7: What are the top 5 countries with the highest number of movies available on Netflix?
````sql
SELECT country , count(country) as top_5 FROM netflix
WHERE type = 'Movie'
GROUP BY country
ORDER BY top_5 DESC
LIMIT 5;
````
**Results:**
country|top_5|
-----------|--------------|
United States     |           2058|
India    |           893|
United Kingdom      |            206|
Canada  |           122|
Spain     |            97|


#### Question 8: Which TV show on Netflix has the highest number of seasons?
````sql
SELECT title, MAX(duration) AS max_seasons FROM netflix
WHERE type = 'TV Show'
GROUP BY title
ORDER BY max_seasons DESC 
LIMIT  1;
````
**Results:**
title|max_seasons|
-----------|--------------|
The Office (U.S.)     |           9 Seasons|


#### Question 9: Retrieve the top 10 directors who have the highest number of titles available on Netflix
````sql
SELECT director, COUNT(*) AS title_count
FROM netflix
WHERE type IN ('Movie', 'TV Show') and director is not null
GROUP BY director
ORDER BY title_count DESC
LIMIT 10;
````
**Results:**
director|title_count|
-----------|--------------|
Rajiv Chilaka     |           19|
Raúl Campos, Jan Suter    |           18|
Suhas Kadav      |            16|
Marcus Raboy  |           15|
Jay Karas     |            14|
Cathy Garcia-Molina     |           13|
Youssef Chahine    |           12|
Martin Scorsese      |            12|
Jay Chapman  |           12|
Steven Spielberg     |            11|


#### Question 10: Find the release year with the highest number of movies released on Netflix.
````sql
SELECT release_year, COUNT(release_year) AS movie_count
FROM netflix
WHERE type = 'Movie'
GROUP BY release_year
ORDER BY movie_count DESC
LIMIT 1;
````
**Results:**
release_year|movie_count|
-----------|--------------|
2017     |           767|
