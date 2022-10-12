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

The SQL TRUNCATE TABLE command is used to delete complete data from an existing table.

	TRUNCATE TABLE table_name;

Usage ==> truncate table orders;	

## ************ 19 - UPDATE Command *****************

The UPDATE statement is used to update records in a table 

	UPDATE table_name SET column1= value1, column2= value2 WHERE Condition;

Usage:- 1:- Update Customers SET ContactName= 'Juan' WHERE Country='Mexico';

2:- update orders
set order_price=1100
where order_id = 4;


## ************ 20 - CONSTRAINT *****************

SQL CONSTRAINT are used to specify rules for the data in a table.

NOT NULL:- Ensure that a column cannot have a NULL value.

UNIQUE:- Ensure that all values in a column are different.

PRIMARY KEY:- A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table.

FOREIGN KEY:- Prevent actions that would destroy links between tables.

CHECK:- Ensures that the  values in a  column satisfies a specific condition.

DEFAULT:- Sets a default value for a column if no value is specified.

## ************ 21 - NOT NULL *****************

By Default a table column can hold NULL Values. The NOT NULL Constraint enforces a column to NOT accept NULL values.

CREATE TABLE Persons(
ID int NOT NULL,
LastName varchar(255) NOT NULL,
FirstName varchar(255) NOT NULL,
Age int
);

Usage:- insert into persons(lastname, firstname) values('Krishna', 'Thakur'); ==> This throws an error 1364. Field Id doesn't have default value.

insert into persons(id, lastname, firstname) values(1,'Krishna', 'Thakur'); ==> This works perfectly fine.

==> drop table Persons; ==> To delete persons table.

## ************ 22 - SQL UNIQUE CONSTRAINT*****************

The UNIQUE constraint ensures that all values in a column are different.

CREATE TABLE Persons(
ID int NOT NULL UNIQUE ,
LastName varchar(255) NOT NULL,
FirstName varchar(255),
Age int
);

insert into persons(id, lastname, firstname) values(1,'Krishna', 'Thakur');

select * from Persons;

insert into persons(id, lastname, firstname) values(1,'Krishna', 'Thakur');

Note:- If we again insert the value with same id then it will not allow to add duplicate value into table. It throws an error code 1062. Duplicate entry '1' for key 'Persons.ID'.
So we have to change the ID value.

insert into persons(id, lastname, firstname) values(2,'Krishna', 'Thakur');

## ************ 23 - SQL CHECK CONSTRAINT*****************

The CHECK constraint is used to limit the value range that can be placed in a column.

If you define a CHECK constraint on a column it will allow only certain value for this column.

CREATE TABLE Persons(
ID int NOT NULL,
LastName varchar(255) NOT NULL,
FirstName varchar(255),
Age int,
CHECK (Age>=18)
);

insert into persons(id, lastname, firstname, age) values(2,'Krishna', 'Thakur', 12); 

The above command will throw an Error Code: 3819. Check constraint 'persons_chk_1' is violated. because we insert age 12 which is less than 18 which is not allowed.

So to remove this error we have to insert age greater than or equal to 18.

insert into persons(id, lastname, firstname, age) values(2,'Krishna', 'Thakur', 28); 


## ************ 24 - PRIMARY KEY (Unique + Not NULL)*****************

The PRIMARY KEY constraint uniquely identifies each record in a table.
PRIMARY KEY must contain UNIQUE values, and cannot contain NULL values.
A table can have only ONE Primary key.

CREATE TABLE Persons(
ID int NOT NULL,
LastName varchar(255) NOT NULL,
FirstName varchar(255),
Age int,
PRIMARY KEY (ID)
);


		-- Creating a Primary Key --

			create table orders(
			order_id int primary key,
			order_number int,
			location varchar(255)
			);

			insert into orders(order_id, order_number, location) values(1, 100, 'Delhi');

			insert into orders(order_id, order_number, location) values(2, 101, 'Gurgaon');

			insert into orders(order_id, order_number, location) values(3, 102, 'Noida');

			select * from orders;


## ************ 25 - FOREIGN KEY *****************

The FOREIGN KEY constraint is used to prevent actions that would destroy links between tables.
A FOREIGN KEY is a field (or collection of fields) in one table, that refers to the PRIMARY KEY in another table.
The table with the foreign key is called the child table, and the table with the primary key is called the referenced or parent table.

CREATE TABLE Orders(
 OrderID int NOT NULL,
 OrderNumber int NOT NULL,
 PersonID int,
 PRIMARY KEY(OrderID),
 FOREIGN KEY(PersonID) REFERENCES Persons(PersonID)
);



		-- Creating a Foreign Key --

		create table Person(
		person_id int,
		person_name varchar(255),
		order_id int,
		foreign key(order_id) references orders(order_id)

		);

		insert into Person(person_id, person_name, order_id) values(10, 'Krishna', 10);

		The above insert command will thrown an error.
		Error Code: 1452. Cannot add or update a child row: a foreign key constraint fails (`demo_db`.`person`, CONSTRAINT `person_ibfk_1` FOREIGN KEY (`order_id`) REFERENCES `orders` (`order_id`)). 
		
		Because the Order_Id value is different from the parent table(orders table). To remove this error we have to keep the order_id value same as orders table.

		insert into Person(person_id, person_name, order_id) values(10, 'Krishna', 1);

		Now it will works perfectly fine.

Important Point about Primary key  and Foreign Key:-

1. A Table can have only one primary key (unique + not null).
2. Foreign key - To make relationship between two or more than two tables .
3. One table contain primary key and other table contain foreign key.
4. A common column in both the tables (common column should have same datatype).
5. Primary key(parent table) + Foreign key(child table).

## ************ 26 - DEFAULT Constraint *****************

The DEFAULT constraint is used to set a default value for a column.

The default value will be added to all new records, if no other value is specified.

CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    City varchar(255) DEFAULT 'Delhi'
);

insert into Persons(ID, LastName, FirstName, Age, City) values (1,'Thakur','Krishna',28,'Noida');

select * from persons;

insert into Persons(ID, LastName, FirstName, Age) values (2,'Thakur','Krishna',28);

The above insert command will update the city value Delhi by default.


The DEFAULT constraint can also be used to insert system values, by using functions like CURRENT_DATE():

CREATE TABLE Orders (
    ID int NOT NULL,
    OrderNumber int NOT NULL,
    OrderDate date DEFAULT CURRENT_DATE()
);


** DEFAULT on ALTER TABLE
	To create a DEFAULT constraint on the "City" column when the table is already created, use the following SQL:

		ALTER TABLE Persons
		ALTER City SET DEFAULT 'Sandnes';

** DROP a DEFAULT Constraint

To drop a DEFAULT constraint, use the following SQL:

	ALTER TABLE Persons
	ALTER City DROP DEFAULT;


## ************ 27 - JOIN Operation *****************

A JOIN clause is used to combine rows from two or more tables based on a related column between them.

INNER JOIN/JOIN:- Return rows that have matching values in both tables.

LEFT JOIN:- Return all Rows from the left table, even if there are no matches in right table.

RIGHT JOIN:- Return all Rows from the Right table, even if there are no matches in the left table.

FULL JOIN:- Return rows when there is a match in one of the tables.

SELF JOIN:- A self join is a regular join, but the table is joined with itself.

CROSS JOIN:- The CROSS JOIN keyword returns all records from both tables (table1 and table2).


## ************  INNER JOIN Operation *****************

Usage:- Select table1.column1, table2.column2... FROM table1 INNER JOIN table2 ON
table1.common_field = table2.common_field;

For Example:- select orders.person_id, persons.firstname, persons.lastname, orders.order_number from persons inner join
orders on persons.person_id = orders.person_id;

## ************  LEFT JOIN Operation *****************

select persons.firstname, persons.lastname, orders.order_number, orders.person_id from persons left join
orders on persons.person_id = orders.person_id;

## ************  RIGHT JOIN Operation *****************

select persons.firstname, persons.lastname, orders.order_number, orders.person_id from persons right join
orders on persons.person_id = orders.person_id;


## ************ 28 - INCREMENT *****************


Auto Increment allows a unique number to be generated when a new record is inserted into a
table.

Usate:- CREATE TABLE Persons(
 Person_ID NOT NULL auto_increment,
 LastName varchar(255) NOT NULL,
 FirstName varchar(255),
 Age int,
 PRIMARY KEY(Person_ID)
);


create table hello(
person_id int primary key auto_increment,
personname varchar(255),
salary int
);

insert into hello(personname, salary) values('Krishna Thakur', 12000);
insert into hello(personname, salary) values('Mohit Thakur', 10000);
insert into hello(personname, salary) values('Mohit Sharma', 9000);
insert into hello(personname, salary) values('Aashish Thakur', 11000);
insert into hello(personname, salary) values('Ashish Thakur', 15000);

select * from hello;


## ************ 29 - TOP CLAUSE *****************

TOP Clause is used to specify the number of record to return.

Usage:- Select * from person limit 5;


## ************ SQL Command *****************

DDL:- Data Definition Language

DQL:- Data Query Language

DML:- Data Manipulation Language

DCL:- Data Control Language

TCL:- Transaction Control Language

------------------------------------------

DDL:- CREATE, DROP, ALTER, TRUNCATE

DML:- INSERT, DELETE, UPDATE

DQL:- SELECT

TCL:- COMMIT, SAVEPOINT, ROLLBACK

DCL:- GRANT, REVOKE


