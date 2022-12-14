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

## CONSTRAINTS
constraints zijn regels dat we toevoegen aan de databank op table niveau. Tot nu waren we enkel nog maar gewoon om regels toe te voegen op column niveau. Zoals in het bovenste script. Nu gaan we de PRIMARY KEYS ergens anders definieëen.  
De meest gebruikte constraints zijn NOT NULL, PRIMARY KEY, FOREIGN KEY, UNIQUE en CHECK().  
**Not null kan niet gebruikt worden op column niveau.

```sql 
CREATE TABLE products (
id INT,
naam VARCHAR(50),
leveranciers_id INT,
CONSTRAINT boeken_pk PRIMARY KEY (id),
CONSTRAINT naam CHECK (length(naam) > 4),
FOREIGN KEY (leveranciers_id) REFERENCES leveranciers(id) 
);
```
Dankzij de constraints op Table niveau kan er nu niemand meer zomaar de FK van leveranciers verwijderen. 
als je deze wilt verwijderen zonder een:  
``ON DELETE`` -> Geef een error, Constraint violated error.  
``ON DELETE SET NULL`` -> dan krijgt leveranciers_id van products een NULL waarde.  
``ON DELETE CASCADE ``-> dan worden de bijberhorende producten ook verwijderd.  

## Handige commands 
Toont hoe de table opgebouwt is, met constraints
```sql 
SHOW CREATE TABLE producten
```
Toon de bestaande indexen (zoekbomen)
```sql 
SHOW INDEXES FROM producten
```
Maakt een kopie van de tabel met de data. Zonder de constraints.
```sql 
CREATE TABLE producten as (
SELECT * 
FROM producten_BackUp 
```

