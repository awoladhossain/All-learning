# Unlock powerful ways to filter, organize, and group your query results

## SQL - WHERE Clause

**Purpose: Filters rows based on a condition.**

```bash
SELECT * FROM Students
WHERE age > 18;
```

-👉 Returns only students older than 18.

## ORDER BY Clause

**Purpose: Sorts query results in ascending (ASC) or descending (DESC) order.**

```bash
SELECT name, age FROM Students
ORDER BY age DESC;
```

- 👉 Shows students sorted by age, oldest first.

## GROUP BY Clause

**Purpose: Groups rows that share the same values in specified columns. Often used with aggregate functions (COUNT, SUM, AVG).**

```bash
SELECT subject, COUNT(*) AS total_students
FROM Students
GROUP BY subject;
```

- 👉 Groups students by subject and counts them.

## HAVING Clause

**Purpose: Filters groups created by GROUP BY.**

```bash
SELECT subject, COUNT(*) AS total_students
FROM Students
GROUP BY subject
HAVING COUNT(*) > 5;
```

- 👉 Shows only subjects with more than 5 students.

## DISTINCT Clause

**Purpose: Removes duplicate values from the result set.**

```bash
SELECT DISTINCT subject FROM Students;
```

- 👉 Returns each subject only once.

## LIMIT / TOP Clause

**Purpose: Restricts the number of rows returned.**

```bash
SELECT * FROM Students LIMIT 3;
```

```bash
SELECT TOP 3 * FROM Students;
```

- 👉 Shows only the first 3 rows.

## JOIN Clauses (INNER, LEFT, RIGHT, FULL, CROSS, SELF, NATURAL)

**Purpose: Combine rows from multiple tables based on related columns.**

```bash
SELECT s.name, c.course_name
FROM Students s
INNER JOIN StudentCourses sc ON s.student_id = sc.student_id
INNER JOIN Courses c ON sc.course_id = c.course_id;
```

## 🔎 Interview-Style Questions & Answers

- Q: Difference between WHERE and HAVING?

  > A: WHERE filters rows before grouping; HAVING filters groups after GROUP BY.

- Q: Why use GROUP BY with aggregate functions?

  > A: To summarize data (e.g., total sales per region).

- Q: What’s the difference between DISTINCT and GROUP BY?

  > A: DISTINCT removes duplicates directly; GROUP BY organizes rows into groups and can apply aggregates.

- Q: How does ORDER BY affect performance?
  > A: Sorting can be expensive; indexing helps optimize ORDER BY queries.
