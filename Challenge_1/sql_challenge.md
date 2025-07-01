### 💼 **Company:** TCS   |   🏷️ **Level:** Easy

---

# 100 Days SQL Challenge 1: Leap Year Detection

## Problem Statement

You are given a table named `years` with a single column `year` containing integer values representing different years.

**Task:** Write an SQL query to determine whether each year in the table is a leap year or not.

**Expected Output:** Return a result set with two columns:

- `year`: The original year value
- `is_leap_year`: A boolean or string indicator showing whether the year is a leap year


## Table Structure

| Column Name | Data Type | Description |
| ----------- | --------- | ----------- |
| year        | INTEGER   | Year value  |

## DDL Statement

```sql
CREATE TABLE years (
    year INTEGER NOT NULL
);
```

## DML Insert Statement

```sql
INSERT INTO years (year) VALUES
(2020),
(2021),
(2022),
(2023),
(2024),
(1900),
(2000),
(2100),
(1996),
(1997);
```

## Expected Output

```
| year | is_leap_year |
|------|--------------|
| 2020 | true         |
| 2021 | false        |
| 2022 | false        |
| 2023 | false        |
| 2024 | true         |
| 1900 | false        |
| 2000 | true         |
| 2100 | false        |
| 1996 | true         |
| 1997 | false        |
```

**Note:** The expected output shows various test cases including:

- Regular leap years (2020, 2024, 1996)
- Non-leap years (2021, 2022, 2023, 1997)
- Century years that are NOT leap years (1900, 2100)
- Century years that ARE leap years (2000)

## Solutions

For the solutions to these problems, please refer to the [Leap Year Detection - Solutions](sql_challenge_solutions.md) file.