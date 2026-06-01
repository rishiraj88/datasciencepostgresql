# To Create a Moving Window Frame
A windows frame is useful in order to calculate:
- moving average (mean)
- moving sum (total)
over a number of data samples. There are various selection strategies to describe the sample partitions of dataset (rows), with the help of notations such as:
- preceeding rows,
- following rows,
- current row.

## query for moving average and moving total
SELECT
	visit_date,
	daily_visits,
	ROUND(AVG(daily_visits) OVER (ORDER BY visit_date ROWS BETWEEN 2 PRECEDING AND 2 FOLLOWING)) AS moving_avg_5_days,
	MAX(daily_visits) OVER (ORDER BY visit_date ROWS BETWEEN 6 PRECEDING AND CURRENT ROW) AS moving_max_7_days,
	SUM(daily_visits) OVER (PARTITION BY extract(year FROM visit_date), extract(month FROM visit_date) ORDER BY visit_date ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS total_monthly_visits
FROM
	website_traffic
ORDER BY
	visit_date;

## database setup

CREATE TABLE website_traffic (
	visit_date DATE PRIMARY KEY,
	daily_visits INT
);

INSERT INTO website_traffic (visit_date, daily_visits) VALUES
('2023-01-01', 150),
('2023-01-02', 180),
('2023-01-03', 120),
('2023-01-04', 200),
('2023-01-05', 170),
('2023-01-06', 220),
('2023-01-07', 140),
('2023-01-08', 210),
('2023-01-09', 160),
('2023-01-10', 230),
('2023-01-11', 190),
('2023-01-12', 250),
('2023-01-13', 180),
('2023-01-14', 220),
('2023-01-15', 160),
('2023-01-16', 240),
('2023-01-17', 170),
('2023-01-18', 260),
('2023-01-19', 150),
('2023-01-20', 210),
('2023-01-21', 190),
('2023-01-22', 230),
('2023-01-23', 170),
('2023-01-24', 250),
('2023-01-25', 160),
('2023-01-26', 240),
('2023-01-27', 200),
('2023-01-28', 220),
('2023-01-29', 180),
('2023-01-30', 210),
('2023-01-31', 190);

INSERT INTO website_traffic (visit_date, daily_visits) VALUES
('2023-02-01', 230),
('2023-02-02', 180),
('2023-02-03', 210),
('2023-02-04', 160),
('2023-02-05', 250),
('2023-02-06', 200),
('2023-02-07', 220);

SELECT
	visit_date,
	daily_visits,
FROM
	website_traffic;

## Mark your feedback at the Following Contact Points
- **LinkedIn:** <https://www.linkedin.com/in/rishirajopenminds>
- **GitHub:** <https://github.com/rishiraj88>

## Credits and Gratitude
- Thank all who have mentored, taught and guided. Also, always appreciate who have supported with pair programming and more.