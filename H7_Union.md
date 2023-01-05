# Union 
Union gaat alle elementen van beide querries tonen, maar gaat geen dubbels bewaren  
```sql
SELECT first_name, last_name, department_id, job_id
FROM employees
WHERE department_id = 80 

UNION

SELECT first_name, last_name, department_id, job_id
FROM employees
WHERE job_id LIKE '%rep'  ;    
```
# Union all
gaat alles van beide querries tonen, ook dubbels
```sql
SELECT first_name, last_name, department_id, job_id
FROM employees
WHERE department_id = 80 

UNION ALL

SELECT first_name, last_name, department_id, job_id
FROM employees
WHERE job_id LIKE '%rep'  ;    
```
