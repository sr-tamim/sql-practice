# Aggregation

## Count the total number of records in the Grades table
```sql
SELECT COUNT(*) FROM Grades
```
![image](https://github.com/user-attachments/assets/725684d0-effe-45c4-8f3d-858c480ed7bb)

---

## Find the average grade of all students in “CourseID 101”
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
FROM Grades;
```
![image](https://github.com/user-attachments/assets/519f26eb-07f6-40dc-9a9d-2fb34c63ed09)

---

## Determine the highest grade received in the Grades table
```sql
SELECT Grade
FROM Grades
ORDER BY (
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
) DESC
LIMIT 1;
```
![image](https://github.com/user-attachments/assets/44e7587f-d6f2-411c-b56e-0ee3e220b889)

---

## Find the lowest grade for “CourseID 103”
```sql
SELECT Grade
FROM Grades
WHERE CourseID = 103
ORDER BY (
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
LIMIT 1;
```
![image](https://github.com/user-attachments/assets/3091c870-2105-4ab4-86da-f60392f41b9a)

---

## Count the number of students enrolled in each course using GROUP BY
```sql
SELECT CourseID,
COUNT(DISTINCT StudentID) AS StudentCount
FROM Grades
GROUP BY CourseID;
```
![image](https://github.com/user-attachments/assets/05f26394-a6df-416d-a9b3-6694f8872d9f)

---

## Retrieve the total number of students with grades above “B”
```sql
SELECT COUNT(*)
FROM Grades
WHERE 3 < (
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
);
```
![image](https://github.com/user-attachments/assets/9973b17e-21ae-40ce-9e0a-5ea0444ca4a0)

---

## Calculate the average grade for each semester using GROUP BY
```sql
SELECT Semester, AVG(
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
FROM Grades
GROUP BY Semester;
```
![image](https://github.com/user-attachments/assets/c4e8f17f-4078-4a5b-b7c6-d109174a8378)

---

## Use HAVING to display courses where the average grade is above “B+”
```sql
SELECT *
FROM Grades
HAVING (
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
) > 3.3;
```
![image](https://github.com/user-attachments/assets/600d551d-6ff2-4580-ac5e-a76fca49678f)

---

## Determine the total number of unique courses in the Grades table
```sql
SELECT COUNT(DISTINCT CourseID)
FROM Grades;
```
![image](https://github.com/user-attachments/assets/8ebbf870-bb13-409a-be65-2053035be2db)

---

## Count how many students received a grade of “A” or higher
```sql
SELECT COUNT(*)
FROM Grades
WHERE 3.7 <= (
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
);
```
![image](https://github.com/user-attachments/assets/2768fb11-a0be-4942-8429-def6f2b5ede1)
