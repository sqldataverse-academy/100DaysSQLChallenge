# 100 Days SQL Challenge 2 - Min-Max Name Game: Solution

## Problem Recap
Find employees with the shortest and longest first names, along with their character lengths. For ties, select the alphabetically first name.

---

## Solution Approach

The key to solving this problem is:
1. Calculate the length of each first name
2. Find the minimum and maximum lengths
3. Select names with those lengths, ordered alphabetically
4. Handle ties by using alphabetical ordering

---

## SQL Server Solution

### Method 1: Using Window Functions
```sql
WITH name_lengths AS (
    SELECT 
        FIRST_NAME,
        LEN(FIRST_NAME) as name_length,
        ROW_NUMBER() OVER (ORDER BY LEN(FIRST_NAME), FIRST_NAME) as shortest_rank,
        ROW_NUMBER() OVER (ORDER BY LEN(FIRST_NAME) DESC, FIRST_NAME) as longest_rank
    FROM EMPLOYEE
)
SELECT FIRST_NAME, name_length
FROM name_lengths
WHERE shortest_rank = 1 OR longest_rank = 1
ORDER BY name_length;
```

### Method 2: Using RANK() Function
```sql
WITH ranked_names AS (
    SELECT 
        FIRST_NAME,
        LEN(FIRST_NAME) as name_length,
        RANK() OVER (ORDER BY LEN(FIRST_NAME), FIRST_NAME) as min_rank,
        RANK() OVER (ORDER BY LEN(FIRST_NAME) DESC, FIRST_NAME) as max_rank
    FROM EMPLOYEE
)
SELECT FIRST_NAME, name_length
FROM ranked_names
WHERE min_rank = 1 OR max_rank = 1
ORDER BY name_length;
```

---

## PostgreSQL Solution

### Method 1: Using Window Functions
```sql
WITH name_lengths AS (
    SELECT 
        FIRST_NAME,
        LENGTH(FIRST_NAME) as name_length,
        ROW_NUMBER() OVER (ORDER BY LENGTH(FIRST_NAME), FIRST_NAME) as shortest_rank,
        ROW_NUMBER() OVER (ORDER BY LENGTH(FIRST_NAME) DESC, FIRST_NAME) as longest_rank
    FROM EMPLOYEE
)
SELECT FIRST_NAME, name_length
FROM name_lengths
WHERE shortest_rank = 1 OR longest_rank = 1
ORDER BY name_length;
```

### Method 2: Using DISTINCT ON (PostgreSQL Specific)
```sql
(SELECT DISTINCT ON (LENGTH(FIRST_NAME)) 
    FIRST_NAME, LENGTH(FIRST_NAME) as name_length
FROM EMPLOYEE
ORDER BY LENGTH(FIRST_NAME), FIRST_NAME
LIMIT 1)

UNION ALL

(SELECT DISTINCT ON (LENGTH(FIRST_NAME)) 
    FIRST_NAME, LENGTH(FIRST_NAME) as name_length
FROM EMPLOYEE
ORDER BY LENGTH(FIRST_NAME) DESC, FIRST_NAME
LIMIT 1);
```

---

## Key Differences Between SQL Server and PostgreSQL

| Feature | SQL Server | PostgreSQL |
|---------|------------|------------|
| String Length Function | `LEN()` | `LENGTH()` |
| Limit Records | `TOP n` | `LIMIT n` |
| Unique Feature | None | `DISTINCT ON` |

---

## Expected Output
```
AL 2
CHRISTOPHER 11
```

---

## Explanation

1. **AL** has 2 characters - shortest name
2. **CHRISTOPHER** has 11 characters - longest name
3. Both solutions handle alphabetical ordering for tie-breaking
4. The window functions approach is more efficient for larger datasets
5. PostgreSQL's `DISTINCT ON` provides a cleaner solution for this specific problem

---

## Performance Considerations

- **Method 1** (Window Functions): More efficient, single table scan
- **Method 2** (RANK/DISTINCT ON): Best for handling complex tie scenarios

For large datasets, prefer the window functions approach for better performance.