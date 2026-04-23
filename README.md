select * from employeesdata;
use largedata1;

update employeesdata set salary = 80000 where id = 8;

update employeesdata set name = "Yash" where id = 3;

update employeesdata set age = 16, experience = 1, salary = 9000 where id = 4;

UPDATE employeesdata
SET age = CASE
    WHEN id = 1 THEN 21
    WHEN id = 2 THEN 22
    WHEN id = 3 THEN 23
END
WHERE id IN (1, 2, 3);

update employeesdata set
experience = case 
when id = 16 then 1
when id = 17 then 2
when id = 18 then 3
when id = 19 then 4
end 
where id in (16,17,18,19);


select * from employeesdata;

select name,salary,department from employeesdata;

select id,name,salary from employeesdata limit 10;

select * from employeesdata limit 5 offset 25;

select distinct gender from employeesdata;

select * from employeesdata where salary > 80000;

select * from employeesdata where gender = "male";

select * from employeesdata where department = "Data analysis";

select * from employeesdata where salary > 80000 or gender = "others";

select 50 * 50;

select 600 > 90;

select * from employeesdata where not experience = 1;

select * from employeesdata where gender in ("other","male") order by salary desc;


------------------------------------------------------------------------------------
use largedata1;

select * from employeesdata;

select * from employeesdata where id like '%1';

select sum(salary) as result from employeesdata;

select avg(salary) as avg from employeesdata;

select max(salary) as avg from employeesdata;

select count(id) as Count_rows, sum(salary) as Total_Sum, avg(salary) as avg_total,
	min(salary) as min_value, max(salary) from employeesdata;

SELECT DATE_FORMAT(CURRENT_DATE(), '%d %M %Y') AS mydate; 

SELECT DATE_FORMAT(NOW(), '%d %M %Y') AS mydate1;

SELECT DATE_FORMAT('2024-12-12', '%d %M %Y') AS mydate;

SELECT STR_TO_DATE('12-12-2024', '%d-%m-%Y') AS mydate;

select * from employeesdata;

select name, salary, experience from employeesdata order by name limit 5;

select distinct gender from employeesdata order by gender;


-- Total experience for each department
SELECT department, sum(experience) as total
FROM employeesdata GROUP BY department;


-- Maximum salary in each gender
SELECT gender, MAX(salary) AS max_salary
FROM employeesdata
GROUP BY gender;

-- Minimum age in each department
SELECT department, MIN(age) AS min_age
FROM employeesdata
GROUP BY department;

-- Number of employees earning above 60,000 (by gender)
SELECT gender, COUNT(*) AS employee_count
FROM employeesdata
WHERE salary > 60000
GROUP BY gender;


-- Department where MIN salary > 70,000
SELECT department, MIN(salary) AS min_salary
FROM employeesdata GROUP BY department
HAVING MIN(salary) > 70000;

-- Gender where MAX salary > 80,000
SELECT gender, MAX(salary) AS max_salary
FROM employeesdata GROUP BY gender
HAVING MAX(salary) > 80000;

-- Department where AVG salary > 60,000
SELECT department, AVG(salary) AS avg_salary
FROM employeesdata
GROUP BY department
HAVING AVG(salary) > 60000;

-- Gender where TOTAL salary > 70,000
SELECT gender, SUM(salary) AS total_salary
FROM employeesdata
GROUP BY gender
HAVING SUM(salary) > 70000;

-----------------------------------------------------------------------------------------
Joins and if stements
use joins;

select * from user1
left join user2 on
user1.id = user2.srno
union
select * from user1
right join user2 on
user1.id = user2.srno;

select * from cross1 cross join cross2 order by employeeid;

-- SELECT * FROM table_name1 as a JOIN table_name1 as b ON a.id = b.productid;

select * from self as a join self as b on a.id = b.productid;

select * from natural1 natural join natural2;

select * from union_students_2023
union all
select * from union2_students_2024;

use largedata1;
select * from employeesdata where salary > 100000;

select name,age,experience,salary,department,
if(salary > 80000 and experience > 8, "Leave", "Not Leave", "Leave", "Not Leave") as result, 
as result2 from employeesdata;

-----------------------------------------------------------------------------


use analyticfun;

select * from percent_cume;

select *, cume_dist() over(order by sales) as Result from percent_cume;

select * from value_function;

select *, last_value(salary) over(order by salary) as result from value_function;

SELECT *, LAST_VALUE(salary) OVER(ORDER BY salary
ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS 
Highest_Salary FROM value_function;

select *, nth_value(salary,2) over(order by salary) as result
 from value_function;

-- SecondHight_Salary Interview Ques

SELECT salary FROM (
    SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS `DR`
    FROM value_function) AS second_highest
WHERE DR = 2;


select *,day(salary_date) from extract_table;

SELECT EXTRACT(YEAR FROM '2024-12-21') AS year;
SELECT EXTRACT(MONTH FROM '2024-12-21') AS month;
SELECT EXTRACT(DAY FROM '2024-12-21') AS day;
SELECT EXTRACT(HOUR FROM '2024-12-21 15:45:00') AS hour;
SELECT EXTRACT(MINUTE FROM '2024-12-21 11:45:30') AS minute;
SELECT EXTRACT(SECOND FROM '2024-12-21 10:45:50') AS second;

select * from string_functions;

SHOW FULL TABLES WHERE table_type = 'VIEW';      


use largedata1;

create view onlymale as
	select name,salary,gender from employeesdata where gender = "male" ;

select * from onlymale;

create view Experienced_Employees as
 select name,experience from employeesdata where experience > 5;
 
 select * from Experienced_Employees;
 
 create view Management_Employees as
  select name,experience , salary from employeesdata where experience between 5 and 10;
  
  select * from Management_Employees;
  
  use joins;
  
  select * from employeesdata;

drop view Management_Employees;


select * from user2;
create view skills1 as 
select * from user1 
inner join user2 on user1.id = user2.srno;
select * from skills1;
 
 
 
