# DML :- Inserting,deleting,updateing
# DQL :- 
# Agg :- 
# clouse :- 

create database Practice;

use Practice;

select * from employeesdata;

delete from employeesdata where nmae = 10;
SET SQL_SAFE_UPDATES = 0;

update employeesdata set salary = 80000 where id = 9;

update employeesdata set name = "Yash" where id = 3;

update employeesdata set name = "Ankit",age = 20, department = "Web design" 
	where id = 27;

UPDATE employeesdata
SET salary = CASE
	WHEN salary = 50000 THEN 70000
    WHEN salary = 5000 THEN 80000
    WHEN salary = 60000 THEN 90000
END
WHERE salary IN (50000, 5000, 60000);

select * from employeesdata;

select name,experience,salary from employeesdata limit 5;

select count(id) from employeesdata limit 5 offset 9;

select distinct department from employeesdata;

select * from employeesdata where experience >= 20 or gender = "female";

select * from employeesdata where not gender = "male";

select * from employeesdata where gender not in ("male", "other");

select * from employeesdata where salary between 5000 and 10000;

select * from employeesdata where name like 'Y%';

-- Aggregate functions in SQL perform calculations on a set of values and return a single result.

-- 	COUNT(): Counts the number of rows.
-- 	SUM(): Calculates the total sum of a numeric column.
-- 	AVG(): Computes the average of a numeric column.
-- 	MIN(): Finds the minimum value in a column.
-- 	MAX(): Finds the maximum value in a column.

select min(salary) as min_salary from employeesdata;


SELECT DATE_FORMAT(CURRENT_DATE(), '%d %m %y') AS mydate;

SELECT DATE_FORMAT(NOW(), '%d %M %Y') AS mydate;

SELECT DATE_FORMAT('2024-12-12', '%d %M %Y') AS mydate;

SELECT STR_TO_DATE('12-12-2024', '%d-%m-%Y') AS mydate;


select * from employeesdata;

select name,experience,salary,department from employeesdata order by experience;

select distinct gender from employeesdata order by gender;

select gender,count(gender) from employeesdata group by gender;

-- Total experience for each department?

select department, max(experience) from employeesdata group by department;


-- Maximum salary in each gender?

select gender, max(salary) as max_sal from employeesdata group by gender order by max_sal;

-- Minimum age in each department?



-- Find Department Where the Minimum Salary is Greater Than 70,000 using having.

select department,min(salary) from employeesdata group by department having min(salary) >= 70000;

-- Find Genders Where the Total Salary is Greater Than 70,000 using having.

select gender,sum(salary) from employeesdata group by gender having sum(salary) > 70000;


