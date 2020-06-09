# Hadoop Cheat Sheet (Spark 2.2.0)

## WinSCP
Transfer files to Flux (and then to HDFS)

## Putty
Host: `cavium-thunderx.arc-ts.umich.edu`  
Duo two-factor login is required. 

## Terminal
Action|Command
---|---
set python path|`export PYSPARK_PYTHON=/usr/bin/python`
submit job|`spark-submit --master yarn --queue default filename`
Loading PySpark interactive shell|`pyspark --master yarn --queue default`
Loading PySpark w/ options|`pyspark --master yarn --queue default --num-executors 20 --executor-memory 5g --executor-cores 4`
List previous commands|`history`
how much space is left in `/home` quota|`du -sh /home/caoa`


## Useful hadoop specific commands

Apache Hadoop Documentation  
http://hadoop.apache.org/docs/r2.7.1/hadoop-project-dist/hadoop-common/FileSystemShell.html

See Tip #2 below

Action|Command
---|---
list directory|`hdfs dfs -ls`
copy file to hdfs|`hdfs dfs [-put][-copyFromLocal] filename destination`
overwite an existing file on hdfs|`hdfs dfs [-put][-copyFromLocal] -f filename`
get file from hdfs|`hdfs dfs [-get][-copyToLocal] filename destination`
rename file on hdfs|`hdfs dfs -mv oldname newname`
delete file|`hdfs dfs -rm filename`
delete directory|`hdfs dfs -rm -r directory`
get folder size|`hdfs dfs -du -s folder`
delete file and skip trash|`hdfs dfs -rm -skipTrash filename`
delete directory and skip trash|`hdfs dfs -rm -r -skipTrash directory`
empty trash bin (superuser privilege is required)|`hdfs dfs -expunge`

## Tips:
1. Need to be in the main directory when running spark-submit commands
2. `hdfs dfs` prefix is preferable to `hadoops fs` (legacy)
3. To exit PySpark interactive shell, type `exit()` or Ctrl-D

## Accessing a Jupyter Notebook on a remote machine (linux) from another computer browser (windows)
This url details a way to do this https://hsaghir.github.io/data_science/jupyter-notebook-on-a-remote-machine-linux/

OR

Follow these directions
https://github.com/caocscar/twitter-decahose-pyspark#using-jupyter-notebook-with-pyspark

## Problems

### Error
`Exception: Python in worker has different version 2.7 than that in driver 3.5, PySpark cannot run with different minor versions`

### Solution
```
export SPARK_YARN_USER_ENV=PYTHONHASHSEED=0  
export PYSPARK_PYTHON=/sw/dsi/centos7/x86-64/Anaconda3-5.0.1/bin/python
```
Then restart Spark job or interactive shell.
