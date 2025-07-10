# 🌳 X-Node Classifier - Solution

## 💡 Solution Overview

This solution uses a **CASE statement** with **subqueries** to classify each node in the Binary Search Tree based on parent-child relationships.

### 🔍 Logic Breakdown

1. **Root Node**: `p IS NULL` - Node has no parent
2. **Leaf Node**: Node has a parent but doesn't appear as a parent in the dataset
3. **Inner Node**: Node has a parent and also serves as a parent to other nodes

---

## 🔧 SQL Server Solution

```sql
-- SQL Server Implementation
SELECT
    N,
    CASE 
        WHEN P IS NULL THEN 'Root'
        WHEN N NOT IN (
            SELECT 
                DISTINCT P 
            FROM BST 
            WHERE P IS NOT NULL
        ) THEN 'Leaf'
        ELSE 'Inner'
    END AS NodeType
FROM BST
ORDER BY N;
```

### 📊 SQL Server Execution Plan Notes:
- Uses `NOT IN` with `IS NOT NULL` condition to handle NULL values safely
- Subquery filters out NULL values to prevent unexpected results
- Index on columns N and P would optimize performance

---

## 🐘 PostgreSQL Solution

```sql
-- PostgreSQL Implementation
SELECT
    N,
    CASE 
        WHEN P IS NULL THEN 'Root'
        WHEN N NOT IN (
            SELECT 
                DISTINCT P 
            FROM BST 
            WHERE P IS NOT NULL
        ) THEN 'Leaf'
        ELSE 'Inner'
    END AS NodeType
FROM BST
ORDER BY N;
```

### 🔧 PostgreSQL Optimization Tips:
- PostgreSQL handles NULL values in `NOT IN` similarly to SQL Server
- Consider using `NOT EXISTS` for better performance with large datasets
- `EXPLAIN ANALYZE` can help identify optimization opportunities

---

## 🚀 Alternative High-Performance Solution

For better performance with large datasets, consider using `NOT EXISTS`:

```sql
-- Optimized version using NOT EXISTS (Works in both SQL Server & PostgreSQL)
SELECT
    N,
    CASE 
        WHEN P IS NULL THEN 'Root'
        WHEN NOT EXISTS (
            SELECT 1 
            FROM BST b2 
            WHERE b2.P = BST.N
        ) THEN 'Leaf'
        ELSE 'Inner'
    END AS NodeType
FROM BST
ORDER BY N;
```

---

## 📈 Performance Comparison

| Approach | SQL Server | PostgreSQL | Large Dataset |
|----------|------------|------------|---------------|
| `NOT IN` | ✅ Good | ✅ Good | ⚠️ Moderate |
| `NOT EXISTS` | ✅ Good | ✅ Good | ✅ Excellent |
| `LEFT JOIN` | ✅ Good | ✅ Good | ✅ Excellent |

---

## 🎯 Key Takeaways

- **NULL Handling**: Always filter out NULLs when using `NOT IN`
- **Performance**: `NOT EXISTS` often performs better than `NOT IN` for large datasets
- **Readability**: The CASE statement approach is intuitive and easy to understand
- **Portability**: Solution works across different SQL databases with minimal changes

---

## 🧪 Test Results

```
N | NodeType
--|----------
1 | Leaf
2 | Inner
3 | Leaf
5 | Root
6 | Leaf
8 | Inner
9 | Leaf
```

✅ **Status**: All test cases passed successfully!