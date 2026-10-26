# VUA-SEN307 DATABASE SYSTEMS
## Week 4 Practical: Database Design and Normalization

**Department:** Software Engineering  
**Matric Number:** vug-24-11298
**Full Name:** Faith Aladi Emmanuel

### Part 1: Entities and Relationships

The database contains six tables:

1. Department
2. Student
3. Lecturer
4. Course
5. Enrolment
6. CourseLecturer

**Relationships:**
- One department can have many students, lecturers and courses.
- Students can register for many courses.
- A course can have many students.
- Lecturers can teach many courses.
- Enrolment and CourseLecturer connect the related tables.

### Part 2: Normalization

**UNF (Unnormalized Form)**

The original registration sheet contains student details, courses and lecturers. Some cells contain many values.

**1NF (First Normal Form)**

Each cell contains one value. Each student-course registration is recorded in a separate row.

| Matric No. | Student Name | Course Code | Course Title |
|---|---|---|---|
| 20231234 | Ada Obi | SEN307 | Database Systems |
| 20231234 | Ada Obi | SEN301 | Software Architecture |
| 20231235 | John Musa | SEN307 | Database Systems |
| 20231235 | John Musa | COS301 | Operating Systems |
| 20231236 | Grace Okon | SEN301 | Software Architecture |

**Explanation:** 1NF removes multiple values from individual cells.

**2NF (Second Normal Form)**

The data is separated into three tables.

**Student**

| Matric No. (PK) | Student Name |
|---|---|
| 20231234 | Ada Obi |
| 20231235 | John Musa |
| 20231236 | Grace Okon |

**Course**

| Course Code (PK) | Course Title |
|---|---|
| SEN307 | Database Systems |
| SEN301 | Software Architecture |
| COS301 | Operating Systems |

**Enrolment**

| Matric No. (FK) | Course Code (FK) | Session |
|---|---|---|
| 20231234 | SEN307 | 2026/2027 |
| 20231234 | SEN301 | 2026/2027 |
| 20231235 | SEN307 | 2026/2027 |
| 20231235 | COS301 | 2026/2027 |
| 20231236 | SEN301 | 2026/2027 |

**Explanation:** 2NF separates student and course details from registration records.

**3NF (Third Normal Form)**

Department and lecturer details are stored in separate tables to reduce repetition.

### Final Database Schema

- **Department:** dept_id (PK), dept_name
- **Student:** matric_no (PK), full_name, dept_id (FK)
- **Lecturer:** lecturer_id (PK), full_name, dept_id (FK)
- **Course:** course_code (PK), course_title, dept_id (FK)
- **Enrolment:** enrolment_id (PK), matric_no (FK), course_code (FK), academic_session
- **CourseLecturer:** course_code (PK, FK), lecturer_id (PK, FK), academic_session (PK)

**Explanation:** 3NF separates related information into different tables and connects them using foreign keys.

### Conclusion

The database reduces repeated data and organizes student registrations, courses, lecturers and departments into related tables.