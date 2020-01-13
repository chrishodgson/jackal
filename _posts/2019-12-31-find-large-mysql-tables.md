---
title: Find Large MySQL tables
desc: Get a list of tables over a certain size
---

## Return a list of tables over 1GB in size

```sql
SELECT table_schema as `DB`, 
table_name as `Table`,  
round(( (data_length + index_length) /1024/1024/1024), 2) as `GB` 
FROM information_schema.TABLES 
WHERE table_schema = 'DATABASE_NAME' 
HAVING GB > 1 
ORDER BY GB DESC;
```
