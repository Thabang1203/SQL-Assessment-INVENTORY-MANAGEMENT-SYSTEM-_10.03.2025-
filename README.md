SQL Assessment: INVENTORY MANAGEMENT SYSTEM _10.03.2025 
Time Allocated: 3 Hours 
Saving Instructions 
• Create a folder named SQL_YOURFULLNAME on your computer’s desktop and 
save all your queries in that folder.  
• Please make sure to save your work as you work on the questions in the format 
YOURFULLNAME_SQLQueryRelevantName. Example MbomaNdaba 
_Question1and2 
• At the end, kindly send all your files attached on one email to 
anyway@ortsa.org.za 
Assessment Questions 
1. Create a Database 
Write a query to create a database called InventoryDB and a query to use it.    [2] 
2. Create a Items Table 
Create a table called Items with the following fields: 
• ItemID (Primary Key) 
• ItemName 
• Category 
• Price 
• StockQuantity               
3. Insert Item Records 
Insert the following data into the Items table: 
• (001, 'Desk', 'Furniture', 300.00, 20) 
• (002, 'Chair', 'Furniture', 150.00, 50) 
• (003, 'Notebook', 'Stationery', 10.00, 100) 
                                                                                 [2] 
• (004, 'Pen', 'Stationery', 2.00, 200) 
• (005, 'Monitor', 'Electronics', 250.00, 30)          
                                                                                 [5] 
4. Create a Customers Table 
Create a table called Customers with the following fields: 
• CustomerID (Primary Key) 
• FirstName 
• LastName 
• Email 
• Phone                 
5. Insert Customer Records 
Insert the following customer records into the Customers table: 
• (101, 'John', 'Doe', 'john.doe@gmail.com', '123-456-7890') 
• (102, 'Jane', 'Smith', 'jane.smith@gmail.com', '234-567-8901') 
• (103, 'Emily', 'Davis', 'emily.davis@gmail.com', '345-678-9012')       
6. Create an Orders Table 
Create a table called Orders with the following fields: 
• OrderID (Primary Key) 
• CustomerID (Foreign Key) 
• OrderDate 
• TotalAmount              
7. Insert Order Records 
Insert the following order records into the Orders table: 
• (001, 101, '2024-07-01', 600.00) 
• (002, 102, '2024-07-02', 300.00) 
• (003, 103, '2024-07-03', 150.00)           
8. Create an OrderItems Table 
                                                                                           [2] 
                                                                                           [3] 
                                                                                           [2] 
                                                                                           [5] 
Create a table called OrderItems with the following fields: 
• OrderItemID (Primary Key) 
• OrderID (Foreign Key) 
• ItemID (Foreign Key) 
• Quantity 
• LineTotal               
9. Insert Order Item Records 
Insert the following order item records into the OrderItems table: 
• (001, 001, 001, 2, 600.00) 
• (002, 001, 003, 5, 50.00) 
• (003, 002, 002, 2, 300.00) 
• (004, 003, 004, 10, 20.00)            
10. Best-Selling Item 
Write a query to find the best-selling item by total sales amount. Show the 
ItemName and TotalSalesAmount.            
11. Customer with Highest Orders 
                                                                                               [2] 
                                                                                               [5] 
                                                                                               [3] 
Write a query to find the customer who has placed the highest total orders. Show 
the CustomerID, FirstName, LastName, and TotalAmount.          
                                                                                               [3] 
12. Order Summary by Item 
Write a query to display the total quantity sold and total revenue for each item. 
Use GROUP BY to summarize the results.            
13. Order Summary by Customer 
                                                                                                [3] 
Write a query to display the total amount spent by each customer. Use GROUP 
BY to summarize the results.              
                                                                                                [3] 
14. Display All Items 
Write a query to display all items showing ItemID, ItemName, and StockQuantity.  
                                                                                                [2] 
15. Display All Orders 
Write a query to display all orders showing OrderID, CustomerID, OrderDate, and 
TotalAmount.                
                                                                                                [2] 
