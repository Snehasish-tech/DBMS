# DBMS Lab — Assignment 2

## Database: `university1`

This assignment contains SQL queries and their outputs based on the `university1` database.

---

## 16. Display the roll no and name of the students from C.S.E department.

### Query

```sql
SELECT rollNo, name
FROM student
WHERE deptNo = 1;
```

### Output

| rollNo | name             |
| -----: | ---------------- |
|      1 | Parag Roy        |
|      2 | Riturna Kashyap  |
|      3 | Neha             |
|      5 | Surja Sanyal     |
|      7 | Kamalika Samanta |
|      7 | Kamalika Samanta |

---

## 17. Display the roll no, name and year of the male students from E.C.E department.

### Query

```sql
SELECT rollNo, name, year
FROM student
WHERE deptNo = 2
AND sex = 'Male';
```

### Output

| rollNo | name            | year |
| -----: | --------------- | ---: |
|      4 | Raman           |    4 |
|      6 | Susahant Satyam |    1 |
|      9 | Sirajul Islam   |    2 |

---

## 18. Display the rollno, name, degree of the students whose advisor is Mr. Biswanath Pal.

### Query

```sql
SELECT rollNo, name, degree
FROM student
WHERE advisor = 'CS005';
```

### Output

| rollNo | name             | degree |
| -----: | ---------------- | ------ |
|      1 | Parag Roy        | B.E    |
|      2 | Riturna Kashyap  | B.E    |
|      3 | Neha             | B.E    |
|      5 | Surja Sanyal     | M.E    |
|      7 | Kamalika Samanta | M.E    |
|      7 | Kamalika Samanta | M.E    |

> Note: In the given dataset, `CS005` is M. Biswantu Pal.

---

## 19. Display the rollno, name of the M.E female students whose advisor is Mr. Bivas Paramanik.

### Query

```sql
SELECT rollNo, name
FROM student
WHERE degree = 'M.E'
AND sex = 'Female'
AND advisor = 'EC004';
```

### Output

| rollNo | name              |
| -----: | ----------------- |
|     10 | Manisha Chaudhury |

---

## 20. Display the name and phone no of HOD of CSE department.

### Query

```sql
SELECT name, phone
FROM professor
WHERE empId = 'CS006';
```

### Output

| name                 | phone      |
| -------------------- | ---------- |
| M. Sripati Mukherjee | 9435675489 |

---

## 21. Display the name of female Professors of CSE department.

### Query

```sql
SELECT name
FROM professor
WHERE deptNo = 1
AND sex = 'Female';
```

### Output

| name                |
| ------------------- |
| Ms. Kasturi Dikpati |

---

## 22. Display the empid, name, start year of HOD of ECE department.

### Query

```sql
SELECT empId, name, startYear
FROM professor
WHERE empId = 'EC004';
```

### Output

| empId | name               | startYear |
| ----- | ------------------ | --------: |
| EC004 | M. Bivas Paramanik |      2002 |

---

## 23. Display rollno and name of 2nd year M.E male students from ECE department.

### Query

```sql
SELECT rollNo, name
FROM student
WHERE year = 2
AND degree = 'M.E'
AND sex = 'Male'
AND deptNo = 2;
```

### Output

| rollNo | name          |
| -----: | ------------- |
|      9 | Sirajul Islam |

---

## 24. Display the name, degree, courseid, sem of the student who has rollno 1.

### Query

```sql
SELECT s.name, s.degree, e.courseId, e.sem
FROM student s, enrollment e
WHERE s.rollNo = 1
AND e.rollNo = 1;
```

### Output

| name      | degree | courseId | sem |
| --------- | ------ | -------- | --: |
| Parag Roy | B.E    | UCS001   |   6 |

---

## 25. Display the rollno, name and Degree of post graduate students whose Grade is A++.

### Query

```sql
SELECT s.rollNo, s.name, s.degree
FROM student s, enrollment e
WHERE s.rollNo = e.rollNo
AND s.degree = 'M.E'
AND e.grade = 'A++';
```

### Output

| rollNo | name             | degree |
| -----: | ---------------- | ------ |
|      7 | Kamalika Samanta | M.E    |

---

## 26. Display the roll no, Name of students in the CSE department along with their advisor name and his empid.

### Query

```sql
SELECT s.rollNo, s.name, p.name, p.empId
FROM student s, professor p
WHERE s.advisor = p.empId
AND s.deptNo = 1;
```

### Output

| rollNo | Student Name     | Advisor Name    | empId |
| -----: | ---------------- | --------------- | ----- |
|      1 | Parag Roy        | M. Biswantu Pal | CS005 |
|      2 | Riturna Kashyap  | M. Biswantu Pal | CS005 |
|      3 | Neha             | M. Biswantu Pal | CS005 |
|      5 | Surja Sanyal     | M. Biswantu Pal | CS005 |
|      7 | Kamalika Samanta | M. Biswantu Pal | CS005 |
|      7 | Kamalika Samanta | M. Biswantu Pal | CS005 |

---

## 27. Display the name, employee ids, phone nos, in CSE department who have joined before 1995.

### Query

```sql
SELECT name, empId, phone
FROM professor
WHERE deptNo = 1
AND startYear < 1995;
```

### Output

| name                 | empId | phone      |
| -------------------- | ----- | ---------- |
| Dr. Biplab Sarkar    | CS001 | 9434122345 |
| M. Sripati Mukherjee | CS006 | 9435675489 |

---

## 28. Display the empid and Name of professors who teaches post graduate in ECE department.

### Query

```sql
SELECT p.empId, p.name
FROM professor p, teaching t
WHERE p.empId = t.empId
AND t.courseId = 'PEC001';
```

### Output

| empId | name           |
| ----- | -------------- |
| EC003 | M. Somnath Pal |

---

## 29. Display the name and roll no. of the students who read in second sem post graduate in ECE and grade greater than B++.

### Query

```sql
SELECT s.name, s.rollNo
FROM student s, enrollment e
WHERE s.rollNo = e.rollNo
AND s.deptNo = 2
AND s.degree = 'M.E'
AND e.sem = 2
AND e.grade = 'A+';
```

### Output

| name            | rollNo |
| --------------- | -----: |
| Susahant Satyam |      6 |

> Note: In the given dataset, the ECE M.E. student in 2nd semester has grade `A+`, which is higher than `B++`.

---

## 30. Display the names of the professors who teach in undergraduate 6th semester CSE courses.

### Query

```sql
SELECT p.name
FROM professor p, teaching t
WHERE p.empId = t.empId
AND t.courseId = 'UCS001'
AND t.sem = 6;
```

### Output

| name                |
| ------------------- |
| M. Sanjoy Pratihar  |
| Ms. Kasturi Dikpati |
| M. Biswantu Pal     |

---

# Database Reference

| Code         | Meaning              |
| ------------ | -------------------- |
| `deptNo = 1` | C.S.E                |
| `deptNo = 2` | E.C.E                |
| `CS005`      | M. Biswantu Pal      |
| `CS006`      | M. Sripati Mukherjee |
| `EC004`      | M. Bivas Paramanik   |
| `UCS001`     | UG CSE               |
| `PCS001`     | PG CSE               |
| `UEC001`     | UG ECE               |
| `PEC001`     | PG ECE               |

**Database:** MySQL
**Assignment:** 2
**Topic:** SQL Queries
