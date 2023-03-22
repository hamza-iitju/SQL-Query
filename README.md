# SQL-Query

**Duplicate Check SQL Query:** 
```sql
SELECT brand_name, strength, count(*) FROM medicines GROUP BY brand_name, strength HAVING count(*) > 1;
```

**Delete Duplicate Data Query:** 
```sql
Delete FROM medicines WHERE id IN (SELECT id FROM  (SELECT id, ROW_NUMBER() OVER( PARTITION BY brand_name, strength ORDER BY  id ) AS row_num FROM medicines ) t WHERE t.row_num > 1 );
```
