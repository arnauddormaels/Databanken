# Subquerries


## 3 soorten subquerries  
--Nested subquerrie -> subquery in de WHERE of HAVING  clause
--Inline subquerrie -> Subquerrie in de FROM clause
--Scalar subquerrie -> Subquerrie in de Select klasse

## Subquerries met 1 of meerdere resultaten
```sql 
SELECT * 
FROM producten
WHERE leverancierId = (SELECT naam FROM leveranciers = "Bart en GO) 
``` 
Het resultaat van bovenstaande subquerry is 1 resultaat dus dit gaat werken maar als we meerdere resultaten zouden hebben gaat = niet werken hiervoor gebruiken we IN
```sql 
SELECT * 
FROM producten
WHERE leverancierId IN (SELECT naam FROM leveranciers WHERE naam = "B*") 
``` 
Hierbij gaat de subquerrie meerdere resultaten teruggeven dus moeten we IN gebruiken ipv "=".    
```sql
SELECT * 
FROM producten
WHERE leverancierId NOT IN (SELECT naam FROM leveranciers WHERE naam = "B*") 
```
kan ook gebruikt worden voor het omgekeerde effect te verkrijgen van IN.  
``!`` Er mag maar in kolom geselecteerd worden in de subquerry

## ALL, ANY en SOM
In de where clause kan er ook gebruikt worden van <,<=,<>,>=,>.  
Deze kunnen enkel gebruikt worden als de subquerry 1 resultaat returned.  
Maar je kan ook gebruik maken van ALL, ANY en SOM in combinatie met bovenstaande operatoren.  
``All`` -> Tonen waneer de waarde groter is dan **ELKE** waarde in de subquerry.  
``ANY`` (``SOME``) -> Tonen waneer de waarde groter is dan **één** waarde in subquerry.  
```sql
select LAST_NAME, FIRST_NAME, DEPARTMENT_ID, SALARY 
from employees
where SALARY   >  ALL  (   select SALARY
		from employees 
		where DEPARTMENT_ID = 80 )  ;
```
  
    
## EXISTS And NOT EXISTS

```sql
select *
from departments
where EXISTS     ( SELECT *
		from employees
                		where salary > 11000 	
		    and employees.department_id = departments.department_id )  ;
```
