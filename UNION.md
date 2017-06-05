```sql
-- NOTE UNION by default is distinct and can potentially return less records than UNION ALL
SELECT * FROM `sales2010` 
UNION 
SELECT * FROM `sales2011`

SELECT * FROM `sales2010` 
UNION ALL 
SELECT * FROM `sales2011`
```
