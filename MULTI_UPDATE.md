[https://stackoverflow.com/questions/3432/multiple-updates-in-mysql](https://stackoverflow.com/questions/3432/multiple-updates-in-mysql)
```sql
INSERT INTO table (id,Col1,Col2) VALUES (1,1,1),(2,2,3),(3,9,3),(4,10,12)
ON DUPLICATE KEY UPDATE Col1=VALUES(Col1),Col2=VALUES(Col2);
```
