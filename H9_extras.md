## indexen
Indexen helpen bij het zoeken van data.
### Index aanmaken
```sql 
CREATE INDEX id ON products(product_id);
```
### indexen tonen
```sql
SHOW INDEXES FROM products;
```
### Indexen verwijderen
```sql
DROP INDEX id ON products
```

## transacties 
Transacties gaan de data willen aanpassen en gaan de data dat ze willen bewerken blokkeren voor andere gebruikers en sessies. Deze zullen enkel de data kunnen uitlezen van voor de transactie is begonnen. Indien de transactie dan een fout zou geven dat de andere gebruikers een juiste value waarde.  
In de transactie zijn de wijzigingen uiteraard wel zichtbaar.
```sql 
START TRANSACTION;
...
ROLLBACK/COMMIT; 
```
## Data importeren 
```sql
LOAD DATA INFILE 'c:/tmp/discounts.csv'
INFTO TABLE discounts 
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\n'
IGNORE 1 ROWS;

```
## Triggers
```sql 


```
