![image](https://github.com/user-attachments/assets/d47d30d1-4abe-4ba3-95c4-817280a4732f)
![image](https://github.com/user-attachments/assets/c36c4a08-294f-49af-867e-de4e03c9faca)
![image](https://github.com/user-attachments/assets/b97668b9-daa0-46a0-bf77-ca1b9ae3e9ed)
![image](https://github.com/user-attachments/assets/a520ba44-4def-4d09-9395-5a004f26ff62)
![image](https://github.com/user-attachments/assets/3102f39b-7f52-4235-b688-d7cd0fe34a02)
![image](https://github.com/user-attachments/assets/1917061a-4481-4c70-9eba-4d4cb67d6419)
![image](https://github.com/user-attachments/assets/6de3a60c-fb40-4040-9aac-83cb0e017513)


Question.1::
Retrieve a list of courses along with the names of the instructors teaching each course.

Answer::
 ->SELECT c.course_name, concat(i.first_name," ",i.last_name) as instructor_name
 ->FROM courses c
 ->JOIN instructors i ON c.instructor_id = i.instructor_id;

Question.2::
Find the courses that have the highest enrollment, including the number of students enrolled in each of them.

Answer::
 ->SELECT c.course_name, COUNT(e.student_id) AS enrollment_count
 ->FROM courses c
 ->JOIN enrollments e ON c.course_id = e.course_id
 ->GROUP BY c.course_name
 ->ORDER BY enrollment_count DESC
 ->LIMIT 1;

Question.3::
List all students who are enrolled in a specific course and include their contact information.

Answer::
SELECT s.student_name, s.email
 ->FROM students_registration sr
 ->JOIN students s ON sr.student_id = s.student_id
 ->WHERE sr.course_id = 'specific_course_id';*****


Question.4::
Retrieve feedback comments for a specific course and include the names of the students who provided the feedback.

Answer::
 SELECT f.feedback_text, s.firstname
    -> FROM feedback f
    -> JOIN students_registration s ON f.student_id = s.student_id
    -> WHERE f.course_id = '109';
Question.5::
Calculate the average salary of instructors in a specific department.

Answer::
 SELECT AVG(i.salary) AS average_salary
    ->  FROM instructors i
    ->  ;


Question.6::List courses, their instructors, and the payment amounts made by students for each course.

Answer::
 SELECT c.course_name,i.first_name, pi.fees
    -> FROM courses c
    -> JOIN instructors i ON c.instructor_id = i.instructor_id
    -> JOIN payment_information pi ON c.course_id = pi.course_id;


Question.7::Retrieve a list of students who have registered for courses and the departments of the instructors teaching those courses.

Answer::

SELECT s.student_name, d.department
FROM students_registration sr
JOIN courses c ON sr.course_id = c.course_id
JOIN instructors i ON c.instructor_id = i.instructor_id
JOIN faculty f ON i.instructor_id = f.instructor_id
JOIN departments d ON f.department_id = d.department_id;*****


Question.8.::List students who are enrolled in more than one course.

Answer:

SELECT students_registration.FirstName, COUNT(Enrollments.Student_ID) AS NumEnrollments
FROM students_registration
JOIN Enrollments ON students_registration.Student_ID = Enrollments.Student_ID
GROUP BY students_registration.FirstName
HAVING COUNT(Enrollments.Student_ID) > 1;

Question. 9 :: Can you provide the enrollment details, including course information and payment details, for a specific student?

Answer:

SELECT
    Students_Registration.FirstName,
    Students_Registration.LastName,
    Courses.Course_Name,
    Enrollments.Enrollment_Date,
    Payment_Information.Payment_Date,
    Payment_Information.Fees
FROM
    Students_Registration
JOIN
    Enrollments ON Students_Registration.Student_ID = Enrollments.Student_ID
JOIN
    Courses ON Enrollments.Course_ID = Courses.Course_ID
LEFT JOIN
    Payment_Information ON Enrollments.Enrollment_ID = Payment_Information.Enrollment_ID
WHERE
    Students_Registration.Student_ID = [SpecifyStudentID];


Question.10 :QUARY FOR total number of students registered for a specific course by course ID

Answer::
SELECT COUNT(*) AS total_students
FROM students_registration
WHERE course_id = 101;

Question 11 : Can you provide the enrollment details, including course information and payment details, for a specific student?
Answer:
SELECT
    Students_Registration.FirstName,
    Students_Registration.LastName,
    Courses.Course_Name,
    Enrollments.Enrollment_Date,
    Payment_Information.Payment_Date,
    Payment_Information.Fees
FROM
    Students_Registration
JOIN
    Enrollments ON Students_Registration.Student_ID = Enrollments.Student_ID
JOIN
    Courses ON Enrollments.Course_ID = Courses.Course_ID
LEFT JOIN
    Payment_Information ON Enrollments.Enrollment_ID = Payment_Information.Enrollment_ID
WHERE
    Students_Registration.Student_ID = [SpecifyStudentID];


Question 12 :: Calculate Total Fees Collected

answer

SELECT SUM(Fees) AS TotalFeesCollected
FROM Payment_Information;


Question 13 :: Calculate Profit
SELECT (TotalFeesCollected - TotalExpenses) AS TotalProfit
FROM (
    SELECT SUM(Instructors.Salary) AS TotalExpenses
    FROM Instructors
) AS Expenses,
(
    SELECT SUM(Fees) AS TotalFeesCollected
    FROM Payment_Information
) AS Fees;


![image](https://github.com/user-attachments/assets/7ecef6cd-6be8-4878-9168-c77546dd06bd)
![image](https://github.com/user-attachments/assets/322d7f82-ed5c-49a9-be3f-406ffb4cdb47)








