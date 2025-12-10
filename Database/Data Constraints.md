# Constraints act as rules or conditions imposed on the data, dictating what values are permissible and what actions can be taken. They play a crucial role in maintaining the quality and coherence of the database by preventing errors

## NOT NULL

**Ensures a column cannot store NULL values.**

```bash
CREATE TABLE Students (
  student_id INT NOT NULL,
  name VARCHAR(50) NOT NULL
);
```

- 👉 Both student_id and name must always have values.

## UNIQUE

**Ensures all values in a column are different.**

```bash
CREATE TABLE Courses (
  course_id INT UNIQUE,
  course_name VARCHAR(50)
);
```

- 👉 No two courses can share the same course_id.

## PRIMARY KEY

**Combines NOT NULL + UNIQUE.Identifies each row uniquely in a table.**

```bash
CREATE TABLE Students (
  student_id INT PRIMARY KEY,
  name VARCHAR(50)
);
```

- 👉 Each student has a unique student_id.

## FOREIGN KEY

**Links one table to another.Ensures referential integrity.**

```bash
CREATE TABLE StudentCourses (
  student_id INT,
  course_id INT,
  FOREIGN KEY (student_id) REFERENCES Students(student_id),
  FOREIGN KEY (course_id) REFERENCES Courses(course_id)
);
```

- 👉 Guarantees that student_id and course_id exist in their parent tables.

## CHECK

**Ensures values meet a condition.**

```bash
CREATE TABLE Employees (
  emp_id INT PRIMARY KEY,
  age INT CHECK (age >= 18)
);
```

- 👉 Only employees aged 18 or older can be inserted.

## DEFAULT

**Provides a default value if none is specified.**

```bash
CREATE TABLE Orders (
  order_id INT PRIMARY KEY,
  status VARCHAR(20) DEFAULT 'Pending'
);
```

- 👉 If no status is given, it defaults to 'Pending'.

## INDEX (sometimes considered a constraint)

**Speeds up queries by indexing columns.**

```bash
CREATE INDEX idx_student_name
ON Students(name);
```

- 👉 Improves search performance on name.

## 🔎 Interview-Style Questions & Answers

- Q: Difference between PRIMARY KEY and UNIQUE?

  > A: Both enforce uniqueness, but PRIMARY KEY also disallows NULLs and is used to identify rows.

- Q: Why use FOREIGN KEY?

  > A: To maintain referential integrity — prevents inserting values that don’t exist in the parent table.

- Q: How does CHECK differ from WHERE?

  > A: CHECK enforces rules at the schema level (during insert/update), WHERE filters data at query time.

- Q: Can a table have multiple UNIQUE constraints?
  > A: Yes, but only one PRIMARY KEY.
