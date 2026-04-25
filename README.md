 ############### 1-the DB schema script ###############
 
 1- category table 
 CREATE TABLE Category(
   category_id INT PRIMARY KEY, 
   category_name VARCHAR(20) NOT NULL
   ); 

2-product table 
CREATE TABLE Porduct(
  product_id INT PRIMARY KEY, 
  category_id INT, 
  name VARCHAR(20) NOT NULL, 
  description VARCHAR(50), 
  price DECIMAL(7,2) NOT NULL, 
  stock_quantity INT NOT NULL, 
  CONSTRAINT FK_PorductCategory FOREIGN KEY(category_id) REFERENCES Category(category_id)
  ); 

3- customer table 
CREATE TABLE Customer(
  customer_id INT PRIMARY KEY, 
  first_name VARCHAR(20), 
  last_name VARCHAR(20), 
  email VARCHAR(50), 
  password VARCHAR(30)
  ); 

4-order table 
CREATE TABLE Order(
  order_id INT PRIMARY KEY, 
  customer_id INT, 
  order_date timestamp DEFAULT CURRENT_TIMESTAMP  NULL, 
  total_amount DECIMAL(10,3), 
  CONSTRAINT FK_Order_Customer FOREIGN KEY(customer_id) REFERENCES Customer(customer_id)
  ); 

  5-Order_details table 
  CREATE TABLR Order_details(
    order_detail_id INT PRIMARY KEY, 
    order_id INT, 
    product_id INT, 
    quantity INT NOT NULL, 
    unit_price DECIMAL(10, 3), 
    CONSTRAINT FK_Order_Order_details FOREIGN KEY(order_id) REFERENCES Order(customer_id), 
    CONSTRAINT FK_Order_details_Porduct FOREIGN KEY(product_id) REFERENCES Porduct(product_id)
    );


  2-the relationships between entities
  ################################################# 
  1-between Category and Product is one_to_many relationships
  2-between Customer and Order is one-to-many relationships 
  3-between Order and Product is many-to-many relationships 


  3-the ERD diagram of this sample schema
  ####################################### 
  <img width="1101" height="571" alt="_ERD diagram_ drawio" src="https://github.com/user-attachments/assets/d0a13111-d9a5-43bf-aef7-157f2c97b4ba" /> 

4-SQL query to generate a daily report of the total revenue for a specific date. 
select count(*), SUM(price), AVG(price) from orders group by(orders.order_date) having (orders.order_date = '2026-04-25'); 

5-an SQL query to generate a monthly report of the top-selling products in a given month. 
SELECT COUNT(*), ProductID FROM OrderDetails WHERE(orders.order_date = '2026-04-25') GROUP BY (ProductID) ORDER BY(COUNT(*)) DESC; 

6-


    










