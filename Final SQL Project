#1
Show Customers (their full names, customer ID, and country) who are not in the US.

SELECT CS.FirstName,CS.LastName, CS.CustomerId, CS.Country
FROM chinook.customers CS
WHERE CS.Country <> "USA";

#2
Show only the Customers from Brazil.

SELECT *
FROM chinook.customers 
WHERE Country LIKE "%BRAZIL%";

#3
Find the Invoices of customers who are from Brazil. The resulting table should show the customer's full name, Invoice ID, Date of the invoice, and billing country.

SELECT CS.FirstName, CS.LastName, IV.InvoiceId, IV.InvoiceDate, IV.BillingCountry 
FROM chinook.invoices IV
LEFT JOIN chinook.customers CS
ON IV.CustomerId=CS.CustomerId
Where IV.BillingCountry= "Brazil";
4.	Show the Employees who are Sales Agents.
SELECT *
FROM chinook.employees
WHERE TITLE LIKE "%Agent%";

#5
How many purchases were made in Germany?

SELECT COUNT(InvoiceID)
FROM chinook.invoices
where BillingCountry="Germany";

#6
Provide a query that shows the invoices associated with each sales agent. The resulting table should include the Sales Agent's full name.

SELECT ce.FirstName, ce.LastName, ci.InvoiceId
FROM chinook.employees ce
JOIN chinook.customers cs
JOIN chinook.invoices ci
On ce.Employeeid=cs.SupportRepID 
and cs.CustomerId=ci.CustomerId
where ce.title like "%Agent%";

#7
Show the Invoice Total, Customer name, Country, and Sales Agent name for all invoices and customers.

SELECT ci.Total, cs.FirstName, cs.LastName, cs.Country, ce.FirstName, ce.LastName, ci.InvoiceID
FROM chinook.employees ce
JOIN chinook.customers cs
JOIN chinook.invoices ci
on ce.Employeeid=cs.SupportRepID 
and cs.CustomerId=ci.CustomerId
where ce.title like "%Agent%";

#8
How many Invoices were there in 2009?

SELECT COUNT(InvoiceId)
FROM chinook.invoices
WHERE InvoiceDate LIKE "%2009%"

#9
What are the total sales for 2009?

SELECT SUM(Total)
FROM chinook.invoices
WHERE InvoiceDate like "%2009%";

#10
Write a query that includes the purchased track name with each invoice line ID.

SELECT tr.name, it.InvoiceLineId
FROM chinook.invoice_items as it
LEFT JOIN chinook.tracks as tr
ON it.TrackId=tr.TrackId;

#11
Write a query that includes the purchased track name AND artist name with each invoice line ID.

SELECT art.name AS Artist, tr.name as Track, it.InvoiceLineId
FROM chinook.invoice_items as it
JOIN chinook.tracks as tr
ON it.TrackId=tr.TrackId
JOIN chinook.albums as al
ON tr.AlbumId=al.AlbumId
JOIN chinook.artists as art
ON al.ArtistId=art.ArtistId;

#12
Provide a query that shows all the Tracks, and include the Album name, Media type, and Genre.

SELECT tr.name as 'Track Name', 
al.Title as 'Album Name',
mt.Name as 'Media Type',
gs.Name as 'Genre'
FROM chinook.tracks as tr
JOIN chinook.albums as al
ON tr.AlbumId=al.AlbumId
JOIN chinook.media_types as mt
ON tr.MediaTypeId=mt.MediaTypeId
JOIN chinook.genres as gs
ON gs.GenreId=tr.GenreId;

#13
Show the total sales made by each sales agent.

SELECT emp.FirstName,
emp.LastName, 
Round(SUM(inv.Total),2) as 'Total Sales'
FROM chinook.employees as emp
JOIN chinook.customers as cs
ON emp.EmployeeId=cs.SupportRepId
Join chinook.invoices as inv
ON cs.CustomerId=inv.CustomerId
Where emp.title= 'Sales Support Agent'
GROUP BY emp.LastName;

14.	Which sales agent made the most dollars in sales in 2009?

SELECT emp.FirstName,
emp.LastName, 
Round(SUM(inv.Total),2) as 'Total Sales'
FROM chinook.employees as emp
JOIN chinook.customers as cs
on emp.EmployeeId=cs.SupportRepId
Join chinook.invoices as inv
on cs.CustomerId=inv.CustomerId
Where emp.title= 'Sales Support Agent'
and inv.InvoiceDate like '%2009%'
GROUP BY emp.LastName
ORDER BY Round(SUM(inv.Total),2) DESC LIMIT 1;

#15
What are the total sales for each music genre?

SELECT gs.Name as 'Genre Type',
inv.Total as 'Total Sales'
FROM chinook.genres as gs
JOIN chinook.tracks as tr
ON tr.GenreId=gs.GenreId
JOIN chinook.invoice_items as it
ON tr.TrackId=it.TrackId
JOIN chinook.invoices as inv
on inv.InvoiceId=it.InvoiceId
Group by gs.Name;

