# DBMS Lab — Assignment 4

## Database: `university1`

This assignment contains SQL queries and their outputs based on the `university1` database.

---

## 1. Find out the max and minimum credit for undergraduate and postgraduate students.

### Query

```sql
SELECT
MAX(CASE WHEN name LIKE 'UG%' THEN credits END) AS Max_UG_Credit,
MIN(CASE WHEN name LIKE 'UG%' THEN credits END) AS Min_UG_Credit,
MAX(CASE WHEN name LIKE 'PG%' THEN credits END) AS Max_PG_Credit,
MIN(CASE WHEN name LIKE 'PG%' THEN credits END) AS Min_PG_Credit
FROM course;
```

### Output

| Max_UG_Credit | Min_UG_Credit | Max_PG_Credit | Min_PG_Credit |
| ------------: | ------------: | ------------: | ------------: |
|             2 |             2 |             4 |             4 |

---

## 2. Find out the name of professors whose empid starts with alphabet ‘C’ and who teaches in undergraduate courses.

### Query

```sql
SELECT DISTINCT p.name
FROM professor p, teaching t
WHERE p.empId = t.empId
AND p.empId LIKE 'C%'
AND t.courseId IN ('UCS001', 'UEC001');
```

### Output

| name                |
| ------------------- |
| M. Sanjoy Pratihar  |
| Ms. Kasturi Dikpati |
| M. Biswantu Pal     |

---

## 3. Find out the maximum tenure of any courses.

### Query

```sql
SELECT MAX(sem) AS Maximum_Tenure
FROM teaching;
```

### Output

| Maximum_Tenure |
| -------------: |
|              6 |

> Note: Here `sem` is used as the course teaching tenure/semester based on the available dataset.

---

## 4. Display the degree and total number of students enrolled for that course.

### Query

```sql
SELECT s.degree, COUNT(DISTINCT s.rollNo) AS total_students
FROM student s
GROUP BY s.degree;
```

### Output

| degree | total_students |
| ------ | -------------: |
| B.E    |              5 |
| M.E    |              5 |

---

## 5. Display the degree and total number of male/female students enrolled for each course.

### Query

```sql
SELECT degree, sex, COUNT(DISTINCT rollNo) AS total_students
FROM student
GROUP BY degree, sex;
```

### Output

| degree | sex    | total_students |
| ------ | ------ | -------------: |
| B.E    | Male   |              3 |
| B.E    | Female |              2 |
| M.E    | Male   |              3 |
| M.E    | Female |              2 |

---

## 6. Find out the name of the students who haven’t enrolled for postgraduate courses. (Using EXCEPT clause)

### Query

```sql
SELECT name
FROM student
WHERE degree = 'B.E'

EXCEPT

SELECT s.name
FROM student s, enrollment e
WHERE s.rollNo = e.rollNo
AND e.courseId IN ('PCS001', 'PEC001');
```

### Output

| name            |
| --------------- |
| Parag Roy       |
| Riturna Kashyap |
| Neha            |
| Raman           |
| Aparajita       |

> Note: MySQL does not support the `EXCEPT` operator directly. The above query follows the assignment requirement conceptually. For MySQL, `NOT EXISTS` can be used instead.

---

## 7. Find out the name of the professors who teaches both in undergraduate course as well as in the postgraduate course.

### Query

```sql
SELECT DISTINCT p.name
FROM professor p, teaching t1, teaching t2
WHERE p.empId = t1.empId
AND p.empId = t2.empId
AND t1.courseId IN ('UCS001', 'UEC001')
AND t2.courseId IN ('PCS001', 'PEC001');
```

### Output

| name            |
| --------------- |
| M. Biswantu Pal |

---

## 8. Find out the name of the professors who teaches either in undergraduate course or in the postgraduate course.

### Query

```sql
SELECT DISTINCT p.name
FROM professor p, teaching t
WHERE p.empId = t.empId
AND t.courseId IN ('UCS001', 'UEC001', 'PCS001', 'PEC001');
```

### Output

| name                     |
| ------------------------ |
| Dr. Biplab Sarkar        |
| Dr. Supriya Bhattacharya |
| M. Sanjoy Pratihar       |
| Ms. Kasturi Dikpati      |
| M. Biswantu Pal          |
| Dr. B. C. Sarkar         |
| Ms. Smita Hazra          |
| M. Somnath Pal           |

---

## 9. Get the employee id, name of professors who advice at least one female student.

### Query

```sql
SELECT DISTINCT p.empId, p.name
FROM professor p, student s
WHERE p.empId = s.advisor
AND s.sex = 'Female';
```

### Output

| empId | name               |
| ----- | ------------------ |
| CS005 | M. Biswantu Pal    |
| EC004 | M. Bivas Paramanik |

---

## 10. List the names of the professors who have joined after 2000, in alphabetic order.

### Query

```sql
SELECT name
FROM professor
WHERE startYear > 2000
ORDER BY name ASC;
```

### Output

| name                |
| ------------------- |
| M. Biswantu Pal     |
| M. Sanjoy Pratihar  |
| M. Somnath Pal      |
| Ms. Kasturi Dikpati |
| Ms. Smita Hazra     |

---

# Database Reference

| Code         | Meaning |
| ------------ | ------- |
| `deptNo = 1` | C.S.E   |
| `deptNo = 2` | E.C.E   |
| `UCS001`     | UG CSE  |
| `PCS001`     | PG CSE  |
| `UEC001`     | UG ECE  |
| `PEC001`     | PG ECE  |

**Database:** MySQL
**Assignment:** 4
**Topic:** SQL Queries
