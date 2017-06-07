```sql
-- selecting from a subquery
-- note that subquery must have an alias
SELECT AVG(`priority_sum`) FROM (
    SELECT SUM(`priority`) AS priority_sum
    FROM task
    GROUP BY `status`
) AS subquery

-- FAKE TABLE
SELECT 1 AS n UNION ALL SELECT 2 UNION ALL SELECT 3 UNION ALL SELECT 4 UNION ALL SELECT 5;
```
