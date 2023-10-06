# Handling the HDFS file system

## Start Hadoop processes

`start-dfs.sh`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/afc31579-5f53-42c2-a7ac-cdc38f26e6d8)


`start-yarn.sh`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/9f13e926-68d6-43ac-8dd7-f8d4660ac5cd)

## verify that it is running with : 
`jps`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/c3398534-3e46-4d2a-bbf7-a4bf1b151af6)


## access the NameNode web interface with 
`http://localhost:50070`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/b8779ee7-fada-4ec3-9853-e1653915188b)

## Create the following tree in the HDFS '

`hdfs dfs -mkdir -p SDIA/{JAVA/{TPs,Cours},PYTHON/{TPs,Cours}}`
![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/ea7f31e7-34be-4665-968f-e910fb95115f)

`hdfs dfs -ls -R SDIA`
![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/61469a24-8648-4144-9f3f-8adbeaa7a06f)
