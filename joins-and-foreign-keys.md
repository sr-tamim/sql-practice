# Joins and Foreign Keys

### Use an INNER JOIN to retrieve the names of students and the courses they are enrolled in
```sql
SELECT s.Name, c.CourseName
FROM Students s
INNER JOIN Enrollments e ON s.StudentID = e.StudentID
INNER JOIN Courses c ON e.CourseID = c.CourseID;
```
![image](https://github.com/user-attachments/assets/bde05980-cdfd-41a0-9477-853cb3ac1cfb)

---

### Write a query using LEFT JOIN to list all students and their enrollments, including those not enrolled in any courses
```sql
SELECT s.StudentID, s.Name, c.CourseID, c.CourseName
FROM Students s
LEFT JOIN Enrollments e ON s.StudentID = e.StudentID
LEFT JOIN Courses c ON e.CourseID = c.CourseID;
```
![image](https://github.com/user-attachments/assets/4b450557-c743-4d51-96c2-376514f700a2)

---

### Use a RIGHT JOIN to find courses with no students enrolled
```sql
SELECT c.CourseID, c.CourseName
FROM Enrollments e
RIGHT JOIN Courses c ON c.CourseID = e.CourseID
WHERE e.StudentID IS NULL;
```
![image](https://github.com/user-attachments/assets/bb783dac-f3fd-47eb-872a-a987a7c83ef3)

---

### Perform a FULL OUTER JOIN to list all students and courses, including those with no matches
```sql
SELECT s.StudentID, s.Name, c.CourseID, c.CourseName
FROM Students s
LEFT JOIN Enrollments e ON s.StudentID = e.StudentID
LEFT JOIN Courses c ON e.CourseID = c.CourseID;
```
![image](https://github.com/user-attachments/assets/3547639d-553a-4354-82b2-f8eb574cdd51)

---

### Write a query to find the total number of courses each student is enrolled in using a GROUP BY clause
```sql
SELECT e.StudentID, s.Name, COUNT(e.CourseID) AS TotalCourses
FROM Enrollments e
JOIN Students s ON e.StudentID = s.StudentID
GROUP BY e.StudentID, s.Name;
```
![image](https://github.com/user-attachments/assets/5e7b29fb-6de7-46bf-b8f9-e2e36c8c377f)

---

### Retrieve students who are enrolled in “Database Systems” using an INNER JOIN
```sql
SELECT s.StudentID, s.Name
FROM Students s
INNER JOIN Enrollments e ON s.StudentID = e.StudentID
INNER JOIN Courses c ON e.CourseID = c.CourseID
WHERE c.CourseName = 'Database Systems';
```
![image](https://github.com/user-attachments/assets/e364364e-63ba-462c-850f-83515d5939f4)

---

### Use a join to list all courses along with the number of students enrolled in each
```sql
SELECT c.CourseID, c.CourseName, COUNT(e.StudentID) AS NumberOfStudents
FROM Courses c
LEFT JOIN Enrollments e ON c.CourseID = e.CourseID
GROUP BY c.CourseID, c.CourseName;
```
![image](https://github.com/user-attachments/assets/35883a51-d02e-4723-b266-ddaf548da7d0)

---

### Write a query to display students who are not enrolled in any course using a LEFT JOIN and WHERE
```sql
SELECT s.StudentID, s.Name
FROM Students s
LEFT JOIN Enrollments e ON s.StudentID = e.StudentID
WHERE e.CourseID IS NULL;
```
![image](https://github.com/user-attachments/assets/439c82a8-17e7-4ca3-af10-792cb4ecadf3)

---

### Use a join to calculate the average grade of students in the “Computer Sci” major
```sql
SELECT AVG(
    CASE 
        WHEN Grade = 'A+' THEN 4.0
        WHEN Grade = 'A' THEN 3.7
        WHEN Grade = 'A-' THEN 3.5
        WHEN Grade = 'B+' THEN 3.3
        WHEN Grade = 'B' THEN 3.0
        WHEN Grade = 'C+' THEN 2.3
        WHEN Grade = 'C' THEN 2.0
        WHEN Grade = 'D' THEN 1.0
        WHEN Grade = 'F' THEN 0.0
        ELSE NULL
    END
) AS AverageGrade
FROM Students s
INNER JOIN Enrollments e ON s.StudentID = e.StudentID
INNER JOIN Courses c ON e.CourseID = c.CourseID
WHERE s.Major = 'Computer Science';
```
![image](https://github.com/user-attachments/assets/5c73b89b-b45d-4728-a59e-da61a25862bc)

---

### Create a query to retrieve the details of students and their enrolled courses, sorted by StudentID and CourseID
```sql
SELECT s.StudentID, s.Name, c.CourseID, c.CourseName
FROM Students s
INNER JOIN Enrollments e ON s.StudentID = e.StudentID
INNER JOIN Courses c ON e.CourseID = c.CourseID
ORDER BY s.StudentID, c.CourseID;
```
![image](https://github.com/user-attachments/assets/a12b569f-b052-4855-8c27-16ce6a6c1b1e)
