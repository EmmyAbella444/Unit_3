# SOLUTION
```.kv
SELECT * from crime_scene_report where city="SQL City" and type="murder";
--- Someone killed the guard! He took an arrow to the knee!
---Security footage shows that there were 2 witnesses.
-- The first witness lives at the last house on "Northwestern Dr".
-- The second witness, named Annabel, lives somewhere on "Franklin Ave".
--20180115
SELECT * from person;
SELECT * from person where address_street_name="Franklin Ave" and name like"Annabel%";
--- 16371,Annabel Miller
SELECT max(address_number) from person;
--- 4919
SELECT * from person where address_street_name="Northwestern Dr" and address_number=4919;
---- 14887, Morty Schapiro
SELECT * from interview where person_id=16371;
---I saw the murder happen,
-- and I recognized the killer from my gym when I was working out last week on January the 9th.
SELECT * from interview where person_id=14887;
--- I heard a gunshot and then saw a man run out. He had a "Get Fit Now Gym" bag.
-- The membership number on the bag started with "48Z". Only gold members have those bags.
-- The man got into a car with a plate that included "H42W".
SELECT * from get_fit_now_member where membership_status="gold" and id like"48Z%";
---28819,Joe Germuska 48Z7A
---67318,Jeremy Bowers 48Z55
SELECT * from get_fit_now_check_in where check_in_date like "20180115" and membership_id="48Z7A"or membership_id="48Z55";
---67318,Jeremy Bowers 48Z55 1530,1700
SELECT * from drivers_license where plate_number like "H42W%";
---183779,21,65,blue,blonde,female,H42W0X,Toyota,Prius
SELECT * from person where license_id=183779;
---78193,Maxine Whitely, 110,Fisk Rd
SELECT * from interview where person_id=67318;
---I was hired by a woman with a lot of money.
-- I don't know her name but I know she's around 5'5" (65") or 5'7" (67").
-- She has red hair and she drives a Tesla Model S.
-- I know that she attended the SQL Symphony Concert 3 times in December 2017.
SELECT * from drivers_license where car_make="Tesla" and hair_color="red" and gender="female";
--202298
-- 291182
-- 918773
SELECT * from person where license_id=202298;
--99716,Miranda Priestly,202298,1883,Golden Ave,987756388
SELECT * from person where license_id=291182;
--90700,Regina George,291182,332,Maple Ave,337169072
SELECT * from person where license_id=918773;
--78881,Red Korb,918773,107,Camerata Dr,961388910

SELECT * from facebook_event_checkin where event_name="SQL Symphony Concert" and person_id=99716;
--99716,1143,SQL Symphony Concert,20171206
--99716,1143,SQL Symphony Concert,20171212
--99716,1143,SQL Symphony Concert,20171229

SELECT * from income where ssn=987756388 or ssn=337169072 or ssn=961388910;
--310000, 987756388 - biggest

---MURDER IS MIRANDA PRIESTLY

INSERT INTO solution values(1,"Miranda Priestly");
SELECT value FROM solution;
```

# EVIDENCE



![Screen Shot 2023-02-09 at 17 11 13](https://user-images.githubusercontent.com/111819437/217754449-48200804-7619-422f-8121-83cc071ac300.png)
