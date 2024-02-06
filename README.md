# MYSQL Operations

## SQL Lesson 1: SELECT queries 101

```sql
SELECT * 
FROM mytable;
```

## SQL Lesson 2: Queries with constraints (Pt. 1)

```sql
SELECT column, another_column, …
FROM mytable
WHERE condition
    AND/OR another_condition
    AND/OR …;
```
| Operator              | Condition                                          | SQL Example             |
| --------------------- | -------------------------------------------------- | ----------------------- |
| =, !=, < <=, >, >=    | Standard numerical operators                      | col_name != 4           |
| BETWEEN … AND …      | Number is within range of two values (inclusive)  | col_name BETWEEN 1.5 AND 10.5 |
| NOT BETWEEN … AND …  | Number is not within range of two values (inclusive) | col_name NOT BETWEEN 1 AND 10 |
| IN (…)                | Number exists in a list                           | col_name IN (2, 4, 6)   |
| NOT IN (…)            | Number does not exist in a list                   | col_name NOT IN (1, 3, 5) |




