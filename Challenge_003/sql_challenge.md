### 💼 **Company:** Twitter   |   🏷️ **Level:** Medium
---
# 100 Days SQL Challenge 3: X-Node Classifier

## Problem Statement

You are given a table **BST** containing two columns: **N** and **P**, where **N** represents the value of a node in a Binary Search Tree, and **P** is the parent of **N**.

Your task is to write a SQL query to classify each node in the Binary Tree and determine its node type. The output should be ordered by the value of the node.

## Table Structure

| Column | Type    | Description |
|--------|---------|-------------|
| N      | Integer | Node value in the Binary Tree |
| P      | Integer | Parent node value (NULL for root) |

## Requirements

Write a query to find the node type of each node in the Binary Tree. Output one of the following classifications for each node:

- **Root**: If the node is the root node (has no parent)
- **Leaf**: If the node is a leaf node (has a parent but no children)
- **Inner**: If the node is an inner node (has both parent and children)

The result should be ordered by the node value in ascending order.

## Sample Input

### DDL (Data Definition Language)
```sql
CREATE TABLE BST (
    N INTEGER,
    P INTEGER
);
```

### DML (Data Manipulation Language)
```sql
INSERT INTO BST (N, P) VALUES
(1, 2),
(3, 2),
(6, 8),
(9, 8),
(2, 5),
(8, 5),
(5, NULL);
```

**Data Visualization:**

<img src="./asset/Capture_Input.png" alt="BST!" width="600"/>

## Expected Output

| N | Node_Type |
|---|-----------|
| 1 | Leaf      |
| 2 | Inner     |
| 3 | Leaf      |
| 5 | Root      |
| 6 | Leaf      |
| 8 | Inner     |
| 9 | Leaf      |

## Solution Approach

1. **Root Node**: Identify nodes where P IS NULL
2. **Leaf Node**: Find nodes that have a parent but are not parents themselves
3. **Inner Node**: Locate nodes that have both a parent and children
4. Use CASE statement for classification
5. Order results by node value

---

**💡 Tip:** Consider using subqueries or JOINs to check parent-child relationships efficiently!

## Solutions

For the solutions to these problems, please refer to the [X-Node Classifier - Solutions](sql_challenge_solutions.md) file.