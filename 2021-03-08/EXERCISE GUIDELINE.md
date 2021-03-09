# QUERIES FOR "schema.sql" DATABASE

●    Select all guests

	SELECT *
	FROM `ospiti`;

---

●    Select all guests with document type = at CI

	SELECT *
	FROM `ospiti`
	WHERE `document_type` = "CI";

----

●    Select payers who have a linked guest id

	SELECT *
	FROM `paganti`
	WHERE `ospite_id` IS NOT NULL;

----

●    Select all rooms on the first floor

	SELECT *
	FROM `stanze`
	WHERE `floor` = 1;

----

●     Select all guests starting with E 

	SELECT *
	FROM `ospiti`
	WHERE `name` LIKE "E%"
	   OR `lastname` LIKE "E%";

----

●    Select all guests under 30 years of age

	SELECT *
	FROM `ospiti`
	WHERE `date_of_birth` > (CURDATE() - INTERVAL 30 YEAR);

----

●    Select all bookings earlier than May 2018

	SELECT *
	FROM `prenotazioni`
	WHERE `created_at` < "2018-05-01";

----