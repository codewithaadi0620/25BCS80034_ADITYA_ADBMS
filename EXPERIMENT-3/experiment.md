# Experiment 3.2

**Name:** ADITYA

**UID:** 25BCS80034

## Aim

To create an **Employees** table, insert employee records, and perform various SQL aggregate function queries using **COUNT(), SUM(), MAX(), MIN(), DISTINCT, GROUP BY, HAVING,** and **ORDER BY**.

---

## Question

### Step 1

Create the **Employees** table with the following fields:

* `emp_id`
* `emp_name`
* `emp_salary`
* `emp_city`

### Step 2

Insert the given employee records into the table.

### Step 3

Write SQL queries to perform the following operations:

1. Find the total number of employees in each city.
2. Find the total number of employees in each city and sort the result in ascending order.
3. Find the number of employees in each city whose salary is greater than or equal to **90000**.
4. Find the maximum employee salary in each city.
5. Find the minimum employee salary in each city.
6. Find all cities whose minimum employee salary is greater than or equal to **85000**.
7. Display the distinct cities.

---

## Employee Records

| Emp ID | Employee Name |    Salary | City      |
| -----: | ------------- | --------: | --------- |
|    101 | Amit Sharma   |  85000.00 | Mumbai    |
|    102 | Priya Patel   |  95000.00 | Mumbai    |
|    103 | Rahul Verma   |  60000.00 | Delhi     |
|    104 | Ananya Iyer   | 110000.00 | Bangalore |
|    105 | Vikram Singh  |  55000.00 | Delhi     |
|    106 | Sneha Reddy   | 105000.00 | Bangalore |
|    107 | Rohan Das     |  72000.00 | Kolkata   |

---

# SQL Queries Used

## Create Employees Table

```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(100) NOT NULL,
    emp_salary DECIMAL(10,2) NOT NULL,
    emp_city VARCHAR(100) NOT NULL
);
```

## Insert Records

```sql
INSERT INTO employees (emp_id, emp_name, emp_salary, emp_city) VALUES
(101, 'Amit Sharma', 85000.00, 'Mumbai'),
(102, 'Priya Patel', 95000.00, 'Mumbai'),
(103, 'Rahul Verma', 60000.00, 'Delhi'),
(104, 'Ananya Iyer', 110000.00, 'Bangalore'),
(105, 'Vikram Singh', 55000.00, 'Delhi'),
(106, 'Sneha Reddy', 105000.00, 'Bangalore'),
(107, 'Rohan Das', 72000.00, 'Kolkata');
```

---

## 1. Find the Total Number of Employees in Each City

```sql
SELECT emp_city, COUNT(*) AS cnt
FROM employees
GROUP BY emp_city;
```

---

## 2. Find the Total Number of Employees in Each City and Sort by Count (Ascending)

### Method 1

```sql
SELECT emp_city, COUNT(*) AS cnt
FROM employees
GROUP BY emp_city
ORDER BY cnt ASC;
```

### Method 2

```sql
SELECT emp_city, COUNT(emp_id) AS cnt
FROM employees
GROUP BY emp_city
ORDER BY cnt;
```

---

## 3. Find the Number of Employees in Each City Whose Salary is Greater Than or Equal to 90000

### Method 1

```sql
SELECT emp_city,
       SUM(CASE WHEN emp_salary >= 90000 THEN 1 ELSE 0 END) AS cnt
FROM employees
GROUP BY emp_city
ORDER BY cnt DESC, emp_city DESC;
```

### Method 2

```sql
SELECT emp_city,
       COUNT(CASE WHEN emp_salary >= 90000 THEN 1 END) AS cnt
FROM employees
GROUP BY emp_city;
```

---

## 4. Find the Maximum Employee Salary in Each City

```sql
SELECT emp_city,
       MAX(emp_salary) AS max_salary
FROM employees
GROUP BY emp_city;
```

---

## 5. Find the Minimum Employee Salary in Each City

```sql
SELECT emp_city,
       MIN(emp_salary) AS min_salary
FROM employees
GROUP BY emp_city;
```

---

## 6. Find All Cities Whose Minimum Salary is Greater Than or Equal to 85000

```sql
SELECT emp_city,
       MIN(emp_salary) AS min_salary
FROM employees
GROUP BY emp_city
HAVING MIN(emp_salary) >= 85000;
```

---

## 7. Find the Distinct Cities

```sql
SELECT DISTINCT emp_city
FROM employees;
```

---

# Output

### Total Number of Employees in Each City

```text
 Bangalore | 2
 Delhi     | 2
 Kolkata   | 1
 Mumbai    | 2
```

### Employee Count Sorted by Count

```text
 Kolkata   | 1
 Bangalore | 2
 Delhi     | 2
 Mumbai    | 2
```

### Employees with Salary >= 90000

```text
 Bangalore | 2
 Mumbai    | 1
 Delhi     | 0
 Kolkata   | 0
```

### Maximum Salary in Each City

```text
 Bangalore | 110000.00
 Delhi     | 60000.00
 Kolkata   | 72000.00
 Mumbai    | 95000.00
```

### Minimum Salary in Each City

```text
 Bangalore | 105000.00
 Delhi     | 55000.00
 Kolkata   | 72000.00
 Mumbai    | 85000.00
```

### Cities Having Minimum Salary >= 85000

```text
 Bangalore | 105000.00
 Mumbai    | 85000.00
```

### Distinct Cities

```text
Mumbai
Delhi
Bangalore
Kolkata
```

---

## Output Screenshot

![Experiment 2 Output](image.png)

---

## Image Explanation

The screenshot shows the successful creation of the **Employees** table, insertion of employee records, and execution of aggregate function queries using **COUNT(), SUM(), MAX(), MIN(), DISTINCT, GROUP BY, HAVING,** and **ORDER BY**. The output verifies that each query returns the expected results.

---

## Result

The **Employees** table was created successfully, records were inserted, and all aggregate function queries were executed successfully. The results demonstrated the use of **GROUP BY**, **HAVING**, **ORDER BY**, **DISTINCT**, **COUNT()**, **SUM()**, **MAX()**, and **MIN()** in SQL.
