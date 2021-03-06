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
  
10.SELECT InvoiceId, COUNT(*)
   FROM InvoiceLine
   GROUP BY InvoiceId
   
11.SELECT InvoiceLineId, InvoiceId, Track.TrackId, Track.Name
FROM InvoiceLine
JOIN Track
ON Track.TrackId = InvoiceLine.TrackId

12.SELECT InvoiceLineId, InvoiceId, Track.TrackId, Track.Name, Artist.Name
   FROM InvoiceLine
   JOIN Track
   ON Track.TrackId = InvoiceLine.TrackId
   JOIN Album
   ON Album.AlbumId= Track.AlbumId
   JOIN Artist
   ON Artist.ArtistId= Album.ArtistId

13.SELECT BillingCountry, Count (InvoiceId)
   FROM Invoice 
   GROUP BY BillingCountry

14.SELECT Playlist.PlaylistId, Name, COUNT(TrackId)
   FROM Playlist
   JOIN PlaylistTrack
   ON Playlist.PlaylistId=PlaylistTrack.PlaylistId
   GROUP BY Playlist.PlaylistId
  
15.SELECT Track.Name AS Track, Album.Title, MediaType.Name AS Medium, Genre.Name AS Genre
   FROM Album
   JOIN Track
   ON Album.AlbumId  = Track.AlbumId
   JOIN MediaType
   ON MediaType.MediaTypeId= Track.MediaTypeId
   JOIN Genre
   ON Genre.GenreId = Track.GenreId   

16.SELECT Invoice.InvoiceId, COUNT(InvoiceLineId) AS NumofLines
   FROM Invoice
   INNER JOIN InvoiceLine ON Invoice.InvoiceId = InvoiceLine.InvoiceId
   GROUP BY Invoice.InvoiceId

17.SELECT Employee.EmployeeId AS Id, Employee.LastName, Employee.FirstName, SUM( Total)
FROM Invoice
JOIN Customer
ON Invoice.CustomerId = Customer.CustomerId
JOIN Employee
ON Employee.EmployeeId = Customer.SupportRepId
GROUP BY Employee.EmployeeId

18.SELECT Employee.EmployeeId AS Id, Employee.LastName, Employee.FirstName, SUM(Total)
FROM Invoice JOIN Customer 
ON Invoice.CustomerId = Customer.CustomerId 
JOIN Employee
ON Employee.EmployeeId = Customer.SupportRepId 
WHERE InvoiceDate 
BETWEEN '2009-01-01' AND '2009-12-31' 
GROUP BY Employee.EmployeeId
ORDER BY Total DESC LIMIT 1


19.SELECT Employee.EmployeeId AS Id, Employee.LastName, Employee.FirstName, SUM(Total)
FROM Invoice JOIN Customer 
ON Invoice.CustomerId = Customer.CustomerId 
JOIN Employee
ON Employee.EmployeeId = Customer.SupportRepId 
WHERE InvoiceDate 
GROUP BY Employee.EmployeeId
ORDER BY Total ASC LIMIT 1

20.SELECT Employee.LastName, Employee.FirstName, SUM(CustomerId) AS Total 
FROM Customer
JOIN Employee ON Customer.SupportRepId = Employee.EmployeeId
GROUP BY SupportRepId LIMIT 1

21.SELECT BillingCountry, SUM(Total)
FROM Invoice
GROUP BY BillingCountry
ORDER BY BillingCountry DESC LIMIT 1

22.SELECT 
  Track.Name,
  InvoiceLine.TrackId,
  Invoice.InvoiceId,
  COUNT(InvoiceLineId) AS TotalAmount
  FROM InvoiceLine
  inner join Invoice on Invoice.InvoiceId = InvoiceLine.InvoiceId
  inner JOIN Track ON InvoiceLine.TrackId = Track.TrackId
  WHERE InvoiceDate BETWEEN '2013-01-01' AND '2013-12-31'
  GROUP BY Track.Name 
  ORDER BY TotalAmount DESC

23.SELECT 
   Track.Name,
   InvoiceLine.TrackId,
   Invoice.InvoiceId,
   COUNT(InvoiceLineId) AS TotalAmount
   FROM InvoiceLine
   inner join Invoice on Invoice.InvoiceId = InvoiceLine.InvoiceId
   inner JOIN Track ON InvoiceLine.TrackId = Track.TrackId
   GROUP BY Track.Name 
   ORDER BY TotalAmount DESC

24.SELECT Artist.Name,  COUNT(InvoiceLineId) AS TotalDownloads
   FROM InvoiceLine
   INNER JOIN Invoice ON Invoice.InvoiceId = InvoiceLine.InvoiceId
   INNER JOIN Track ON InvoiceLine.TrackId = Track.TrackId
   INNER JOIN Album ON Track.AlbumId = Album.AlbumId
   INNER JOIN Artist ON Album.ArtistId = Artist.ArtistId
   GROUP BY Artist.Name
   ORDER BY TotalDownloads DESC
   
25.SELECT MediaType.Name, COUNT(MediaType.MediaTypeId)
   FROM InvoiceLine
   INNER JOIN Invoice ON Invoice.InvoiceId = InvoiceLine.InvoiceId
   INNER JOIN Track ON InvoiceLine.TrackId = Track.TrackId
   INNER JOIN MediaType ON Track.MediaTypeId = MediaType.MediaTypeId 
   GROUP BY MediaType.MediaTypeId

