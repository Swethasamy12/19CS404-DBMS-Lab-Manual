# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1283" height="581" alt="image" src="https://github.com/user-attachments/assets/26df60e3-49a1-4764-9ffc-461a0dc4256e" />

```sql
SELECT 
    ord_no,
    purch_amt,
    ord_date,
    customer_id,
    salesman_id
FROM orders
WHERE salesman_id IN (
    SELECT salesman_id
    FROM orders
    WHERE customer_id = 3007
);
```

**Output:**

<img width="1281" height="519" alt="image" src="https://github.com/user-attachments/assets/69ed8ece-55c8-4c17-b9a0-72a9984276f9" />

**Question 2**
---
<img width="1286" height="514" alt="image" src="https://github.com/user-attachments/assets/39218f6b-703b-478e-8217-b05e0bb8dc0f" />

```sql
SELECT 
    grade,
    COUNT(*)
FROM customer
WHERE grade > (
    SELECT AVG(grade)
    FROM customer
    WHERE city = 'New York'
)
GROUP BY grade
ORDER BY grade;
```

**Output:**

<img width="772" height="420" alt="image" src="https://github.com/user-attachments/assets/bad90267-39bc-42b3-a8ac-d48c3f40786d" />

**Question 3**
---
<img width="1282" height="649" alt="image" src="https://github.com/user-attachments/assets/dfd49af5-247c-49e7-a084-76648eec84bd" />

```sql
select student_id,student_name,subject,grade
from GRADES g1
where grade =(
       select min(grade)
       from GRADES g2
       where g1.subject=g2.subject
);
```

**Output:**

<img width="1300" height="559" alt="image" src="https://github.com/user-attachments/assets/a1f9e79a-443e-4cee-8a2b-9edf81f13ec7" />

**Question 4**
---
<img width="1282" height="662" alt="image" src="https://github.com/user-attachments/assets/fe7be917-066e-435b-9a30-3c9bcda7b13b" />

```sql
select student_name,grade
from GRADES g1
where grade = (
     select max(grade)
     from GRADES g2
     where g1.subject=g2.subject
);

```

**Output:**

<img width="1275" height="445" alt="image" src="https://github.com/user-attachments/assets/f2b22c55-9c57-4d0e-8583-5859a123e084" />

**Question 5**
---
<img width="1212" height="685" alt="image" src="https://github.com/user-attachments/assets/962ad230-9978-4eb0-9bff-03a2b0edc559" />

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 4500;
```

**Output:**

<img width="1287" height="480" alt="image" src="https://github.com/user-attachments/assets/b6dc63f1-3980-4dec-a846-2cfe101bbefc" />

**Question 6**
---
<img width="1261" height="661" alt="image" src="https://github.com/user-attachments/assets/b1151c5d-f843-4fc8-8162-c95f435fd098" />

```sql
SELECT *
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 1000000
);
```

**Output:**

<img width="1283" height="507" alt="image" src="https://github.com/user-attachments/assets/d6f9ad65-2f68-4e0d-95ca-23825b4f1281" />

**Question 7**
---
<img width="1121" height="491" alt="image" src="https://github.com/user-attachments/assets/a09503e5-dc3e-442f-a4dc-7ef7b06edd4a" />

```sql
select *
from medications 
where dosage = (
     select min(dosage)
     from medications 
);
```

**Output:**

<img width="888" height="479" alt="image" src="https://github.com/user-attachments/assets/873eb7b3-6208-4e37-9c94-4436e3b6d41e" />

**Question 8**
---
<img width="1100" height="718" alt="image" src="https://github.com/user-attachments/assets/75fd988a-9980-4090-94f6-8f0f09184a82" />

```sql
SELECT *
FROM customer
WHERE customer_id = (
    SELECT salesman_id - 2001
    FROM salesman
    WHERE name = 'Mc Lyon'
);
```

**Output:**

<img width="1306" height="371" alt="image" src="https://github.com/user-attachments/assets/681ec8ac-6041-4db6-a79b-e3a3ed014d7f" />

**Question 9**
---
<img width="1290" height="806" alt="image" src="https://github.com/user-attachments/assets/0f93e1c9-6db0-4095-8cd7-56e3c267292f" />

```sql
SELECT 
    ord_no,
    purch_amt,
    ord_date,
    customer_id,
    salesman_id
FROM orders
WHERE salesman_id IN (
    SELECT salesman_id
    FROM salesman
    WHERE city = 'London'
);
```

**Output:**

<img width="1284" height="518" alt="image" src="https://github.com/user-attachments/assets/dcb64fe8-5dfc-4880-bd8e-3ad2853271cd" />

**Question 10**
---
<img width="1186" height="559" alt="image" src="https://github.com/user-attachments/assets/d596ccc7-d573-4f44-82f2-a2dd58b74e2a" />

```sql
SELECT name
FROM customer
WHERE phone IN (
    SELECT distinct phone
    FROM customer
    group by phone
    HAVING COUNT(*) = 1
   
);
```

**Output:**

<img width="795" height="534" alt="image" src="https://github.com/user-attachments/assets/842e4a4d-c99c-4265-8941-ef5755bb9044" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.

