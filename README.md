# SQL (Structured Query Language) Class

### Project Title : Employee Database
---
### Project Overview

This project aims to access, manipulate, and analyze data stored in a company's databases. It will retrieve, filter, and transform data to gain insights and make informed decisions. 
---
### Data Analysis

```SQL
CREATE DATABASE SQL_CLASS

CREATE TABLE dbo.Employee (
staffid varchar (10) NOT NULL,
FirstName varchar (255) NOT NULL,
SecondName varchar (255),
Gender varchar (10),
Date_of_Birth date,
HireDate datetime,
primary key (staffid)
)
Select * from Employee

Insert into Employee (staffid, firstname, secondname, gender,Date_of_Birth, hiredate)
values ( 'AB401', 'ayan', 'olakun', 'female', '1992-08-22', '2018-02-09'),
( 'AB212', 'okorie', 'mercy', 'female','1988-10-09', '2018-10-09'),
( 'AB223', 'joshua', 'chukwuemeka', 'male','1980-10-09', '2022-02-09'),
( 'AB234', 'sanni', 'ibrahim', 'male','1958-10-09', '2019-09-23'),
( 'AB254', 'mercy', 'olanipekun', 'female','1982-10-09', '2020-02-09'),
( 'AB249', 'johnson', 'mercy', 'female','1982-10-09', '2019-12-09'),
( 'AB298', 'ayomide', 'halleluyah', 'female', '1982-10-09','2018-07-11'),
( 'AB260', 'deborah', 'justin', 'female','1982-10-09', '2018-02-09'),
( 'AB281', 'wale', 'olanipekun', 'male','1982-10-09', '2018-02-09')
```
```-------to drop table --------
drop table employee
```

```----delete sql command------
delete from employee
where staffid  = 'ab281'
```

```-----truncate sql command------
truncate table employee
```

```------identity in SQL -----
CREATE TABLE PERSON (
personid int identity (1,1) primary key not null,
personname varchar (255) not null,
age int
)
Select * from Person

insert into PERSON (personname, age)
values ('saidu', 45),
('adebanjo', 49),
('olorunda', 33),
('martha', 88),
('sandi', 100),
('jackson', 22),
('okunola', 19),
('esther', 45)

------Insert more records into Employee table-------

```insert into [dbo].[Employee]
values ( 'AB200', 'ayomide', 'halleluyah', 'female', '1982-10-09','2018-07-11'),
( 'AB405', 'deborah', 'justin', 'female','1982-10-09', '2018-02-09'),
( 'AB282', 'wale', 'olanipekun', 'male','1982-10-09', '2018-02-09'),
( 'AB278', 'shukurat', 'lasisi', 'female','1982-10-09', '2018-02-09'),
( 'AB240', 'johnson', 'mercy', 'female','1982-10-09', '2019-12-09'),
( 'AB299', 'ayomide', 'halleluyah', 'female', '1982-10-09','2018-07-11'),
( 'AB268', 'deborah', 'justin', 'female','1982-10-09', '2018-02-09'),
( 'AB286', 'wale', 'olanipekun', 'male','1982-10-09', '2018-02-09'),
( 'AB270', 'shukurat', 'lasisi', 'female','1982-10-09', '2018-02-09')

select * from [dbo].[Employee]
```
---- to create second table call SALARY TABLE-------

```CREATE TABLE Salary (
salary_id int identity (1,1)not null,
Staffid varchar (255),
firstname varchar (255),
lastname varchar (255),
department nvarchar(max),
salary decimal (10, 3) ---(10: precision, 3:scale)
)
select * from [dbo].[Salary]

insert into salary (staffid, FirstName, lastname, Department, Salary)
values ( 'AB401', 'ayan', 'olakun', 'Information Tech.', 45000.45),
( 'AB212', 'okorie', 'mercy','Account',500000.99999),
( 'AB223', 'joshua', 'chukwuemeka', 'Human Resources',100560.9339999),
( 'AB234', 'sanni', 'ibrahim', 'Sales and Marketing',845688.99),
( 'AB254', 'mercy', 'olanipekun', 'Account',8889.999999),
( 'AB249', 'johnson', 'mercy', 'Information Tech.',234000.90909090),
( 'AB298', 'ayomide', 'halleluyah', 'Logistics', 678000.991999),
( 'AB260', 'deborah', 'justin', 'Logistics',900099.00697969),
( 'AB281', 'wale', 'olanipekun', 'Information Tech',873093.2344)
```

```----SUM, COUNT, MAX, MIN, AVERAGE---------------------------------

SELECT SUM(Salary) AS TOTALSALARY FROM Salary

SELECT AVG(Salary) AS AVERAGESALARY FROM Salary

SELECT COUNT(Staffid) AS EmployeeCount FROM EMPLOYEE

SELECT COUNT(Staffid) AS NumberOfEmployee FROM Salary
```

```--update staff name-----

select * from [dbo].[Employee]

update employee
set secondname = 'Endurance'
where staffid = 'AB405'
```

```----UPDATE DEPARTMENT-------

select * from [dbo].[Salary]

UPDATE SALARY
SET department = 'Information Tech.'
where Staffid = 'AB234'

SELECT * FROM Salary
WHERE Staffid = 'AB281'
```
----CREATE ADDITIONAL COLUMN INTO EMPLOYEE TABLE-------

```ALTER TABLE EMPLOYEE
ADD State_of_Origin varchar (50)

select * from employee

UPDATE EMPLOYEE
SET State_of_Origin = 'Ekiti'
where staffid = 'AB268'
```
```CREATE TABLE Payment (
paymentid int identity (1,1) primary key,
Account_No bigint not null,
staffid int,
Bank varchar (255) default 'Zenith Bank',
Payment_Method varchar (50) check (Payment_Method = 'Cash' or Payment_Method = 'Transfer')
)

alter table payment
alter column staffid varchar (30)

select * from Payment

insert into Payment (account_no,staffid,payment_method )
values (2033030303, 'AB200', 'transfer'),
(2123459910, 'AB401',  'transfer'),
(2034562240, 'AB254',  'cash'),
(2234556303, 'AB212',  'transfer'),
(2033037703, 'AB249',  'cash'),
(2033030303, 'AB298',  'cash'),
(2455657503, 'AB260',  'transfer'),
(2045595953, 'AB281',  'cash'),
(2033030303, 'AB273',  'transfer'),
(2077778903, 'AB299',  'transfer'),
(2033030301, 'AB286', 'transfer'),
(2123459911, 'AB260',  'transfer'),
(2034562241, 'AB270',  'cash'),
(2234556302, 'AB104',  'transfer'),
(2033037705, 'AB268',  'cash'),
(2033030306, 'AB270',  'cash'),
(2455657509, 'AB300',  'transfer')
```
------those who received their salary by cash-----

```SELECT * FROM Payment
WHERE Payment_Method = 'Cash'
```

```select * from Payment
where Payment_Method = 'TRANSFER'
```
```SELECT COUNT(*)  AS ZenithStaff FROM Payment
where Bank = 'Zenith Bank'
```
```SELECT COUNT(*)  FROM Payment
where Bank = 'GT BANK'
```
```SELECT COUNT(*)  FROM Payment
where Payment_Method = 'Transfer'
```
```SELECT COUNT(*)  FROM Payment
where Payment_Method = 'cASH'
```
---Analysis on Employee table------

```select * from Employee

select count(*)  from employee 
where state_of_origin  = 'Kano'
```
```select count(*)  from employee 
where gender  = 'male'
```

```select count(*)  from Salary
where department  = 'Human Resources'
```

```select top 5 * from Salary
select * from Salary
where salary > 700000

select Staffid,
salary *from Salary
where salary < 700000
```
--------Group By----------

```Select *from Employee

Select Count(staffid) as staffperstate, State_of_Origin from Employee
Group by State_of_Origin

Select *from Salary

Select Count(staffid) as department, department from Salary 
Group by department
```
--------Order By------------

```Select Count(staffid) as staffperstate, State_of_Origin from Employee
Group by State_of_Origin
Order by count(staffid)desc

Select Count(staffid) as staffperstate, State_of_Origin from Employee
Group by State_of_Origin
Order by count(staffid)asc
```
--------Having---------

```Select Count(staffid) as staffperstate, State_of_Origin from Employee
Group by State_of_Origin
Having COUNT (staffid)>=3

Select Count(staffid) as staffperstate, State_of_Origin from Employee
Group by State_of_Origin
Having COUNT (staffid)<=3
```
-------Sort by Column Index-----

```Select Count(staffid) as staffperstate, State_of_Origin from Employee
Group by State_of_Origin
Order by 1 asc

Select Count(staffid) as staffperstate, State_of_Origin from Employee
Group by State_of_Origin
Order by 2 asc
```
-------Comparison/Relational Operator------------

< Less than
> Greater than 
<> Not Equal

```Select *from Salary

Select *from Salary
where salary = 500001.000

Select *from Salary
where salary > 500001.000

Select *from Salary
where salary < 500001.000
```
--------Range Operators----------

Between 
Not Between

```Select *from Salary
Where Salary between 50000 and 70000

Select *from Salary
Where Salary not between 50000 and 70000
```
