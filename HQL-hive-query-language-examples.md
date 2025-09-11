
# Hive SQL Examples

### **Q1. Sample Data Load**

```sql

CREATE DATABASE learning;
USE learning;
SET hive.cli.print.current.db = true;
SET hive.cli.print.header = true;

CREATE TABLE `customers` (  
  `customerNumber` int,  
  `customerName` varchar(50),  
  `contactLastName` varchar(50),  
  `contactFirstName` varchar(50),  
  `phone` varchar(50),  
  `addressLine1` varchar(50),  
  `addressLine2` varchar(50),  
  `city` varchar(50),  
  `state` varchar(50),  
  `postalCode` varchar(15),  
  `country` varchar(50),  
  `salesRepEmployeeNumber` int,  
  `creditLimit` decimal(10,2)  
) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',';
```

```sql
-- Insert sample data
insert  into `customers` values (103,'Atelier graphique','Schmitt','Carine ','40.32.2555','54, rue   fàcRoyale',NULL,'Nantes',NULL,'44000','France',1370,'21000.00'),(112,'Signal Gift Stores','King','Jean','7025551838','8489 Strong St.',NULL,'Las Vegas','NV','83030','USA',1166,'71800.00'),(114,'Australian Collectors, Co.','Ferguson','Peter','03 9520 4555','636 St Kilda Road','Level 3','Melbourne','Victoria','3004','Australia',1611,'117300.00'),(119,'La Rochelle Gifts','Labrune','Janine ','40.67.8555','67, rue des Cinquante Otages',NULL,'Nantes',NULL,'44000','Frace',1370,'118200.00'),(121,'Baane Mini Imports','Bergulfsen','Jonas ','07-98 9555','Erling Skakkes gate 78',NULL,'Stavern',NULL,'4110','Norway',1504,'81700.00'),(124,'Mini Gifts Distributors Ltd.','Nelson','Susan','4155551450','5677 Strong St.',NULL,'San Rafael','CA','97562','USA',1165,'210500.00'),(125,'Havel & Zbyszek Co','Piestrzeniewicz','Zbyszek ','(26) 642-7555','ul. Filtrowa 68',NULL,'Warszawa',NULL,'01-012','Poland',NULL,'0.00'),(128,'Blauer See Auto, Co.','Keitel','Roland','+49 69 66 90 2555','Lyonerstr. 34',NULL,'Frankfurt',NULL,'60528','Germany',1504,'59700.00'),(129,'Mini Wheels Co.','Murphy','Julie','6505555787','5557 North Pendale Street',NULL,'San Francisco','CA','94217','USA',1165,'64600.00'),(131,'Land of Toys Inc.','Lee','Kwai','2125557818','897 Long Airport Avenue',NULL,'NYC','NY','10022','USA',1323,'114900.00'),(141,'Euro+ Shopping Channel','Freyre','Diego ','(91) 555 94 44','C/ Moralzarzal, 86',NULL,'Madrid',NULL,'28034','Spain',1370,'227600.00'),(144,'Volvo Model Replicas, Co','Berglund','Christina ','0921-12 3555','Berguvsvägen  8',NULL,'Luleå',NULL,'S-958 22','Sweden',1504,'53100.00'),(145,'Danish Wholesale Imports','Petersen','Jytte ','31 12 3555','Vinbæltet 34',NULL,'Kobenhavn',NULL,'1734','Denmark',1401,'83400.00'),(146,'Saveley & Henriot, Co.','Saveley','Mary ','78.32.5555','2, rue du Commerce',NULL,'Lyon',NULL,'69004','France',1337,'123900.00'),(148,'Dragon Souveniers, Ltd.','Natividad','Eric','+65 221 7555','Bronz Sok.','Bronz Apt. 3/6 Tesvikiye','Singapore',NULL,'079903','Singapore',1621,'103800.00'),(151,'Muscle Machine Inc','Young','Jeff','2125557413','4092 Furth Circle','Suite 400','NYC','NY','10022','USA',1286,'138500.00'),(157,'Diecast Classics Inc.','Leong','Kelvin','2155551555','7586 Pomptont.',NULL,'Allentown','PA','70267','USA',1216,'100600.00'),(161,'Technics Stores Inc.','Hashimoto','Juri','6505556809','9408 Furth Circle',NULL,'Burlingame','CA','94217','USA',1165,'84600.00'),(166,'Handji Gifts& Co','Victorino','Wendy','+65 224 1555','106 Linden Road Sandown','2nd Floor','Singapore',NULL,'069045','Singapore',1612,'97900.00'),(167,'Herkku Gifts','Oeztan','Veysel','+47 2267 3215','Brehmen St. 121','PR 334 Sentrum','Bergen',NULL,'N 5804','Norway  ',1504,'96800.00'),(168,'American Souvenirs Inc','Franco','Keith','2035557845','149 Spinnaker Dr.','Suite 101','New Haven','CT','97823','USA',1286,'0.00'),(169,'Porto Imports Co.','de Castro','Isabel ','(1) 356-5555','Estrada da saúde n. 58',NULL,'Lisboa',NULL,'1756','Portugal',NULL,'0.00'),(171,'Daedalus Designs Imports','Rancé','Martine ','20.16.1555','184, chaussée de Tournai',NULL,'Lille',NULL,'59000','France',1370,'82900.00'),(172,'La Corne D\'abondance, Co.','Bertrand','Marie','(1) 42.34.2555','265, boulevard Charonne',NULL,'Paris',NULL,'75012','France',1337,'84300.00'),(173,'Cambridge Collectables Co.','Tseng','Jerry','6175555555','4658 Baden Av.',NULL,'Cambridge','MA','51247','USA',1188,'43400.00'),(175,'Gift Depot Inc.','King','Julie','2035552570','25593 South Bay Ln.',NULL,'Bridgewater','CT','97562','USA',1323,'84300.00'),(177,'Osaka Souveniers Co.','Kentary','Mory','+81 06 6342 5555','1-6-20 Dojima',NULL,'Kita-ku','Osaka',' 530-0003','Japan',1621,'81200.00'),(181,'Vitachrome Inc.','Frick','Michael','2125551500','2678 Kingston Rd.','Suite 101','NYC','NY','10022','USA',1286,'76400.00'),(186,'Toys of Finland, Co.','Karttunen','Matti','90-224 8555','Keskuskatu 45',NULL,'Helsinki',NULL,'21240','Finland',1501,'96500.00'),(187,'AV Stores, Co.','Ashworth','Rachel','(171) 555-1555','Fauntleroy Circus',NULL,'Manchester',NULL,'EC2 5NT','UK',1501,'136800.00'); 

```

```sql
CREATE TABLE `payments` (  
  `customerNumber` int,  
  `checkNumber` varchar(50),  
  `paymentDate` date,  
  `amount` decimal(10,2)  
) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',';
```

```sql
-- Insert sample data

insert  into `payments` values (103,'HQ336336','2016-10-19','6066.78'),(103,'JM555205','2016-10-05','14571.44'),(103,'OM314933','2016-10-18','1676.14'),(112,'BO864823','2016-10-17','14191.12'),(112,'HQ55022','2016-10-06','32641.98'),(112,'ND748579','2016-10-20','33347.88'),(114,'GG31455','2016-10-20','45864.03'),(114,'MA765515','2016-10-15','82261.22'),(114,'NP603840','2016-10-31','7565.08'),(114,'NR27552','2016-10-10','44894.74'),(119,'DB933704','2016-10-14','19501.82'),(119,'LN373447','2016-10-08','47924.19'),(119,'NG94694','2016-10-22','49523.67'),(121,'DB889831','2016-10-16','50218.95'),(121,'FD317790','2016-10-28','1491.38'),(121,'KI831359','2016-10-04','17876.32'),(121,'MA302151','2016-10-28','34638.14'),(124,'AE215433','2016-10-05','101244.59'),(124,'BG255406','2016-10-28','85410.87'),(124,'CQ287967','2016-10-11','11044.30'),(124,'ET64396','2016-10-16','83598.04'),(124,'HI366474','2016-10-27','47142.70'),(124,'HR86578','2016-10-02','55639.66'),(124,'KI131716','2016-10-15','111654.40'),(124,'LF217299','2016-10-26','43369.30'),(124,'NT141748','2016-10-25','45084.38'),(128,'DI925118','2016-10-28','10549.01'),(128,'FA465482','2016-10-18','24101.81'),(128,'FH668230','2016-10-24','33820.62'),(128,'IP383901','2016-10-18','7466.32'),(129,'DM826140','2016-10-08','26248.78'),(129,'ID449593','2016-10-11','23923.93'),(129,'PI42991','2016-10-09','16537.85'),(131,'CL442705','2016-10-12','22292.62'),(131,'MA724562','2016-10-02','50025.35'),(131,'NB445135','2016-10-11','35321.97'),(141,'AU364101','2016-10-19','36251.03'),(141,'DB583216','2016-10-01','36140.38'),(141,'DL460618','2016-10-19','46895.48'),(141,'HJ32686','2016-10-30','59830.55'),(141,'ID10962','2016-10-31','116208.40'),(141,'IN446258','2016-10-25','65071.26'),(141,'JE105477','2016-10-18','120166.58'),(141,'JN355280','2016-10-26','49539.37'),(141,'JN722010','2016-10-25','40206.20'),(141,'KT52578','2016-10-09','63843.55'),(141,'MC46946','2016-10-09','35420.74'),(141,'MF629602','2016-10-16','20009.53'),(141,'NU627706','2016-10-17','26155.91'),(144,'IR846303','2016-10-12','36005.71'),(144,'LA685678','2016-10-09','7674.94'),(145,'CN328545','2016-10-03','4710.73'),(145,'ED39322','2016-10-26','28211.70'),(145,'HR182688','2016-10-01','20564.86'),(145,'JJ246391','2016-10-20','53959.21'),(146,'FP549817','2016-10-18','40978.53'),(146,'FU793410','2016-10-16','49614.72'),(146,'LJ160635','2016-10-10','39712.10'),(148,'BI507030','2016-10-22','44380.15'),(148,'DD635282','2016-10-11','2611.84'),(148,'KM172879','2016-10-26','105743.00'),(148,'ME497970','2016-10-27','3516.04'),(151,'BF686658','2016-10-22','58793.53'),(151,'GB852215','2016-10-26','20314.44'),(151,'IP568906','2016-10-18','58841.35'),(151,'KI884577','2016-10-14','39964.63'),(157,'HI618861','2016-10-19','35152.12'),(157,'NN711988','2016-10-07','63357.13'),(161,'BR352384','2016-10-14','2434.25'),(161,'BR478494','2016-10-18','50743.65'),(161,'KG644125','2016-10-02','12692.19'),(161,'NI908214','2016-10-05','38675.13'),(166,'BQ327613','2016-10-16','38785.48'),(166,'DC979307','2016-10-07','44160.92'),(166,'LA318629','2016-10-28','22474.17'),(167,'ED743615','2016-10-19','12538.01'),(167,'GN228846','2016-10-03','85024.46'),(171,'GB878038','2016-10-15','18997.89'),(171,'IL104425','2016-10-22','42783.81'),(172,'AD832091','2016-10-09','1960.80'),(172,'CE51751','2016-10-04','51209.58'),(172,'EH208589','2016-10-20','33383.14'),(173,'GP545698','2016-10-13','11843.45'),(173,'IG462397','2016-10-29','20355.24'),(175,'CITI3434344','2016-10-19','28500.78'),(175,'IO448913','2016-10-19','24879.08'),(175,'PI15215','2016-10-10','42044.77'),(177,'AU750837','2016-10-17','15183.63'),(177,'CI381435','2016-10-19','47177.59'),(181,'CM564612','2016-10-25','22602.36'),(181,'GQ132144','2016-10-30','5494.78'),(181,'OH367219','2016-10-16','44400.50'),(186,'AE192287','2016-10-10','23602.90'),(186,'AK412714','2016-10-27','37602.48'),(186,'KA602407','2016-10-21','34341.08'),(187,'AM968797','2016-10-03','52825.29'),(187,'BQ39062','2016-10-08','47159.11'),(187,'KL124726','2016-10-27','48425.69'),(189,'BO711618','2016-10-03','17359.53'),(189,'NM916675','2016-10-01','32538.74'),(198,'FI192930','2016-10-06','9658.74'),(198,'HQ920205','2016-10-06','6036.96'),(198,'IS946883','2016-10-21','5858.56'),(201,'DP677013','2016-10-20','23908.24'),(201,'OO846801','2016-10-15','37258.94'),(202,'HI358554','2016-10-18','36527.61'),(202,'IQ627690','2016-10-08','33594.58'),(204,'GC697638','2016-10-13','51152.86'),(204,'IS150005','2016-10-24','4424.40'),(205,'GL756480','2016-10-04','3879.96'),(205,'LL562733','2016-10-05','50342.74'),(205,'NM739638','2016-10-06','39580.60'),(209,'BOAF82044','2016-10-03','35157.75'),(209,'ED520529','2016-10-21','4632.31'),(209,'PH785937','2016-10-04','36069.26'),(211,'BJ535230','2016-10-09','45480.79'),(216,'BG407567','2016-10-09','3101.40'),(216,'ML780814','2016-10-06','24945.21'),(216,'MM342086','2016-10-14','40473.86'),(219,'BN17870','2016-10-02','3452.75'),(219,'BR941480','2016-10-18','4465.85'),(227,'MQ413968','2016-10-31','36164.46'),(227,'NU21326','2016-10-02','53745.34'),(233,'BOFA23232','2016-10-20','29070.38'),(233,'II180006','2016-10-01','22997.45'),(233,'JG981190','2016-10-18','16909.84'),(239,'NQ865547','2016-10-15','80375.24'),(240,'IF245157','2016-10-16','46788.14'),(240,'JO719695','2016-10-28','24995.61'),(242,'AF40894','2016-10-22','33818.34'),(242,'HR224331','2016-10-03','12432.32'),(242,'KI744716','2016-10-21','14232.70'),(249,'IJ399820','2016-10-19','33924.24'),(249,'NE404084','2016-10-04','48298.99'),(250,'EQ12267','2016-10-17','17928.09'),(250,'HD284647','2016-10-30','26311.63'),(250,'HN114306','2016-10-18','23419.47'),(256,'EP227123','2016-10-10','5759.42'),(256,'HE84936','2016-10-22','53116.99'),(259,'EU280955','2016-10-06','61234.67'),(259,'GB361972','2016-10-07','27988.47'),(260,'IO164641','2016-10-30','37527.58'),(260,'NH776924','2016-10-24','29284.42'),(276,'EM979878','2016-10-09','27083.78'),(276,'KM841847','2016-10-13','38547.19'),(276,'LE432182','2016-10-28','41554.73'),(276,'OJ819725','2016-10-30','29848.52'),(278,'BJ483870','2016-10-05','37654.09'),(278,'GP636783','2016-10-02','52151.81'),(278,'NI983021','2016-10-24','37723.79'),(282,'IA793562','2016-10-03','24013.52'),(282,'JT819493','2016-10-02','35806.73');

```

---

### **Q2. How to create an empty table in Hive from another table without copying data?**

**Option 1:**

```sql
create table payments_copy as 
select * from learning.payments where 1=2;
```

**Option 2 (Efficient way):**

```sql
create table payments_copy1 like learning.payments;
show create table learning.payments;
```

**Comparison: Creating Empty Table from Existing Table**

| Feature/Aspect              | **Option 1** – `CREATE TABLE ... AS SELECT * WHERE 1=2` | **Option 2** – `CREATE TABLE ... LIKE` |
|-----------------------------|--------------------------------------------------------|----------------------------------------|
| **Purpose**                 | Creates new table with same columns, but no rows        | Creates an exact schema copy (columns, datatypes, constraints, indexes) |
| **Performance**             | Slower – scans source table metadata via query engine   | Faster – metadata-only operation, no data scan |
| **Indexes/Constraints**     | ❌ Not preserved (only column definitions copied)       | ✅ Preserved (primary key, unique keys, defaults, indexes, etc.) |
| **Storage Usage**           | Higher (query planner overhead, temporary structures)   | Minimal (only schema copied) |
| **Ease of Use**             | Workaround style; less explicit                        | Cleaner, purpose-built syntax |
| **When to Use**             | Rare cases where `LIKE` not supported                  | Best practice for schema cloning |
| **Example**                 | `CREATE TABLE payments_copy AS SELECT * FROM learning.payments WHERE 1=2;` | `CREATE TABLE payments_copy1 LIKE learning.payments;` |


---

### **Q3. Can we join data between tables residing in two different databases/datasets?**

✅ Yes, prefix the schema before every table name.

---

### **Q4. Can we insert multiple records into a Hive/BigQuery table without using the load command?**

✅ Yes, as shown in the sample insert script above.

---

### **Q5. Duplicate Handling**

* Insert duplicate rows for testing:

```sql
-- Insert 9 duplicate rows into payments
insert  into `payments` values 
(103,'HQ336336','2016-10-19','6066.78'),
(103,'JM555205','2016-10-05','14571.44'),
(103,'OM314933','2016-10-18','1676.14'),
(112,'BO864823','2016-10-17','14191.12'),
(112,'HQ55022','2016-10-06','32641.98'),
(114,'GG31455','2016-10-20','45864.03'),
(114,'MA765515','2016-10-15','82261.22'),
(114,'NP603840','2016-10-31','7565.08'),
(114,'NR27552','2016-10-10','44894.74');
```

```sql
-- Insert 3 duplicate rows into customers
insert  into `customers` values 
(103,'Atelier graphique','Schmitt','Carine ','40.32.2555','54, rue   fàcRoyale',NULL,'Nantes',NULL,'44000','France',1370,'21000.00'),
(112,'Signal Gift Stores','King','Jean','7025551838','8489 Strong St.',NULL,'Las Vegas','NV','83030','USA',1166,'71800.00'),
(114,'Australian Collectors, Co.','Ferguson','Peter','03 9520 4555','636 St Kilda Road','Level 3','Melbourne','Victoria','3004','Australia',1611,'117300.00');
```

---

### **Q6. How to de-duplicate a given table?**

👉 **Option 1:**

```sql
select distinct * from payments; -- returns 273 records
```

👉 **Option 2 (Better):**

```sql
select customerNumber, checkNumber, paymentDate, amount
from payments
group by customerNumber, checkNumber, paymentDate, amount;
```

---

### **Q7. How to identify which customer table records are duplicated and how many duplicates exist?**

* **Where vs Having:**

  * `WHERE` = filter before aggregation
  * `HAVING` = filter after aggregation

**Duplicate check for payments:**

```sql
select customerNumber, checkNumber, paymentDate, amount, count(1)
from payments
group by customerNumber, checkNumber, paymentDate, amount
having count(1) > 1;
```

**Duplicate check for customers:**

```sql
select customernumber, customername, contactlastname, contactfirstname,
phone, addressline1, addressline2, city, state, postalcode, country,
salesrepemployeenumber, creditlimit, count(1)
from customers
group by customernumber, customername, contactlastname, contactfirstname,
phone, addressline1, addressline2, city, state, postalcode, country,
salesrepemployeenumber, creditlimit
having count(1) > 1;
```

---

### **Q8. How to remove/delete duplicate payments and retain only de-duplicated data?**

**Approaches:**

* `GROUP BY`
* `DISTINCT`
* `WINDOW FUNCTIONS`
* `CTE`

---

#### Case 1: Regular Table (Small Data Volume)

```sql
-- Create duplicate table
create table payments_dup as select * from payments;

-- Remove duplicates
insert overwrite table payments_dup
select distinct * from payments_dup;
```

**Delete data less than or equal to `2016-10-29`:**

```sql
insert overwrite table payments_dup
select * from payments_dup where paymentdate > '2016-10-29';
```

---

#### Case 2: Partitioned Table (Large Data Volume)

```sql
CREATE TABLE `payments_part` (  
  `customerNumber` int,  
  `checkNumber` varchar(50),  
  `amount` decimal(10,2)  
) PARTITIONED BY (`paymentDate` date)  
ROW FORMAT DELIMITED FIELDS TERMINATED BY ',';
```

```sql
set hive.exec.dynamic.partition.mode=nonstrict;

insert overwrite table payments_part partition (paymentdate)
select customernumber, checknumber, amount, paymentdate from payments;
```

**Find duplicates:**

```sql
select customernumber, checknumber, amount, paymentdate, count(1)
from payments_part
group by customernumber, checknumber, amount, paymentdate
having count(1) > 1;
```

**Remove duplicates:**

```sql
insert overwrite table payments_part partition (paymentdate)
select distinct customernumber, checknumber, amount, paymentdate
from payments_part;
```



