# DBMS Lab — Assignment 1

## Database: `university1`

This assignment contains SQL queries and their outputs based on the `university1` database.

---

## 1. Show the roll no and name of the students who read B.E.

### Query

```sql
SELECT rollNo, name
FROM student
WHERE degree = 'B.E';
```

### Output

| rollNo | name            |
| -----: | --------------- |
|      1 | Parag Roy       |
|      2 | Riturna Kashyap |
|      3 | Neha            |
|      4 | Raman           |
|      8 | Aparajita       |

---

## 2. Show the roll no and name of the students who read M.E.

### Query

```sql
SELECT rollNo, name
FROM student
WHERE degree = 'M.E';
```

### Output

| rollNo | name              |
| -----: | ----------------- |
|      5 | Surja Sanyal      |
|      6 | Susahant Satyam   |
|      7 | Kamalika Samanta  |
|      9 | Sirajul Islam     |
|     10 | Manisha Chaudhury |
|      7 | Kamalika Samanta  |

---

## 3. Show the roll no and name of the male students.

### Query

```sql
SELECT rollNo, name
FROM student
WHERE sex = 'Male';
```

### Output

| rollNo | name            |
| -----: | --------------- |
|      1 | Parag Roy       |
|      2 | Riturna Kashyap |
|      4 | Raman           |
|      5 | Surja Sanyal    |
|      6 | Susahant Satyam |
|      9 | Sirajul Islam   |

---

## 4. Show the roll no and name of the female students.

### Query

```sql
SELECT rollNo, name
FROM student
WHERE sex = 'Female';
```

### Output

| rollNo | name              |
| -----: | ----------------- |
|      3 | Neha              |
|      7 | Kamalika Samanta  |
|      8 | Aparajita         |
|     10 | Manisha Chaudhury |
|      7 | Kamalika Samanta  |

---

## 5. Show the department id and phone no of Computer Sc & Engg. Dept.

### Query

```sql
SELECT deptId, phone
FROM department
WHERE name = 'C.S.E';
```

### Output

| deptId | phone   |
| -----: | ------- |
|      1 | 2558777 |

---

## 6. Show the Emp id, name, sex and phone no of the professors who joined before 2000.

### Query

```sql
SELECT empId, name, sex, phone
FROM professor
WHERE startYear < 2000;
```

### Output

| empId | name                 | sex  | phone      |
| ----- | -------------------- | ---- | ---------- |
| CS001 | Dr. Biplab Sarkar    | Male | 9434122345 |
| EC001 | Dr. B. C. Sarkar     | Male | 9456128867 |
| CS006 | M. Sripati Mukherjee | Male | 9435675489 |

---

## 7. Show the name and phone no of the male professors.

### Query

```sql
SELECT name, phone
FROM professor
WHERE sex = 'Male';
```

### Output

| name                     | phone      |
| ------------------------ | ---------- |
| Dr. Biplab Sarkar        | 9434122345 |
| Dr. Supriya Bhattacharya | 9345134677 |
| M. Sanjoy Pratihar       | 9332657342 |
| M. Biswantu Pal          | 9544123876 |
| Dr. B. C. Sarkar         | 9456128867 |
| M. Somnath Pal           | 9435129078 |
| M. Sripati Mukherjee     | 9435675489 |
| M. Bivas Paramanik       | 9453215789 |

---

## 8. Show the roll no, course id and grade of top graded students.

### Query

```sql
SELECT rollNo, courseId, grade
FROM enrollment
WHERE grade = 'A++';
```

### Output

| rollNo | courseId | grade |
| -----: | -------- | ----- |
|      7 | PCS001   | A++   |

---

## 9. Show the roll no and course id of the first year students.

### Query

```sql
SELECT rollNo, courseId
FROM enrollment
WHERE year = 1;
```

### Output

| rollNo | courseId |
| -----: | -------- |
|      6 | PEC001   |
|      7 | PCS001   |

---

## 10. Show the roll no and course id of the other than 1st year students.

### Query

```sql
SELECT rollNo, courseId
FROM enrollment
WHERE year <> 1;
```

### Output

| rollNo | courseId |
| -----: | -------- |
|      1 | UCS001   |
|      2 | UCS001   |
|      3 | UCS001   |
|      4 | UEC001   |
|      5 | PCS001   |
|      8 | UEC001   |
|      9 | PEC001   |
|     10 | PEC001   |

---

## 11. Show the credit point of undergraduate C.S.E course.

### Query

```sql
SELECT credits
FROM course
WHERE name = 'UG CSE';
```

### Output

| credits |
| ------: |
|       2 |

---

## 12. Show the course name whose credit points are 4.

### Query

```sql
SELECT name
FROM course
WHERE credits = 4;
```

### Output

| name   |
| ------ |
| PG CSE |
| PG ECE |

---

## 13. Show the start year and phone no of the female professors.

### Query

```sql
SELECT startYear, phone
FROM professor
WHERE sex = 'Female';
```

### Output

| startYear | phone      |
| --------: | ---------- |
|      2003 | 9414321908 |
|      2002 | 9465123417 |

---

## 14. Show the roll no and course id of the students who have below A grade.

### Query

```sql
SELECT rollNo, courseId
FROM enrollment
WHERE grade IN ('B++', 'B');
```

### Output

| rollNo | courseId |
| -----: | -------- |
|      2 | UCS001   |
|      8 | UEC001   |
|     10 | PEC001   |

---

## 15. Show the Roll no, year and degree of the student whose name is Aparajita.

### Query

```sql
SELECT rollNo, year, degree
FROM student
WHERE name = 'Aparajita';
```

### Output

| rollNo | year | degree |
| -----: | ---: | ------ |
|      8 |    2 | B.E    |

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
**Assignment:** 1
**Topic:** SQL Queries
