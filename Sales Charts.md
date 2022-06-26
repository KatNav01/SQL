# Sales Charts

## 1: How many orders were placed in January?

```
SELECT
      COUNT(orderID) 
  FROM BIT_DB.jansales
;
```

## 2: How many of those orders were for an iPhone?

```
SELECT
      COUNT(*) 
  FROM BIT_DB.JanSales
WHERE Product="iPhone"
;
```

## 3: Select the customer account numbers for all the orders that were placed in February.

```
SELECT
      acctnum
  FROM BIT_DB.FebSales sales
  INNER JOIN BIT_DB.customers
      ON sales.orderID=customers.order_id
;
```

## 4: Which product was the cheapest one sold in January, and what was the price?

```
SELECT DISTINCT
      Product,
      price
  FROM BIT_DB.JanSales
WHERE price IN 
  (SELECT MIN(price) FROM BIT_DB.JanSales)
;
```


## 5: What is the total revenue for each product sold in January? (Revenue can be calculated using the number of products sold and the price of the products).

```
SELECT
      Product,
      SUM(quantity)*price AS "January Revenue"
  FROM BIT_DB.JanSales
GROUP BY Product
;
```

## 6: Which products were sold in February at _548 Lincoln St, Seattle, WA 98101_, how many of each were sold, and what was the total revenue?

```
SELECT
      Product,
      SUM(Quantity) AS total_sold,
      SUM(Quantity)*price AS revenue,
      location
  FROM BIT_DB.FebSales
WHERE location="548 Lincoln St, Seattle, WA 98101"
GROUP BY Product
;
```

## 7: How many customers ordered more than 2 products at a time in February, and what was the average amount spent for those customers?

```
SELECT
      COUNT(customers.acctnum) number_of_accounts,
      AVG(quantity)*price average_revenue
  FROM BIT_DB.FebSales sales
  INNER JOIN BIT_DB.customers
    ON sales.orderID=customers.order_id
WHERE sales.quantity > 2
;
```

## 8: List all the products sold in Los Angeles in February, and include how many of each were sold.

```
SELECT distinct
            Product,
            location,
            SUM(quantity)
      FROM BIT_DB.FebSales
WHERE location like '%Los Angeles%'
GROUP BY Product
;
```

## 9: How many locations are there in New York that sold more than 1 product in January?

```
SELECT
      COUNT(distinct location)
FROM BIT_DB.JanSales
WHERE location LIKE '%new york%'
AND quantity > 1
ORDER BY location
;
```

## 10: How many of each type of headphone were sold in February?

```
SELECT
      product,
      SUM(quantity) AS total_sold
FROM BIT_DB.FebSales
WHERE Product LIKE '%headphone%'
GROUP BY product
;
```


## 11: What was the average amount spent per account in February?

```
SELECT
      SUM(quantity*price)/COUNT(acctnum) AS average_spent
FROM BIT_DB.FebSales sales
JOIN BIT_DB.customers
ON sales.orderID=customers.order_id
;
```

## 12: What was the average quantity of products purchased per account in February? (Hint: just like question 3, we want the overall average, not the average for each account individually).

```
SELECT
      SUM(quantity)/COUNT(acctnum) AS average_products
FROM BIT_DB.FebSales sales
JOIN BIT_DB.customers
ON sales.orderID=customers.order_id
;
```

## 13: Which product brought in the most revenue in January and how much revenue did it bring in total?  

```
SELECT
      product,
      SUM(quantity*price) AS revenue
     FROM BIT_DB.JanSales
GROUP BY product
ORDER BY revenue desc
LIMIT 1
;
```

