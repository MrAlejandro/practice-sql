
```sql
-- using multiple columns for equality check
SELECT * FROM `task` WHERE (`status`, `priority`) = (21, 20);
SELECT * FROM `task` WHERE ROW (`status`, `priority`) = (21, 20)
SELECT * FROM `task` WHERE ROW (`status`, `priority`) = (SELECT 21, 20 FROM task LIMIT 1);
SELECT * FROM `task` WHERE ROW (`status`, `priority`) IN (SELECT 21, 20 FROM task);

-- the "EXISTS" keyword
SELECT * FROM task AS outer_taks WHERE EXISTS (
    SELECT * FROM task AS inner_task WHERE inner_task.`status` = 21 AND outer_taks.`status` = inner_task.`status`
);
```
