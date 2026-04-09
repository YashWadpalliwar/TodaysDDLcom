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





 
 
 
