# SQL Island Practice
### Testing new SQL skills in the [SQL Island](https://sql-island.informatik.uni-kl.de/) game. You can find a quick tutorial on how to change the language settings [here](https://medium.com/@trvlingteacher/sql-island-a-fun-way-to-learn-sql-e0cec7cce458).


```
SELECT 
  * 
FROM village;
```

```
SELECT 
  *
FROM inhabitant;
```

```
SELECT 
  * 
FROM inhabitant 
  WHERE job = 'butcher';
```

```
SELECT 
  *
FROM inhabitant
  WHERE state = "friendly";
```

```
SELECT 
  *
FROM inhabitant
  WHERE state = "friendly"
  AND job = "weaponsmith";
```

```
SELECT 
  *
FROM inhabitant
  WHERE state = "friendly"
  AND job LIKE "%smith%";
```

```
UPDATE item SET owner = 20 
  WHERE owner IS NULL;
```

```
SELECT 
  *
FROM item
  WHERE owner = 20;
```

```
SELECT 
  *
FROM inhabitant
  WHERE state = "friendly" 
  AND (job = "dealer" OR job = "merchant");
```

```
UPDATE item SET owner = 15 
  WHERE item = 'teapot' OR item = 'ring' ;
```


```
UPDATE inhabitant SET name = 'Felix' 
  WHERE personid = 20;
```


```
SELECT 
  * 
FROM inhabitant
  WHERE job LIKE "%baker%"
  ORDER BY gold DESC;
```

```
SELECT 
  * 
FROM inhabitant
  WHERE job LIKE "%pilot%";
```

```
SELECT 
  inhabitant.name 
FROM village, inhabitant 
  WHERE village.villageid = inhabitant.villageid 
  AND village.villageid = 3
  AND inhabitant.personid = 13
;
```

```
SELECT 
  COUNT(gender) 
FROM village, inhabitant 
  WHERE village.villageid = inhabitant.villageid 
  AND inhabitant.gender = 'f'
  AND village.villageid = 3
;
```

```
SELECT 
  inhabitant.name 
FROM village, inhabitant 
  WHERE village.villageid = inhabitant.villageid 
  AND inhabitant.gender = 'f'
  AND village.villageid = 3
	; 
```

```
SELECT 
  SUM(inhabitant.gold) 
FROM inhabitant, village
  WHERE village.villageid = inhabitant.villageid
  AND (inhabitant.job LIKE '%baker%' 
    OR inhabitant.job LIKE '%merchant%' 
    OR inhabitant.job LIKE '%dealer%')
;
```

```
SELECT 
  state, 
  AVG(inhabitant.gold) 
FROM inhabitant 
  GROUP BY state 
  ORDER BY AVG(inhabitant.gold);
```

```
DELETE FROM inhabitant 
  WHERE name = 'Dirty Diane';
```

```
UPDATE inhabitant 
  SET state = 'friendly' 
  WHERE personid = 8;
```
