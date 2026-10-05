# DBMS Lab — Assignment 3

## Database: `university1`

This assignment contains SQL queries and their outputs based on the `university1` database.

---

## 1. Get the empid, name of senior most professors.

### Query

```sql
SELECT empId, name
FROM professor
WHERE startYear = (SELECT MIN(startYear) FROM professor);
```

### Output

| empId | name                 |
| ----- | -------------------- |
| CS006 | M. Sripati Mukherjee |

---

## 2. Get the rollno, name of the students whose gender is same as their advisor.

### Query

```sql
SELECT s.rollNo, s.name
FROM student s, professor p
WHERE s.advisor = p.empId
AND s.sex = p.sex;
```

### Output

| rollNo | name              |
| -----: | ----------------- |
|      1 | Parag Roy         |
|      2 | Riturna Kashyap   |
|      4 | Raman             |
|      5 | Surja Sanyal      |
|      6 | Susahant Satyam   |
|      7 | Kamalika Samanta  |
|      7 | Kamalika Samanta  |
|      9 | Sirajul Islam     |
|     10 | Manisha Chaudhury |

---

## 3. Get the courseid, coursename, sem taught by advisor of C.S.E dept.

### Query

```sql
SELECT t.courseId, c.name, t.sem
FROM teaching t, course c
WHERE t.courseId = c.courseId
AND t.empId = 'CS006';
```

### Output

No records found.

> Note: `CS006` is the C.S.E department HOD/advisor in the given dataset, but no teaching record is available for `CS006`.

---

## 4. Get the courseid, coursename, sem taught by H.O.D of each dept.

### Query

```sql
SELECT t.courseId, c.name, t.sem
FROM teaching t, course c, department d
WHERE t.courseId = c.courseId
AND t.empId = d.hod;
```

### Output

No records found.

> Note: The HODs `CS006` and `EC004` do not have teaching records in the given dataset.

---

## 5. Get the post graduate male student and course credit point from C.S.E dept.

### Query

```sql
SELECT s.name, e.courseId, c.credits
FROM student s, enrollment e, course c
WHERE s.rollNo = e.rollNo
AND e.courseId = c.courseId
AND s.deptNo = 1
AND s.degree = 'M.E'
AND s.sex = 'Male';
```

### Output

| name         | courseId | credits |
| ------------ | -------- | ------: |
| Surja Sanyal | PCS001   |       4 |

---

## 6. Get the courseid, coursename, department name which has at least one female student.

### Query

```sql
SELECT DISTINCT c.courseId, c.name, d.name AS department
FROM course c, enrollment e, student s, department d
WHERE c.courseId = e.courseId
AND e.rollNo = s.rollNo
AND c.deptNo = d.deptId
AND s.sex = 'Female';
```

### Output

| courseId | courseName | department |
| -------- | ---------- | ---------- |
| UCS001   | UG CSE     | C.S.E      |
| PCS001   | PG CSE     | C.S.E      |
| UEC001   | UG ECE     | E.C.E      |
| PEC001   | PG ECE     | E.C.E      |

---

## 7. Get the courseid, coursename, department name which is not a 6 point course.

### Query

```sql
SELECT c.courseId, c.name, d.name AS department
FROM course c, department d
WHERE c.deptNo = d.deptId
AND c.credits <> 6;
```

### Output

| courseId | courseName | department |
| -------- | ---------- | ---------- |
| UCS001   | UG CSE     | C.S.E      |
| PCS001   | PG CSE     | C.S.E      |
| UEC001   | UG ECE     | E.C.E      |
| PEC001   | PG ECE     | E.C.E      |

> Note: In the given dataset, no course has 6 credits.

---

## 8. Get the courseid, coursename which has at least one A++ grade student.

### Query

```sql
SELECT DISTINCT c.courseId, c.name
FROM course c, enrollment e
WHERE c.courseId = e.courseId
AND e.grade = 'A++';
```

### Output

| courseId | courseName |
| -------- | ---------- |
| PCS001   | PG CSE     |

---

## 9. Get the rollno, name of the female student taught by the advisor of CSE dept.

### Query

```sql
SELECT s.rollNo, s.name
FROM student s
WHERE s.advisor = 'CS006'
AND s.sex = 'Female';
```

### Output

No records found.

> Note: No student has `CS006` as advisor in the given dataset.

---

## 10. Get the course id, coursename which have any final year student.

### Query

```sql
SELECT DISTINCT c.courseId, c.name
FROM course c, enrollment e
WHERE c.courseId = e.courseId
AND e.year = 4;
```

### Output

| courseId | courseName |
| -------- | ---------- |
| UEC001   | UG ECE     |

---

# Database Reference

| Code         | Meaning              |
| ------------ | -------------------- |
| `deptNo = 1` | C.S.E                |
| `deptNo = 2` | E.C.E                |
| `CS006`      | M. Sripati Mukherjee |
| `EC004`      | M. Bivas Paramanik   |
| `UCS001`     | UG CSE               |
| `PCS001`     | PG CSE               |
| `UEC001`     | UG ECE               |
| `PEC001`     | PG ECE               |

**Database:** MySQL
**Assignment:** 3
**Topic:** SQL Queries
