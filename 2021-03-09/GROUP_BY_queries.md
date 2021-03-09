Count guests by year of birth

    SELECT count(id),YEAR(`date_of_birth`)
    FROM `ospiti` 
    GROUP BY YEAR(`date_of_birth`);

---

Sum the prices of payments by status

    SELECT SUM(price), `status` 
    FROM `pagamenti` 
    GROUP BY `status`;

---

Count how many times each room has been booked

    SELECT COUNT(id) 
    AS `bookings_qty`,`stanza_id` 
    AS `room_number`
    FROM `prenotazioni` 
    GROUP BY `stanza_id`;

---

Analyze to see if there are hours when bookings are more frequent

    SELECT COUNT(id),HOUR(`created_at`) 
    FROM `prenotazioni` 
    GROUP BY HOUR(`created_at`) 
    ORDER BY COUNT(*) DESC;

---

How many bookings did the guest who made the most bookings make?

    SELECT COUNT(id),`ospite_id` 
    FROM `prenotazioni_has_ospiti` 
    GROUP BY `ospite_id` 
    ORDER BY COUNT(*) DESC 
    LIMIT 2;

---
