# SubQueries

## Find the names of all courses that have at least one student enrolled using a subquery
```sql
SELECT * FROM `Courses`
WHERE CourseID IN (
    SELECT CourseID
    FROM Enrollments
    WHERE Enrollments.CourseID = Courses.CourseID
);
```
![image](https://github.com/user-attachments/assets/4f2110c6-c682-48ef-9547-913eed7090c7)

---

## Write a query to find students who are not enrolled in any courses
```sql
SELECT * FROM Students
WHERE StudentID NOT IN (
    SELECT StudentID
    FROM Enrollments
);
```
![image](https://github.com/user-attachments/assets/78267863-bdee-419c-8367-b2d0d217b2b0)

---

## Retrieve the names of students who are enrolled in “Database Systems” using a subquery
```sql
SELECT * FROM Students
WHERE StudentID IN (
    SELECT StudentID
    FROM Enrollments e
    JOIN Courses c ON e.CourseID = c.CourseID
    WHERE c.CourseName = "Database Systems"
);
```
![image](https://github.com/user-attachments/assets/f5402e6d-5cbf-4090-bd82-b6d8e5f17008)

---

## Find courses that are not taken by any students using a subquery
```sql
SELECT * FROM Courses
WHERE NOT EXISTS (
    SELECT 1 FROM Enrollments
    WHERE Courses.CourseID = Enrollments.CourseID
);
```
![image](https://github.com/user-attachments/assets/3941b3c4-d875-4a64-9db5-1b2d31c31223)

---

## Write a query to find the average grade of students in courses where credits are greater than 3
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
FROM Enrollments
WHERE EXISTS (
    SELECT 1 FROM Courses
    WHERE Courses.CourseID = Enrollments.CourseID
    AND Credits > 3
);
```
![image](https://github.com/user-attachments/assets/321f1b0f-41ff-47f7-94d5-20b3c907564c)

---

## Retrieve the CourseName for all courses in which a grade of “A” was received using a subquery
```sql
SELECT CourseName FROM Courses
WHERE EXISTS (
    SELECT 1 FROM Enrollments WHERE Grade = "A"
    AND Enrollments.CourseID = Courses.CourseID
);
```
![image](https://github.com/user-attachments/assets/bc296611-8906-47e5-bdef-1acbe828dd0e)

---

## Use a subquery to find courses with more than two students enrolled
```sql
SELECT *
FROM Courses
WHERE CourseID IN (
    SELECT e.CourseID
    FROM Enrollments e
    GROUP BY e.CourseID
    HAVING COUNT(e.EnrollmentID) > 2
);
```
![image](https://github.com/user-attachments/assets/1b01e996-d622-418b-b41f-09a996d369a1)

---

## Find students who have taken all courses in the “Computer Sci” major using a correlated subquery
```sql
SELECT s.StudentID, s.Name
FROM Students s
WHERE EXISTS (
    SELECT c.CourseID
    FROM Courses c
    WHERE c.Major = 'Computer Science'
    AND EXISTS (
        SELECT e.EnrollmentID
        FROM Enrollments e
        WHERE e.CourseID = c.CourseID
        AND e.StudentID = s.StudentID
    )
);
```
![image](https://github.com/user-attachments/assets/6dfcccb1-ef2c-45b4-b94d-acfa706648b1)

---

## Write a query to find students who have the highest grade in their enrolled courses using a subquery
```sql
SELECT e.StudentID, s.Name, e.CourseID, e.Grade
FROM Enrollments e
JOIN Students s ON e.StudentID = s.StudentID
WHERE (
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
) = (
    SELECT MAX(
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
    )
    FROM Enrollments e1
    WHERE e1.CourseID = e.CourseID
);
```
![image](https://github.com/user-attachments/assets/ddf7ec3d-43ef-4957-a80a-1907dad8a6f5)

---

## Retrieve details of courses in which the number of credits exceeds the average credits across all courses
```sql
SELECT *
FROM Courses
WHERE Credits > (
    SELECT AVG(Credits)
    FROM Courses
);
```
![image](https://github.com/user-attachments/assets/793032d9-98b6-48ef-9ad0-68abe00e6331)
