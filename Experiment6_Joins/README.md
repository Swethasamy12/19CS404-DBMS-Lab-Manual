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

<img width="1252" height="448" alt="504172057-5adcee9f-d601-4ee9-8a0c-c53f5097b3fb" src="https://github.com/user-attachments/assets/12f24359-010f-451f-8b6e-e2000e008150" />

```
SELECT s.name
FROM salesman s
LEFT JOIN customer c ON s.salesman_id = c.salesman_id
WHERE c.city = 'New York';
```

**Output:**

<img width="460" height="342" alt="504172229-2b2acd68-ea78-4639-b2cf-154e128c28c3" src="https://github.com/user-attachments/assets/7a924f65-bad5-45e9-8355-80f6f0279f76" />

**Question 2**

<img width="1290" height="416" alt="504172420-ab7dd23e-3b92-4b05-9ec3-06c9a8fcc1ba" src="https://github.com/user-attachments/assets/460566e0-97b1-4dfe-a851-09c0ebede5d5" />

```
SELECT c.cust_name
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id;
```

**Output:**

<img width="710" height="770" alt="504172554-8c6bfdc6-6000-40cb-b2b7-72f2c8c52579" src="https://github.com/user-attachments/assets/09e8bca3-f787-4e03-9b97-6333bf8513b4" />

**Question 3**

<img width="1277" height="631" alt="504172654-fc672435-2843-4c37-9228-f3f6594fb78f" src="https://github.com/user-attachments/assets/68874eda-8c0d-496f-b833-293a5b466484" />

```
SELECT 
    c.cust_name ,
    c.city ,
    c.grade,
    s.name as  Salesman  ,
    s.city 
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;
```

**Output:**

<img width="1246" height="579" alt="504172808-19eb1741-7d7d-4c3e-b8d6-82e76bf6b8ed" src="https://github.com/user-attachments/assets/b2e2ca42-4a14-4e1e-b051-3bebd9d135ee" />

**Question 4**

<img width="1322" height="836" alt="504173047-e9b1508c-7c3a-40f8-98b8-4360db6e4e89" src="https://github.com/user-attachments/assets/4f13f1d4-f49c-4c69-b939-538157a1dabb" />

```
SELECT 
    c.cust_name, 
    c.city, 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt AS "Order Amount", 
    s.name, 
    s.commission
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
LEFT JOIN 
    salesman s ON c.salesman_id = s.salesman_id;
```

**Output:**

<img width="1339" height="766" alt="504173407-f7381fc5-8f94-4e9b-a26a-a68ae2deb523" src="https://github.com/user-attachments/assets/cb07548b-4c92-4f7f-9be0-7fb26afaf301" />

**Question 5**

<img width="1278" height="626" alt="504173501-c3a1bab0-c023-47ae-b658-7f23dad04619" src="https://github.com/user-attachments/assets/38ee1725-166c-4a84-beed-28dee202e009" />

```
SELECT 
    c.cust_name AS "Customer Name", 
    c.city, 
    s.name AS "Salesman", 
    s.city , 
    s.commission 
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    c.city != s.city
    AND s.commission > 0.12;
```

**Output:**

<img width="1251" height="452" alt="504173666-39bcfc9c-acfd-4c48-a1bc-13ac845f7190" src="https://github.com/user-attachments/assets/70e10677-251e-4a7e-8212-16d5014a8748" />

**Question 6**

<img width="1043" height="592" alt="504173753-7068e639-0c92-4bb9-bb59-504eb55f8eed" src="https://github.com/user-attachments/assets/87fd87a3-a5b9-41fc-9de3-b7e0c631662e" />

```
SELECT
    s.name AS Salesman,
    c.cust_name,
    s.city
FROM
    salesman s
JOIN
    customer c ON s.city = c.city;
```

**Output:**

<img width="1142" height="646" alt="504173872-6ea3e0e4-7855-40a5-ad72-4f0880c0de27" src="https://github.com/user-attachments/assets/9a0bb6e2-1d82-4af4-9c0a-746065fa0d5e" />

**Question 7**

<img width="1290" height="504" alt="504173979-5996936d-5db1-48b0-8ffd-0f9b36df204b" src="https://github.com/user-attachments/assets/ea6671c9-5ed3-4b43-8b02-7aab7087b36b" />

```
SELECT 
    p.first_name AS patient_name,
    t.*
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id;
```

**Output:**

<img width="1308" height="355" alt="504174147-5ca6856d-b274-42a9-8ca5-c14879ee75d5" src="https://github.com/user-attachments/assets/a99dfdf7-e75a-4193-a333-cc38c2c5f885" />

**Question 8**

<img width="1298" height="756" alt="504174257-d90f7e65-6508-42ae-8574-a6e1cfd1a89f" src="https://github.com/user-attachments/assets/8cefc481-a5fe-4602-9d0c-ebd07415ba21" />

```
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount"
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
ORDER BY 
    o.ord_date ASC;
```

**Output:**

<img width="1294" height="617" alt="504174492-72dceebf-f294-4a3f-b7f6-323831345c87" src="https://github.com/user-attachments/assets/3f2539fb-9627-4db0-9005-c03925a1e82b" />

**Question 9**

<img width="1196" height="583" alt="504174654-c6af2d40-86e2-47c0-92dd-6d293ce23a79" src="https://github.com/user-attachments/assets/e7eb56d4-7405-4604-b743-b28441b0d094" />

```
SELECT 
    p.*,
    d.first_name AS doctor_name
FROM 
    patients p
INNER JOIN 
    doctors d ON p.doctor_id = d.doctor_id;
```

**Output:**

<img width="1885" height="384" alt="504174762-691dd8db-237d-479a-969a-d7a59bc767bb" src="https://github.com/user-attachments/assets/cf382980-edd8-4577-a0a0-1df887503af8" />

**Question 10**

<img width="1247" height="523" alt="504174849-3b282fd0-6f3a-4074-b00e-c84d4be0f679" src="https://github.com/user-attachments/assets/4b4512c5-ccf7-4697-a3f4-1b36b87d8d8e" />

```
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    appointments a ON p.patient_id = a.patient_id
WHERE 
    a.appointment_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="1869" height="338" alt="504174927-e8db03cc-7339-48e6-923e-5e4d97bd08b1" src="https://github.com/user-attachments/assets/a13cce95-3e63-48cd-9fdd-2ee980f161a5" />

## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
