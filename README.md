# Snowflake-notes ❄️

day 1:
- Architecture
- Virtual warehouses (size and scaling) <br />

day 2:
- Scaling policy(standard, economy)
- auto-scaling in the two types
- ETL
- snowflake editions
- roles
- stages (external, internal)
- implemented staging from s3 and loading using 'copy into' command 

day 3:
- on_error field to handle error (continue, skip_file, error_limit, error limit in percentage).
- stage and file formatting objects. Separately for good coding practice.

day 4:
- copy-options (to have more control) 
    - on_error
    - validation_mode (return errors, return_n_rows)

- Saving rejected files with and without validation_mode

day 5:
- saving errors after validation check:
- select rejected_record from table(result_scan(last_query_id()));
- savings errors with on_error = 'continue'
- select * from table(validate(orders, job_id => '_last'));
- query_id: copy into statement query id


day 6:
- copy options, SIZE_LIMIT 
- irrespective of size_limit, first file loaded. If file1_size > size_limit second file not loaded. Else second file loaded. If file1_size +file2_size > size_limit, third file not loaded and so on...

day 7:
- copy options: return_only_failed
- used with on_error continue and set to true (default false). returns the names of files that had error(s) and just returns an aggregate of files loaded successfully.

day 8:
- copy options: truncatecolumns
- default : false
- set : true (if loading string length exceeds target column length, truncate it to match target col length)

day 9:
- copy options: force
- default : false (snowflake metadata, if file loaded prev and no changes since, will not be loaded again to prevent duplicates)
- set : true (file will be loaded again, potential duplicates)

day 10:
- copy options: load_history
- local db: info schema: views: load_history
- snowflake: acc usage: views: load_history
- to retrieve history of data loaded into tables using copy into cmd




