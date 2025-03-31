/*1. Create a Database **/

/*Write a query to create a database called InventoryDB and a query to use it*/


CREATE DATABASE InventoryDB

USE InventoryDB


/* 2. Create a Items Table*/

/*Create a table called Items with the following fields:*/


CREATE TABLE Items (

ItemID INT Primary Key,ItemName VARCHAR(50),

Category VARCHAR(50),Price DECIMAL,

StockQuantity INT

)


/*3. Insert Item Records*/

/*Insert the following data into the Items table:*/


INSERT INTO Items

VALUES

(001, 'Desk', 'Furniture', 300.00, 20),

(002, 'Chair', 'Furniture', 150.00, 50),

(003, 'Notebook', 'Stationery', 10.00, 100),

(004, 'Pen', 'Stationery', 2.00, 200),

(005, 'Monitor', 'Electronics', 250.00, 30);


/*4. Create a Customers Table*/

/*Create a table called Customers with the following fields:*/


CREATE TABLE Customers (

CustomerID INT Primary Key,FirstName VARCHAR(50),

LastName VARCHAR(50), Email VARCHAR(50),

Phone INT

);

ALTER TABLE Customers ALTER COLUMN Phone VARCHAR(50)


/*5. Insert Customer Records*/

/*Insert the following customer records into the Customers table:*/


INSERT INTO Customers

VALUES

(101, 'John', 'Doe', 'john.doe@gmail.com', '123-456-7890'),

(102, 'Jane', 'Smith', 'jane.smith@gmail.com', '234-567-8901'),

(103, 'Emily', 'Davis', 'emily.davis@gmail.com', '345-678-9012');


/*6. Create an Orders Table*/

/*Create a table called Orders with the following fields:*/


CREATE TABLE Orders (

OrderID INT Primary Key,

CustomerID INT FOREIGN KEY REFERENCES Customers(CustomerID),

OrderDate DATE,

TotalAmount DECIMAL,

);


/*7. Insert Order Records*/

/*Insert the following order records into the Orders table:*/


INSERT INTO Orders

VALUES

(001, 101, '2024-07-01', 600.00),

(002, 102, '2024-07-02', 300.00),

(003, 103, '2024-07-03', 150.00);



/*8. Create an OrderItems Table*/

/*Create a table called OrderItems with the following fields:*/


CREATE TABLE OrderItems(

OrderItemID INT Primary Key,

OrderID INT FOREIGN KEY REFERENCES ORDERS(OrderID),

ItemID INT FOREIGN KEY REFERENCES Items( ItemID),

Quantity INT,LineTotal DECIMAL

);


/*9. Insert Order Item Records*/

/*Insert the following order item records into the OrderItems table:*/


INSERT INTO OrderItems

VALUES

(001, 001, 001, 2, 600.00),

(002, 001, 003, 5, 50.00),

(003, 002, 002, 2, 300.00),

(004, 003, 004, 10, 20.00);


/*10. Best-Selling Item*/

/*Write a query to find the best-selling item by total sales amount. Show the ItemName and TotalSalesAmount.*/


SELECT i.ItemName, SUM(oi.LineTotal) AS TotalSalesAmount

FROM OrderItems oi

INNER JOIN

Items i ON oi.ItemID = i.ItemID

GROUP BY

i.ItemName

HAVING

SUM(oi.LineTotal) = (

SELECT

MAX(TotalSalesAmount)

FROM (

SELECT SUM(oi.LineTotal) AS TotalSalesAmount

FROM

OrderItems oi

GROUP BY

oi.ItemID

) AS Best_Selling_Item

);


/*11. Customer with Highest Orders*/

/*Write a query to find the customer who has placed the highest total orders. Show the CustomerID, FirstName, LastName, and TotalAmount.*/


SELECT c.CustomerID, c.FirstName, c.LastName,

SUM(o.TotalAmount) AS TotalAmount

FROM

Orders o

JOIN

Customers c ON o.CustomerID = c.CustomerID

GROUP BY

c.CustomerID,

c.FirstName,

c.LastName

HAVING

SUM(o.TotalAmount) = (

SELECT MAX(TotalAmount)

FROM

( SELECT SUM(o.TotalAmount) AS TotalAmount

FROM Orders o

GROUP BY

o.CustomerID

) AS HighestOrders

);


/*12. Order Summary by Item*/

/*Write a query to display the total quantity sold and total revenue for each item. Use GROUP BY to summarize the results.*/


SELECT

i.ItemName,

SUM(oi.Quantity) AS TotalQuantitySold,

SUM(oi.LineTotal) AS TotalRevenue

FROM

OrderItems oi

JOIN

Items i ON oi.ItemID = i.ItemID

GROUP BY

i.ItemName;


/*13. Order Summary by Customer*/

/*Write a query to display the total amount spent by each customer. Use GROUP BY to summarize the results.*/


SELECT c.CustomerID, c.FirstName, c.LastName,

SUM(o.TotalAmount) AS TotalAmountSpent

FROM

Orders o

JOIN

Customers c ON o.CustomerID = c.CustomerID

GROUP BY

c.CustomerID,

c.FirstName,

c.LastName;


/*14. Display All Items */

/*Write a query to display all items showing ItemID, ItemName, and StockQuantity.*/


SELECT i.ItemID, i.ItemName, i.StockQuantity

FROM

Items i;


/*15. Display All Orders*/

/*Write a query to display all orders showing OrderID, CustomerID, OrderDate, and TotalAmount.*/


SELECT o.OrderID, o.CustomerID,

o.OrderDate, o.TotalAmount

FROM

Orders o;
