# KIET Student Academic Management REST API

Spring Boot REST API for the MSE-2 sample assessment. It uses an in-memory `List<Student>`; no database is required.

## Requirements
- JDK 17 or newer
- Maven (or IntelliJ IDEA's bundled Maven)
- Postman (for API testing)

## Run in IntelliJ
1. Extract the ZIP.
2. Open the `student-academic-management` folder in IntelliJ as a Maven project.
3. Wait for Maven dependencies to download.
4. Run `StudentApplication.java`.
5. Confirm the console shows the three startup log messages.
6. Test the endpoints at `http://localhost:8080`.

If your project already uses a different installed JDK, set the IntelliJ Project SDK and Maven importer JDK to that installed version. Keep the `java.version` in `pom.xml` compatible with your chosen JDK.

## Endpoints

| Method | URL | Purpose |
|---|---|---|
| GET | `/students` | Get all students |
| GET | `/students/101` | Get student by ID |
| POST | `/students` | Add a student |
| PUT | `/students/101` | Update student 101 |
| DELETE | `/students/105` | Delete student 105 |
| GET | `/students/search?branch=CSE&year=2` | Search by branch and year |
| GET | `/students/topper?cgpa=9.0` | Find students with CGPA >= given value |

## Postman request examples

### Add student
- Method: `POST`
- URL: `http://localhost:8080/students`
- Body → raw → JSON

```json
{
  "studentId": 106,
  "name": "Amit Kumar",
  "email": "amit@kiet.edu",
  "branch": "CSE(AI)",
  "year": 2,
  "cgpa": 8.75
}
```

### Update student
- Method: `PUT`
- URL: `http://localhost:8080/students/101`
- Body → raw → JSON

```json
{
  "studentId": 101,
  "name": "Rahul Sharma",
  "email": "rahul@kiet.edu",
  "branch": "CSE(AI & ML)",
  "year": 3,
  "cgpa": 9.05
}
```

For GET and DELETE, no request body is needed. Select `Body → raw → JSON` for POST and PUT.

## Important note
The data is stored only in memory. Restarting the application resets the list to the five sample students.
