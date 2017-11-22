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

See Tip #2 below

action|command
---|---
list directory|`hdfs dfs -ls`
copy file to hdfs|`hdfs dfs [-put][-copyFromLocal] filename destination`
overwite an existing file on hdfs|`hdfs fs [-put][-copyFromLocal] -f filename`
grab file from hdfs|`hdfs dfs [-get][-copyToLocal] filename destination`
delete file|`hdfs dfs -rm filename`
delete directory|`hdfs dfs -rm -r directory`

## Tips:
1. Need to be in the main directory (flux-hadoop-login) when running spark-submit commands
2. `hdfs dfs` prefix is preferable to `hadoops fs` (legacy)

## Problems

### Error
Exception: Python in worker has different version 2.7 than that in driver 3.5, PySpark cannot run with different minor versions

### Solution
export SPARK_YARN_USER_ENV=PYTHONHASHSEED=0  
export PYSPARK_PYTHON=/sw/lsa/centos7/python-anaconda3/created-20170424/bin/python  
spark-submit --master yarn-client --queue default filename
