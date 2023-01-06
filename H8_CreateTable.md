## Table aanmaken
```sql
CREATE TABLE producten (
id int PRIMARY KEY ATUO_INCREMENT, 
QR_code CHAR(10) NOT NULL,
naam VARCHAR(20) DEFAULT 'new',
prijs DECIMAL(5,2) DEFAULT 0,
created_on DATETIME DEFAULT now(),
FOREIGN KEY (leverancier_id) REFERENCES leveranciers(id)

```

## Data toevoegen
```sql
INSERT INTO producten(id,QR_code,naam) VALUES 
('123', '6785123543', 'Chocolat'),
('456', '4568798458', 'Coca');

```
## CHAR(size) 
size -> vast aantal karakters.

## VARCHAR(size)
size -> maximum aantal karakters


## FLOAT/DOUBLE
32/64bit komma getal.
Nooit gerbuiken voor financiële waarden


## DECIMAL
DECIMAL(p,s)
p -> Aantal bits dat gebruikt moeten gereserveerd worden voor het getal.
s -> Aantal cijfers achter de komma

## DATE
enkel datum

## TIME
enkel tijd

## DATETIME 
datum en tijd


