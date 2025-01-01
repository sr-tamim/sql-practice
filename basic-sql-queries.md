# Basic SQL Queries

### Retrieve all columns of data from the Students table.
```sql
SELECT * FROM Students;
```
![image](https://github.com/user-attachments/assets/28c7851c-38b0-44f3-a4ce-1e4a5a23aede)

<br/>

### Write a query to retrieve the Name and Major of all students.
```sql
SELECT Name, Major FROM Students;
```
![image](https://github.com/user-attachments/assets/bae538f0-4b5f-4bef-99cc-784030ee937f)


### Find students who are majoring in “Computer Science”.
```sql
SELECT * FROM Students
WHERE Major = "Computer Science";
```
![image](https://github.com/user-attachments/assets/4669b8bb-670d-404b-a400-920269808159)


### Retrieve students whose GPA is greater than 3.5.
```sql
SELECT * FROM Students
WHERE GPA > 3.5;
```
![image](https://github.com/user-attachments/assets/841ae765-8806-4524-bdac-ab707d78ced7)


### Find students enrolled in the year 2021.
```sql
SELECT * FROM Students
WHERE EnrollmentYear = 2021;
```
![image](https://github.com/user-attachments/assets/e5c0d5c7-eb9e-49e2-a869-d50c718ef64f)


### Write a query to retrieve the details of students aged between 20 and 22.
```sql
SELECT * FROM Students
WHERE Age BETWEEN 20 AND 22;
```
![image](https://github.com/user-attachments/assets/b08c3d1e-97f2-4c22-8073-02a5cf59d139)


### Retrieve the names of students whose names start with “A”.
```sql
SELECT * FROM Students
WHERE Name LIKE "A%";
```
![image](https://github.com/user-attachments/assets/2bc89304-3ee3-4113-abb4-dd4b11dbbd3f)


### Sort the students by their GPA in descending order.
```sql
SELECT * FROM Students
ORDER BY GPA DESC;
```
![image](https://github.com/user-attachments/assets/7193bb06-0157-42e0-9b54-ee029b058aad)


### List all students who are younger than 21.
```sql
SELECT * FROM Students
WHERE Age < 21;
```
![image](https://github.com/user-attachments/assets/d0176401-f80d-49ed-b24f-d4163ccdf6e9)


### Retrieve students whose Major is either “Biology” or “History”.


```sql
SELECT * FROM Students
WHERE Major IN ("Biology", "History");
```
![image](https://github.com/user-attachments/assets/536324f8-ee25-4913-a97e-67049e5d0924)
