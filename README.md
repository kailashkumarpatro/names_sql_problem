# names_sql_problem

sql interview questions
we will discuss a famous sql interview proble where we need to segregare fist_name,middle_name and last_name from the customer_table 

Scirpts
create table customers1  (customer_name varchar(30))
insert into customers1 values ('Ankit Bansal')
,('Vishal Pratap Singh')
,('Michael'); 


		   with cte as (
		   select customer_name, len(customer_name) -len(replace(customer_name,' ','')) as no_of_spaces,
		                         charindex(' ',customer_name) as first_space, 
								 charindex(' ',customer_name,charindex(' ',customer_name)+1) as second_space from customers123) 

								 select *, case when no_of_spaces = 0 then customer_name else SUBSTRING(customer_name,1,first_space) 
								 end as fisrt_name,
								 case when no_of_spaces <= 1  then null  else substring(customer_name,first_space,second_space-first_space) end as 
							
								 middle_name ,
								 case when no_of_spaces = 0 then null 
								when no_of_spaces = 1 then SUBSTRING(customer_name,first_space+1,len(customer_name)-second_space)
								when no_of_spaces = 2 then substring(customer_name,second_space+1,len(customer_name))end as last_name from cte 
