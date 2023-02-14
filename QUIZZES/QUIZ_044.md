# QUIZ 044
![Screen Shot 2023-02-14 at 22 34 40](https://user-images.githubusercontent.com/111819437/218760005-11ccbdb2-8509-44fe-8876-507a9b3862f5.png)


## CODE

```.py
--1) How many tables are there in the database?
---There are 4 tables

--2) How many Male inhabitants are Friendly?
SELECT count(*) from INHABITANT where gender="Male" and state="Friendly";
---4

--3) What is the average gold by village?
SELECT avg(gold) from INHABITANT group by villageid;
--- 1) 129.16666666666666
--- 2) 112.5
--- 3) 137.5
--- 4) 118.75


--4)How many items are there that start with the letter “A”
SELECT count(*) from ITEM where item like"A%";
---3

--5)How many different jobs are there?
SELECT job from INHABITANT group by job;
--- 15 different jobs - Armorer, Baker, Bard, Blacksmith,Brewer, Butcher, Candle Maker, Carpenter, Farmer, Herbalist, Hunter,Merchant,Potter,Tailor,Weaver

--6)What are the items owned by the herbalists?
SELECT personid from INHABITANT where job="Herbalist";
--- 4,18
SELECT * from ITEM where owner=4 or owner=18
-- Dagger
```
