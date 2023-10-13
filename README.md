# Handling the HDFS file system

### What is HDFS ?
```text 
HDFS is a distributed file system that handles large data sets running on commodity hardware.
It is used to scale a single Apache Hadoop cluster to hundreds (and even thousands) of nodes.
HDFS is one of the major components of Apache Hadoop, the others being MapReduce and YARN.
```

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

![Untitled Diagram drawio](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/8cfdf06f-590a-470b-b6b2-1ecdc54cc5df)

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

## Create files in local
`touch {TP1CPP,TP2CPP,TP1JAVA,TP2JAVA,TP3JAVA}`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/44a99928-3cef-44b3-bcc2-749b70c1c0f4)

## Copy From Local to HDFS
`hdfs dfs -copyFromLocal {TP1CPP,TP2CPP} SDIA/PYTHON/TPs`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/0ffa9ce5-ca4f-4c6b-9791-1ad2e9d9f7c9)

## Display content of repository 
`hdfs dfs -ls -R SDIA`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/b3ab4d14-e043-4563-9cee-5a28440369f7)

## Remove file and directory
`hdfs dfs -rm SDIA/PYTHON/TPs/TP1CPP`

`hdfs dfs -rmr SDIA/JAVA`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/ce6f558f-ba16-4639-a3fc-630d0e27ce1b)

## Hadoop API FileSystem

The following example shows how to read from a text file in HDFS :

```java
public class Read {
    public static void main(String[] args) throws IOException {
        Configuration configuration = new Configuration();
        configuration.set("fs.defaultFS","hdfs://localhost:9000");
        FileSystem fileSystem = FileSystem.get(configuration);
        Path path = new Path("/user/hadoop/TP1JAVA/text");
        FSDataInputStream fsDataInputStream = fileSystem.open(path);
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(fsDataInputStream, StandardCharsets.UTF_8));
        String line = null;
        while((line = bufferedReader.readLine()) != null){
            System.out.println(line);
        }

        fsDataInputStream.close();
        bufferedReader.close();
    }
}
```

![image](https://github.com/el-moudni-hicham/bigdata-hdfs/assets/85403056/4bd68c9c-7e27-48dd-adaa-4eabf0b6a88e)

The following example shows how to write to a text file in HDFS :

```java
public class Write {
    public static void main(String[] args) throws IOException {
        Configuration configuration = new Configuration();
        configuration.set("fs.defaultFS","hdfs://localhost:9000");
        FileSystem fileSystem = FileSystem.get(configuration);
        Path path = new Path("/user/hadoop/TP1JAVA/text");
        FSDataOutputStream fsDataOutputStream = fileSystem.create(path);
        BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(fsDataOutputStream, StandardCharsets.UTF_8));

        bufferedWriter.write("JAVA1");
        bufferedWriter.newLine();
        bufferedWriter.write("PYTHON");
        bufferedWriter.newLine();

        bufferedWriter.close();
        fsDataOutputStream.close();
    }
}
```
