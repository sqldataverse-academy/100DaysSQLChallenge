# 100 Days SQL Challenge 1: Leap Year Detection - Solutions

## Solution 1: Using CASE Statement with Modulo Operations

```sql
SELECT 
    year,
    CASE 
        WHEN year % 400 = 0 THEN 'true'
        WHEN year % 100 = 0 THEN 'false'
        WHEN year % 4 = 0 THEN 'true'
        ELSE 'false'
    END AS is_leap_year
FROM years
ORDER BY year;
```

**Explanation:**
- First check if divisible by 400 (leap year)
- Then check if divisible by 100 (not leap year)
- Then check if divisible by 4 (leap year)
- Otherwise, not a leap year

## Solution 2: Using Boolean Logic (PostgreSQL/MySQL)

```sql
SELECT 
    year,
    (year % 4 = 0 AND year % 100 != 0) OR (year % 400 = 0) AS is_leap_year
FROM years
ORDER BY year;
```

**Explanation:**
- A year is leap if: (divisible by 4 AND not divisible by 100) OR (divisible by 400)
- This directly implements the leap year logic in boolean form

## Performance Comparison

| Solution | Readability | Performance | Database Compatibility |
|----------|-------------|-------------|----------------------|
| Solution 1 | High | Good | Excellent |
| Solution 2 | Medium | Best | Good |

## Recommended Solution

**Solution 1** is recommended for most use cases because:
- Easy to read and understand
- Follows the leap year rules step by step
- Works across all SQL databases
- Good performance for typical datasets

## Test Results

All solutions should produce the following output:

```
| year | is_leap_year |
|------|--------------|
| 1900 | false        |
| 1996 | true         |
| 1997 | false        |
| 2000 | true         |
| 2020 | true         |
| 2021 | false        |
| 2022 | false        |
| 2023 | false        |
| 2024 | true         |
| 2100 | false        |
```