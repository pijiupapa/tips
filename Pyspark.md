# python环境变量设置

pyspark库不能使用pip安装，会导致无法正常使用集群配置和资源。应设置spark路径下的pyspark库。

```
echo 'export PYTHONPATH=/opt/cloudera/parcels/SPARK2-2.2.0.cloudera4-1.cdh5.13.3.p0.603055/lib/spark2/python:/opt/cloudera/parcels/SPARK2-2.2.0.cloudera4-1.cdh5.13.3.p0.603055/lib/spark2/python/lib/py4j-0.10.7-src.zip:$PYTHONPATH'>/etc/profile.d/pyspark.sh
source /etc/profile
```

