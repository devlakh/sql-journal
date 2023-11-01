# sql-journal
sql-journal A List of Querying Ingridients

♙ Collapse ROWS Based on A Column with identical data - STRING ♙
    
    SELECT 
    authors.academic_works_id, 
    GROUP_CONCAT(JSON_OBJECT('name',authors.given_name,'dob',authors.date_of_birth) SEPARATOR '\0') 
    AS authors_data 
    FROM authors 
    GROUP BY authors.academic_works_id
