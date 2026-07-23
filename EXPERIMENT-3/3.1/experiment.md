# Experiment 3.2

**Name:** ADITYA  
**UID:** 25BCS80034

---

## Aim

To retrieve the cities that have exactly **one employee** using the `GROUP BY` and `HAVING` clauses.

---

## Question

Write an SQL query to display the employee city along with the number of employees in that city, considering only those cities where the employee count is exactly **1**.

---

## SQL Query

```sql
SELECT emp_city, COUNT(*) AS cnt
FROM Employees
GROUP BY emp_city
HAVING COUNT(*) = 1;
```

---

## Output

| emp_city | cnt |
|----------|-----|
| Kolkata  | 1   |

---

## Explanation

- `GROUP BY emp_city` groups all employees based on their city.
- `COUNT(*)` counts the number of employees in each city.
- `HAVING COUNT(*) = 1` filters the grouped results and returns only those cities having exactly one employee.

---

## Result

The query successfully displays the city having exactly one employee along with its employee count.