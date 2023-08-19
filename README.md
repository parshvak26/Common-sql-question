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
