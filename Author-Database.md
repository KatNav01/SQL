# Author Database

## Create table about the people and what they do here

```
CREATE TABLE authors (id INTEGER PRIMARY KEY,
    fullname TEXT,
    birthdate TEXT,
    age INTEGER);
    
INSERT INTO authors (fullname, birthdate,   age)
    VALUES ("Neil Gaimen", "November 10,        1960", 62);
INSERT INTO authors (fullname, birthdate, age)
    VALUES ("Terry Pratchett", "April 28,       1948", 67);
INSERT INTO authors (fullname, birthdate, age)
    VALUES ("Stephen Baxter", "November 13, 1957", 65);
    
CREATE TABLE books (id INTEGER PRIMARY KEY,
    author_id INTEGER,
    title TEXT,
    release_date INTEGER,
    adaptation TEXT);
   
INSERT INTO books (author_id, title, release_date, adaptation)
    VALUES (1, "Coraline", 2002, "Yes");
INSERT INTO books (author_id, title, release_date, adaptation)
    VALUES (1, "Good Omens", 1990, "Yes");
INSERT INTO books (author_id, title, release_date, adaptation)
    VALUES (2, "Good Omens", 1990, "Yes");
INSERT INTO books (author_id, title, release_date, adaptation)
    VALUES (2, "The Color of Magic", 1983, "No");
INSERT INTO books (author_id, title, release_date, adaptation)
    VALUES (3, "The Long Earth", 2013, "No");
INSERT INTO books (author_id, title, release_date, adaptation)
    VALUES (2, "The Long Earth", 2013, "No");
INSERT INTO books (author_id, title, release_date, adaptation)
    VALUES (3, "Time", 2000, "No");
INSERT INTO books (author_id, title, release_date, adaptation)
    VALUES (2, "The Carpet People", 1971, "No");
INSERT INTO books (author_id, title, release_date, adaptation)
    VALUES (1, "Stardust", 1999, "yes");
INSERT INTO books (author_id, title, release_date, adaptation)
    VALUES (3, "Deep Future", 2001, "NO");
    
CREATE TABLE co_written_books (id INTEGER PRIMARY KEY, 
    author1_id INTEGER,  author2_id INTEGER);
    
INSERT INTO co_written_books ( author1_id,  author2_id)
    VALUES(1, 2);
INSERT INTO co_written_books ( author1_id,  author2_id)
    VALUES(2, 3);

```

## Queries start here:

### Multiple JOINS: Which authors have worked together?

```
SELECT  a.fullname AS "Author 1", 
        b.fullname AS "Author 2"
    FROM co_written_books AS co
    JOIN authors AS a
        ON co.author1_id = a.id
    JOIN authors as b
        ON co.author2_id = b.id
;
```
        
### GROUP BY Statement: What books have which authors worked on? 

```
SELECT  authors.fullname AS "Author", 
        books.title AS "Book"
    FROM books
    JOIN authors
    ON books.author_id = authors.id
    GROUP BY books.title
;
```
    
### Which books have been written since 2000? 

```
SELECT  authors.fullname AS "Author",  
        books.title AS "Book Title", 
        books.release_date AS "Release Date"
    FROM books 
    JOIN authors
        ON books.author_id = authors.id
    WHERE books.release_date > 2000
;
```

### WHERE Clause: Which authors have written books that have been adapted into movies? */

```
SELECT authors.fullname AS "Authors with Adapted Books",
        books.title AS "Book"
    FROM books
    JOIN authors
        ON books.author_id = authors.id
    WHERE books.adaptation LIKE "%yes"
    GROUP BY authors.fullname
;
```

## To experiment with different methods of answering and displaying the same question, find another way to query the above question.

### CASE Statment and LIKE Operator: Which authors have written books that have been adapted into movies?

```
SELECT books.title AS "Book Title", 
    CASE 
        WHEN books.adaptation LIKE "%Yes" THEN "Adapted"
        WHEN books.adaptation LIKE "%No" THEN "Not Adapted"
    END AS "Adapted Status"
FROM books
    JOIN authors
        ON books.author_id = authors.id
    GROUP BY books.title
    ORDER BY "Adapted Status"
;
```

## WHERE Clause: Which books have been released in the last 30 years and are adapted?

```
SELECT  authors.fullname AS "Author",
        books.title AS "Title",
        books.adaptation AS "Adaptation Status"
    FROM books
    JOIN authors
        ON books.author_id = authors.id
    WHERE books.adaptation LIKE "%yes"
        AND release_date > 1992
;
```
