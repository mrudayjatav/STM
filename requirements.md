# STUDENTS RECORD MANAGEMENT SYSTEM

### Database Tables Required:
1. Colleges
2. Students
3. Enrollments
4. Courses
5. Attendance
6. Grade

### Database Schema Design:
#### <span style="color:#feb236">Colleges</span>
(college_id, college_name, address, phone, email)
#### <span style="color:#feb236">Students</span>
(student_id, college_id, first_name, last_name, date_of_birth, gender, address, phone, email, enrollment_date)
#### <span style="color:#feb236">Enrollments</span>
(enrollment_id, student_id, course_id, enrollment_date)
#### <span style="color:#feb236">Courses</span>
(course_id, college_id, course_name, course_description, credits)
#### <span style="color:#feb236">Attendance</span>
(attendance_id, student_id, course_id, attendance_date, status)
#### <span style="color:#feb236">Grade</span>
(grade_id, student_id, course_id, grade)

## SQL Script & Queries:
### 1 DDL:
#### <span style="color:#feb236">Colleges</span>
    CREATE TABLE Colleges (
    college_id INT PRIMARY KEY AUTO_INCREMENT,
    college_name VARCHAR(100),
    address VARCHAR(100),
    phone VARCHAR(15),
    email VARCHAR(50)
    );
#### <span style="color:#feb236">Students</span>
    CREATE TABLE Students (
        student_id INT PRIMARY KEY AUTO_INCREMENT,
        college_id INT,
        first_name VARCHAR(50),
        last_name VARCHAR(50),
        date_of_birth DATE,
        gender CHAR(1),
        address VARCHAR(100),
        phone VARCHAR(15),
        email VARCHAR(50),
        enrollment_date DATE,
        FOREIGN KEY (college_id) REFERENCES Colleges(college_id)
    );
#### <span style="color:#feb236">Enrollments</span>
    CREATE TABLE Enrollments (
        enrollment_id INT PRIMARY KEY AUTO_INCREMENT,
        student_id INT,
        course_id INT,
        enrollment_date DATE,
        FOREIGN KEY (student_id) REFERENCES Students(student_id),
        FOREIGN KEY (course_id) REFERENCES Courses(course_id)
    );
#### <span style="color:#feb236">Courses</span>
    CREATE TABLE Courses (
        course_id INT PRIMARY KEY AUTO_INCREMENT,
        college_id INT,
        course_name VARCHAR(100),
        course_description TEXT,
        credits INT,
        FOREIGN KEY (college_id) REFERENCES Colleges(college_id)
    );
#### <span style="color:#feb236">Attendance</span>
    CREATE TABLE Attendance (
        attendance_id INT PRIMARY KEY AUTO_INCREMENT,
        student_id INT,
        course_id INT,
        attendance_date DATE,
        status CHAR(1),
        FOREIGN KEY (student_id) REFERENCES Students(student_id),
        FOREIGN KEY (course_id) REFERENCES Courses(course_id)
    );
#### <span style="color:#feb236">Grade</span>
    CREATE TABLE Grades (
        grade_id INT PRIMARY KEY AUTO_INCREMENT,
        student_id INT,
        course_id INT,
        grade CHAR(2),
        FOREIGN KEY (student_id) REFERENCES Students(student_id),
        FOREIGN KEY (course_id) REFERENCES Courses(course_id)
    );
### 2 DML:
### 3 DQL:
## Procedures & Functions:
## Indexs & Performance Optimization
## Security & Backup
