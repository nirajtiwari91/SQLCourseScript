SQL Backup DB

******QUERY***************
Create DataBASE Customer --Create Database
USE CUSTOMER  --Use Database
DROP DATABASE CUSTOMER --Drop Database
--Create Table
CREATE TABLE tblCustomer
( 
  ID INT Primary key IDENTITY(1,1),
  FirstName VARCHAR(50) NOT NULL,
  LastName VARCHAR(50) NOT NULL,
  Gender VARCHAR(50) NOT NULL,
  Address VARCHAR(50) NOT NULL
)
Drop Table  tblCustomer--Drop Table

--Alter DataTypes
Alter table tblCustomer Alter Column Gender VARCHAR(10)
--Added New Columns
Alter table tblCustomer ADD CITY VARCHAR(50)
--Drop Column
Alter table tblCustomer drop column CITY

--UNIQUE
Create table tblGuestCustomer
( 
 ID INT NOT NULL UNIQUE,
 NAME VARCHAR(50)

)
--FOREGNKEY
create table tblcountry(
CountryID INT PRIMARY KEY IDENTITY(1,1),
CountryName varchar(200)
)

Create table tblState
(
StateID INT PRIMARY KEY IDENTITY(1,1),
StateName varchar(200),
CountryID INT FOREIGN KEY REFERENCES tblcountry(CountryID)
)
--Default constra
Create table tblSignUp
(
 ID INT PRIMARY KEY IDENTITY(1,1),
 Name VARCHAR(50),
 Mode varchar(50) default 'Signup'
)

INSERT INTO tblSignUp(Mode)
VALUES('mode')

select * from tblSignUp

select getutcdate()
select convert(varchar(10), getdate(), 112)

--Views
select * from tblSignUp

Create view ViewtblSignUp as 
select * from tblSignUp

select * from ViewtblSignUp

--Injection
Create table tblLogin
(Username varchar(10),
Password varchar(10))

insert into tblLogin values('Niraj', '12345')
SELECT * FROM tblLogin WHERE Username = 'Niraj' --and Password = '12345'

--Select
select * from tblCustomer
select ID, FirstName, LastName, Gender, Address from tblCustomer

Insert into tblCustomer(FirstName, LastName, Gender, Address)
Values('Alok', 'Tiwari', 'Male', 'Noida')
--Distinct
select Distinct FirstName, LastName, Gender, Address from tblCustomer
--Where
select ID, FirstName, LastName, Gender, Address from tblCustomer order by FirstName desc
--Update
Update tblCustomer set firstname='Ravi' where ID = 2
--delete
delete from tblCustomer where ID = 2
--Top
select top 8 ID, FirstName, LastName, Gender, Address from tblCustomer
--MIN AND MAX
SELECT * FROM tblCustomer
SELECT MIN(ID) AS MINID, MAX(ID) AS MAXID from tblCustomer
--Count
SELECT * FROM tblCustomer
SELECT SUM(ID) AS TotalRecord from tblCustomer
--Like
Select * from tblCustomer where FirstName like '%J'
--IN
Select * from tblCustomer where ID IN (1,3,5)
--BETWEEN 
Select * from tblCustomer where ID BETWEEN 1 AND 3
--Aliases
SELECT MIN(ID) AS MINID, MAX(ID) AS MAXID from tblCustomer
select firstname as name from tblcustomer
--Group by and having
select count(ID) as recordcount, firstname from
tblCustomer group by firstname having firstname = 'Alok'
--Exists
select C.ID from tblcustomer c where exists (select 1 from tblcustomer where ID  =100)
--copy table with data
select * into tblnewtable from tblcustomer
select * from tblnewtable
--case
select ID, FirstName, LastName, 
CASE WHEN GENDER = 'Male' then 1 else 2 end as Gender, Address from tblcustomer
--isnull, nullf if
select id, isnull(name, 'blank') as name, mode from tblSignUp
select id, isnull(name, 'blank') as name, nullif(mode, 'mode') from tblSignUp
--Operarors
select 4/5 as total
*****************************
