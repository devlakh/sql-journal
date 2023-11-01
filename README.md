# sql-journal
sql-journal A List of Querying Ingridients

♙ Collapse ROWS Based on A Column with identical data ♙
    
    SELECT JSON_ARRAY(JSON_OBJECT('<key1>',<table>.<column1>), JSON_OBJECT('<key2>',<table>.<column2>)) 
    AS <new column name>
    FROM <table>
    GROUP BY <table>.<column with identical data>;
