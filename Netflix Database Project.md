## 1: How would you join the two tables? 

```
SELECT
      *
      FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info" titles
      LEFT JOIN "CharlotteChaze/BreakIntoTech"."netflix_people" people
      	ON titles.show_id=people.show_id
;
```

## 2: How many movie titles are there in the database? (movies only, not tv shows)?

```
SELECT
      count(*)
  FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info"
 WHERE type='Movie'
;
```

## 3: When was the most recent batch of tv shows and/or movies added to the database?

```
SELECT
      MAX(DATE(date_added))
  FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info"
;
```

## 4: List all the movies and tv shows in alphabetical order.


```
SELECT 
      title 
  FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info"
ORDER BY title
;
```

## 5: Who was the Director for the movie Bright Star? 

```
SELECT
      people.director,
      titles.title 
  FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info" titles
    LEFT JOIN "CharlotteChaze/BreakIntoTech"."netflix_people" people
      ON titles.show_id=people.show_id
WHERE title='Bright Star'
;
```

## 6: What is the oldest movie in the database and what year was it made?  

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
