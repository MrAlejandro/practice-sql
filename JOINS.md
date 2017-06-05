```sql
-- CROSS means decart product (each tuple from the left table will be extended with data from the second table)
SELECT * FROM emp 
CROSS JOIN dept;

-- if one table is empty the result will be empty too
SELECT * FROM emp 
CROSS JOIN empty_table;

-- this is a shorter way to do a CROSS JOIN 
SELECT * FROM emp, dept;
```
