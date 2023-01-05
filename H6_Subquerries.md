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
Hierbij gaat de subquerrie meerdere resultaten teruggeven dus moeten we IN gebruiken ipv "="  
```sql
NOT IN 
``` kan ook gebruikt worden voor het omgekeerde effect te verkrijgen van IN
