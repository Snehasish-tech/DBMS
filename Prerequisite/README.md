# DBMS Lab — University Database Management System

## Prerequisite

This project contains the basic **University Database Management System** created using MySQL. It is used as the base database for DBMS Lab Assignments 1, 2, 3 and 4.

---

## Database Name

`university1`

---

## Description

This project creates a university database using MySQL.

The database contains information about:

* Departments
* Professors
* Students
* Courses
* Enrollment
* Teaching
* Course Prerequisites

The database is used to practice different SQL concepts such as:

* `SELECT`
* `WHERE`
* `JOIN`
* Subqueries
* Aggregate Functions
* `GROUP BY`
* `ORDER BY`
* `LIKE`
* `DISTINCT`
* Set Operations

---

## Technologies Used

* MySQL
* MySQL Workbench

---

# Database Structure

The database contains the following 7 tables:

| No. | Table Name     |
| --: | -------------- |
|   1 | `department`   |
|   2 | `professor`    |
|   3 | `student`      |
|   4 | `course`       |
|   5 | `enrollment`   |
|   6 | `teaching`     |
|   7 | `prerequisite` |

---

# SQL Code

## 1. Create Database

```sql
CREATE DATABASE IF NOT EXISTS university1;

USE university1;
```

---

## 2. Create Department Table

```sql
CREATE TABLE department (
    deptId INT PRIMARY KEY,
    name VARCHAR(50),
    hod VARCHAR(10),
    phone VARCHAR(15)
);

INSERT INTO department (deptId, name, hod, phone)
VALUES
(1, 'C.S.E', 'CS006', '2558777'),
(2, 'E.C.E', 'EC004', '2558776');
```

---

## 3. Create Professor Table

```sql
CREATE TABLE professor (
    empId VARCHAR(10) PRIMARY KEY,
    name VARCHAR(100),
    sex VARCHAR(10),
    startYear INT,
    deptNo INT,
    phone VARCHAR(15)
);

INSERT INTO professor
(empId, name, sex, startYear, deptNo, phone)
VALUES
('CS001', 'Dr. Biplab Sarkar', 'Male', 1982, 1, '9434122345'),
('CS002', 'Dr. Supriya Bhattacharya', 'Male', 2000, 1, '9345134677'),
('CS003', 'M. Sanjoy Pratihar', 'Male', 2003, 1, '9332657342'),
('CS004', 'Ms. Kasturi Dikpati', 'Female', 2003, 1, '9414321908'),
('CS005', 'M. Biswantu Pal', 'Male', 2004, 1, '9544123876'),
('EC001', 'Dr. B. C. Sarkar', 'Male', 1986, 2, '9456128867'),
('EC002', 'Ms. Smita Hazra', 'Female', 2002, 2, '9465123417'),
('EC003', 'M. Somnath Pal', 'Male', 2005, 2, '9435129078'),
('CS006', 'M. Sripati Mukherjee', 'Male', 1977, 1, '9435675489'),
('EC004', 'M. Bivas Paramanik', 'Male', 2002, 2, '9453215789');
```

---

## 4. Create Student Table

```sql
CREATE TABLE student (
    rollNo INT,
    name VARCHAR(100),
    degree VARCHAR(10),
    year INT,
    sex VARCHAR(10),
    deptNo INT,
    advisor VARCHAR(10)
);

INSERT INTO student
(rollNo, name, degree, year, sex, deptNo, advisor)
VALUES
(1, 'Parag Roy', 'B.E', 3, 'Male', 1, 'CS005'),
(2, 'Riturna Kashyap', 'B.E', 3, 'Male', 1, 'CS005'),
(3, 'Neha', 'B.E', 3, 'Female', 1, 'CS005'),
(4, 'Raman', 'B.E', 4, 'Male', 2, 'EC004'),
(5, 'Surja Sanyal', 'M.E', 2, 'Male', 1, 'CS005'),
(6, 'Susahant Satyam', 'M.E', 1, 'Male', 2, 'EC004'),
(7, 'Kamalika Samanta', 'M.E', 1, 'Female', 1, 'CS005'),
(8, 'Aparajita', 'B.E', 2, 'Female', 2, 'EC004'),
(9, 'Sirajul Islam', 'M.E', 2, 'Male', 2, 'EC004'),
(10, 'Manisha Chaudhury', 'M.E', 2, 'Female', 2, 'EC004'),
(7, 'Kamalika Samanta', 'M.E', 1, 'Female', 1, 'CS005');
```

---

## 5. Create Course Table

```sql
CREATE TABLE course (
    courseId VARCHAR(10) PRIMARY KEY,
    name VARCHAR(50),
    credits INT,
    deptNo INT
);

INSERT INTO course
(courseId, name, credits, deptNo)
VALUES
('UCS001', 'UG CSE', 2, 1),
('PCS001', 'PG CSE', 4, 1),
('UEC001', 'UG ECE', 2, 2),
('PEC001', 'PG ECE', 4, 2);
```

---

## 6. Create Enrollment Table

```sql
CREATE TABLE enrollment (
    rollNo INT,
    courseId VARCHAR(10),
    sem INT,
    year INT,
    grade VARCHAR(5)
);

INSERT INTO enrollment
(rollNo, courseId, sem, year, grade)
VALUES
(1, 'UCS001', 6, 3, 'A'),
(2, 'UCS001', 6, 3, 'B'),
(3, 'UCS001', 6, 3, 'A+'),
(4, 'UEC001', 8, 4, 'A'),
(5, 'PCS001', 4, 2, 'A+'),
(6, 'PEC001', 2, 1, 'A+'),
(7, 'PCS001', 2, 1, 'A++'),
(8, 'UEC001', 4, 2, 'B++'),
(9, 'PEC001', 4, 2, 'A'),
(10, 'PEC001', 4, 2, 'B++');
```

---

## 7. Create Teaching Table

```sql
CREATE TABLE teaching (
    empId VARCHAR(10),
    courseId VARCHAR(10),
    sem INT,
    year INT,
    classroom VARCHAR(10)
);

INSERT INTO teaching
(empId, courseId, sem, year, classroom)
VALUES
('CS001', 'PCS001', 2, 1, 'PC-1'),
('CS001', 'PCS001', 4, 2, 'PC-2'),
('CS002', 'PCS001', 2, 1, 'PC-1'),
('CS003', 'UCS001', 6, 3, 'UC-1'),
('CS004', 'UCS001', 6, 3, 'UC-1'),
('CS005', 'PCS001', 2, 1, 'PC-1'),
('CS005', 'UCS001', 6, 3, 'UC-1'),
('EC001', 'UEC001', 4, 2, 'UE-1'),
('EC002', 'UEC001', 4, 2, 'UE-1'),
('EC003', 'PEC001', 4, 2, 'PE-1'),
('EC003', 'UEC001', 6, 3, 'UE-1');
```

---

## 8. Create Prerequisite Table

```sql
CREATE TABLE prerequisite (
    preReqCourse VARCHAR(20),
    courseId VARCHAR(10)
);

INSERT INTO prerequisite
(preReqCourse, courseId)
VALUES
('H.S', 'UCS001'),
('B.E', 'PCS001'),
('H.S', 'UEC001'),
('B.E', 'PEC001');
```

---

# Display All Tables

To display all the tables available in the database:

```sql
SHOW TABLES;
```

### Tables

```text
department
enrollment
prerequisite
professor
student
teaching
course
```

---

# Display Table Data

## Department

```sql
SELECT * FROM department;
```

## Professor

```sql
SELECT * FROM professor;
```

## Student

```sql
SELECT * FROM student;
```

## Course

```sql
SELECT * FROM course;
```

## Enrollment

```sql
SELECT * FROM enrollment;
```

## Teaching

```sql
SELECT * FROM teaching;
```

## Prerequisite

```sql
SELECT * FROM prerequisite;
```

---

# Display All Table Data Together

All table records can also be displayed using:

```sql
SELECT * FROM department;

SELECT * FROM professor;

SELECT * FROM student;

SELECT * FROM course;

SELECT * FROM enrollment;

SELECT * FROM teaching;

SELECT * FROM prerequisite;
```

---

# Database Relationships

The main relationships between the tables are:

* `department.deptId` → `professor.deptNo`
* `department.deptId` → `student.deptNo`
* `professor.empId` → `student.advisor`
* `course.courseId` → `enrollment.courseId`
* `course.courseId` → `teaching.courseId`
* `professor.empId` → `teaching.empId`
* `course.courseId` → `prerequisite.courseId`

---

# Assignments

This database is used for the following DBMS Lab assignments:

* [Assignment 1](../Assignment-1/README.md)
* [Assignment 2](../Assignment-2/README.md)
* [Assignment 3](../Assignment-3/README.md)
* [Assignment 4](../Assignment-4/README.md)

---



## Project Information

**Database:** MySQL
**Tool:** MySQL Workbench
**Project:** University Database Management System
**Purpose:** DBMS Lab Practice
