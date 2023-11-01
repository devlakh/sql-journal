# sql-journal
sql-journal A List of Querying Ingridients

♙ Collapse ROWS Based on A Column with identical data ♙
    
    SELECT 
    authors.academic_works_id, 
    GROUP_CONCAT(
    	JSON_OBJECT(
    		'name',CONCAT(authors.prefix,' ',authors.given_name,' ',authors.middle_name,' ',authors.last_name,' ',authors.suffix)
    		,'department',authors.department
    	) SEPARATOR '\0'
    )
    AS collapsed_authors 
    FROM authors 
    GROUP BY authors.academic_works_id


♙ Grab Main Table With Collapsed Sub Table ♙

    SELECT * FROM academic_works JOIN(SELECT 
    authors.academic_works_id, 
    GROUP_CONCAT(
        JSON_OBJECT(
            'name',CONCAT(authors.prefix,' ',authors.given_name,' ',authors.middle_name,' ',authors.last_name,' ',authors.suffix)
            ,'department',authors.department
        ) SEPARATOR '\0'
    )
    AS collapsed_authors 
    FROM authors 
    GROUP BY authors.academic_works_id) 
    AS authors_temp ON authors_temp.academic_works_id = academic_works.id

