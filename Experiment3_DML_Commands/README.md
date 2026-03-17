# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
```
Write a SQL statement to Update the grade of all customers in Chennai city as  5. 

Customer table (customer_id,cust_name,city,grade,salesman_id)
```
```sql
UPDATE Customer
set grade =5
where city='Chennai';
```

**Output:**

<img width="1212" height="556" alt="image" src="https://github.com/user-attachments/assets/3ba291eb-33bc-4c25-b234-f64568f6164f" />


**Question 2**
```
Write a SQL query to determine the age group of value1 in the Calculations table as 'Child' if it is less than 13, 'Teen' if it is between 13 and 19, and 'Adult' if it is 20 or older.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0
```
```sql
select id,value1,
case when value1<13 then 'Child'
when value1 between 13 and 19 then 'Teen'
else 'Adult'
end as age_group
from calculations;
```

**Output:**

<img width="1116" height="435" alt="image" src="https://github.com/user-attachments/assets/cacad2e4-1959-4998-bba3-862cc285c6e8" />


**Question 3**
```
 Update the total selling price to quantity sold multiplied by updated selling price per unit where product id is 10 in the sales table.

SALES TABLE
name               type
-----------------  ---------------
sale_id            INT
sale_date          DATE
product_id         INT
quantity           INT
sell_price         DECIMAL(10,2)
total_sell_price   DECIMAL(10,2)
```
```sql
update SALES set total_sell_price = quantity*sell_price
where product_id =10;
```

**Output:**

<img width="1207" height="581" alt="image" src="https://github.com/user-attachments/assets/dbd191b1-7c82-4cdd-8939-75d8375faed0" />


**Question 4**
```
Write a query to fetch details of employees whose EmpLname ends with an alphabet ‘A’ and contains five alphabets.
EmployeeInfo Table

EmpID EmpFname EmpLname Department Project Address         DOB         Gender
1     Sanjay   Mehra    HR         P1      Hyderabad(HYD)  01/12/1976   M

2     Ananya   Mishra    Admin     P2      Delhi(DEL)      02/05/1968   F

```
```sql
select* from EmployeeInfo where EmpLname like '____a';

```

**Output:**

<img width="1201" height="306" alt="image" src="https://github.com/user-attachments/assets/7f8c9bd9-d7ee-4c6e-b110-0c3ddd5c4431" />


**Question 5**
```
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```
```sql
delete from customer where CUST_NAME like '%Holmes%';
```

**Output:**

<img width="1202" height="619" alt="image" src="https://github.com/user-attachments/assets/f09235b4-bb79-4285-9f47-8affd64ba3f6" />


**Question 6**
```
Write a SQL statement to get the EmployeeID, FirstName, BirthDate, Age from employees table whose age is older than 50.

[Note: Calculate age from BirthDate field (consider current date as '2023-12-30')]

employees table

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           EmployeeID  INTEGER       0                       1
1           LastName    VARCHAR(15)   0                       0
2           FirstName   VARCHAR(15)   0                       0
3           BirthDate   DATETIME      0                       0
4           Photo       VARCHAR(25)   0                       0
5           Notes       VARCHAR(10)   0                       0
 
```
```sql
SELECT
    EmployeeID,
    FirstName,
    BirthDate,
    (strftime('%Y', '2023-12-30') - strftime('%Y', BirthDate))
    - (strftime('%m-%d', '2023-12-30') < strftime('%m-%d', BirthDate)) AS age
FROM employees
WHERE
    (strftime('%Y', '2023-12-30') - strftime('%Y', BirthDate))
    - (strftime('%m-%d', '2023-12-30') < strftime('%m-%d', BirthDate)) > 50;
```

**Output:**

<img width="1040" height="637" alt="image" src="https://github.com/user-attachments/assets/734dddb0-fb04-41fc-af7e-f271996cd4fe" />


**Question 7**
```
Write a query to fetch details of employees with the address as “DELHI(DEL)” from EmployeeInfo table.
 
EmpID       EmpFname    EmpLname    Department  Project     Address     DOB         Gender
----------  ----------  ----------  ----------  ----------  ----------  ----------  ----------
2           Ananya      Mishra      Admin       P2          Delhi(DEL)  1968-05-02  F
5           Ankit       Kapoor      Admin       P2          Delhi(DEL)  1994-07-03  M
```
```sql
SELECT *
FROM EmployeeInfo
WHERE Address = 'Delhi(DEL)';
```

**Output:**

<img width="1218" height="343" alt="image" src="https://github.com/user-attachments/assets/3b58deb6-1803-4afc-b1b0-d2a895e64c28" />


**Question 8**
```
write a SQL query to identify customers who do not belong to the city of 'New York' or have a grade value that exceeds 100. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
```
```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE city <> 'New York'
  AND grade = 100;
```

**Output:**

<img width="1220" height="471" alt="image" src="https://github.com/user-attachments/assets/9749a930-9833-432a-a7e2-a1719565eac0" />


**Question 9**
```
Write a SQL query to Delete customers from 'customer' table where 'OPENING_AMT' is between 4000 and 6000.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```
```sql
DELETE FROM customer
WHERE OPENING_AMT BETWEEN 4000 AND 6000;
```

**Output:**

<img width="1198" height="708" alt="image" src="https://github.com/user-attachments/assets/dc06f2f8-23dc-4e2c-8975-397f989e4538" />


**Question 10**
```
Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.


Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```
```sql
UPDATE employees
SET email = 'Unavailable';
```

**Output:**

<img width="1198" height="510" alt="image" src="https://github.com/user-attachments/assets/bd4335f4-486d-4a02-96a1-ea0ce04137b0" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
