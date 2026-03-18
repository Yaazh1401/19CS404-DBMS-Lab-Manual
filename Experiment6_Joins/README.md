# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**

Write the SQL query that achieves the selection of the "cust_name" and "city" columns from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for customers in the city 'London'.

<img width="871" height="342" alt="image" src="https://github.com/user-attachments/assets/c6077ee0-6256-4790-88bf-b3dc44456ef4" />

```sql
SELECT c.cust_name, 
       c.city, 
       o.ord_no, 
       o.ord_date, 
       o.purch_amt
FROM customer c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
WHERE c.city = 'London';
```

**Output:**

<img width="1208" height="563" alt="image" src="https://github.com/user-attachments/assets/08619ad6-4844-4583-a8de-10dda4471371" />


**Question 2**

Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the city 'London'.

<img width="853" height="366" alt="image" src="https://github.com/user-attachments/assets/b4ad685a-52b3-4f12-8a2b-2475d73975fc" />

```sql
SELECT s.name
FROM salesman s
LEFT JOIN customer c
ON s.salesman_id = c.salesman_id
WHERE c.city = 'London';
```

**Output:**

<img width="584" height="542" alt="image" src="https://github.com/user-attachments/assets/fe458f71-6247-4db3-8bb5-d5e4d9fb0964" />


**Question 3**

Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and conditions filtering for test results with the test name 'X-Ray' and a result of 'Normal'.

<img width="803" height="347" alt="image" src="https://github.com/user-attachments/assets/d1e8377c-ec37-4747-9fea-e8613fd55359" />

```sql
SELECT p.*
FROM patients p
INNER JOIN test_results t
ON p.patient_id = t.patient_id
WHERE t.test_name = 'X-Ray'
AND t.result = 'Normal';
```

**Output:**

<img width="1201" height="425" alt="image" src="https://github.com/user-attachments/assets/77633ab8-0a18-4b0a-a844-99bbd9d3f106" />


**Question 4**

Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the test name from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.

<img width="822" height="353" alt="image" src="https://github.com/user-attachments/assets/01d1f450-4c61-4bf2-8328-9e3f74094c52" />

```sql
SELECT p.first_name AS patient_name, t.test_name
FROM patients p
INNER JOIN test_results t
ON p.patient_id = t.patient_id;
```

**Output:**

<img width="750" height="611" alt="image" src="https://github.com/user-attachments/assets/038095f4-6a4a-47c1-a08e-370c8fdf6d23" />


**Question 5**

Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
```sql
SELECT c.cust_name, 
       c.city, 
       o.ord_no, 
       o.ord_date, 
       o.purch_amt AS "Order Amount"
FROM customer c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
ORDER BY o.ord_date ASC;
```

**Output:**

<img width="1198" height="935" alt="image" src="https://github.com/user-attachments/assets/346ab1ce-72f4-4c72-bc27-699d8e240aab" />


**Question 6**

Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "doctor_id" column and conditions filtering for patients whose doctor has the first name 'Emily', last name 'Johnson', and a non-null discharge date.

<img width="812" height="353" alt="image" src="https://github.com/user-attachments/assets/c1f7f937-3334-4e3c-9d86-9a0fb0b0c342" />

```sql
SELECT p.first_name AS patient_name
FROM patients p
INNER JOIN doctors d
ON p.doctor_id = d.doctor_id
WHERE d.first_name = 'Emily'
AND d.last_name = 'Johnson'
AND p.discharge_date IS NOT NULL;
```

**Output:**

<img width="472" height="467" alt="image" src="https://github.com/user-attachments/assets/458195d2-bceb-4359-b150-1a105ac3e1a0" />


**Question 7**

From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```sql
SELECT c.cust_name,
       c.city,
       c.grade,
       s.name AS Salesman,
       s.city AS city
FROM customer c
INNER JOIN salesman s
ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id ASC;
```

**Output:**

<img width="1213" height="845" alt="image" src="https://github.com/user-attachments/assets/f0f82e10-fa4b-4c03-9150-ee8aae77e27d" />


**Question 8**

Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the specialization from the "doctors" table (aliased as "Doctor_specialization"), with an inner join on the "doctor_id" column and a condition filtering for patients admitted between '2024-01-01' and '2024-01-31'.

PATIENTS TABLE:
name             type
---------------  ---------------
patient_id       INT
first_name       VARCHAR(50)
last_name        VARCHAR(50)
date_of_birth    DATE
admission_date   DATE
discharge_date   DATE
doctor_id        INT

DOCTORS TABLE:

name             type
---------------  ---------------
doctor_id        INT
first_name       VARCHAR(50)
last_name        VARCHAR(50)
specialization   VARCHAR(100)
```sql
SELECT p.first_name AS patient_name,
       d.specialization AS Doctor_specialization
FROM patients p
INNER JOIN doctors d
ON p.doctor_id = d.doctor_id
WHERE p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="802" height="463" alt="image" src="https://github.com/user-attachments/assets/d3a14c03-271c-44f2-a262-5a41228a4e67" />


**Question 9**

Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "appointments" table (aliased as "a"), with an inner join on the "patient_id" column.

<img width="850" height="356" alt="image" src="https://github.com/user-attachments/assets/5cef52cc-4f62-4d0e-9471-7c58368352cf" />

```sql
SELECT p.first_name AS patient_name, a.*
FROM patients p
INNER JOIN appointments a
ON p.patient_id = a.patient_id;
```

**Output:**

<img width="1199" height="637" alt="image" src="https://github.com/user-attachments/assets/efb24d4f-d524-4aac-b4bf-9b47ce7e9d79" />


**Question 10**

Write the SQL query that accomplishes the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.

PATIENTS TABLE:

name             type
---------------  ---------------
patient_id       INT
first_name       VARCHAR(50)
last_name        VARCHAR(50)
date_of_birth    DATE
admission_date   DATE
discharge_date   DATE
doctor_id        INT

SURGERIES TABLE:

name             type
---------------  ---------------
surgery_id       INT
patient_id       INT
surgeon_id       INT
surgery_date     DATE

```sql
SELECT p.first_name, s.*
FROM patients p
INNER JOIN surgeries s
ON p.patient_id = s.patient_id
WHERE p.first_name = 'Alice';
```

**Output:**

<img width="1211" height="488" alt="image" src="https://github.com/user-attachments/assets/fcd50b01-7977-4ca1-a350-bce0384f36bd" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
