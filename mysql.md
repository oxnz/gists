MySQL
-----

### Login using the command line client

    mysql --host=hostname --user=username --password=password db_name

### Run script on DB

    mysql --user=root db_name < /home/ahorne/schema.sql

### Process Management

Note that "\G" only works in command line client, but causes an easier to read output.

    show processlist\G;
    kill <proc>

### Database Sizing

    SELECT table_schema "Data Base Name",
    sum( data_length + index_length ) / 1024 /
    1024 "Data Base Size in MB",
    sum( data_free )/ 1024 / 1024 "Free Space in MB"
    FROM information_schema.TABLES
    GROUP BY table_schema ;

### Table Sizing

    SELECT table_name "Table Name", ( data_length + index_length ) / 1024 / 1024 "Table Size in MB", table_rows
    FROM information_schema.TABLES where table_schema="billing";

### Index Sizing

    show table status in my_db like 'table_name';
    show index in my_db.table_name

### Dump to File

    select foo from table_name into outfile '/tmp/codes.txt'

### Dump as SQL

    mysqldump -u root db_name table_name

To protect blob data add:

    --hex-blob 

### Find Tables in Database Referencing a Table

    select table_name
    from information_schema.KEY_COLUMN_USAGE
    where table_schema = 'my_schema'
    and referenced_table_name = 'my_table';