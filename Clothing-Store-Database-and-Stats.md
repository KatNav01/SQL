## Clothing Sotre Database and Stats

```
CREATE TABLE clothing 
(id INTEGER PRIMARY KEY, 
name TEXT, 
price INTEGER, 
rating INTEGER, 
quantity INTEGER);

INSERT INTO clothing VALUES(1, "Stretch Pants", 15, 4, 15);
INSERT INTO clothing VALUES(2, "Loose Fit Pants", 17, 3.5, 10);
INSERT INTO clothing VALUES(3, "Graphic T-Shirt", 15, 4, 21);
INSERT INTO clothing VALUES(4, "Plain White T-Shirt", 10, 5, 32);
INSERT INTO clothing VALUES(5, "Thermal Longsleeve Shirt", 18, 5, 12);
INSERT INTO clothing VALUES(6, "Plain Longsleeve Shirt", 13, 4, 3);
INSERT INTO clothing VALUES(7, "Shin-Length Socks", 5, 5, 12);
INSERT INTO clothing VALUES(8, "Ankle-Length Socks", 3, 3.5, 12);
INSERT INTO clothing VALUES(9, "Fleece Jacket", 25, 3.5, 23);
INSERT INTO clothing VALUES(10, "Peacoat", 60, 5, 3);
INSERT INTO clothing VALUES(11, "No-Show Socks", 2.50, 3, 15);
INSERT INTO clothing VALUES(12, "Sports Bra", 15, 4.5, 12);
INSERT INTO clothing VALUES(13, "Thermal Longjohns", 13, 4, 18);
INSERT INTO clothing VALUES(14, "Sports Sneakers", 120, 5, 21);
INSERT INTO clothing VALUES(15, "Hiking Boots", 150, 5, 24);
```

```
SELECT * FROM clothing;
```

```
SELECT * FROM clothing 
ORDER BY price DESC;
```
```
SELECT AVG(price) FROM clothing;
```
```
SELECT MIN(price) FROM clothing;
```
```
SELECT MAX(price) FROM clothing;
```
```
SELECT * FROM clothing WHERE rating > 4
ORDER BY price DESC;
```
```
SELECT * FROM clothing WHERE rating < 4
ORDER BY price ASC;
```
