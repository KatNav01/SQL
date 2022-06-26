# SQL Murder Mystery

This code was written for the [SQL Murder Mystery Game](https://mystery.knightlab.com/). The game is a very useful tool for brushing up on the most common types of inquiries. 

### **_Spoiler Alert!_**
If you are planning to use the game as practice, I would not recommend reading through this file! **_Spoiler Alert!_**


## Pull up the crime scene report: 
```
SELECT 
  * 
  FROM crime_scene_report
WHERE city LIKE '%sql city%'
  AND date LIKE '%20180115%'
  AND type LIKE '%murder%';
```

Security footage shows that there were 2 witnesses. The first witness lives at the last house on "Northwestern Dr". The second witness, named Annabel, lives somewhere on "Franklin Ave".




## Find the two witnesses from the report:

```
SELECT 
	*
FROM person
	JOIN interview
		ON person.id = interview.person_id
	WHERE address_street_name LIKE '%northwestern dr%'
	ORDER BY address_number DESC
	LIMIT 1
	;
```

ID: 14887, Name: Morty Schapiro, Address: 4919 Northwestern DR., Liscence ID: 118009, SSN: 111564949 (assuming the houses are numbered in ASC order from the beginning of the street.)
		Transcript: I heard a gunshot and then saw a man run out. He had a "Get Fit Now Gym" bag. The membership number on the bag started with "48Z". Only gold members have those bags. The man got into a car with a plate that included "H42W".
```
SELECT 
	*
FROM person
	JOIN interview
		ON person.id = interview.person_id
	WHERE address_street_name LIKE '%franklin%'
	AND name LIKE '%annabel%'
	;
```
ID: 16371, Name: Annabel Miller, Liscence Number: 490173, Address: 103 Franklin Ave, SSN: 318771143
	Transcript: I saw the murder happen, and I recognized the killer from my gym when I was working out last week on January the 9th.



## Who fits that criteria on the Get Fit tables? 

```
SELECT 
		*
	FROM get_fit_now_check_in check_in
	JOIN get_fit_now_member member
		ON check_in.membership_id = member.id
	WHERE check_in_date LIKE '%20180109%'
	AND member.membership_status LIKE '%gold%'
	AND check_in.membership_id LIKE '%48z%'
	;
```

Member ship ID: 48Z7A
Check in Date: 20180109
Check in Time: 1600
Check out time: 1730
ID: 48Z7A
Person ID: 28819
Name: Joe Germuska
Membership Start Date: 20160305
Membership status: gold
	
Member ship ID: 48Z55
Check in Date: 20180109
Check in Time: 1530
Check out time: 1700
ID: 48Z55
Person ID: 67318
Name: Jeremy Bowers
Membership Start Date: 20160101
Membership status: gold


## Now let's narrow down the cars of the two suspects: 
```
SELECT 
		*
	FROM drivers_license
	JOIN person
		ON drivers_license.id = person.license_id
	JOIN get_fit_now_member member
		ON person.id = member.person_id
	WHERE plate_number LIKE '%H42W%'
	AND gender = 'male'
	AND membership_status LIKE '%gold%'
	;
```


## The murderer is Jeremy Bowers - now let's take a look at the interview transcript to see who hired him. 

```
SELECT 
		*
	FROM interview
	WHERE person_id = 67318
	;
```


I was hired by a woman with a lot of money. I don't know her name but I know she's around 5'5" (65") or 5'7" (67"). She has red hair and she drives a Tesla Model S. I know that she attended the SQL Symphony Concert 3 times in December 2017.

```
SELECT 
		*
	FROM person
	JOIN drivers_license license
		ON person.license_id = license.id
	JOIN facebook_event_checkin facebook
		ON person.id = facebook.person_id
	WHERE license.hair_color LIKE '%red%'
		AND license.car_make LIKE '%tesla%'
		AND license.car_model LIKE '%S%'
		AND license.height BETWEEN 65 AND 67
;

```
Miranda Priestly is the only person to fit all of the descriptions. She is the murderer


        
