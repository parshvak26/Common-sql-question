# Common-sql-question

select product_id from products
where low_fats ='Y' and recyclable ='Y';

-----------------------------------------------------------------------

select name from customer 
where referee_id != 2 or referee_id is null;

------------------------------------------------------------------------

select name, population, area from world
where area >= 3000000 or population >=25000000;

------------------------------------------------------------------------

select distinct author_id as id from views
where author_id = viewer_id
order by id;

-------------------------------------------------------------------------

select tweet_id from tweets
where length(content) >15;

-------------------------------------------------------------------------

select u.unique_id, e.name from employees as e
left join employeeUNI as u on e.id = u.id

-------------------------------------------------------------------------

SELECT v.customer_id, COUNT(v.visit_id) AS count_no_trans 
from Visits v 
LEFT JOIN Transactions t 
ON v.visit_id = t.visit_id  
WHERE t.transaction_id IS NULL 
GROUP BY v.customer_id; 

-------------------------------------------------------------------------

Select s.machine_id, 
        round(avg(e.timestamp-s.timestamp), 3) as processing_time
from Activity s 
join Activity e
on s.machine_id = e.machine_id 
and s.process_id = e.process_id
and s.activity_type = 'start' 
and e.activity_type = 'end'
group by s.machine_id;

-------------------------------------------------------------------------

select w1.id from weather as w1, weather as w2
where datediff(w1.recorddate, w2.recorddate) = 1 and w1.temperature > w2.temperature

-----------------------------------------------------------------------------------

SELECT v.customer_id, COUNT(v.visit_id) AS count_no_trans 
from Visits v 
LEFT JOIN Transactions t 
ON v.visit_id = t.visit_id  
WHERE t.transaction_id IS NULL 
GROUP BY v.customer_id; 

-----------------------------------------------------------------------------------

select c.name from (select a.name, count(a.id) countname from employee as a left join employee as b on a.id = b.managerid group by a.name) as c where c.countname >=5

----------------------------------------------------------------------------------------------------------------------------------------------

select p.product_name, s.year, s.price from sales as s
join product as p on p.product_id = s.product_id

--------------------------------------------------------------------------------------

select u.unique_id, e.name from employees as e
left join employeeUNI as u on e.id = u.id 
----------------------------------------------------------------------------------------

# Write your MySQL query statement below
select e.name, b.bonus from employee e
left join bonus b on e.empid = b.empid
where b.bonus <1000 or b.bonus is null;

----------------------------------------------------------------------------------------

select s.student_id, s.student_name, su.subject_name, count(e.subject_name) as attended_exams from students as s 
cross join subjects as su
left join examinations as e on e.student_id = s.student_id and  su.subject_name = e.subject_name
group by s.student_id, e.subject_name, su.subject_name
order by s.student_id, su.subject_name

----------------------------------------------------------------------------------------------

select s.user_id, round(avg(case when c.action ='confirmed' then 1.00 else 0.00 end), 2) as confirmation_rate
from signups as s
left join confirmations c on s.user_id = c.user_id 
group by s.user_id

----------------------------------------------------------------------------------------------

select * from cinema 
where id %2 != 0 and description != 'boring'
order by rating desc

----------------------------------------------------------------------------------------------------

select p.product_id, round(sum(u.units*p.price) / sum(u.units), 2) as average_price from prices p
join unitssold u on u.product_id = p.product_id and u.purchase_date between p.start_date and p.end_date
group by p.product_id

-----------------------------------------------------------------------------------------------------------

select p.project_id, round( avg(e.experience_years) ,2) as average_years from project p
join employee e on p.employee_id = e.employee_id
group by project_id

-----------------------------------------------------------------------------------------------------------

select contest_id, round( count(distinct user_id ) *100 / (select count(user_id) from users) ,2) as percentage from register
group by contest_id
order by percentage desc, contest_id

-------------------------------------------------------------------------------------------------------------


SELECT
  DATE_FORMAT(trans_date, '%Y-%m') AS month,
  country,
  COUNT(*) AS trans_count,
  SUM(IF(state = 'approved', 1, 0)) AS approved_count,
  SUM(amount) AS trans_total_amount,
  SUM(IF(state = 'approved', amount, 0)) AS approved_total_amount
FROM Transactions
GROUP BY DATE_FORMAT(trans_date, '%Y-%m'), country;

------------------------------------------------------------------------------------------------------------------------------
