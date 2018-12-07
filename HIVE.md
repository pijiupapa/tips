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
set serde 'org.apache.hadoop.hive.serde2.OpenCSVSerde'
WITH SERDEPROPERTIES ('separatorChar'='\u0001','serialization.null.format'='','quoteChar'='\"');`

本地文件导入

`load data local inpath '/tmp/files.csv' into table table_name;`

导出到本地文件

`insert overwrite local directory '/tmp/files.csv' ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' select * from table_name;`

合并输出文件

`cat file1.csv ,file2.csv > file.csv`

`cat files/* > file.csv`

