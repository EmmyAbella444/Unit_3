
# QUIZ 045

![Screen Shot 2023-02-14 at 23 02 30](https://user-images.githubusercontent.com/111819437/218767547-e452fc1e-d589-441a-8c9a-3372cd4e6c14.png)

## Code and evidence
```.py
SELECT * from customers;
SELECT *from accounts;

SELECT account_id,sum(amount) from transactions where transaction_type="deposit" group by account_id;
SELECT account_id,sum(amount) from transactions where transaction_type="withdraw" group by account_id;
--1 = 1000
--2 = 5000
--3 = 1500
--4 = 4000
--5 = 2000
--6 = 6000
--7 = 1700
--8 = 5500
--9 =  1200
--10 = 4500
--11 = 1300
--12 = 4600 ***
--13 = 2200 ***
--14 = 6000
--15 = 2300 ***
--16 = 7000
--17 = 2400 ***
--18 = 6000
--19 = 2500 ***
--20 = 7000
SELECT account_id,balance from accounts group by account_id;
--  1,1000
--  2,5000
--  3,1500
--  4,4000
--  5,2000
--  6,6000
--  7,1700
--  8,5500
--  9,1200
--  10,4500
--  11,1300
--  12,5000
--  13,1400
--  14,6000
--  15,1500
--  16,7000
--  17,1600
--  18,6000
--  19,1700
--  20,7000

SELECT * from customers where customer_id=12 or customer_id=13 or customer_id=15 or customer_id=17 or customer_id=19;
--12,Matthew,Martin,matthewmartin@email.com
--13,Ashley,Taylor,ashleytaylor@email.com
--15,Nicholas,Lewis,nicholaslewis@email.com
--17,David,Clark,davidclark@email.com
--19,Daniel,Green,danielgreen@email.com
```
