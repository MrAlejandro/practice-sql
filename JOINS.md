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
-- in both tables) - NOT RECOMMENDED TO USE (because it may use more than one 
-- column in hidden ON statement)
SELECT * FROM emp 
NATURAL JOIN dept

-- another way to write the queries above
SELECT * FROM emp 
JOIN dept USING (`deptno`)
```

![left outer join](https://www.w3schools.com/sql/img_leftjoin.gif)
```sql
-- note that OUTER can be omitted
SELECT * FROM emp 
LEFT [OUTER] JOIN dept ON 1=1
    AND emp.`deptno` = dept.`deptno`;
```

![right outer join](https://www.w3schools.com/sql/img_rightjoin.gif)
```sql
-- note that OUTER can be omitted
SELECT * FROM emp 
RIGHT [OUTER] JOIN dept ON 1=1
    AND emp.`deptno` = dept.`deptno`;
```

![full outer join](https://www.w3schools.com/sql/img_fulljoin.gif)
```sql
-- note that OUTER can be omitted, MySQL does not have FULL JOIN
SELECT * FROM emp 
FULL [OUTER] JOIN dept ON 1=1 
    AND emp.`deptno` = dept.`deptno`;

-- FULL JOIN emulation for MySQL
SELECT * FROM emp
LEFT JOIN dept ON emp.`deptno` = dept.`deptno`
UNION ALL
SELECT * FROM emp
RIGHT JOIN dept ON emp.`deptno` = dept.`deptno`
WHERE emp.`deptno` IS NULL;
```

```sql
-- SUBJUERIES VS JOIN with the same results

-- this one is the slowes
SELECT emp.* 
FROM emp WHERE EXISTS (
	SELECT * 
    FROM dept WHERE emp.deptno = dept.deptno
)
ORDER BY empno;

-- this one is faster than the previous one
SELECT emp.* 
FROM emp WHERE emp.deptno IN (
	SELECT dept.deptno FROM dept
)
ORDER BY empno;

-- this one is the fastest (for my specific conditions)
SELECT emp.* 
FROM emp 
JOIN dept ON emp.deptno = dept.deptno
ORDER BY empno;
```
