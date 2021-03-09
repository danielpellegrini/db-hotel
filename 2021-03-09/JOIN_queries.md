What are the names of the guests who made more than two bookings?

    SELECT COUNT(*),`ospite_id`,`ospiti`.name,`ospiti`.lastname 
    FROM `prenotazioni_has_ospiti` 
    INNER JOIN `ospiti` 
    ON `prenotazioni_has_ospiti`.`ospite_id` = `ospiti`.id
    GROUP BY `ospite_id` 
    HAVING COUNT(*) > 2;

---

Print all guests for each reservation

    SELECT `prenotazione_id`,`ospite_id`,`ospiti`.name,`ospiti`.lastname 
    FROM `prenotazioni_has_ospiti` 
    INNER JOIN `ospiti` 
    ON `prenotazioni_has_ospiti`.`ospite_id` = `ospiti`.id;

---

Print First Name, Last Name, Price and Paying Amount for all bookings made in May 2018

    SELECT `ospiti`.name 
    AS 'guest_name', `ospiti`.lastname 
    AS 'guest_surname', `pagamenti`.price 
    AS 'price', `paganti`.name 
    AS 'payer_name', `paganti`.lastname 
    AS 'payer_surname' 
    FROM paganti INNER JOIN `pagamenti`
    ON paganti.id = `pagamenti`.pagante_id
    INNER JOIN `prenotazioni`
    ON `pagamenti`.prenotazione_id = `prenotazioni`.id
    INNER JOIN `prenotazioni_has_ospiti`
    ON prenotazioni.id = `prenotazioni_has_ospiti`.prenotazione_id
    INNER JOIN ospiti
    ON `prenotazioni_has_ospiti`.ospite_id = `ospiti`.id
    WHERE MONTH(`prenotazioni`.created_at) = 05
    AND YEAR(`prenotazioni`.created_at) = 2018;

---

Add all the prices for first floor rooms

    SELECT SUM(`price`) 
    FROM `pagamenti` 
    INNER JOIN `prenotazioni` 
    ON `pagamenti`.`prenotazione_id` = `prenotazioni`.id 
    INNER JOIN `stanze` 
    ON `prenotazioni`.stanza_id = `stanze`.id 
    WHERE `stanze`.floor = 1;

---

Get billing information for booking with id=7

    SELECT paganti.name,paganti.lastname,paganti.address,ospiti.`date_of_birth`,`ospiti`.`document_type`,ospiti.`document_number`,pagamenti.price
    FROM pagamenti 
    INNER JOIN paganti 
    ON pagamenti.`pagante_id` = paganti.id 
    INNER JOIN ospiti 
    ON paganti.`ospite_id` = ospiti.id 
    WHERE prenotazione_id = 7 ;

---

Have all the rooms been booked once?
 (View rooms not yet booked)

    SELECT COUNT(*),stanze.id, room_number
    AS `not_yet_booked_rooms`
    FROM prenotazioni 
    RIGHT JOIN stanze 
    ON prenotazioni.`stanza_id`= stanze.id 
    WHERE prenotazioni.`stanza_id` IS  NULL
    GROUP BY stanze.id DESC;

---
