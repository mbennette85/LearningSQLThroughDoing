# LearningSQLThroughDoing
SQL beginning trial

1.SELECT FirstName, Lastname, CustomerId, Country FROM customer
  WHERE Country !='USA'

2. SELECT FirstName, Lastname, CustomerId, Country FROM customer
   WHERE Country = 'Brazil'

3. SELECT LastName, FirstName, InvoiceId, InvoiceDate, BillingCountry, Country 
   FROM Customer JOIN Invoice ON Customer.CustomerId=Invoice.CustomerId 
   WHERE Country = 'Brazil'

4. SELECT EmployeeId, LastName, FirstName, Title, ReportsTo, Email
   FROM Employee
   WHERE Title = 'Sales Support Agent'
   OR Title = 'Sales Manager'

5.SELECT DISTINCT BillingCountry
  FROM Invoice

6.SELECT Employee.LastName, Employee.FirstName, InvoiceId, InvoiceDate
  FROM Employee 
  JOIN Customer ON Employee.EmployeeId = Customer.SupportRepId
  JOIN Invoice ON Customer.CustomerId = Invoice.CustomerId

7.SELECT Total, Customer.LastName, Customer.FirstName, Customer.Country, Employee.LastName, Employee.FirstName
  FROM Employee 
  JOIN Customer ON Employee.EmployeeId = Customer.SupportRepId
  JOIN Invoice ON Customer.CustomerId = Invoice.CustomerId

8.SELECT CustomerId, InvoiceDate, Total
  FROM Invoice
  Where InvoiceDate BETWEEN '2009-01-01' AND '2011-12-31'
  &&
  SELECT SUM(Total)
  FROM Invoice
  Where InvoiceDate BETWEEN '2009-01-01' AND '2011-12-31'
  
9.SELECT COUNT(*)
  FROM InvoiceLine
  WHERE InvoiceId = 37
  
10.  
  
  


