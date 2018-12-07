# 库

## 备份

`pg_dump dbname > outfile`

远程备份

`pg_dump -h host dbname > outfile`

备份压缩

`pg_dump dbname | gzip > filename.gz`

## 还原

`psql dbname < infile`

远程还原

`psql -h host dbname < infile`

还原压缩

`gunzip -c filename.gz | psql dbname`

# 表

## 导出

`COPY (SELECT * FROM tablename) TO '/tmp/filename.csv' (FORMAT CSV, DELIMITER ',', HEADER FALSE, QUOTE '"');`

`COPY tablename TO '/tmp/filename.csv'  WITH (FORMAT CSV, DELIMITER ',', HEADER FALSE, QUOTE '"');`

## 导入

`COPY tablename ( column_name , ...) FROM 'filename' WITH (FORMAT csv, DELIMITER ',', HEADER FALSE);`