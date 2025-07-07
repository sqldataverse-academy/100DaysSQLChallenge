### 💼 **Company:** Infosys   |   🏷️ **Level:** Medium

---

# 100 Days SQL Challenge 2 - Min-Max Name Game

## Problem Statement

You're working as a data analyst and need to identify employees with the most compact and most elaborate first names from the company database. Your task is to find the employees whose first names have the minimum and maximum character lengths, along with displaying those exact lengths.

If multiple employees share the same shortest or longest name length, select the one whose name appears first alphabetically.

## Table Structure

**EMPLOYEE Table:**

| Field | Type | Description |
|-------|------|-------------|
| ID | NUMBER | Employee ID |
| FIRST_NAME | VARCHAR2(50) | Employee's first name |
| LAST_NAME | VARCHAR2(50) | Employee's last name |
| DEPARTMENT | VARCHAR2(30) | Department |
| SALARY | NUMBER | Salary |

## Requirements

- Find the employee with the **shortest** first name
- Find the employee with the **longest** first name
- Display both the name and its character count
- For ties, choose the alphabetically first name
- Output format: `FIRST_NAME LENGTH`

## Sample Input

### DDL
```sql
CREATE TABLE EMPLOYEE (
    ID INT,
    FIRST_NAME VARCHAR(50),
    LAST_NAME VARCHAR(50),
    DEPARTMENT VARCHAR(30),
    SALARY INT
);
```

### DML
```sql
INSERT INTO EMPLOYEE VALUES (1, 'JOHN', 'SMITH', 'IT', 50000);
INSERT INTO EMPLOYEE VALUES (2, 'AL', 'JOHNSON', 'HR', 45000);
INSERT INTO EMPLOYEE VALUES (3, 'ALEXANDER', 'BROWN', 'FINANCE', 55000);
INSERT INTO EMPLOYEE VALUES (4, 'MIKE', 'DAVIS', 'IT', 48000);
INSERT INTO EMPLOYEE VALUES (5, 'ANN', 'WILSON', 'HR', 47000);
INSERT INTO EMPLOYEE VALUES (6, 'CHRISTOPHER', 'TAYLOR', 'FINANCE', 60000);
INSERT INTO EMPLOYEE VALUES (7, 'ZAKHARIAH', 'WHITE', 'HR', 65000);
INSERT INTO EMPLOYEE VALUES (8, 'AP', 'TAYLOR', 'FINANCE', 80000);
INSERT INTO EMPLOYEE VALUES (9, 'ALEXANDER', 'WILSON', 'IT', 45000);
```

## Expected Output

```
AL 2
CHRISTOPHER 11
```

**Explanation:**
- **AL** has the shortest first name (2 characters)
- **CHRISTOPHER** has the longest first name (11 characters)

## Solutions

For the solutions to these problems, please refer to the [Min-Max Name Game - Solutions](sql_challenge_solutions.md) file.