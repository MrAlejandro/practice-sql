
```sql
-- using multiple columns for equality check
SELECT * FROM `task` WHERE (`status`, `priority`) = (21, 20);
SELECT * FROM `task` WHERE ROW (`status`, `priority`) = (21, 20)
SELECT * FROM `task` WHERE ROW (`status`, `priority`) = (SELECT 21, 20 FROM task LIMIT 1);
SELECT * FROM `task` WHERE ROW (`status`, `priority`) IN (SELECT 21, 20 FROM task);
```
