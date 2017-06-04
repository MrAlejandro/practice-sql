```sql
-- selecting from a subquery
-- note that subquery must have an alias
SELECT AVG(`priority_sum`) FROM (
    SELECT SUM(`priority`) AS priority_sum
    FROM task
    GROUP BY `status`
) AS subquery
```
