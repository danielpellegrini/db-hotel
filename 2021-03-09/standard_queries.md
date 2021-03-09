Select all guests that have been identified with the card 
identity

    SELECT *
    FROM `ospiti`
    WHERE `document_type` = "CI";

---


Select all guests born after 1988

    SELECT * 
    FROM `ospiti` 
    WHERE `date_of_birth` > '1988-12-31';
	

---

Select all guests over 20 years old (at the time of the query execution)

  	SELECT `name`, `lastname`, `date_of_birth`, TIMESTAMPDIFF(YEAR, `date_of_birth`, CURRENT_TIMESTAMP) AS `age`
    FROM `ospiti`
    WHERE TIMESTAMPDIFF(YEAR, `date_of_birth`, CURRENT_TIMESTAMP) > 20;  

---

Select all guests whose name starts with D

    SELECT *
    FROM `ospiti`
    WHERE `name` LIKE "D%"
	   
---

Calculate total accepted orders

    SELECT COUNT(id) , SUM(`price`) AS 'total'
    FROM `pagamenti` 
    WHERE status = 'accepted';

---

What is the maximum price paid?

    SELECT MAX(`price`) 
    AS 'highest_paid_price' 
    FROM `pagamenti` 
    WHERE `status` = 'accepted';

---

Select approved guests born in 1975 with a driving license

    SELECT * 
    FROM `ospiti` 
    WHERE `document_type` = 'Driver License' 
    AND YEAR(`date_of_birth`) = 1975;

---

How many guests are also payers?

    SELECT COUNT(`id`)
    AS 'paying_guests' 
    FROM `paganti` 
    WHERE `ospite_id` IS NOT NULL;

---

How many beds does the hotel have in total?

    SELECT SUM(`beds`) 
    AS 'available_beds' 
    FROM `stanze`;

---
