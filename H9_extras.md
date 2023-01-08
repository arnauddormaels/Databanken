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
delimiter 
CREATE TRIGGER upd_check BEFORE UPDATE ON products
FOR EACH ROW 
BEGIN 
  IF NEW.prijs < 0 THEN
    SET NEW.prijs = 0;
  ELSEIF NEW.prijs > 100 THEN 
    SET NET.prijs = 100;
  END IF;
END;
delimeter;

```

## Stored procedures en functions 
Een stored procedure is een stukkje code dat je op een andere plaats kan aanroepen.
```sql
delimeter 
CREATE PROCEDURE productenPerLeverancier (IN leverancier_id INT, OUT aantal_productenPerLeverancier INT)
BEGIN
SELECT COUNT(*) INTO aantal_productenPerLeverancier 
FROM producten 
GROUP BY leverancier_id
END 
delimiter;
```

Call van een stored procedure 
```sql
productenPerLeverancier(5, @aantal);
