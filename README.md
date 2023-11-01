# sql-journal
sql-journal A List of Querying Ingridients

♙ Collapse ROWS Based on A Column with identical data - STRING ♙
    
    SELECT 
    GROUP_CONCAT(authors.given_name, '<column separetor>' ,authors.date_of_birth SEPARATOR '<row separator>') 
    AS authors_data
    FROM authors
    GROUP BY authors.academic_works_id;
