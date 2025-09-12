
# Hive SQL Examples

### **Q1. Sample Data Load**

```sql

--Prerequisite: Start the Hadoop cluster and History Server
start-all.sh
start-history-server.sh
jps


--Prerequisite: Creating a Hive database
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

**Comparison:**

| Phase             | **Option 1: DISTINCT \***                                                                      | **Option 2: GROUP BY (selected keys)**                                                                                      |
| ----------------- | ---------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| **Map Phase**     | - Reads **all columns** from table. <br> - No column pruning. <br> - No map-side aggregation.  | - Reads **only selected columns** (4 in this case) → column pruning. <br> - Performs **map-side aggregation** (if enabled). |
| **Shuffle Phase** | - **Shuffles entire rows** (all columns) across network. <br> - High shuffle size = heavy I/O. | - **Shuffles only group keys** (customerNumber, checkNumber, paymentDate, amount). <br> - Much smaller shuffle size.        |
| **Reduce Phase**  | - Reducers eliminate duplicates by comparing full rows. <br> - More memory and CPU overhead.   | - Reducers finalize aggregation. <br> - Less memory and CPU used because data already partially aggregated.                 |
| **Network I/O**   | Very high (large data shuffled).                                                               | Lower (only necessary columns shuffled).                                                                                    |
| **Performance**   | Slower (inefficient for large tables).                                                         | Faster and more scalable.                                                                                                   |
| **Best Use Case** | Small tables or when full row uniqueness is needed.                                            | Large tables where deduplication is required on specific keys.                                                              |

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
**Note: DELETE statement is not supported in Hive**

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

**Enable Partition Strict Mode:**
```sql
-- Enable strict mode
SET hive.exec.dynamic.partition.mode=strict;

-- At least one partition must be static
INSERT OVERWRITE TABLE payments_part PARTITION (paymentdate='2023-10-21')
SELECT customernumber, checknumber, amount
FROM payments
WHERE paymentdate = '2023-10-21';
```

---

### **Q9. Show the customer info who made the very first payment and last payment to our company? or the very first customer of the company?**

```sql
SELECT * 
FROM payments_part 
WHERE paymentdate IN (SELECT MIN(paymentdate) FROM payments_part);
```

---

### **Q10. Show the first payment made by a given customer to our company?**

```sql
SELECT * 
FROM payments 
WHERE customernumber = 496;
```


**Analytical/windowing functions commonly used:**

* `row_number()`
* `rank()`, `dense_rank()`
* `sum()`, `cume_sum()`
* `avg()`, `count()`, `min()`, `max()`
* `first_value()`, `last_value()`
* `lead()`, `lag()`

```sql
SELECT *,
       FIRST_VALUE(amount) OVER (PARTITION BY customernumber ORDER BY paymentdate DESC) 
FROM payments 
WHERE customernumber = 205;
```

| payments.customernumber | payments.checknumber | payments.paymentdate | payments.amount | first_value_window_0 |
|---|---|---|---------------|---|
| 205 | GL756480 | 2016-10-04 | `3879.96`     | `3879.96` |
| 205 | LL562733 | 2016-10-05 | 50342.74      | `3879.96` |
| 205 | NM739638 | 2016-10-06 | 39580.60      | `3879.96` |


---

### **Q11. Show the first payment, last made by the given customer?**

```sql
-- First Payment
SELECT * 
FROM payments 
WHERE customernumber = 496 
  AND paymentdate IN (
        SELECT MIN(paymentdate) 
        FROM payments_part 
        WHERE customernumber = 496
);
```

```sql
-- Last Payment
SELECT * 
FROM payments 
WHERE customernumber = 496 
  AND paymentdate IN (
        SELECT MAX(paymentdate) 
        FROM payments_part 
        WHERE customernumber = 496
);
```

---

### **Q12. Using Co-related query: Show the first payment, last made by all the customers?**

```sql
SELECT a.* 
FROM payments AS a 
WHERE a.paymentdate IN (
    SELECT MAX(b.paymentdate) 
    FROM payments AS b 
    WHERE b.customernumber = a.customernumber
);
```

---

### **Q13. Show the last (but one) or second recent payment made by the customer 496?**

❌ Note: Nested subqueries with `NOT IN` are tricky in Hive.

```sql
SELECT a.* 
FROM payments AS a
WHERE a.customernumber = 496 
  AND a.paymentdate IN (
        SELECT MAX(b.paymentdate) 
        FROM payments AS b  
        WHERE b.customernumber = 496 
          AND b.paymentdate NOT IN (
                SELECT MAX(c.paymentdate) 
                FROM payments AS c 
                WHERE c.customernumber = 496
        )
);
```

---

### **Q14. Multi column subquery**

```sql
SELECT a.* 
FROM payments AS a
WHERE (a.customernumber, a.paymentdate) IN (
    SELECT c.customernumber, c.paymentdate 
    FROM payments_part AS c 
    WHERE c.customernumber = 496
);
```

---

### **Q15. How to achieve multi column subquery in Hive? (By converting to Joins)**

```sql
-- Using CONCAT
SELECT a.* 
FROM payments AS a
WHERE CONCAT(a.customernumber, a.paymentdate) IN (
    SELECT CONCAT(c.customernumber, c.paymentdate) 
    FROM payments_part AS c 
    WHERE c.customernumber = 496
);

-- Using JOIN
SELECT a.* 
FROM payments AS a 
INNER JOIN payments_part AS c
    ON (c.customernumber = a.customernumber 
        AND a.paymentdate = c.paymentdate 
        AND c.customernumber = 496);
```

⚠️ Error Case:

```
FAILED: SemanticException [Error 10249]: 
Line 2:151 Unsupported SubQuery Expression 'paymentdate': 
Nested SubQuery expressions are not supported.
```

---

### **Q16. Using Windowing/Analytical Functions**

👉 Insert sample record for testing:

```sql
INSERT INTO payments_part PARTITION(paymentdate='2016-10-30') 
VALUES (496,'HQ336436',52166.01);
```

#### Show the lowest payment, highest, number of payments made by the customer 496?

```sql
SET hive.cli.print.header=true;

SELECT customernumber,
       paymentdate,
       amount,
       RANK()        OVER (PARTITION BY customernumber ORDER BY amount DESC)        AS rnk,
       DENSE_RANK()  OVER (PARTITION BY customernumber ORDER BY amount DESC)        AS d_rank,
       ROW_NUMBER()  OVER (PARTITION BY customernumber ORDER BY amount DESC)        AS rownum,
       CUME_DIST()   OVER (PARTITION BY customernumber ORDER BY paymentdate)        AS cumulative_dist
FROM payments_part 
WHERE customernumber = 496;
```

✅ **Sample Output:**

| customernumber | checknumber | amount   | paymentdate | Rnk | D\_R | RowNum | Cumulative\_Dist |
| -------------- | ----------- | -------- | ----------- | --- | ---- | ------ | ---------------- |
| 496            | MN89921     | 52166.01 | 2016-10-30  | 1   | 1    | 1      | ...              |
| 496            | HQ336436    | 52166.01 | 2016-10-31  | 2   | 1    | 1      | ...              |
| 496            | MB342426    | 32077.44 | 2016-10-16  | 3   | 2    | 3      | ...              |
| 496            | EU531600    | 30253.75 | 2016-10-25  | 4   | 3    | 4      | ...              |

---

### **Q17. Show the second, third largest payment made by the customer 496?**

```sql
SELECT customernumber, paymentdate, amount, rownumdt  
FROM (
    SELECT customernumber,
           paymentdate,
           amount,
           RANK()        OVER (PARTITION BY customernumber ORDER BY amount DESC)        AS rnk,
           DENSE_RANK()  OVER (PARTITION BY customernumber ORDER BY amount DESC)        AS d_rank,
           ROW_NUMBER()  OVER (PARTITION BY customernumber ORDER BY amount DESC)        AS rownum,
           CUME_DIST()   OVER (PARTITION BY customernumber ORDER BY paymentdate)        AS cumulative_dist,
           ROW_NUMBER()  OVER (PARTITION BY customernumber ORDER BY paymentdate DESC)   AS rownumdt
    FROM payments_part 
    WHERE customernumber = 496
) AS temp
WHERE rownum IN (2,3);
```

---

### **Q18. Show the customer purchase rate whether growing up or leaning down from the overall largest and smallest payment made?**

```sql
SELECT customernumber,
       paymentdate,
       amount,
       max_amt,
       min_amt,
       CASE 
            WHEN min_amt = amount OR max_amt = amount THEN "No Change"
            WHEN min_amt < amount  THEN "purchase capacity is improved"
            WHEN max_amt > amount  THEN "purchase capacity is reduced"
            ELSE "No Change"  
       END AS purchase_capacity
FROM (
    SELECT customernumber,
           paymentdate,
           amount,
           MAX(amount) OVER (PARTITION BY customernumber) AS max_amt,
           MIN(amount) OVER (PARTITION BY customernumber) AS min_amt 
    FROM payments_part 
    WHERE customernumber = 496
) AS temp
ORDER BY paymentdate;
```

---

### **Q19. Show the customer purchase rate whether growing up or leaning down from the immediate previous and next payment made?**

➡️ Using **Analytical Functions (LAG & LEAD)**

```sql
-- CASE WHEN condition THEN result ... END
SELECT customernumber,
       paymentdate,
       amount,
       amount_paid_previous_day,
       amount_paid_next_day,
       CASE 
            WHEN amount_paid_previous_day > amount THEN "purchase capacity is reduced"
            WHEN amount_paid_previous_day IS NULL THEN "First Transaction"
            WHEN amount_paid_previous_day = amount THEN "no change in the purchase amount"
            ELSE "purchase capacity is improved"
       END AS lag,
       CASE 
            WHEN amount_paid_next_day > amount THEN "next day payment is high"
            WHEN amount_paid_next_day IS NULL THEN "next day payment is same"
            WHEN amount_paid_previous_day = amount THEN "no change in the purchase amount"
            ELSE "next day payment is same"
       END AS lead
FROM (
    SELECT customernumber,
           paymentdate,
           LAG(amount)  OVER (PARTITION BY customernumber ORDER BY paymentdate) AS amount_paid_previous_day,
           amount,
           LEAD(amount) OVER (PARTITION BY customernumber ORDER BY paymentdate) AS amount_paid_next_day
    FROM curatedds.payments 
    WHERE customernumber IN (496)
) AS temp
ORDER BY customernumber, paymentdate;
```

---

### **Q20. How to create random unique alphanumeric values?**

```sql
SELECT REGEXP_REPLACE(REFLECT('java.util.UUID','randomUUID'), '-', '') AS row_num,
       p.* 
FROM payments AS p;
```

---

### **Q21. How to create surrogate key or sequence number?**

```sql
CREATE EXTERNAL TABLE payments_increment (
    paymentid INT,
    customernumber INT,
    checknumber STRING,
    paymentdate DATE,
    amount DOUBLE
) 
ROW FORMAT DELIMITED 
FIELDS TERMINATED BY ',' 
LOCATION '/user/hduser/paymentsincr';

-- Insert with sequence generation
INSERT INTO TABLE payments_increment 
SELECT ROW_NUMBER() OVER() + COALESCE(pi.maxseq,0),
       customernumber,
       checknumber,
       paymentdate,
       amount 
FROM payments AS p
LEFT OUTER JOIN (
    SELECT 1 AS dummy, MAX(paymentid) maxseq 
    FROM payments_increment
) AS pi;

-- Verify result
SELECT * 
FROM payments_increment 
WHERE customernumber = 496;
```

---

### **Q22. How to create version numbers for the payments made by the customers?**

#### (a) Without considering history (fresh versioning)

```sql
CREATE TABLE payments_version (
    customerNumber INT,
    version INT,
    checkNumber VARCHAR(50),
    paymentDate DATE,
    amount DECIMAL(10,2)
) ROW FORMAT DELIMITED 
FIELDS TERMINATED BY ',';

-- Insert with row_number()
INSERT OVERWRITE TABLE payments_version 
SELECT customernumber,
       ROW_NUMBER() OVER (PARTITION BY customernumber ORDER BY paymentdate),
       checknumber,
       paymentdate,
       amount 
FROM payments;
```

#### (b) With historical lookup (**SCD Type 2**)

```sql
INSERT INTO TABLE payments_version 
SELECT p.customernumber,
       ROW_NUMBER() OVER (PARTITION BY p.customernumber ORDER BY paymentdate) + COALESCE(maxversion,0),
       checknumber,
       paymentdate,
       amount 
FROM payments AS p
LEFT OUTER JOIN (
    SELECT customernumber, MAX(version) maxversion 
    FROM payments_version 
    GROUP BY customernumber
) AS pi 
ON pi.customernumber = p.customernumber;

-- Verify result
SELECT * 
FROM payments_version 
WHERE customernumber = 496;
```

---

### **Q23. Update the data based on another table (using JOIN)?**

```sql
UPDATE curatedds.customer_50 cs
SET cs.city = c.city
FROM curatedds.customers c
WHERE c.customernumber = cs.customernumber;
```

---

### **Q24. Joins: Inner, Outer (Left, Right, Full), Semi, Anti, Self, Cross**

#### Insert sample data

```sql
INSERT INTO payments 
VALUES (1000,'HQ336336','2016-10-19','6066.78'),
       (1003,'JM555205','2016-10-05','14571.44');
```

---

#### (a) Show only customers who didn’t make payments (e.g., customer 481)

```sql
SELECT * 
FROM payments 
WHERE customernumber = 481;
```

```sql
SELECT c.customernumber, c.customername, p.amount 
FROM customers c 
LEFT JOIN payments p 
       ON c.customernumber = p.customernumber 
WHERE c.customernumber IN (496,481);
```

```sql
SELECT c.customernumber, c.customername 
FROM customers c 
WHERE NOT EXISTS (
    SELECT p.customernumber 
    FROM payments p 
    WHERE p.customernumber = c.customernumber
)
AND c.customernumber IN (496,481);
```

```sql
SELECT c.customernumber, c.customername 
FROM customers c 
WHERE c.customernumber NOT IN (
    SELECT customernumber 
    FROM payments p
)
AND c.customernumber IN (496,481);
```

---

#### (b) Show only customers who **made payments** and their amounts

```sql
-- Using INNER JOIN
SELECT c.customernumber, c.customername, p.amount 
FROM customers c 
INNER JOIN payments p 
       ON c.customernumber = p.customernumber 
WHERE c.customernumber IN (496,481);
```

```sql
-- Using EXISTS
SELECT c.customernumber, c.customername 
FROM customers c 
WHERE EXISTS (
    SELECT p.customernumber 
    FROM payments p 
    WHERE p.customernumber = c.customernumber
);
```

```sql
-- Using IN
SELECT c.customernumber, c.customername 
FROM customers c 
WHERE c.customernumber IN (
    SELECT customernumber 
    FROM payments p
);
```

---

#### (c) Show customers with **no details** who made payments anonymously

```sql
SELECT c.customernumber, c.customername, p.amount 
FROM customers c 
RIGHT OUTER JOIN payments p 
       ON c.customernumber = p.customernumber 
WHERE c.customernumber IS NULL
  AND p.customernumber IN (496,1000);
```

---

#### (d) Show customers **and** payments info (both sides)

```sql
SELECT c.customernumber, c.customername, p.amount 
FROM customers c 
FULL OUTER JOIN payments p 
     ON c.customernumber = p.customernumber;
```

---

### **Q25. Show me the customers who paid the payments at least once. Another important example: I want to know whether the given customer is a repeating or new?**

**Concept:**

* **INNER JOIN** returns rows from both tables when there is a match.
* **LEFT SEMI JOIN** returns only rows from the left table if at least one match exists in the right table.
* Performance: **INNER JOIN** iterates over all matches, while **LEFT SEMI JOIN** stops after the first match.

**Example:**

```sql
select c.* 
from customers c 
left semi join payments p 
on (c.customernumber = p.customernumber and c.customernumber=496);

select c.customernumber, c.customername 
from customers c 
inner join (
    select max(customernumber) as customernumber from payments
) p 
on (c.customernumber=p.customernumber);
```

---

### **Q26. Show the customers who made the payment in a range of amounts (6000–10000 and 30000–50000).**

**Concept:**

* Use **UNION ALL** to combine results from multiple ranges.

**Example:**

```sql
select * 
from payments 
where amount between 6000 and 10000

union all 

select * 
from payments 
where amount between 30000 and 50000;
```

---

### **Q27. Show me the combined result of two different tables picking 1 column from table1 and 2 columns from table2. Can we union tables with different columns or data types?**

**Concept:**

* Yes, by adding **dummy columns** and **casting datatypes**.

**Example:**

```sql
select p.customernumber, p.amount, 'NA' as country 
from retail.payments p 
where p.amount between 6000 and 10000

union all 

select customernumber, 0 as amount, country 
from retail.customers 
where customernumber > 400;
```

---

### **Q28. Can we union two tables which contain different number of columns or different data types?**

**Concept:**

* Yes, but columns must match in **count** and **type** after adjustment.

**Example 1:**

```sql
select * from payments_version 
union 
select customernumber,0 as version,checknumber, paymentdate, amount 
from payments;
```

**Example 2 (with type cast):**

```sql
select customernumber, cast(version as string) as version, checknumber, paymentdate, amount 
from payments_version 

union 

select customernumber, 'zero' as version, checknumber, paymentdate, amount 
from payments;
```

---

### **Q29. Show the customers who made the payment (INTERSECT) and the anonymous customers (MINUS).**

**Concept:**

* **INTERSECT** → common rows between two datasets.
* **MINUS** → rows in one dataset not present in the other.

**Example:**

```sql
select * from payments 
intersect 
select customernumber, checknumber, paymentdate, amount 
from payments_version;

select * from payments 
minus 
select customernumber, checknumber, paymentdate, amount 
from payments_version;
```

---

### **Q30. Show me the customers who have more than 1 phone number and more than 1 address.**

**Concept:**

* Use **GROUP BY** with **HAVING** for filtering.

**Example:**

```sql
insert into customers 
values (103,'Atelier graphique','Schmitt','Carine','908-199-0411',
        '55, rue Royale',NULL,'Nantes',NULL,'44000','France',1370,'21000.00');

select customernumber, count(distinct phone) as cnt, count(distinct addressline1) as cnt2
from customers 
group by customernumber 
having cnt > 1 and cnt2 > 1;
```

---

### **Q31. How do you create structured data (struct/json) from a set of columns in Hive?**

**Concept:**

* Use `named_struct` or `struct()` functions to group columns.

**Example:**

```sql
select named_struct("id", customernumber, "name", customername) 
from customers;

select strct.id 
from (
    select struct(customernumber as id, customername as name) strct 
    from curatedds.customers
);
```

---

### **Q32. How to collect column values as an array (pivot a column into a row)?**

**Concept:**

* Use `collect_list()` or `array_agg()` to gather column values into arrays.

**Example:**

```sql
select customernumber, collect_list(phone) as grouped_phone 
from customers 
where customernumber in (103,112) 
group by customernumber;

select customernumber, array_agg(phone) as grouped_phone 
from curatedds.customers 
where customernumber in (103,112) 
group by customernumber;
```

---

### **Q33. How to load semi-structured data (with arrays) into Hive?**

**Concept:**

* Use **collection items terminated by** clause for arrays.

**Example:**

```sql
create table orderpages (
    customernumber string,
    comments string,
    pagenavigation array<string>,
    pagenavigationidx array<int>
) 
row format delimited fields terminated by ',' 
collection items terminated by '$';

load data local inpath '/home/hduser/orderstg' 
overwrite into table orderpages;
```

---

### **Q34. How to collect array values as rows (unpivot array column)?**

**Concept:**

* Use `explode()` to expand arrays into multiple rows.

**Example:**

```sql
select explode(pagenavigation) 
from orderpages;
```

---

### **Q35. Show me the position of array elements in Hive (order of navigation).**

**Concept:**

* Use `posexplode()` to get both **index** and **value**.

**Example:**

```sql
select posexplode(pagenavigation) 
from orderpages;
```

---

### **Q36. Display customer number, comments, and pages navigated (array expansion with lateral view).**

**Concept:**

* Use **LATERAL VIEW + posexplode()** to flatten arrays with positions.

**Example:**

```sql
select customernumber, comments, idx, pgnavigation_column 
from orderpages 
lateral view posexplode(pagenavigation) exploded_tbl as idx, pgnavigation_column;
```

---


### **Q37. Why is ORDER BY costly in Hive? How can you avoid using it?**

**Concept:**

* `ORDER BY` → Single reducer → Performance bottleneck.
* Alternatives:

  * **DISTRIBUTE BY + SORT BY** → Parallel sort with multiple reducers.
  * **CLUSTER BY** → Equivalent to `DISTRIBUTE BY + SORT BY` on same columns.
* If only top records needed → use `LIMIT`.

**Example:**

```sql
set mapred.reduce.tasks=3;

-- Costly: single reducer
select * from payments order by customernumber, amount;

-- Efficient: multiple reducers
select * from payments 
distribute by customernumber 
sort by customernumber, amount;

-- Equivalent shortcut
select * from payments cluster by customernumber, amount;

-- Fetch only top N
select * from payments order by customernumber, amount limit 100;
```

---

### **Q38. How to split and join a string in Hive?**

**Concept:**

* `split(string, delimiter)` → splits into array.
* `concat_ws(delimiter, col1, col2, …)` → joins values with delimiter.

**Example:**

```sql
select 
    split("Inceptez Technologies"," ") as splitted,
    concat_ws(" ","Inceptez","Technologies") as joined;
```

---

### **Q39. Which Hive analytic/windowing functions have you used in projects?**

**Functions commonly used:**

* `row_number()`
* `rank()`, `dense_rank()`
* `sum()`, `cume_sum()`
* `avg()`, `count()`, `min()`, `max()`
* `first_value()`, `last_value()`
* `lead()`, `lag()`

---

### **Q40. Is DELETE and UPDATE possible in Hive?**

**Concept:**

* Yes, but only in **ACID-enabled tables** (transactional tables).
* Alternatives:

  * Partition-wise overwrite.
  * `INSERT OVERWRITE` with new dataset.

---

### **Q41. What is a surrogate key in database?**

**Concept:**

* A **system-generated unique key** (not derived from business data).
* Can be implemented in Hive using `row_number()`.

**Example:**

```sql
select row_number() over(order by customernumber) as surrogate_key, * 
from customers;
```

---

### **Q42. Join scenario: A has 2000, B has 1000, with 500 matches. What will be output?**

| **Join Type**    | **Result Count**          | **Meaning**                                               |
| ---------------- | ------------------------- | --------------------------------------------------------- |
| Inner Join       | 500                       | Matching customers with payments                          |
| Left Semi Join   | 500                       | Customers with at least one payment                       |
| Left Outer Join  | 2000                      | All customers, with/without payment                       |
| Right Outer Join | 1000                      | All payments, regardless of customer table                |
| Full Outer Join  | 2500                      | All customers + all payments (union with overlap handled) |
| Cross Join       | 2,000 × 1,000 = 2,000,000 | Cartesian product                                         |

---

### **Q43. UNION vs UNION ALL**

* **UNION** → Removes duplicates.
* **UNION ALL** → Keeps duplicates.

---

### **Q44. Pick max salary employee from each department.**

```sql
select dept_name, max(salary) as max_salary 
from emp 
group by dept_name;
```

---

### **Q45. Where do you see SQL pivot kind of feature in Hive/Spark?**

**Concept:**

* Pivot = Convert rows → columns (and vice versa).
* In Hive: `explode`, `lateral view`, `pivot`.
* In Spark: `pivot()` in DataFrame API.

---

### **Q46. Difference between `count(*)` and `count(1)`**

* `count(*)` → counts all rows (including nulls).
* `count(1)` → logically same, but often optimized as selecting constant instead of full row.
* Both yield same result, but **`count(1)` can be slightly more efficient**.

---

### **Q47. First Value and Last Value in Hive**

**Concept:**

* Return first/last value in partition/window.

**Example:**

```sql
select 
    first_value(salary) over(partition by dept_name order by salary) as first_sal,
    last_value(salary) over(partition by dept_name order by salary) as last_sal
from emp;
```

---

### **Q48. Lead and Lag in Hive**

**Concept:**

* `lead()` → next row.
* `lag()` → previous row.

**Example:**

```sql
select 
    empno, salary,
    lead(salary,1) over(partition by dept_name order by salary) as next_sal,
    lag(salary,1) over(partition by dept_name order by salary) as prev_sal
from emp;
```

---

### **Q49. Window Function Questions**

* Already covered above: `row_number`, `rank`, `dense_rank`, `lead`, `lag`, `first_value`, `last_value`, aggregates.

---

### **Q50. WITH Clause in Hive (CTE)**

**Concept:**

* Used for reusing subqueries in a single query (acts like temporary table).

**Example (CTE):**

```sql
with T1 as (
    select custno, category 
    from txnrecords 
    where category='Games'
),
T2 as (
    select custno, category 
    from txnrecords 
    where category='Puzzles'
)
select * from T1 
inner join T2 on T1.custno=T2.custno;
```

**Example (Temp Table):**

```sql
create temporary table temp1 as 
select custno, category 
from txnrecords 
where category='Games';
```

---

### **Q51. Fetch the latest record (most recent transaction).**

**Option 1 – row\_number():**

```sql
select * 
from (
    select row_number() over(order by txnno desc) as rno, t.* 
    from txnrecords t
) tmp
where rno = 1;
```

**Option 2 – max(txnno):**

```sql
select * 
from txnrecords 
where txnno = (select max(txnno) from txnrecords);
```

---

### **Q52. Null handling in Join**

**Scenario:**

* Table A → `Null, James, Null`
* Table B → `James, Null, Robert`
* **Inner join ignores NULL matches.**

**Example:**

```sql
create table nulltbl1(id int, name string);
create table nulltbl2(id int, amt decimal(5,2));

insert into nulltbl1 values (1,'a'),(2,'b'),(null,'c');
insert into nulltbl2 values (1,5.5),(null,1.33),(3,22.33);

select a.*, b.* 
from nulltbl1 a 
inner join nulltbl2 b 
on a.id = b.id;
```

👉 `NULL` keys won’t be returned.

---

### **Q53. Change date format in Hive**

**Concept:**

* Use `unix_timestamp()` + `from_unixtime()` to reformat.

**Example:**

```sql
select 
    txnno, custno, amount, category, product, city, state, spendby,
    from_unixtime(unix_timestamp(txndate,'MM-dd-yyyy'),'yyyy-MM-dd') as new_format,
    from_unixtime(unix_timestamp(txndate,'MM-dd-yyyy')) as ts_format
from txnrecords;
```

---
