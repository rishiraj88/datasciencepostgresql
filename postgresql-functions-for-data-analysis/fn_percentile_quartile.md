# Query to get Percentile and Quartile
For the purpose, posgres features the following function:
- PERCENTILE_CONT() WITHIN GROUP

## using the function PERCENTILE_CONT() for data analysis
### one method
SELECT 
	student_name,
	grade,
	CASE
		WHEN grade <= (SELECT PERCENTILE_CONT(0.25) WITHIN GROUP (ORDER BY grade) FROM student_grades) THEN '1st quartile'
		WHEN grade <= (SELECT PERCENTILE_CONT(0.50) WITHIN GROUP (ORDER BY grade) FROM student_grades) THEN '2nd quartile'
		WHEN grade <= (SELECT PERCENTILE_CONT(0.75) WITHIN GROUP (ORDER BY grade) FROM student_grades) THEN '3rd quartile'
		ELSE '4th quartile'
	END AS quartile_label
FROM 
	student_grades
ORDER BY 
	student_name;

### alternative method
WITH quartiles AS (
	SELECT 
		PERCENTILE_CONT(0.25) WITHIN GROUP (ORDER BY grade) AS q1,
		PERCENTILE_CONT(0.50) WITHIN GROUP (ORDER BY grade) AS q2,
		PERCENTILE_CONT(0.75) WITHIN GROUP (ORDER BY grade) AS q3
	FROM 
		student_grades
)
SELECT 
	student_name,
	grade,
	CASE
		WHEN grade <= (SELECT q1 FROM quartiles) THEN '1st quartile'
		WHEN grade <= (SELECT q2 FROM quartiles) THEN '2nd quartile'
		WHEN grade <= (SELECT q3 FROM quartiles) THEN '3rd quartile'
		ELSE '4th quartile'
	END AS quartile_label
FROM 
	student_grades
ORDER BY student_name;

## database setup

CREATE TABLE student_grades (
	student_id INT PRIMARY KEY,
	student_name VARCHAR(50),
	grade INT
);

INSERT INTO student_grades (student_id, student_name, grade) VALUES
(1, 'Aisha', 85),
(2, 'Carlos', 92),
(3, 'Wei', 78),
(4, 'David', 88),
(5, 'Fatima', 95),
(6, 'Hiroshi', 82),
(7, 'Grace', 75),
(8, 'Sofia', 90),
(9, 'Ivy', 87),
(10, 'Liam', 80);

SELECT 
	student_id,
	student_name,
	grade
FROM student_grades;

## Mark your feedback at the Following Contact Points
- **LinkedIn:** <https://www.linkedin.com/in/rishirajopenminds>
- **GitHub:** <https://github.com/rishiraj88>

## Credits and Gratitude
- Thank all who have mentored, taught and guided. Also, always appreciate who have supported with pair programming and more.