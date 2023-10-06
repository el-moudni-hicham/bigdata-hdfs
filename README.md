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

## Create the following tree in the HDFS 
`hdfs dfs -mkdir -p SDIA/{JAVA/{TPs,Cours},PYTHON/{TPs,Cours}}`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/ea7f31e7-34be-4665-968f-e910fb95115f)

`hdfs dfs -ls -R SDIA`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/61469a24-8648-4144-9f3f-8adbeaa7a06f)

## Create files in a directory
`hdfs dfs -touchz SDIA/PYTHON/Cours/{CoursPY1,CoursPY2,CoursPY3}`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/be3c5d4d-0d35-49f4-aba0-70e236a3f0d5)

## Add content to files 
`echo "Hi SDIA!" | hadoop fs -appendToFile - SDIA/PYTHON/Cours/CoursPY2`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/74b427d0-51a8-4911-bc0b-357200c1d03a)

## Display Content of files
`hdfs dfs -cat SDIA/PYTHON/Cours/CoursPY2`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/04827615-6775-4873-92fa-a4eae55cb85c)

## Copy files to another repository
`hdfs dfs -cp -f SDIA/PYTHON/Cours/{CoursPY1,CoursPY2,CoursPY3} SDIA/JAVA/Cours`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/736b19c6-f3ce-437a-94e6-2a2209c762cf)

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/e88bda5d-7469-41dd-8c19-bb897fbda0ee)

## Remove a file
`hdfs dfs -rm SDIA/JAVA/Cours/CoursPY1`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/e5dbd232-f22f-4b95-94ad-20a1107ee5a9)

## Rename files
`hdfs dfs -mv SDIA/JAVA/Cours/CoursPY2 SDIA/JAVA/Cours/CoursJAVA2`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/f720bccf-dbd3-4f2f-9e8c-1d777f92a13e)
