SELECT * FROM ftd.users_data;

SELECT * FROM users_data 
WHERE id IS NULL OR current_age IS NULL OR gender IS NULL;

SELECT * FROM cards_data 
WHERE id IS NULL 
OR client_id IS NULL 
OR card_brand IS NULL 
OR card_type IS NULL;

-- Transactions with missing keys
SELECT * FROM transactions_data 
WHERE client_id IS NULL OR
card_id IS NULL OR 
amount IS NULL OR 
mcc IS NULL;

SELECT * FROM mcc_code 
WHERE Value IS NULL OR 
Name IS NULL;


-- -- Duplicate users
SELECT id, COUNT(*) 
FROM users_data 
GROUP BY id 
HAVING COUNT(*) > 1;


SELECT id, COUNT(*) FROM cards_data
GROUP BY id 
HAVING COUNT(*) > 1;



SELECT * FROM users_data
WHERE GENDER = "M" or "m" ;


SELECT * FROM transactions_data 
WHERE amount > 100000;



SELECT t.*
FROM transactions_data t
JOIN users_data u ON t.client_id = u.id
JOIN cards_data c ON t.card_id = c.id
JOIN mcc_code m ON t.mcc = m.Value;
