# Project 1.13

This project was completed within the SQLite Studio space. This is an open source database engine useful for creating and managing databases. You can find more info on it [here](https://www.sqlite.org/index.html).

## 1. Show Customers (their full names, customer ID, and country) who are not in the US.

```
SELECT
	FirstName,
	LastName,
	CustomerID,
	Country
FROM chinook.customers
	WHERE customers.Country <> "USA"
;
```

## 2. Show only the Customers from Brazil.

```
SELECT
	FirstName,
	LastName,
	CustomerID,
	Country
FROM chinook.customers
	WHERE customers.Country = "Brazil"
;
```

## 3. Find the Invoices of customers who are from Brazil. The resulting table should show the customer's full name, Invoice ID, Date of the invoice, and billing country.

```
SELECT
	cust.FirstName,
	cust.LastName,
	inv.InvoiceId,
	inv.InvoiceDate,
	inv.BillingCountry
FROM chinook.customers AS cust
LEFT JOIN chinook.invoices AS inv
	ON cust.customerId = inv.customerId
;
```

## 4. Show the Employees who are Sales Agents.

```
SELECT
	*
FROM chinook.employees
	WHERE title LIKE "Sales Support Agent"
;
```

## 5. Find a unique/distinct list of billing countries from the Invoice table.

```
SELECT DISTINCT
	invoices.BillingCountry
FROM chinook.Invoices
	ORDER BY BillingCountry ASC
;
```

## 6. Provide a query that shows the invoices associated with each sales agent. The resulting table should include the Sales Agent's full name.

```
SELECT
	emp.firstname,
	emp.lastname,
	inv.invoiceid
FROM chinook.invoices AS inv
	JOIN chinook.customers AS cust
		ON inv.invoiceid = cust.customerid
	JOIN chinook.employees as emp
		ON cust.supportrepid = emp.employeeid
ORDER BY inv.invoiceid ASC
;
```

## 7. Show the Invoice Total, Customer name, Country, and Sales Agent name for all invoices and customers.

```
SELECT
	cust.firstname,
	cust.lastname,
	inv.total AS "Invoice Total",
	cust.country,
	emp.firstname as "Sales Rep"
FROM chinook.invoices AS inv
	JOIN chinook.customers AS cust
		ON inv.invoiceid = cust.customerid
	JOIN chinook.employees as emp
		ON cust.supportrepid = emp.employeeid
;
```

## 8. How many Invoices were there in 2009?

```
SELECT DISTINCT
	COUNT(invoiceid)
FROM chinook.invoices AS inv
	WHERE invoicedate LIKE "%2009%"
;
```

## 9. What are the total sales for 2009?

```
SELECT
	SUM(total)
FROM chinook.Invoices as inv
	WHERE invoicedate LIKE "%2009%"
;
```

## 10. Write a query that includes the purchased track name with each invoice line item.

```
SELECT
	items.InvoiceLineId,
	tracks.Name
FROM chinook.invoice_items AS items
JOIN chinook.tracks
	ON items.trackid = tracks.TrackId
;
```

## 11. Write a query that includes the purchased track name AND artist name with each invoice line item.

```
SELECT
	items.invoicelineid,
	tracks.name AS "Track Name",
	tracks.Composer
FROM chinook.invoice_items AS items
JOIN chinook.tracks
	ON items.trackid = tracks.TrackId
;
```

## 12. Provide a query that shows all the Tracks, and include the Album name, Media type, and Genre.

```
SELECT
	tracks.Name AS "Track Name",
	albums.title AS "Album Title",
	types.name AS "Media Type",
	genres.Name AS "Genre"
FROM chinook.tracks
JOIN chinook.albums
	ON tracks.AlbumId = albums.AlbumId
JOIN chinook.media_types AS types
	ON tracks.MediaTypeId = types.mediatypeid
JOIN chinook.genres
	ON tracks.GenreId = genres.GenreId
;
```

## 13. Show the total sales made by each sales agent.

```
SELECT
	emp.firstname AS "Employee",
	ROUND(SUM(inv.total), 2) AS "Total Sales" 

FROM chinook.employees AS emp
JOIN chinook.customers AS cust
	ON emp.employeeid = cust.supportrepid
JOIN chinook.invoices AS inv
	ON cust.customerid = inv.customerid

WHERE emp.title Like "%sales%"
GROUP BY emp.firstname
ORDER BY "Total Sales" DESC
;
```

## 14. Which sales agent made the most in sales in 2009?

```
SELECT
	emp.firstname AS "First Name",
	emp.lastname AS "Last Name",
	ROUND(SUM(inv.total), 2) AS "Total Sales" 

FROM chinook.employees AS emp
JOIN chinook.customers AS cust
	ON emp.employeeid = cust.supportrepid
JOIN chinook.invoices AS inv
	ON cust.customerid = inv.customerid

WHERE emp.title Like "%sales%"
	AND inv.invoicedate LIKE "%2009%"
GROUP BY emp.firstname
ORDER BY "Total Sales" DESC LIMIT 1
;
```



