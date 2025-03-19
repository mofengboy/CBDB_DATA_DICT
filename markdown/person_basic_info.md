# 人物基本信息查询

## 查询某位人物的基本信息

```sql
SELECT 
    p.c_personid,
    p.c_name_chn,
    p.c_name,
    p.c_index_year,
    p.c_birthyear,
    p.c_deathyear,
    p.c_dy,
    p.c_notes
FROM 
    BIOG_MAIN p
WHERE 
    p.c_name_chn = '张居正'
    OR p.c_name = 'Zhang Juzheng';
```

## 查询人物的亲属关系

```sql
SELECT 
    p1.c_name_chn as person_name,
    p2.c_name_chn as relative_name,
    k.c_kin_code,
    k.c_notes
FROM 
    BIOG_MAIN p1
    JOIN KIN_DATA k ON p1.c_personid = k.c_personid
    JOIN BIOG_MAIN p2 ON k.c_kin_id = p2.c_personid
WHERE 
    p1.c_name_chn = '张居正';
```

## 查询人物的官职信息

```sql
SELECT 
    p.c_name_chn,
    o.c_office_name_chn,
    o.c_office_rank,
    o.c_office_year,
    o.c_notes
FROM 
    BIOG_MAIN p
    JOIN BIOG_OFFICE_DATA o ON p.c_personid = o.c_personid
WHERE 
    p.c_name_chn = '张居正'
ORDER BY 
    o.c_office_year;
```

## 说明
- 第一个查询获取人物的基本信息，包括姓名、生卒年等
- 第二个查询获取人物的亲属关系，包括亲属姓名和关系类型
- 第三个查询获取人物的官职信息，按时间排序
- 可以根据需要修改查询条件，如使用其他人物姓名或添加更多筛选条件 