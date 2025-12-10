# SQL Operators" refers to the fundamental symbols and keywords within the SQL that enable users to perform various operations. Operators let you build complex query condition

## Arithmetic Operators

**Used for mathematical calculations.**

```bash
SELECT Salary, Bonus, Salary + Bonus AS TotalIncome
FROM Employees;
```

## Comparison Operators

**Used to compare values.**

```bash
SELECT * FROM Students
WHERE age >= 18;
```

## Logical Operators

**Used to combine conditions.**

> AND → Both conditions must be true
> OR → At least one condition true
> NOT → Negates condition
> IN → Matches any value in a list
> BETWEEN → Within a range
> LIKE → Pattern matching (with % or \_)
> IS NULL → Checks for NULL values

```bash
SELECT * FROM Students
WHERE age BETWEEN 18 AND 25
AND subject IN ('Math', 'English');
```

## Bitwise Operators

**Operate on binary representations of numbers.**

```bash
SELECT 5 & 3 AS BitwiseAND;  -- Result: 1
```

## Compound Operators

**Shortcut operators that combine assignment with arithmetic/bitwise.**

```bash
UPDATE Employees
SET Salary += 5000
WHERE EmpID = 1;
```

## 🔎 Interview-Style Questions & Answers

- Q: Difference between WHERE age = NULL and WHERE age IS NULL?

  > A: = cannot be used with NULL. Use IS NULL to check for NULL values.

- Q: How does LIKE differ from =?

  > A: = checks exact match, LIKE allows pattern matching ('A%' = starts with A).

- Q: What’s the difference between BETWEEN and IN?

  > A: BETWEEN checks ranges, IN checks discrete values.

- Q: When would you use bitwise operators in SQL?
  > A: For flag-based columns (e.g., permissions stored as bits).
