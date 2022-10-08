# ************SQL Tutorial******************

## ************ 0 - Creating Database******************

==> It is used to Creaating a Database.

==> CREATE DATABASE Demo_DB;

## ************ 1 - Creating Table******************

==> It is used to create a Table.

create table Demo_DB.Hello
(
	PersonID int,
	firstName varchar(255),
	lastName varchar(255),
	city varchar(255),
    salary int
);

## ************ 2 - Inserting Data into Table******************

==> It is used to Insert the value in Table.

insert into Demo_DB.Hello(personid, firstname, lastname, city, salary) 
values(1, 'Krishna','Thakur','Hathras', 10000);

Select * from Demo_DB.Hello;

insert into Demo_DB.Hello(personid, firstname, lastname, city, salary) 
values(2, 'Aashish','Sharma','Sikandra Rao', 11000);

insert into Demo_DB.Hello(personid, firstname, lastname, city, salary) 
values(3, 'Anurag','Yadav','Sikandra Rao', 10000);

insert into Demo_DB.Hello(personid, firstname, lastname, city, salary) 
values(4, 'Mohit','Sharma','Aligarh', 10000);

insert into Demo_DB.Hello(personid, firstname, lastname, city, salary) 
values(5, 'Lokesh','Yadav','Gurgaon', 8000);

insert into Demo_DB.Hello(personid, firstname, lastname, city, salary) 
values(1, 'Krishna','Thakur','Hathras', 10000);

insert into Demo_DB.Hello(personid, firstname, lastname, city, salary) 
values(1, 'Krishna','Thakur','Hathras', 12000);

## ************ 3 - AND & OR Operator******************

SELECT * from Demo_DB.hello where firstname = "Krishna" AND lastname = "Thakur";

Select * from Demo_DB.hello where firstname = "Krishna" OR lastname = "Sharma";

Select * from Demo_DB.hello where firstname = "Krishna" OR lastname = "Sharma";


## ************ 4- Where Clause******************

select * from Demo_DB.Hello where PersonID = 3;


## ************ 5 - ORDER BY *****************

==> By default sort in Ascending order we can also use 'DESC' keyword to sort in Descending order.

Select * from Demo_DB.Hello;

Select * from Demo_DB.Hello order by salary;

Select * from Demo_DB.Hello order by salary DESC;


## ************ 6 - Distinct Statement *****************

==> It  is used to print the original value. It removes the duplicate value from columns

Select distinct(firstname) from Demo_DB.Hello;


## ************ 7 - Delete Statement *****************

==> Delete Statement is used to delete the rows in a Table.

Note:- If you don't write the 'Where' Clause, All the records will be deleted.

### SET SQL_SAFE_UPDATES = 0; // This command is used when Sql gives an error 1175. You are using safe update.

delete from Demo_DB.Hello where PersonID = 1 AND firstname = "Mohit";

Note:- If we don't want to use Database name with table(Demo_DB.Hello ) then we have use this command first

==> USE Demo_DB;

After this we can simply use simple command without database name.

Select * from Hello;

## ************ 8 - Date Time *****************

Select now(), curdate(), curtime();

## ************ 9 - Date Time *****************

AVG():- Select AVG(column_name) from table_name;

COUNT():- Select COUNT(column_name) from table_name;

LCASE():- Select LCASE(column_name) from table_name;

MAX():- Select MAX(column_name) from table_name;

MIN():- Select MIN(column_name) from table_name;

SUM():- Select SUM(column_name) from table_name WHERE condition;

ROUND():- Select column_name, ROUND(column_name, decimals) from table_name;

SUBSTRING():- is used to get part of a String.
				SELECT LastName, SUBSTR(FirstName, 1, 1) AS Initial from Persons;

UCASE():- Select UCASE(column_name) from table_name;

REPLACE():- Select REPLACE(CustomerName, 'Brown', 'Hello') from Orders;


Example==>

Select avg(salary) from hello;

select count(salary) from hello;

select LCASE(firstName) from hello;

select UCASE(firstName) from hello;

select MAX(salary) from hello;

select MIN(salary) from hello;

Select SUM(Salary) from hello;

Select SUM(Salary) from hello where salary > 10000;


## ************ 10 - GROUP BY Statement *****************

==> GROUP BY Statement is used in conjunction with aggregate functions (Above Function in 9 points all are aggregate function) to group the result set by one or more columns.

Usage ==> SELECT Column_name(s), FROM table_name WHERE Condition GROUP BY column_name(s);

--------------Create Another Table to Use Group By-----------------------------------

create table orders(
order_id int,
order_price int,
customer varchar(255)
);

insert into orders(order_id, order_price, customer) values(1, 1200, "John");

insert into orders(order_id, order_price, customer) values(2, 2500, "Brown");

insert into orders(order_id, order_price, customer) values(3, 4500, "John");

insert into orders(order_id, order_price, customer) values(4, 800, "Taylor");

insert into orders(order_id, order_price, customer) values(5, 5000, "John");

insert into orders(order_id, order_price, customer) values(6, 3000, "Brandon");

insert into orders(order_id, order_price, customer) values(7, 200, "Steven");

insert into orders(order_id, order_price, customer) values(8, 2100, "Thomas");

insert into orders(order_id, order_price, customer) values(9, 1200, "John");

insert into orders(order_id, order_price, customer) values(10, 1100, "Marie");

select * from orders;

-- Question 1:- Find the total sum(Total Orders) from each customers;--

	==>	select * from orders;

	==> select customer, sum(order_price) from orders group by customer;

	==> select customer, count(order_price) from orders group by customer;


## ************ 11 - HAVING Clause *****************

==> The HAVING clause was added to SQL because the WHERE keyword cannot be used with 
aggregate functions.

Usage ==> Select Customer Sum(order_price) from orders group by Customer Having Sum(Order_Price)<4000;


-- Question 2:- We want to find the if any customer have a total order of more than 2000. --

select customer, sum(order_price) from orders group by customer having sum(order_price) > 2000;

## ************ 12 - ALTER TABLE STATEMENT *****************

ALTER TABLE statement is used to add, delete, or modify columns in existing table.

1:- To Add Column in Table ==> (ALTER TABLE table_name ADD column_name dataType)

2:- To Delete Column in Table ==> (ALTER TABLE table_name drop column column_name)

3:- To Change the data types of a column in a table ==> (ALTER TABLE table_name modify column column_name dataTypes) 

Usage ==>1:- alter table orders add location varchar(255);

2:- alter table orders drop column location;

3:- alter table orders modify column order_price int;


## ************ 13 - ALIAS *****************

SQL ALIAS :- You can give a table or a column another name by using an alias. It is a temporary name.

USAGE==> Select Column_name as alias_name from table_name;

		select customer as customer_name from orders;	


## ************ 14 - DROP *****************

SQL DROP DATABASE :- The DROP DATABASE Statement is used to drop an existing SQL Database.

SQL DROP TABLE:- The DROP TABLE Statement is used to drop an existing table in a Database.

USAGE:- 1:- DROP DATABASE Database_name;

2:- DROP TABLE Table_name;

	drop table orders;

	drop database Demo_DB;


## ************ 15 - Between Operator *****************

Ther BETWEEN Operator is used in a WHERE Clause to select a range of data between two values. Begin and end value are included.

SELECT * FROM Products WHERE Price BETWEEN 10 and 20

select * from orders where order_price between 1000 and 2500;

## ************ 16 - IN Operator *****************

IN Operator allows you to specify multiple values in a WHERE Clause. The number of values in
the parenthesis can be one or more, with each values seperated by commas.


USAGE:- SELECT * From Persons where LASTNAME IN ("JAMES", "KRISHNA");

select * from orders where customer in ("John", "Brown");

select order_price, customer from orders where customer in ("John", "Brown");


## ************ 17 - SQL LIKE Operator *****************

THE SQL LIKE Operator is used in a WHERE Clause to search for a specified Pattern in a column.

WHERE CustomerName LIKE 'a%'  ==> Finds any values that start with "a".

WHERE CustomerName LIKE '%a'  ==> Finds any values that ends with "a".

WHERE CustomerName LIKE '%or%' ==> Finds any values that have "or" in any positions.

WHERE CustomerName LIKE '%_r%' ==> Finds any values that have "r" in the second positions.

WHERE CustomerName LIKE '%a_%' ==> Finds any values that start with "a" and are atleast 2 character in length.

WHERE CustomerName LIKE '%a__%' ==> Finds any values that start with "a" and are atleast 3 character in length.

WHERE ContactName LIKE 'a%o' ==> Finds any values that start with "a" and  ends with "o".

USAGE ==> 1:- select * from orders where customer like "j%";

2:- select * from orders where customer like "%n";

3:- select * from orders where customer like "%ow%";

## ************ 18 - TRUNCATE Command *****************


