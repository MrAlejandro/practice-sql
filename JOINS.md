```sql
-- CROSS means decart product (each tuple from the left table will be extended with data
-- from the second table)
SELECT * FROM emp 
CROSS JOIN dept;

-- if one table is empty the result will be empty too
SELECT * FROM emp 
CROSS JOIN empty_table;

-- this is a shorter way to do a CROSS JOIN 
SELECT * FROM emp, dept;
```

![inner join](https://www.w3schools.com/sql/img_innerjoin.gif)
```sql
-- INNER JOIN: all records where deptno is NULL or does not have respective record 
-- in the coresponding table will be omitted
SELECT * FROM emp 
INNER JOIN dept ON 1=1
    AND emp.`deptno` = dept.`deptno`;
    
-- shorter way to do an INNER JOIN
SELECT * FROM emp, dept 
WHERE emp.`deptno` = dept.`deptno`

-- another way to write the previous two (joins by the columns with equal names
-- in both tables)
SELECT * FROM emp 
NATURAL JOIN dept
```
