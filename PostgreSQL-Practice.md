# PostgreSQL Practice
This code was written using Postgre SQL syntax. You can learn more about Postgre SQL as well as download the engine [here](https://www.postgresql.org/).


  
 ## Try to figure out which attribute you'd use to be able to join the two tables 

```
SELECT 
   * 
FROM "CharlotteChaze/BreakIntoTech"."netflix_people" people
   LEFT JOIN "CharlotteChaze/BreakIntoTech"."netflix_titles_info" titles
   ON "people".show_id="titles".show_id
;
``` 

## How many movie titles are there in the database? (movies only, not tv shows)

```
SELECT 
   COUNT(*) 
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info" titles
   WHERE titles.type='Movie'
;
```


## When was the most recent batch of tv shows and/or movies added to the database?

```
SELECT 
   max(date(date_added)) 
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info"
;
```
##### List all the movies and tv shows in alphabetical order.
```
SELECT 
   title 
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info"
   ORDER BY title;
```
##### Who was the Director for the movie Bright Star?
```
SELECT 
   titles.title,
   people.director 
FROM "CharlotteChaze/BreakIntoTech"."netflix_people" people
   LEFT JOIN "CharlotteChaze/BreakIntoTech"."netflix_titles_info" titles
      ON "people".show_id="titles".show_id
   WHERE titles.title='Bright Star'
;
```
##### What is the oldest movie in the database and what year was it made?
```
SELECT 
   title,
   MIN(titles.release_year) AS "Release Date"
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info" titles
   WHERE type='Movie'
   GROUP BY title, release_year
   ORDER BY release_year ASC
   LIMIT 1
;
```

## How would you join the two tables? 

```
SELECT 
  *
	FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info" titles
	LEFT JOIN "CharlotteChaze/BreakIntoTech"."netflix_people" people
		ON titles.show_id=people.show_id;
```
## How many movie titles are there in the database? (movies only, not tv shows)? 

```
SELECT 
  count(*)
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info"
  WHERE type='Movie';
```
  
## When was the most recent batch of tv shows and/or movies added to the database?

```
SELECT 
  MAX(DATE(date_added))
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info"
;
```

## List all the movies and tv shows in alphabetical order.

```
SELECT 
  title 
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info"
  ORDER BY title;
```

## Who was the Director for the movie Bright Star?

```
SELECT 
  people.director, 
  titles.title 
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info" titles
 LEFT JOIN "CharlotteChaze/BreakIntoTech"."netflix_people" people
 ON titles.show_id=people.show_id
WHERE title='Bright Star';
```

## What is the oldest movie in the database and what year was it made? 

```
SELECT 
  title, 
  MIN(release_year) 
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info"
  WHERE type='Movie'
  GROUP BY release_year, title
  ORDER BY release_year
  LIMIT 1
;
```
