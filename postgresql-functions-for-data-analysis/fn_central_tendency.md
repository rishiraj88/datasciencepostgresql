# to find the central tendency of a dataset
Out of numerous statistical measures, the measures of central tendency are especially interesting. Postgres offers the following popular functions for the purpose:
- COUNT()
- ROUND()
- PERCENTILE_CONT()
- MODE()

## query to calculate statistics over data
SELECT 
	species_name,
	count(*) as core_count,
	ROUND(AVG(age), 2) AS mean_age,
	PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY age) AS median_age,
	MODE() WITHIN GROUP (ORDER BY age) AS mode_age
FROM 
	tree_core
GROUP BY 
	species_name;

## database setup

CREATE TABLE tree_core (
	core_id CHAR(6) PRIMARY KEY,
	species_name VARCHAR(50),
	age INT
);

INSERT INTO tree_core (core_id, species_name, age) VALUES
('A1B2C3', 'Oak', 67),
('D4E5F6', 'Pine', 29),
('G7H8I9', 'Maple', 18),
('U3V4W5', 'Maple', 110),
('X6Y7Z8', 'Maple', 105),
('C3D4E5', 'Maple', 8),
('A9B0C1', 'Oak', 70),
('T4U5V6', 'Maple', 5),
('J0K1L2', 'Oak', 71),
('M3N4O5', 'Pine', 30),
('P6Q7R8', 'Maple', 20),
('S9T0U1', 'Oak', 72),
('V2W3X4', 'Pine', 31),
('W7X8Y9', 'Maple', 6),
('Y5Z6A7', 'Maple', 19),
('B8C9D0', 'Oak', 69),
('E1F2G3', 'Pine', 28),
('H4I5J6', 'Maple', 21),
('K7L8M9', 'Oak', 70),
('H2I3J4', 'Maple', 110),
('K5L6M7', 'Oak', 68),
('N8O9P0', 'Pine', 30),
('Q1R2S3', 'Maple', 105),
('N0O1P2', 'Pine', 30),
('Q3R4S5', 'Maple', 20),
('T6U7V8', 'Oak', 71),
('D2E3F4', 'Pine', 30),
('G5H6I7', 'Maple', 115),
('J8K9L0', 'Oak', 55),
('M1N2O3', 'Pine', 31),
('Z0A1B2', 'Maple', 7),
('W9X0Y1', 'Pine', 32),
('F6G7H8', 'Maple', 10),
('Z2A3B4', 'Maple', 19),
('C5D6E7', 'Oak', 63),
('F8G9H0', 'Pine', 30),
('I1J2K3', 'Oak', 70),
('L4M5N6', 'Oak', 65),
('O7P8Q9', 'Pine', 31),
('R0S1T2', 'Pine', 29),
('P4Q5R6', 'Maple', 100),
('S7T8U9', 'Oak', 70),
('V0W1X2', 'Pine', 30),
('Y3Z4A5', 'Maple', 120),
('B6C7D8', 'Oak', 72),
('E9F0G1', 'Pine', 30);

SELECT 
	core_id,
	species_name,
	age
FROM 
	tree_core

## Mark your feedback at the Following Contact Points
- **LinkedIn:** <https://www.linkedin.com/in/rishirajopenminds>
- **GitHub:** <https://github.com/rishiraj88>

## Credits and Gratitude
- Thank all who have mentored, taught and guided. Also, always appreciate who have supported with pair programming and more.