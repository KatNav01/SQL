# App Impersonator Project 

```
CREATE TABLE measurements
(id INTEGER PRIMARY KEY,
userID INTEGER,
date TEXT,
heart_rate INTEGER,
stress_index INTEGER, 
hrv_score INTEGER);

INSERT INTO measurements VALUES
(1, 1, "01/05/2021", 70, 42, 60);
INSERT INTO measurements VALUES
(2, 2, "01/05/2021", 100, 70, 74);
INSERT INTO measurements VALUES
(3, 2, "01/06/2021", 89, 68, 70);
INSERT INTO measurements VALUES
(4, 3, "01/08/2021", 85, 35, 55);
INSERT INTO measurements VALUES
(5, 4, "01/05/2021", 65, 13, 52);
SELECT * FROM measurements;
```
```
CREATE TABLE users 
(id INTEGER PRIMARY KEY,
gender TEXT,
age INTEGER,
activity_score INTEGER);

INSERT INTO users VALUES
(1, "male", 30, 3);
INSERT INTO users VALUES
(2, "female", 24, 2);
INSERT INTO users VALUES
(3, "female", 32, 5);
INSERT INTO users VALUES
(4, "male", 75, 3);
```

## Editing Tables and Data:

```
UPDATE measurements
SET date = "01/10/2021" WHERE id = 5;
```
```
UPDATE users
SET age = 25 WHERE id = 2;
```
```
ALTER TABLE measurements ADD mood TEXT;
```
```
UPDATE measurements
SET mood = "motivated" WHERE id = 3;
```
```
INSERT INTO users VALUES
(5, "female", 64, 1);
```
```
INSERT INTO measurements VALUES
(6, 5, "02/04/2021", 65, 24, 35, "Relaxed");
```
```
ALTER TABLE users ADD name TEXT;
```
```
UPDATE users
SET name = "Sam" WHERE id = 1;
UPDATE users
SET name = "Shanique" WHERE id = 2;
UPDATE users
SET name = "Mei Ling" WHERE id = 3;
UPDATE users
SET name = "Banda" WHERE id = 4;
UPDATE users 
SET name = "Sally" WHERE id = 5;
```
```
DELETE FROM users WHERE id  = 1;
DELETE FROM measurements WHERE userID = 1;
```
```
SELECT * FROM measurements;
SELECT * FROM users;
```
