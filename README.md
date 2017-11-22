# Hadoop Cheat Sheet (Spark 1.6.0)

## WinSCP
Transfer files to Flux (and then to HDFS)

## Putty
Host: flux-hadoop-login.arc-ts.umich.edu

## Terminal
activity|command
---|---
copy file to hdfs system|`hdfs dfs -put filename`
set python path|`export PYSPARK_PYTHON=/usr/bin/python`
submit job|`spark-submit --master yarn-client --queue default filename`
Loading pyspark interactive console|`pyspark --master yarn-client --queue default`
List previous commands|`history`

## Useful hadoop specific commands
action|command
---|---
list directory|`hdfs dfs -ls`
copy file to hdfs|`hdfs dfs -put filename`
grab file from hdfs|`hdfs dfs -get filename`
delete file|`hdfs dfs -rm filename`
delete directory|`hdfs dfs -rm -r directory`
overwite an existing file|`hadoop fs -put -f filename`

## Tips:
Need to be in the main directory (flux-hadoop-login) when running spark-submit commands

## Problems

### Error
Exception: Python in worker has different version 2.7 than that in driver 3.5, PySpark cannot run with different minor versions

### Solution
export SPARK_YARN_USER_ENV=PYTHONHASHSEED=0  
export PYSPARK_PYTHON=/sw/lsa/centos7/python-anaconda3/created-20170424/bin/python  
spark-submit --master yarn-client --queue default filename
