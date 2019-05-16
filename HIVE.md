# HIVE

创建表

`IF NOT EXISTS
 CREATE TABLE db.tableName(
​            id string)
​            ROW FORMAT SERDE 
​            'org.apache.hadoop.hive.serde2.lazy.LazySimpleSerDe' 
​            WITH SERDEPROPERTIES ('serialization.null.format'='') 
​            STORED AS TEXTFILE;`

修改表

`ALTER TABLE db.tableName
set SERDEPROPERTIES ('field.delim'=',','serialization.null.format'='\\N','quoteChar'='\"');`

本地文件导入

`load data [local] inpath '/tmp/files.csv' [overwrite] into table table_name;`

导出到本地文件

`insert overwrite [local] directory '/tmp/files.csv' ROW FORMAT DELIMITED FIELDS TERMINATED BY '\u0001' null defined as '' select * from table_name;`

合并输出文件

`cat file1.csv ,file2.csv > file.csv`

`cat files/* > file.csv`

## hive sql

将一行数据的字段old_col以','为分隔符切分，得到多行数据

`SELECT id, new_col FROM tableName lateral view explode(split(old_col,',')) old_col AS new_col;`

例：

| id   | old_col |
| ---- | ------- |
| 1    | A,B,C   |

| id   | new_col |
| ---- | ------- |
| 1    | A       |
| 1    | B       |
| 1    | C       |

将多行数据的字段old_col以‘,’为分隔符合并，得到一行数据（相同字段去重）

`SELECT id, concat_ws(',',collect_set(old_col)) as new_col FROM tableName;`

例：

| id   | old_col |
| ---- | ------- |
| 1    | A       |
| 1    | B       |
| 1    | A       |

| id   | new_col |
| ---- | ------- |
| 1    | A,B     |

