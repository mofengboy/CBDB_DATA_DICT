# 地址信息查询

## 查询某地的所有人物

```sql
SELECT 
    p.c_name_chn,
    p.c_index_year,
    a.c_addr_type,
    a.c_addr_id,
    a.c_notes
FROM 
    BIOG_MAIN p
    JOIN BIOG_ADDR_DATA a ON p.c_personid = a.c_personid
WHERE 
    a.c_addr_id = 'ADDR_1234'  -- 替换为实际地址ID
ORDER BY 
    p.c_index_year;
```

## 查询某人在某地的活动记录

```sql
SELECT 
    p.c_name_chn,
    a.c_addr_type,
    a.c_addr_id,
    a.c_year,
    a.c_notes
FROM 
    BIOG_MAIN p
    JOIN BIOG_ADDR_DATA a ON p.c_personid = a.c_personid
WHERE 
    p.c_name_chn = '张居正'
    AND a.c_addr_id = 'ADDR_1234'  -- 替换为实际地址ID
ORDER BY 
    a.c_year;
```

## 查询某地的行政区划变化

```sql
SELECT 
    ac.c_addr_id,
    ac.c_addr_name_chn,
    ac.c_addr_type,
    ac.c_addr_level,
    ac.c_parent_id,
    ac.c_notes
FROM 
    ADDR_CODES ac
WHERE 
    ac.c_addr_id = 'ADDR_1234'  -- 替换为实际地址ID
    OR ac.c_parent_id = 'ADDR_1234';
```

## 说明
- 第一个查询获取某地所有相关人物的信息
- 第二个查询获取特定人物在特定地点的活动记录
- 第三个查询获取某地的行政区划信息及其下级行政区划
- 可以根据需要修改查询条件，如使用其他地址ID或添加更多筛选条件 