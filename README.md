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

select p.product_name, s.year, s.price from sales as s
join product as p on p.product_id = s.product_id

--------------------------------------------------------------------------------------
