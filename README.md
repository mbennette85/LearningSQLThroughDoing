# LearningSQLThroughDoing
SQL beginning trial

1.SELECT FirstName, Lastname, CustomerId, Country FROM customer
WHERE Country !='USA'

2. SELECT FirstName, Lastname, CustomerId, Country FROM customer
WHERE Country = 'Brazil'

3. SELECT LastName, FirstName, InvoiceId, InvoiceDate, BillingCountry, Country 
FROM Customer JOIN Invoice ON Customer.CustomerId=Invoice.CustomerId 
WHERE Country = 'Brazil'

4. 
