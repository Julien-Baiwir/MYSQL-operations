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


## SQL Lesson 3: Queries with constraints (Pt. 2)

| Operator  | Condition                                      | Example                   |
| --------- | ---------------------------------------------- | ------------------------- |
| =         | Case sensitive exact string comparison         | col_name = "abc"          |
| != or <>  | Case sensitive exact string inequality comparison | col_name != "abcd"     |
| LIKE      | Case insensitive exact string comparison       | col_name LIKE "ABC"       |
| NOT LIKE  | Case insensitive exact string inequality comparison | col_name NOT LIKE "ABCD" |
| %         | Used anywhere in a string to match a sequence of zero or more characters (only with LIKE or NOT LIKE) | col_name LIKE "%AT%" |
| _         | Used anywhere in a string to match a single character (only with LIKE or NOT LIKE) | col_name LIKE "AN_"     |
| IN (…)    | String exists in a list                        | col_name IN ("A", "B", "C") |
| NOT IN (…)| String does not exist in a list                | col_name NOT IN ("D", "E", "F") |


## SQL Lesson 4: Filtering and sorting Query results

### Select query with unique results
```sql
SELECT DISTINCT column, another_column, …
FROM mytable
WHERE condition(s);

SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC;

SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

## SQL 5 Review: Simple SELECT Queries

```sql
SELECT query
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

## SQL Lesson 6: Multi-table queries with JOINs

Database normalization

Multi-table queries with JOINs

```sql
SELECT column, another_table_column, …
FROM mytable
INNER JOIN another_table 
    ON mytable.id = another_table.id
WHERE condition(s)
ORDER BY column, … ASC/DESC
LIMIT num_limit OFFSET num_offset;
 ```

 ## SQL Lesson 7: OUTER JOINs

```sql
SELECT column, another_column, …
FROM mytable
INNER/LEFT/RIGHT/FULL JOIN another_table 
    ON mytable.id = another_table.matching_id
WHERE condition(s)
ORDER BY column, … ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

## SQL Lesson 8: A short note on NULLs

```sql
SELECT column, another_column, …
FROM mytable
WHERE column IS/IS NOT NULL
AND/OR another_condition
AND/OR …;
```

## SQL Lesson 9: Queries with expressions

```sql
SELECT particle_speed / 2.0 AS half_particle_speed
FROM physics_data
WHERE ABS(particle_position) * 10.0 > 500;


SELECT col_expression AS expr_description, …
FROM mytable;


SELECT column AS better_column_name, …
FROM a_long_widgets_table_name AS mywidgets
INNER JOIN widget_sales
ON mywidgets.id = widget_sales.widget_id;
```

## SQL Lesson 9: Queries with expressions

```sql
SELECT particle_speed / 2.0 AS half_particle_speed
FROM physics_data
WHERE ABS(particle_position) * 10.0 > 500;
SELECT col_expression AS expr_description, …
FROM mytable;

SELECT column AS better_column_name, …
FROM a_long_widgets_table_name AS mywidgets
INNER JOIN widget_sales
ON mywidgets.id = widget_sales.widget_id;
```


## SQL Lesson 10: Queries with aggregates (Pt. 1)

```sql
SELECT AGG_FUNC(column_or_expression) AS aggregate_description, …
FROM mytable
WHERE constraint_expression;
```

#Common aggregate functions

| Function   | Description                                                                                                 |
| ---------- | ----------------------------------------------------------------------------------------------------------- |
| COUNT(*)   | A common function used to count the number of rows in the group if no column name is specified. Otherwise, count the number of rows in the group with non-NULL values in the specified column. |
| MIN(column)| Finds the smallest numerical value in the specified column for all rows in the group.                     |
| MAX(column)| Finds the largest numerical value in the specified column for all rows in the group.                      |
| AVG(column)| Finds the average numerical value in the specified column for all rows in the group.                       |
| SUM(column)| Finds the sum of all numerical values in the specified column for the rows in the group.                  |

#Grouped aggregate functions
SELECT AGG_FUNC(column_or_expression) AS aggregate_description, …
FROM mytable
WHERE constraint_expression
GROUP BY column;


## SQL Lesson 11: Queries with aggregates (Pt. 2)

```sql
SELECT group_by_column, AGG_FUNC(column_expression) AS aggregate_result_alias, …
FROM mytable
WHERE condition
GROUP BY column
HAVING group_condition;
```

## SQL Lesson 12: Order of execution of a Query

```sql
SELECT DISTINCT column, AGG_FUNC(column_or_expression), …
FROM mytable
JOIN another_table
  ON mytable.column = another_table.column
WHERE constraint_expression
GROUP BY column
HAVING constraint_expression
ORDER BY column ASC/DESC
LIMIT count OFFSET COUNT;
```
