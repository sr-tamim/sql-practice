# Basic SQL Queries

### Retrieve all columns of data from the Students table.
```sql
SELECT * FROM Students;
```

### Write a query to retrieve the Name and Major of all students.
```sql
SELECT Name, Major FROM Students;
```

### Find students who are majoring in “Computer Science”.
```sql
SELECT * FROM Students
WHERE Major = "Computer Science";
```

### Retrieve students whose GPA is greater than 3.5.
```sql
SELECT * FROM Students
WHERE GPA > 3.5;
```

### Find students enrolled in the year 2021.
```sql
SELECT * FROM Students
WHERE EnrollmentYear = 2021;
```

### Write a query to retrieve the details of students aged between 20 and 22.
```sql
SELECT * FROM Students
WHERE Age BETWEEN 20 AND 22;
```

### Retrieve the names of students whose names start with “A”.
```sql
SELECT * FROM Students
WHERE Name LIKE "A%";
```

### Sort the students by their GPA in descending order.
```sql
SELECT * FROM Students
ORDER BY GPA DESC;
```

### List all students who are younger than 21.
```sql
SELECT * FROM Students
WHERE Age < 21;
```

### Retrieve students whose Major is either “Biology” or “History”.
```sql
SELECT * FROM Students
WHERE Major IN ("Biology", "History");
```
