# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
```
Write a SQL query to find the total amount of fruits with a unit type of 'LB'.

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
```
```sql
SELECT SUM(inventory) AS total
FROM fruits
WHERE unit = 'LB';
```

**Output:**

<img width="590" height="371" alt="image" src="https://github.com/user-attachments/assets/cc457aca-9f91-4bfc-a6fc-c34682c486da" />

**Question 2**
```
Write a SQL query to find the number of employees whose age is greater than 32.

Sample table: employee

id name age address salary

1  Paul 32  California 20000

4  Mark 25  Richtown  65000

5 David  27  Texas  85000


```
```sql
select count(*) as COUNT from employee where age>32;
```

**Output:**
<img width="459" height="400" alt="image" src="https://github.com/user-attachments/assets/48293a20-b64e-4814-af42-0f73026b38a8" />

**Question 3**
```
Write a SQL query to find the youngest employee in the company?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
```
```sql
SELECT name AS Employee_Name, age AS Age
FROM employee
order by age asc
limit 1;
```

**Output:**

<img width="648" height="390" alt="image" src="https://github.com/user-attachments/assets/fb288764-5e14-4f76-b6ce-22490dbf080a" />


**Question 4**
```
What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table
```
<img width="1014" height="179" alt="image" src="https://github.com/user-attachments/assets/ea661cb2-b7c5-43c8-864f-919eefcb4776" />

```sql
SELECT DoctorID, COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID;

```

**Output:**

<img width="717" height="709" alt="image" src="https://github.com/user-attachments/assets/701384e4-ffc2-4e7a-b57d-f6fcd3119415" />


**Question 5**
```
How many appointments are scheduled for each doctor?

Sample table:Appointments Table
```
<img width="1007" height="179" alt="image" src="https://github.com/user-attachments/assets/45ef0353-e746-431d-ba92-19504a4cf1ff" />

```sql
-SELECT DoctorID, COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID;
```

**Output:**

<img width="717" height="709" alt="image" src="https://github.com/user-attachments/assets/7fd200f5-2d99-4d23-9fa1-e6c244fce1b3" />

**Question 6**
```
What is the total number of appointments scheduled for each day?

Sample table:Appointments Table

```
<img width="1005" height="177" alt="image" src="https://github.com/user-attachments/assets/b1803a2b-be7c-46bd-b98e-89b61071f29a" />

```sql
SELECT date(AppointmentDateTime) AS AppointmentDate,
       COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY date(AppointmentDateTime);
```

**Output:**

<img width="802" height="718" alt="image" src="https://github.com/user-attachments/assets/35e5e7a1-bb08-4610-a00d-ef244dbc2db3" />

**Question 7**
```
Write the SQL query that achieves the selection of product names and the maximum price for each category from the "products" table, and includes only those products where the maximum price is greater than 15.

Sample table: products

```
<img width="791" height="183" alt="image" src="https://github.com/user-attachments/assets/958cd862-d6ae-43fa-9065-94e5017da909" />

```sql
SELECT p.category_id,
       p.product_name,
       p.price AS Price
FROM products p
JOIN (
    SELECT category_id, MAX(price) AS max_price
    FROM products
    GROUP BY category_id
    HAVING MAX(price) > 15
) m
ON p.category_id = m.category_id
AND p.price = m.max_price;
```

**Output:**

<img width="844" height="470" alt="image" src="https://github.com/user-attachments/assets/4af222b1-2a68-418a-9e2d-a4cd5888abfa" />


**Question 8**
```
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

Sample table: employee1
```
<img width="818" height="169" alt="image" src="https://github.com/user-attachments/assets/0e167faf-0749-4094-9a9d-458bc377862e" />

```sql
SELECT jdate, SUM(workhour)
FROM employee1
GROUP BY jdate
HAVING SUM(workhour) > 40;
```

**Output:**

<img width="681" height="459" alt="image" src="https://github.com/user-attachments/assets/ab44b1a8-b408-4177-893c-8931c2275a8a" />

**Question 9**
```
Write the SQL query that accomplishes the selection of number of products for each category from products table which includes only those products where the category ID is greater than 2.

Sample table: products
```
<img width="822" height="196" alt="image" src="https://github.com/user-attachments/assets/224aaab0-d4c3-4017-8ecd-a6cd831d81a2" />

```sql
SELECT category_id, COUNT(*) AS COUNT
FROM products
WHERE category_id > 2
GROUP BY category_id;
```

**Output:**

<img width="683" height="413" alt="image" src="https://github.com/user-attachments/assets/c7ca0eae-5728-42d6-8d84-739e4e2ed5c9" />


**Question 10**
```
Write the SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.

Sample table: employee1
```
<img width="804" height="185" alt="image" src="https://github.com/user-attachments/assets/ca854207-eff7-4355-b33c-63801f6af147" />

```sql
SELECT occupation, SUM(workhour)
FROM employee1
GROUP BY occupation
HAVING SUM(workhour) > 20;
```

**Output:**

<img width="699" height="527" alt="image" src="https://github.com/user-attachments/assets/af011441-4aa6-434a-8d2c-4e18f0d50090" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
