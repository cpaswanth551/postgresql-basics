
---

# Student Database SQL Queries Tutorial

This README provides an overview of SQL queries used to manage and analyze student and subject data in a relational database. The database consists of two main tables: **studenttb** and **subjecttb**.

## Database Structure

### 1. `studenttb`
This table contains information about students.

| Column   | Type    | Description                  |
|----------|---------|------------------------------|
| id       | Integer | Unique identifier for each student |
| name     | String  | Name of the student          |
| std      | Integer | Standard/class of the student |
| marks    | Integer | Marks obtained by the student |

### Sample Data

```plaintext
"id","name","std","marks"
1,"Rajan",5,75
2,"Sanjay",5,80
3,"Priya",6,85
4,"Anil",6,90
5,"Neha",7,95
6,"Amit",7,78
7,"Vijay",8,88
8,"Sunita",8,83
9,"Pooja",9,92
10,"Ravi",9,76
```

### 2. `subjecttb`
This table contains information about the subjects that students are enrolled in.

| Column      | Type    | Description                          |
|-------------|---------|--------------------------------------|
| student_id  | Integer | Identifier linking to the student in `studenttb` |
| subject     | String  | Name of the subject                  |
| mark        | Integer | Marks obtained in the subject        |

### Sample Data

```plaintext
"student_id","subject","mark"
1,"Math",85
1,"Science",78
2,"English",88
2,"Math",90
3,"Math",92
4,"Science",89
5,"Math",94
6,"English",87
7,"Science",82
8,"Math",88
```

## SQL Queries

### Basic Queries

1. **Grouping Students by Standard**
   ```sql
   SELECT std FROM studenttb GROUP BY std;
   ```
   This query retrieves distinct standards from the `studenttb`.

2. **Counting Students per Standard**
   ```sql
   SELECT std, COUNT(*) FROM studenttb GROUP BY std ORDER BY std DESC;
   ```
   This query counts the number of students in each standard and orders the results in descending order.

3. **Average Marks per Standard**
   ```sql
   SELECT std, AVG(marks) AS avg_marks FROM studenttb GROUP BY std;
   ```
   This query calculates the average marks of students in each standard.

4. **Maximum Marks per Standard**
   ```sql
   SELECT std, MAX(marks) AS max_marks FROM studenttb GROUP BY std;
   ```
   This query retrieves the highest marks obtained by students in each standard.

5. **Counting Students with More than One Subject**
   ```sql
   SELECT std, COUNT(marks) AS count_students FROM studenttb GROUP BY std HAVING COUNT(*) > 1;
   ```
   This query counts the number of students in each standard who are enrolled in more than one subject.

### Advanced Queries

1. **Number of Subjects per Student**
   ```sql
   SELECT s.name, COUNT(sub.student_id) AS avg_marks
   FROM studenttb s 
   JOIN subjecttb sub ON s.id = sub.student_id   
   GROUP BY name;
   ```
   This query counts the number of subjects each student is enrolled in.

2. **Students with More Than One Subject (Including Marks)**
   ```sql
   SELECT s.name, sub.subject, sub.mark AS total_mark 
   FROM studenttb s 
   JOIN subjecttb sub ON s.id = sub.student_id 
   WHERE s.id IN (
       SELECT student_id FROM subjecttb 
       GROUP BY student_id HAVING COUNT(subject) > 1
   );
   ```
   This query retrieves the names, subjects, and marks of students who are enrolled in more than one subject.

## Conclusion

This document serves as a reference for querying student and subject data in a relational database. It provides essential SQL commands for analyzing and managing student performance based on various metrics. Future users can expand on these queries to further meet their specific data analysis needs.

---

Feel free to modify any section as per your specific requirements!