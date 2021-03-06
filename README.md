# til
> Today I Learned
- Collection & record regarding my daily learning. 
- Tech + product + business. 

---

## Progress

### 20210722
- Scala
	- generic type
	- upper/lower bound
	
### 20210720
- Java
	- mini progrject : Employer system
- Scala
	- flat map `transform to` for
	- design pattern
		- proxy
		- decorator
- Flink
	- SQL, Table API
	- status programming
		- exactly once

### 20210717
- Java
	- RMI VS RCP
		- [ref1](https://www.geeksforgeeks.org/difference-between-rpc-and-rmi/)
	- RMI in java
		- [ref1](https://www.tutorialspoint.com/java_rmi/java_rmi_introduction.htm)
- Flink
	- Exactly one when `sink`
		- Idempotent writes (冪等寫入)
			- [ref](https://stackoverflow.com/questions/2597876/how-to-make-write-operation-idempotent)
		- Transactional write (事務寫入)
			- Either all success or all fail
			- DB ACID
				- [ref](https://oldmo860617.medium.com/database-transaction-acid-156a3b75845e)
- Spark
	- make Spark CAN coneect to remote HIVE
		- put core-site.xml .... in main/resources -> 

- Scala
	- RMI in Scala
	- FP map filter and remove
		- [code](https://github.com/yennanliu/utility_Scala/blob/master/src/main/scala/AkkaDemo4SparkMasterWorker/master/SparkMaster.scala#L72-L77)

### 20210716
- Java
	- Hadoop filesystem for HDFS IO

### 20210703
- Java
	- SPRING VS Sprting MVC VS SPRING BOOT
		- [ref1](https://codertw.com/%E4%BC%BA%E6%9C%8D%E5%99%A8/141111/)
		- [ref2](https://kknews.cc/zh-tw/code/rlqroa4.html)
	- Spring IOC
		- Inversion Of Control
		- [ref1](https://ithelp.ithome.com.tw/articles/10156571)
		- [ref2](https://www.itread01.com/content/1550530454.html)
	- Spring DI
		- Dependency Injection
		- [ref1](https://iter01.com/520833.html)
	- java pojo
		- Plain old Java object
		- [ref1](https://www.baeldung.com/java-pojo-class)
		- [ref2](https://programdoubledragon.blogspot.com/2017/12/javabean-pojo.html)
- Scala
	- Design pattern : factory
	- Design pattern : abstract factory	


### 20210702
- Java
	- [java native memory tunnning](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr007.html)
- Spark
	- combineByKey
- Flink
	- Window API

### 20210629
- Spark
	- spark.speculation (Boolean)
		- `If set to "true", performs speculative execution of tasks. This means if one or more tasks are running slowly in a stage, they will be re-launched.`
		- https://spark.apache.org/docs/2.3.0/configuration.html
		- https://stackoverflow.com/questions/45265682/speculative-execution-mapreduce-spark

### 20210624
- Spark stream
	- spark stream save offset (in java)
		- https://blog.csdn.net/xueba207/article/details/50381821
	- spark stream Spark Streaming `numRecords must not be negative` error
		- https://blog.csdn.net/xueba207/article/details/51135423?utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-3.baidujs&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-3.baidujs

### 20210612
- https://medium.com/erens-tech-book/%E7%90%86%E8%A7%A3-process-thread-94a40721b492
- https://docs.python.org/zh-tw/3.8/library/collections.html#collections.defaultdict

### 20210531
- Flink
	- keyedStream and its op
	- datastream -> keyedStream
	- datastream op

### 20210530
- Scala
	- AKKA mini project : yellow chicken messenger
		- AKKA internet programming (via pcpip)
		- closure, curry review
- Java
	- abstract class, method, examples
	- polymorphism, downcasting review
- Spring framework
	- search twitter via controller
		- [ref](https://github.com/yennanliu/JavaHelloWorld/blob/main/SpringTwitter/src/main/java/com/yen/tweet/controller/TweetController.java)
	- code review
- Flink
	- DataStream API : basics
	- DataStream API : transformation
	- DataStream API : aggregation
	- user defined source
- Hadoop
	- file IO upload (via java client)
	- file IO download (via java client)
	- check file or directory (via java client)
- Django
	- ListView, DetailView

### 20210517
- Flink
	- slot
	- parallelism
	- combine 2 "missions" into one mission : if
		- one to one
		- parallelism are the same
		-  [ref1](https://www.youtube.com/watch?v=pYJsPxfytrY&list=PLmOn9nNkQxJGLnTsoWaHfvXrfpWiihoxV&index=14)
		- [ref2](https://www.youtube.com/watch?v=pYJsPxfytrY&list=PLmOn9nNkQxJGLnTsoWaHfvXrfpWiihoxV&index=15)
	- job DAG in taskmanager, workmanager, actual implementation step
- Spark
	- aggregatedBykey -> foldedBykey -> reducedBykey
- Java
	- block : more examples (static block, regular block)

### 20210516
- Hadoop
	- java client app : more file IO demos
	
### 20210515
- Hadoop
	- java client app : file IO, file delete, repartition
- Spark
	- reducebyKey VS groupby
	- map source code
- Scala
	- AKKA intro
	- AKKA factory
	- AKKA actror
	- async
- Java
	- singleton use cases
	- "餓漢式" VS "懶漢式" and its demo code

### 20210512
- Flink
	- Rolling policy
		- Row-encoded Formats
			- Custom RollingPolicy : Rolling policy to override the DefaultRollingPolicy
			- bucketCheckInterval (default = 1 min) : Millisecond interval for checking time based rolling policies
		- Bulk-encoded Formats
			- Bulk Formats can only have `OnCheckpointRollingPolicy`, which rolls (ONLY) on every checkpoint. 
		- [ref1](https://www.gushiciku.cn/pl/pdso/zh-tw)
		- [ref2](https://min.news/tech/e3d77943f8784d74b2d6eca0545a3ec3.html)
		- [ref3](https://ci.apache.org/projects/flink/flink-docs-release-1.13/docs/connectors/datastream/streamfile_sink/)
		- [ref4](http://jacobs.wanhb.cn/2018/12/20/Flink%E5%AE%9E%E6%88%98%E6%80%BB%E7%BB%93/)
- Hadoop
	- distcp command argument
		- [ref1](https://hadoop.apache.org/docs/current/hadoop-distcp/DistCp.html)

### 20210511
- Scala
	- build.sbt shadow dependency when assembly to jar
		- [ref1](https://stackoverflow.com/questions/57521738/how-to-solve-sbt-dependency-problem-with-spark-and-whisklabs-docker-it-scala)

### 20210510
- Java
	- static intro
	- static method, use example, use case
- Spark
	- zip
- Hadoop
	- java client install, intro

### 20210509
- Django
	- use `base.html` (html patten) and extend it in other htmls
		- [base.html](https://github.com/yennanliu/dj-restaurants/blob/main/mysite/templates/base.html)
		- [menu.html](https://github.com/yennanliu/dj-restaurants/blob/main/mysite/templates/menu.html)
- Flink
	- submit jobs
	- stand alone VS yarn
	- stand alone VS yarn architecture
	- Note : only stand alone mood has `flink UI` (or will use yarn UI)
	- flink CLI
	- core cocept : task manager, job manager, resource manager task slot... ( may different in stand alone VS yarn mood)

### 20210508
- AWS EMR
	- basics : master node, task node, worker node ..
	- how namenode, datanode installed in EMR clusters
	- minimum requirement for a working EMR clusters
	- hive : basics
	- hive 1.x over mapreduce VS hive 2.x on tez
		- [ref](https://www.infoq.cn/article/apache-tez-saha-murthy?fbclid=IwAR3LpojhZRbUYWHBRX97CDLOhr0BpzgNsbL_IzqLOznPrOOBkEdSZMc8SDI)
	- beestream 

### 20210507
- HDFS
	- more basic commands : 
		- check file size : hdfs dfs -du, hdfs dfs -du -h, hdfs dfs -du -h -s
		- file permission : -chgrp, chmod, -chown
			- [example](https://github.com/yennanliu/utility_shell/blob/master/hadoop/hadoop_command.sh#L205)
	- HDFS RM API
		- [example](https://github.com/yennanliu/utility_shell/blob/master/hadoop/hadoop_command.sh#L218)
- Spark
	- union, intersect, Cartesian product

### 20210506
- Flink
	- save kafka event to HDFS
		- [code](https://github.com/yennanliu/flinkhelloworld/blob/master/src/main/scala/streamKafkaToHDFS/streamKafkaToHDFSV1.scala)

### 20210505
- Flink
	- process from socket
	- process from kafka
	- process from socket and save to HDFS
	- submit job command to local job manager
	- stand alone mood VS job manager- task manager - worker mode
- Spark
	- source code : repartition VS coalesce
	- source code : filter
	- source code : distinct
	- process stream from multiple kafaka topic and save to different HDFS bucket
		- [code](https://github.com/yennanliu/KafkaSparkPoc/blob/main/spark/src/main/scala/com/yen/streamKafkaToHDFS/streamKafkaToHDFSV2.scala)

### 20210503
- Java
	- class Encapsulation
- Spark
	- RDD partition, map, flatMap source code go through
- Hadoop
	- hdfs architecture
		- basic
		- HA
	- data block & size  -> default block size : 128 MB
	- common hdfs issues
	- factors affect HDFS IO speed
		- partition
		- block size
		- file counts
		- hard disk speed (data transmission)
		- metastore

### 20210501
- DynamoDB
	- read capacity unit (RCU)
	- write capacity unit (WCU)
	- architecture
	- index, secondary index
	- sorting key
	- partition
	- read/write consistency
	- basic commands

### 20210430
- Scala
	- mini project : customer system - modify/delete customer
- Java
	- unit-test intro
	- toString, equals re-write
- Django
	- user permission, comment permission
	- local auth, comment auth

### 20210429
- Spark
	- mapPartition - define partition explicitly
	- "nearby rules" ( mapping with anonymous func)
		- [ref](https://www.youtube.com/watch?v=TVWJ-YBfKWQ&list=PLmOn9nNkQxJF-qlCCDx9WsdAe6x5hhH77&index=33)


### 20210427
- Scala
	- [parallel collections](https://github.com/yennanliu/utility_Scala/blob/master/src/main/scala/ScalaAdvance/parallel_Demo_1.scala)
	- [operaor](https://github.com/yennanliu/utility_Scala/blob/master/src/main/scala/ScalaBasic/Operator_demo1.scala)
- Java
	- [extends intro](https://github.com/yennanliu/JavaHelloWorld/blob/main/src/main/java/Basics/Extends_demo1)

### 20210426
- Spark
	- add watermark to stream strcture df
		- [code](https://github.com/yennanliu/KafkaSparkPoc/blob/main/spark/src/main/scala/com/yen/streamSocketToHDFS/streamSocketEventToHDFSV4.scala)
	- load stream with schema
		- [code](https://github.com/yennanliu/KafkaSparkPoc/blob/main/spark/src/main/scala/com/yen/streamSocketToHDFS/streamSocketEventToHDFSV3.scala)
- Scala
	- mini project : customer system - adding customer
- Java
	- `==` VS equals
	- re-write `equals`
- Hadoop
	 - hadoop source code intro
	 - compile Hadoop source code
- Flink
	- submit task, and test
	
### 20210425
- Java
	- `==` intro
	- `equals` intro

### 20210424
- Java
	- object's finalize() method
	- java's gc (garbage collection) mechanism
- Spark
	- spark core source code visit
	- ways create RDD
	- defince RDD partition explicitly
- Hadoop
	 - sync time within clusters
	 
### 20210421
- Scala
	- [try - catch example](https://github.com/yennanliu/utility_Scala/blob/master/src/main/scala/ScalaBasic/ExceptionDemo3.scala)
- Java
	- polymorphism upcasting
	- polymorphism downcasting

### 20210418
- Hadoop
	- Thing to note when lanuch hadoop cluster in "distributed" mood

### 20210417
- Django
	- form model (generate form from Django class)
		- [example](https://github.com/yennanliu/dj-restaurants/blob/main/mysite/restaurants/views.py#L25)
	- login auth
- Scala
	- DatetimeUtils
- Java
	- polymorphism examples
- Spark
	- stand alone VS yarn VS local
	- spark yarn mood job history config setup

### 20210416
- Java
	- polymorphism intro
- Scala
	- "control abstraction"
		- [video](https://www.youtube.com/watch?v=wxF1PWk7U4E&list=PLmOn9nNkQxJEqCNXBu5ozT_26xwvUbHyE&index=172)

### 20210415
- Spark
	- case class -> RDD -> df (?)
	- Array -> RDD -> df
	- df -> Parquet (append mood)

### 20210413
- Python
	- multi processing
		- [multi parallel process via multiprocessing](https://stackabuse.com/parallel-processing-in-python/)
		- [multi process via threading](https://realpython.com/intro-to-python-threading/)
	- multi threading
		- [code](https://github.com/yennanliu/utility_Python/blob/master/multi_treading/multi_thread2.py)

### 20210410
- Django
	- form interact with views, urls and DB
		- [commit](https://github.com/yennanliu/dj-restaurants/commit/ea148eca550de9dba416b2958c799937914af4a9)
- Scala
	- Currying Function
	- closure
		- [ref](https://www.tutorialspoint.com/scala/scala_closures.htm#:~:text=A%20closure%20is%20a%20function,variables%20declared%20outside%20this%20function.&text=Now%20factor%20has%20a%20reference,its%20current%20value%20each%20time.)
- Java
	- steps by stpes : children class instantiation
- Spark
	- SparkYarnCluster running mode intro

### 20210409
- MapReduce
	- MapReduce OOM exception (out of memory)
	 	- [ref1](https://community.cloudera.com/t5/Support-Questions/Map-and-Reduce-Error-Java-heap-space/td-p/45874)
- Hadoop Streaming
	- [ref1](https://blog.csdn.net/baichoufei90/article/details/82861440)
- Java
	- super call attr, methods...
	- super call constructor
- Spark
	- - SparkYarnStandAlone running mode intro

### 20210408
- Zookeeper
	- [zk cli](http://www.corejavaguru.com/bigdata/zookeeper/cli)

### 20210407
- Scala
	- [future](https://docs.scala-lang.org/overviews/scala-book/futures.html)

### 20210406
- Java
	- override details 

### 20210405
- Scala
	- anonymous function
- Java
	- debug in Eclipse
	- debug in Eclipse in a project
- Saprk
	- spark stand alone architecture
	- spark stand alone env setup/build

### 20210404
- Scala
	- partialFunction
- Django
	- model
	- admin app

### 20210401
- gRPC intro : [ref](https://pjchender.blogspot.com/2021/03/grpc-golang.html?fbclid=IwAR3xhGHhRQHLYm0I7Z3A42-PSU5CYRqRI4ioP0Gc0hq3vZtWNH0ky--k2nc)
- Java
	- Spring
		- cache
- Hadoop 
	- checksum
		- [ref1](http://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-common/FileSystemShell.html#checksum)
		- [ref2](https://blog.csdn.net/lb812913059/article/details/79718303)
		- [ref3](https://community.cloudera.com/t5/Community-Articles/Comparing-checksums-in-HDFS/ta-p/248617)
	- FileSystem javs class
		- [hadoop/fs/FileSystem](https://hadoop.apache.org/docs/r2.8.2/api/org/apache/hadoop/fs/FileSystem.html)
		- [hadoop/fs/FileStatus](https://hadoop.apache.org/docs/r2.8.2/api/org/apache/hadoop/fs/FileStatus.html)

### 20210331
- Scala
	- pattern matching "nest structure" 1
- Java
	- Inheritance intro
- Spark-stream
	- [streaming-kafka-integration](http://spark.apache.org/docs/latest/streaming-kafka-integration.html)
	- [streaming-programming-guide](http://spark.apache.org/docs/latest/streaming-programming-guide.html)

### 20210330
- Scala
	- pattern matching "inner" expression :  ```case first::second::rest => println(first, second, rest.length)```
- Java
	- mini project : CMutility
		- project summary
- Hadoop
	- scp
	-  sudo chown give file permission from root to user : [code](https://github.com/yennanliu/utility_shell/blob/master/hadoop/hadoop_command.sh#L14)
- Docker support file system

### 20210329
- Scala
	- case class
- Java
	- mini project : CMutility
		- "CustomView" delete client 
- Distcp
	- what if file already existed in the "destination path" ?
		- https://hadoop.apache.org/docs/current/hadoop-distcp/DistCp.html
		- By default, files already existing at the destination are skipped (i.e. not replaced by the source file). A count of skipped files is reported at the end of each job, but it may be inaccurate if a copier failed for some subset of its files, but succeeded on a later attempt.
	- atomic commit
		- https://hadoop.apache.org/docs/current/hadoop-distcp/DistCp.html
		- `-atomic {-tmp <tmp_dir>}`
		- `-atomic instructs DistCp to copy the source data to a temporary target location, and then move the temporary target to the final-location atomically. Data will either be available at final target in a complete and consistent form, or not at all. Optionally, -tmp may be used to specify the location of the tmp-target. If not specified, a default is chosen. Note: tmp_dir must be on the final target cluster. `

### 20210328
- Scala
	- var match pattern
	- for loop match pattern
	- Nest class (inner, outer) review
- Java
	- mini project : CMutility
		- "CustomView" delete/modify client
- Django
	- [restaurants app](https://github.com/yennanliu/dj-restaurants)
		- views, urls, db model, db migration

### 20210326
- Scala
	- pattern match with tuple
- Java
	- mini project : CMutility
		- "CustomView" development
- Flink
	- env set up (config, scripts) intro

### 20210325
- Airflow
	- [dynamic-task-definition-in-airflow](https://stackoverflow.com/questions/48825335/dynamic-task-definition-in-airflow)
	- [airflow-trigger-schedule-dag-rerun-on-completion-file-sensor](https://stackoverflow.com/questions/44770070/apache-airflow-trigger-schedule-dag-rerun-on-completion-file-sensor)
	- [hdfs_sensor](https://airflow.apache.org/docs/apache-airflow/1.10.4/_modules/airflow/sensors/hdfs_sensor.html#HdfsSensor)

### 20210324
- Scala
	- pattern match with List, class array
- Airflow
	- [retrieve a value in xcom pushed via BashOperator](https://groups.google.com/g/airbnb_airflow/c/-5WvigVS0ks/m/90b41NaMAQAJ)

### 20210323
- Airflow
	- [Airflow 2.0: DAG Authoring Redesigned : XCom, XComArg, @task decorator, Custom XCom backends](https://medium.com/apache-airflow/airflow-2-0-dag-authoring-redesigned-651edc397178)
	- [example_xcom](https://github.com/apache/airflow/blob/master/airflow/example_dags/example_xcom.py)
	- [xom example1](https://towardsdatascience.com/elementals-of-airflow-part-1-6e4ce1de4dfb)
- Hadoop
	- Hadoop run jar (built from scala)

### 20210322
- Scala
	- value with pattern match
- Spark-streaming
	- updateStatusBykey more examples

### 20210321
- Airflow
	- dynamic workflows in DAG
		- [ref1](https://stackoverflow.com/questions/41517798/proper-way-to-create-dynamic-workflows-in-airflow)
- Scala
	- pattern match "daemon"
	- pattern match more examples
- Java
	- import
	- MVC more understanding

### 20210320
- Scala
	- GENERIC CLASSES
		- [ref1](https://docs.scala-lang.org/tour/generic-classes.html)
		- [ref2](https://www.jianshu.com/p/caca1ba8976e)
	- match intro (pattern match)
- Java
	- package intro
	- MVC intro
- Spark-streaming
	- transform
	- updateStatusBykey

### 20210319
- Server
	- generate public key so can ssh connect to remote server : [ref](https://cloud.ibm.com/docs/ssh-keys?topic=ssh-keys-generating-and-using-ssh-keys-for-remote-host-authentication) : useful for airflow
- Unix
	- [unix file permission](https://www.elated.com/understanding-permissions/)
- Hadoop
	- [Hadoop Delegation Token 1](https://www.athemaster.com/resources/47)
	- [Hadoop Delegation Token 2](https://www.athemaster.com/resources/48)

### 20210318
- Scala
	- group op : stream, view, concurrent 
- Java
	- `this` example, `this` call constructor

### 20210311
- Java
	 - Encapsulation basic usage
- Scala
	- flatMap, filter (functional programming)
- Spark
	- executor memory
	- executor OOM
	- groupBykey
	- cache VS persist

### 20210310
- Java
	- [Java Class Modifiers](https://www.w3schools.com/java/java_modifiers.asp)
- Scala	
	- Map operation (functional programming)
	- high order function intro
		- [ref](https://docs.scala-lang.org/tour/higher-order-functions.html)
		- Functions that accept functions

### 20210309
- Hive
	- make db, create table, load jar, load data, add partition : [ref code](https://github.com/yennanliu/utility_shell/blob/master/hive/hive_command.sql)
- Bash
	- split string by value
		- [code1](https://github.com/yennanliu/utility_shell/blob/master/text/split_string1.sh)
		- [code2](https://github.com/yennanliu/utility_shell/blob/master/text/split_string2.sh)
- Scala
	- set
- Java
	- Encapsulation implementation (getter, setter)

### 20210308
- HDFS
	- `filter` : exclude files with pattern when copy via distcp
		- [ref1](https://sapser.github.io/bigdata/2016/09/30/distcp-filters-usage)
		- [ref2](https://cloudera.ericlin.me/2016/01/how-to-use-filters-to-exclude-files-when-in-distcp/)
- Java
	- anonymous object implementation
		- [ref1](https://github.com/yennanliu/JavaHelloWorld/blob/main/src/main/java/Basics/AnonymousObject1.java)
		- [ref2](https://github.com/yennanliu/JavaHelloWorld/blob/main/src/main/java/Basics/AnonymousObject2.java)

### 20210307
- Java
	- Encapsulation intro
- Scala
	- Map (immuatable, mutable)
	- Map create, get values from Map
	- go through Map, add/delete elements from Map
- HDFS
	- [Unable to close file because the last block does not have enough number of replicas](https://blog.csdn.net/u013289115/article/details/105220663/?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-0&spm=1001.2101.3001.4242)
	- [understanding-hdfs-recovery-processes pt.1](https://blog.cloudera.com/understanding-hdfs-recovery-processes-part-1/)
	- [understanding-hdfs-recovery-processes pt.2](https://clouderatemp.wpengine.com/blog/2015/03/understanding-hdfs-recovery-processes-part-2/)
	- [appendDesign3](https://github.com/yennanliu/data_science_repo/blob/master/book/hadoop/appendDesign3.pdf)
- Flink
	- [Unable to close file because the last block does not have enough number of replicas](https://blog.csdn.net/knowledgeaaa/article/details/103117868)
	- [bulk-format](https://ci.apache.org/projects/flink/flink-docs-stable/dev/connectors/streamfile_sink.html#bulk-encoded-formats)

### 20210306
- Scala
	- either : left, right
		- [ref1](https://alvinalexander.com/scala/scala-either-left-right-example-option-some-none-null/)
		- [ref2](https://www.scala-lang.org/api/2.12.0/scala/util/Either.html)

	- option : some, none

- Spark-streaming
	- digest from kafka (low level api)
		- [ref](https://www.youtube.com/watch?v=sDytAIL7CJY&list=PLmOn9nNkQxJF-qlCCDx9WsdAe6x5hhH77&index=100)

- Hadoop
	- RM : resource manager : manage resources : [ref](https://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/ResourceManagerHA.html)
	- NM : node manager : manager for single node : [ref](https://hadoop.apache.org/docs/r3.1.1/hadoop-yarn/hadoop-yarn-site/NodeManager.html)

### 20210305
- Spark-streaming
	- Kafka integration : spark-streaming-kafka jar
		- KafkaUtils : read stream from kafka
		- KafkaCluster : save the offset
	- mainly using kafka `low level` API
		- low level : Direct Dstrean
		- high level : Receiver Dstream
	- [ref](https://www.youtube.com/watch?v=kBvFSbXjKD4&list=PLmOn9nNkQxJF-qlCCDx9WsdAe6x5hhH77&index=97)
- Scala
	- Queue op : enqueue, dequeue, last, head...
- Java
	- class design part 2, class in-memory (stack, heap)
	- Spring with css, jquery
- Apache Flume : 
	- Apache Flume is a distributed, reliable, and available system for efficiently collecting, aggregating and moving large amounts of log data from many different sources to a centralized data store.
	- [ref1](https://flume.apache.org/FlumeUserGuide.html)
	- [ref2](https://data-flair.training/blogs/apache-flume-installation-tutorial/)
	- [ref3](https://blog.csdn.net/qq_39521554/article/details/81194772)
- Kafka:
	- kafka connect:
		- https://www.confluent.io/blog/kafka-connect-deep-dive-converters-serialization-explained/
		- https://www.confluent.io/blog/kafka-connect-deep-dive-error-handling-dead-letter-queues/
		- https://talks.rmoff.net/DQkDj3#sw2vXks
		- https://www.instaclustr.com/apache-kafka-connect-architecture-overview/
- Big Data SMACK:  `Apache Spark, Mesos, Akka, Cassandra, and Kafka`
	- https://bigdata-madesimple.com/smackspark-mesos-akka-kafka/

### 20210304
- Scala
	- Queue : basic ops
- Spark
	- spark read ORC data : [ref](https://sparkbyexamples.com/spark/spark-read-orc-file-into-dataframe/)
```python
# pyspark
orc_data = spark.read.orc(orc_path)
orc_data.createOrReplaceTempView("orc_table")
```
	
### 20210303
- Scala
	- List basics ops 1-3
	- tuple
	- Scala object <--> Java object
- Java
	- recursion
	- method pass dynamic param

### 20210302
- Scala
	- apply re-visit
	- case class VS case class instance
- HDFS
	- stale datanode

### 20210301
- Java
	- value transfer : basic data structure
	- value transfer : reference class/array
- Scala
	- Java collections <--> Scala collections
	- 1-D, N-D (dimension) array
	- tuple
	- list
	- update list method : (1), (2)

### 20210228
- Scala
	- dynamic array
	- 1-D  (dimension) array
	- immutable, mutable relation

### 20210225
- Java
	- Lambda function
	- array class in-memory

- Scala
	- immutable and mutable
	- immutable and mutable layer

### 20210224
- Spark
	- [ScalaReflection](https://github.com/apache/spark/blob/master/sql/catalyst/src/main/scala/org/apache/spark/sql/catalyst/ScalaReflection.scala)
- Scala
	- Option:
		- [ref1](https://blog.csdn.net/JasonDing1354/article/details/46788787)
		- [ref2](https://www.tutorialspoint.com/scala/scala_options.htm)

### 20210223
- Scala
	- companion
	- Object VS class : [ref](https://github.com/yennanliu/utility_Scala/blob/master/src/main/scala/ScalaBasic/Class_VS_Object_2.scala)

- Java
	- static method/value....

### 20210221
- Flink
	- flink save to HDFS
	- flink api with scala 2.12.X (to fix)
		- [scala versions](https://www.scala-lang.org/download/)
- Luigi
	- allocate workers to jobs
- Airflow
	- default config, init DB get DAG reloaded
- Java
	- object, class in-momory
	- Spring RESTful
- Scala
	- implicit value
	- implicit class
	- implicit method
	- implicit transformation
	- "class in class"
- SBT
	- allocate more resources on scala/sbt build server : [ref](https://github.com/yennanliu/utility_shell/blob/master/intellij/intellij_command.sh)

### 20210217
- Hadoop
	- [QoS (quality of service)](https://tech.ebayinc.com/engineering/quality-of-service-in-hadoop/) : use Qos deal with namenode slowdown

### 20210215
- Java
	- class im-memory
		-[ref](https://github.com/yennanliu/CS_basics/tree/master/doc/pic/java)
	- class basics
	
### 20210214
- Flink
	- scala example implementation
		- [GroupedProcessingTimeWindowExample.scala](https://github.com/yennanliu/flinkhelloworld/blob/master/src/main/scala/examples/GroupedProcessingTimeWindowExample.scala)
		- [TopSpeedWindowing.scala](https://github.com/yennanliu/flinkhelloworld/blob/master/src/main/scala/examples/TopSpeedWindowing.scala)
- Scala
	- review : super in parent, children class, constructor
		
### 20210210
- Hadoop
	- Hadoop rebalancing
		- [ref1](https://www.informit.com/articles/article.aspx?p=2755708&seqNum=5)
	- Hadoop NN active, standby (HA)
	- Hadoop config
	- Hadoop pseudo mode
	- HDFS formatting
	- Hadoop MR (map reduce) job (wordcount)
	- Hadoop check logs
- Scala
	- trait (sth similar to java interface)
	- trait basics, trait "dynamic import"
	- trait implementation
- Java
	- interface
- Git
	- git stash, git stash apply
		- [ref code](https://github.com/yennanliu/utility_shell/blob/master/git_github/git_command.sh#L91)

### 20210201
- Scala
	- Companion, Singleton
	- Anonymity sub class
	- abstract class
- Hadoop
	- HDFS trash
	- "small files" in Namenode
	- copy files
- Java
	- Bit operation   (>>, <<, ..)
	- logic operation (||, &&, |, &, ^, ...)

### 20210129
- Hadoop
	- kerberos, core-site.xml...
- Airflow
	- ssh to local machine (via insert setting to connections table in DB)
	- [example](https://github.com/DataEngDev/airflow_in_docker_compose/blob/master/docs/quick_start_airflow.md)
- Scala
	- super method, re-write method

### 20210125
- Hadoop
	- hadoop streaming concept
	- hadoop streaming arguments
	- hadoop streaming output
	- hadoop streaming avoid key as prefix :
		- [ref](https://stackoverflow.com/questions/7153087/hadoop-compress-file-in-hdfs/9572706)
	- [ref1](http://hadoop.apache.org/docs/r1.2.1/streaming.html#:~:text=Hadoop%20streaming%20is%20a%20utility,mapper%20and%2For%20the%20reducer.)
- Scala
	- super method in class
	- transform class type
	- rewrite method
- Spark streaming
	- left, right join

### 20210124
- Hadoop kerberos
	 - [ref1](https://www.twblogs.net/a/5c3608aabd9eee35b21d35ed)
- Hadoop realms

### 20210123
- Java Visibility of Variables and Methods
	-  Visibility modifiers
		- default, public , protected, private
	- [ref1](https://www.oreilly.com/library/view/learning-java-4th/9781449372477/ch06s04.html#:~:text=Private%20members%20are%20not%20visible,other%20classes%20in%20the%20package.&text=The%20protected%20modifier%20allows%20special%20access%20permissions%20for%20subclasses.&text=Methods%20and%20variables%20are%20always,doesn't%20address%20that%20scope.)
	- [ref2](https://www.runoob.com/java/java-modifier-types.html)
	- [ref3](https://www.youtube.com/watch?v=t0rVwF5AF4E&list=PLmOn9nNkQxJEqCNXBu5ozT_26xwvUbHyE&index=69)

### 20210120
- Scala
	- import packages
	- OOP design 1st part
	
- Hadoop
	- namespace intro
	- connection between namenode, datanode
	- set up namespace in datanode
	- white, black list
	
- Spark stream
	- join stream
	
- Airflow
	- docker-compose airflow
	
### 20210114
- Hadoop
	- [NS2](https://hadoop.apache.org/docs/r2.7.0/hadoop-project-dist/hadoop-hdfs/HDFSHighAvailabilityWithQJM.html)
- Java
	- [Stack](https://www.javatpoint.com/java-stack)

### 20210112
- Scala
	- constructor parameter, attribution
	- @BeanProperty
	- Scala class create steps
- Java
	- basic data type revisit : char, double, float...
	- variable
	- operator

### 20210111
- Spark-streaming
	- joining streaming to static source
	
### 20210110
- System design
	- GFS (google file system)
	- big table
- Scala
	- constructor
- Java
	- constructor
- Hadoop
	- haddop 1 VS hadoop 2
	- hadoop version
	- hadoop ecosystem (in layers)
	- hadoop architecture

### 20210108
- Java
	- JDK, JRE, JVM
	- JDK : java development kit (for java program development), including JRE.
	- JRE : java runtime environment (offer environment for java program running), including JVM.
	- JVM : java virtual machine (the virtual machine that runs java program).
	- summary:
		- JDK = JRE + development kit ( e.g. javac ..)
		- JRE = JVM + JAVA SE library
	- [ref](https://www.youtube.com/watch?v=JMqb_VP_Myw&list=PLmOn9nNkQxJH0qBIrtV6otI0Ep4o2q67A&index=27)
- Scala
	- default value, class, class Polymorphism, more OOP
- Spark-streaming
	- sliding window VS tumbling window
- Hadoop
	- `NameNode (nn)` : storage metadata for data, e.g. : created_time, doc name, doc structure, partition, access level ..
	- `DataNode (dn)` : storage data (data block) and data block information
	- `Secondary NameNode (2nn)` : monitor hadoop backend processing, do snapshot on hadoop data 

### 20210107
- Scala
	- class attribute value, class member value
	- default value must with explicit type 
		- [video](https://www.youtube.com/watch?v=_4nmcvaB3Tg&list=PLmOn9nNkQxJEqCNXBu5ozT_26xwvUbHyE&index=53)
- Java
	- getter, setter : 
		- the way encapsulation for field in the object.
		- The `public access interface` for `private values/field` interaction
		- In OOP, we want to keep some values "private", prevent them from changed by others, so we use `setter` set up the values, and `getter` get the values
		- [ref](https://pydoing.blogspot.com/2011/05/java-getter-and-setter.html)
		- [ref2](https://dotblogs.com.tw/law1009/2012/01/06/64665)
- Hadoop
	- [BZIP2 is splittable in hadoop](https://stackoverflow.com/questions/14820450/best-splittable-compression-for-hadoop-input-bz2)
	- [Spark process BZIP2](https://www.waitingforcode.com/apache-spark/bzip2-compression-apache-spark/read)
- Spark-streaming
	- watermarking on windows
	- watermarking on output modes (append..)

### 20210106
- Spark-streaming
	- watermark
	- watermark with window
- Scala
	- error handling
	- exception
		- try-catch-finally
	- Scala OOP
		- everything in Scala is "object"

### 20210105
- Kubernetes
	- [Kubernetes Tutorial for Beginners [FULL COURSE in 4 Hours]](https://www.youtube.com/watch?v=X48VuDVv0do)
### 20210104
- Hadoop
	- klist
	- kinit
	- hadoop client connect to clusters
	- hadoop compress
- Flink
	- value broadcast
	- cache
	- distributed cache
	- [ref code](https://github.com/yennanliu/flinkhelloworld/blob/master/src/main/scala/examples/BatchDemoDistributedCache.scala)

### 20210103
- Hadoop
	- keytab & Kerberos
		- ref : https://codertw.com/%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80/585988/
	- hadoop-streaming
		- ref : https://hadoop.apache.org/docs/r1.2.1/streaming.html#:~:text=Hadoop%20streaming%20is%20a%20utility,mapper%20and%2For%20the%20reducer
- Spark-streaming
	- Tumbling window VS sliding window
		- Tumbling window : `Non-overlap` window
		- Sliding window : `Overlap` window
		
### 20210102
- Scala
	- recursion
	- function 
		- without return : Unit
		- type inference
		- case class
- Spark-streaming
	- working with kafka
	- kafka stream serialization & deserialization
	- kafka AVRO sinks 
	- kafka AVRO sources
	- Stateless VS Stateful
- Hive
	- general intro
	- architecture
	
### 20201226
- Java
	- Ternary Operator
		- [ref1](https://yubin551.gitbook.io/java-note/basic_java_programming/operator/ternary_instanceof)
- Scala
	- Control logic
	
### 20201225
- Spark
	- Streaming basic
	- Streaming config
	- Streaming from port

### 20201224
- Scala
	- `Implicit`
		- `implicit` is the way that you dont need to pass parameters explicitly in functions in Scala, but Scala will be able to find them from the `implitict scope` once you defined them. Use implicit can make your function more general and easy to import/deal with different cases per pattern
		- [ref](https://docs.scala-lang.org/tour/implicit-parameters.html)
	- Scala `control logic` (if else..)
- HDFS
	- compression HDFS file
		- [ref](https://dev.classmethod.jp/articles/compress-output-of-hadoop-streaming-on-emr/)
- Flink
	- java code exmaple
	- pipeline workflow
	- clusters build doc
	- build project with maven
	
- Airflow
	- work with macro, timestamp

### 20201223
- Scala
	- run object method directly in application scala
	- Scala read std in from CLI
	- Scala read args in from CLI
		- [ref](https://www.youtube.com/watch?v=L5guBZlFsU8&list=PLmOn9nNkQxJEqCNXBu5ozT_26xwvUbHyE&index=31)
		- [ref code : read args](https://github.com/yennanliu/utility_Scala/blob/master/src/main/scala/ScalaBasic/ScalaReadCLIArgs_Demo1.scala)
		- [ref code : read std](https://github.com/yennanliu/utility_Scala/blob/master/src/main/scala/ScalaBasic/ScalaReadCLIArgs_Demo1.scala)

- Hive
	- [Metastore](https://jaceklaskowski.gitbooks.io/mastering-spark-sql/spark-sql-hive-metastore.html)
	- [Catelog](https://docs.cloudera.com/csa/1.2.0/flink-sql-table-api/topics/csa-hive-catalog.html)

### 20201222
- Alluxio
	- HDFS cache
	- [Alluxio](https://www.alluxio.io/)
- HDFS
	- compression
	- file type
- Scala
	- akka intro : [ref](https://www.yangbajing.me/scala-web-development/)

### 20201217
- git
	- git stash
	- git stash list
	- git stash pop stash@{2}
	- git stash pop ( = git stash pop stash@{0})
	- git stash apply stash@{0} ( = git stash pop stash@{0} )
	- git stash drop stash@{0}
	- [ref](https://gitbook.tw/chapters/faq/stash.html)
	
- hadoop distcp arguments
- Scala
	- implicits
	- partial function
	- partial apply function
	
### 20201216
- sbt
	- sbt docker
		- [poc project](https://github.com/yennanliu/sbtDockerPOC)
		- [spark-jobserver](https://github.com/yennanliu/spark-jobserver)
- Scala
	- Typeconfig
	- load different config
	
### 20201211
- Hadoop
	- hadoop distcp
		- atomic
		- update
		- replace
- SBT
	- sbt-docker
	- sbt publish
- Scala
	- AppConfig
	- Configfactory

### 20201210
- Kafka
	- Confluent examples
		- https://kafka-tutorials.confluent.io/kafka-connect-datagen-local/kafka.html
		- https://kafka-tutorials.confluent.io/create-tumbling-windows/ksql.html

### 20201209
- Kafka
	- consumer low level API
	- source code go through
- Scala
	- Any, AnyValue, AnyRef
	- implicit transform
	- can give "low level" dtype to "high level" dtype, but not vice versa
- Hive
	- alter table command
	- update schema
	- external VS internal table
	- ddl build, alter table
- sbt
	- build-info
	- sbt version
	- sbt assembly, sbt plugin

### 20201125
- Scala
	- comment -> auto generate API doc
	- var, val point to storage space
	- how scala use/re-write part of java lib as well as write itself one
	- sbt publish
		- [ref](https://www.itdaan.com/tw/7467238dd6d1)
- Hive
	- repartition
- [Apache ORC](https://orc.apache.org/)
	- the smallest, fastest columnar storage for Hadoop workloads.
- Jenkins
	- check `.git` when specific branch is merged/... then run
	
### 20201124
- Spark
	- dataframe concat 2 / multitple columns
	- saveToTable/save partition by list of columns
	- data skew consideration (per executor)
- Hive
	- external table
	- partition
	- create table from parquet file
- Airflow
	- run hive distcp
	- run spark

### 20201124
- Kafka
	- Producer hive level API implementation
		- [ProducerHighLevelAPI](https://github.com/yennanliu/KafkaHelloWorld/blob/master/KafkaJava/src/main/java/KafkaCourse/ProducerHighLevelAPI.java)
	- kafka stream
	- source code
- Scala
	- scala compile process
	- scala basic syntax/style revisit
	- scala VS java
- Java
	- Spring RESTful API dev
		- [/src/main/java/com/yen/payrollREST](https://github.com/yennanliu/JavaHelloWorld/tree/main/SpringRESTService/src/main/java/com/yen/payrollREST)

### 20201116
- Kafka
	- high level API
	- low level API
	- re-write method
	- re-load method
	- Java API consumer
	- Java API producer
- Zookeeper
	- zookeeper file structure (storage for meta)
- Apache Flume
	- https://flume.apache.org/
- Apache Nifi
	- https://nifi.apache.org/
- Spark
	- RM (resource manager)
	- AM (application manager)

### 20201115
- Kafka
	- Java API consumer source code
	- Java API producer source code
	
### 20201111
- Hive
	- save partitioned hive tabl
	- insert file/HDFS file to existing hive table

- Spark
	- set up metastore, warehouse path for hive IO
	- write df to hive with option

### 20201107
- Redis 
	- 5 main data structure
		- Strings
		- Lists
		- Sets
			- can save "offset" of kafka consumer, avoid "duplicated consuming" issue
		- Hashes
		- Sorted sets
		- Bitmaps and HyperLogLogs (also supports)
		- ref
			- https://redis.io/topics/data-types
			- https://redis.io/topics/data-types-intro
- Java
	- project naming
		- "domain name inverse" + "project name" + "module" + "program type"
		- example:
			- com.yen + bigdata.spark + services + aaa.java
		-  "module" : controller, service, bin...
	- Multi-threading
	- Multi-process
		- thread
		- runnable
		- callable
	- process cycle
		- NEW
		- RUNNABLE
			- READY
			- RUNNING
		- BLOCKED
		- WATING
		- TIMED_WATING
		- TERMINATED
	- process priority
	- process sleep
	- process yield
- Flink
	- Watermark
		- ordering stream
		- non-ordering stream
		- multi-thread stream
	- Window

### 20201106
- Luigi
	- luigi.Task
	- luigi basic concepts review
	- luigi get arg, config...
- Hadoop
	- discp
- Hive
	- hive partitioned table
	- spark save to hive partitioned table
- Docker
	- spark/hadoop physical/pseudo memory using setting
		- [example](https://github.com/yennanliu/data_infra_repo/commit/f74da253e5d159c853bd832aeab46e9092ac54f4)
- Spark
	- run via yarn/client...
- Python args
	- [example](https://github.com/yennanliu/utility_Python/blob/master/args_kwargs/args_kwargs_demo_2.py)

### 20201030
- SBT
	- [sbt-docker](https://index.scala-lang.org/regis-leray/sbt-docker/sbt-docker/0.6.0?target=_2.12_1.0)
		- [sbt-docker repo](https://github.com/marcuslonnberg/sbt-docker)
- Spark
	- Dataframe filter
		- `df.filter("col1 not like 'MSL%' and col2 not like 'HCP%'").show`
		- https://stackoverflow.com/questions/42951905/spark-dataframe-filter

- Hadoop-Spark set up via Docker-compose
	- [repo](https://github.com/yennanliu/data_infra_repo/tree/master/hadoop_yarn_spark)

### 20201028
- Shell
	- run 1 shell func inside the other shell func
		- [example](https://github.com/yennanliu/utility_shell/blob/master/export_var_func.sh)
- Spark
	- Spark-submit tuning : memory usage caculation
	- network traffic 
		-  more data size -> more traffic -> cost more time

### 20201027
- Spark
	- Spark-submit config
	- Spark-submit tuning
	- Spark-submit with different env
- Java
	- build project with maven
	- maven commands
	- [pom.xml set up](https://github.com/yennanliu/JavaHelloWorld/blob/main/pom.xml)
	- add dependency in  pom.xml
	- unit test in java

### 20201026 
- Kafka 
	- partition mode
	- offset background concept
	- load data with load

### 20201020
- Flink
	- Broadcast VS accumulator
- MongoDB
	- PyMongo API : find, find_one

- Design pattern
	- [intro video](https://www.youtube.com/watch?v=pkm5jQfnKGs&feature=youtu.be&fbclid=IwAR0lJWhN4ZivfrrYs9cI1L80EuZNQ61Byaj897irXtHFq4g5tyXRSxmLe4s)
	- [book](https://www.books.com.tw/products/0010750585?fbclid=IwAR3wCw19RRmz9-pMovdwvYE1f2LS-sovTLbYcgxafiSCLgushx2sXjFC4zU)
	- [example repo in java](https://github.com/skyyen999/bigTalkDesignPatternJava?fbclid=IwAR22te7g9hUwLfwXD0jL8omYWGGcJPfKn5Mow4wsOf8rSyTBW6WGQmbXU5w)
	- [blog](https://skyyen999.gitbooks.io/-study-design-pattern-in-java/content/?fbclid=IwAR2Cc4m1v0X1jwquD7K61ER3G88g58Cg6clsF0syOLI7PNagnY8O9PCPrio)

### 20201018
- Flink
	- Broadcast (in DataStream/Flink)
- Java
	- Random access files
	- serialize/deserialize
		- transform data into binary for 
			- transmission
			- storage
	- Buffer
	- NIO

### 20201017
- Scala
	- Class VS Object
		- [example](https://github.com/yennanliu/utility_Scala/blob/master/src/main/scala/ScalaBasic/Class_VS_Object_1.scala)

- Distributed system
	- Load balancer -> "register center", e.g. Zookeeper
		- [video](https://www.youtube.com/watch?v=JUq1N8NClcg&list=PLmOn9nNkQxJEDjzl0iBYZ3WuXUuUStxZl&index=2&fbclid=IwAR1LZf_G0hMF2oqAFKk7wYLjPmwyR36nLX6XtlrZ0EW20u1a-3dxfLNgJ_M)
	- Kafka
		- Message center dispense within multiple distributed system
		- [Leanring resource](https://www.youtube.com/watch?v=HLSQDk2asjY&list=PLmOn9nNkQxJEDjzl0iBYZ3WuXUuUStxZl&index=1&fbclid=IwAR15KewM8y7CdrrvdO3WaRaPOIpK8Ub-tZ-1JClHTQmE95vdyJyd9rymdxE)
- Java
	- File IO
	- stream transformation
	- Spring framework 

- Flink
	- Table api, SQL api
	- [Leanring resource](https://www.youtube.com/watch?v=SmqmIvgqp5M&list=PLmOn9nNkQxJGLnTsoWaHfvXrfpWiihoxV&index=1&fbclid=IwAR2wIc2BGMiA-JTi41X_YDd3EVrdO0NQCG4VnGPRVNJScHON40CmKGIvCSY)
- Zookeeper
	- as "information center, can do some cache"
	- python zookeeper client :
		- [kazoo](https://kazoo.readthedocs.io/en/latest/)
	- Load balancer -> Zookeeper

### 20201014
- Python
	- multi - processing
		- tuning
		- get pid, parent pid..
		- start, join
		- [example](https://github.com/yennanliu/utility_Python/blob/master/multiprocessing/multi_process_6.py)
- HDFS
	- REST http API
	- webhdfs check
- Hadoop
	- kerberos
	- core-default.xml
	- connection auth

### 20201008
- HDFS
	- client connect to HDFS (file IO)
		- webhdfs -> simpe file move/OP
		- pyarrow -> lot of files, heavy OP, or serializatio
	- Java connect to HDFS

### 20201006
- Java
	- Stream
	- Array List
- Flink
	- Batch, Sink API
- Spark
	- custom Spark shell port in config
- Kafka
	- [acks](https://medium.com/better-programming/kafka-acks-explained-c0515b3b707e)
		- acks=0 —the write is considered successful the moment the request is sent out. No need to wait for a response.
		- acks=1 — the leader must receive the record and respond before the write is considered successful.
		- acks=all — all online in sync replicas must receive the write. If there are less than min.insync.replicas online, then the write won’t be processed.

### 20201004
- Kafka
	- Asyc producer (sending msg)
	- serializer - deserializer
- Flink
	- [SocketWindowCount](https://github.com/yennanliu/flinkhelloworld/blob/master/src/main/scala/examples/SocketWindowWordCount.scala)
- Java
	- Map, HashMap, HashMapTree...

### 20200930
- HDFS
	- hdfs copy, create directory, check file size
		- [ref](https://github.com/yennanliu/utility_shell/blob/master/hadoop/hadoop_command.sh)
	- do above OP via python (subprocess, queue...)

### 20200929
- Scala
	- Try orElse getOrElse
	- Try catch excaption
	- Try[Unit]
	- Any
- HDFS
	- file op, compress, ls, mv...
- Python
	- subprocess
		- check_output
	- [persist-queue](https://pypi.org/project/persist-queue/)
		- persist-queue implements a file-based queue and a serial of sqlite3-based queues
		
### 20200928
- RabbitMQ
	- Scala examples
		- [ref](https://github.com/rabbitmq/rabbitmq-tutorials)
	- RPC (Remote procedure call) example
- API
	- GRPC
	- REST VS GRPC VS GRAPHQL VS OPENAPI...
		- [ref](https://medium.com/@sankar.p/how-grpc-convinced-me-to-chose-it-over-rest-30408bf42794)
- Java
	- for each
	- HashSet
	- MapSet
	- Map
	- sorting
- Git
	- git squash
		- [example](http://jiduanyaoji.logdown.com/hints/2015/05/14/how-to-commit-into-a-multiple)
	- git log 

### 20200927
- Flink
	- config on Hadoop, Yarn
	- run flink via Hadoop, stand alone
	- scala Flink shell
- Hadoop
	- Build hadoop namenode-datanode
	- set up zookeeper
	- think about HA

### 20200926
- Kafaka
	- kfaka stream
		- join 
		- transformation
		- group by
	- kafka unit test

### 20200924
- RabbitMQ
	- config
	- inport/export queue setting
- Elasticsearch
	- Define logging dtype
	- dtype

### 20200923
- RabbitMQ
	- intro
	- simple sender, receiver model
	- working queue
	- broker (exchanger)
	- publish/subscribe

### 20200920
- Flink
	- cluster mood
		- standalone
		- Flink on yarn
	- Flink works with HDFS/yarn..

### 20200919
- Java
	- System & Runtime class
	- Math & Random class
	- Java basic data strcture class (byte char short long int Boolean float double )
- Scala
	- logger (log4j)
- Kafka
	- Partitioner

### 20200918
- Scala
	- date format
	- long
	- log4j 
	- joda-time
	- json4s

### 20200915
- SBT
	- [sbt Resolvers](https://www.scala-sbt.org/1.x/docs/Resolvers.html)
	- [sbt shading](https://github.com/rallyhealth/sbt-shading)
	- [sbt exclude](https://www.scala-sbt.org/1.x/docs/Library-Management.html)
- Java
	- [netty](https://netty.io/)
	- Common lib (java.lang)

### 20200913
- ES
	- [REST command](https://github.com/yennanliu/utility_shell/blob/master/elasticsearch/elasticsearch_command.sh)
	- ES api command
	- ES general concepts
- Java
	- garbage collection (GC)

### 20200911
- Java
	- Error handling
		- error 
		- exception
	- try{} catch{Exception e}
	- throws
	- finally

### 20200910
- Scala
	- Some
	- Future  (in JS as well ?)
	- Finagle (lib for API/http call)
	- import, re-write class, trait, method...
	- Getters, Setters 

### 20200909
- Scala
	- [type](https://hongjiang.info/scala-type-system-type-keyword/?fbclid=IwAR0W9k3M3jaraNihrOVbD2Wsmxaj8LLzZAH7SVXcls7f2y-8XxS1dTtjNNc)
	- option
	- [`::`](https://hongjiang.info/scala-pitfalls-5/?fbclid=IwAR0W9k3M3jaraNihrOVbD2Wsmxaj8LLzZAH7SVXcls7f2y-8XxS1dTtjNNc)
	- [implicit - 1](http://icejoywoo.github.io/2018/12/29/scala-implicit.html?fbclid=IwAR0W9k3M3jaraNihrOVbD2Wsmxaj8LLzZAH7SVXcls7f2y-8XxS1dTtjNNc),
	[implicit- 2](https://docs.scala-lang.org/zh-cn/overviews/core/implicit-classes.html?fbclid=IwAR0W9k3M3jaraNihrOVbD2Wsmxaj8LLzZAH7SVXcls7f2y-8XxS1dTtjNNc)

### 20200908
- Scala
	- option
	- this
	- Future
	- [sbt-buildinfo](https://github.com/sbt/sbt-buildinfo) 
- RabbitMQ
- Spark
	- regex expression in spark 

### 20200907
- Scala
	- case class
	- Sealed Class
	- import from compiled jar
	- [json4s](https://github.com/json4s/json4s)
- Spark
	- send df to ES

### 20200906
- Flink
	- intro
	
### 20200905
- Java
	- Lambda internal class
	- Lambda function
	- functional programming

### 20200904
- Dev-op
	- Ansible
- IntelliJ
	- ctrl + ctrl (in IntelliJ console) => find "main" script
- Scala
	- Twitter-server
- SBT
	- sbt run

### 20200903
- Git
	- [`git fetch` VS `git clone`](https://gitbook.tw/interview#:~:text=%E4%B8%8D%E9%81%8E%EF%BC%8Cfetch%20%E6%8C%87%E4%BB%A4%E5%8F%AA%E5%81%9A,%E4%B8%A6%E4%B8%8D%E6%9C%83%E9%80%B2%E8%A1%8C%E5%90%88%E4%BD%B5%E3%80%82&text=pull%20%E6%8C%87%E4%BB%A4%E5%85%B6%E5%AF%A6%E5%81%9A%E7%9A%84,fetch%20%E5%8A%A0%E4%B8%8Amerge%20%E6%8C%87%E4%BB%A4%E3%80%82)
		- `git clone` = git fetch + git merge
		- git fetch : only copy files from remote branch to local branch, NO MERGE
		- git clone : copy files from remote branch to local branch, AND MERGE
	- [git merge](https://git-scm.com/book/zh-tw/v2/%E4%BD%BF%E7%94%A8-Git-%E5%88%86%E6%94%AF-%E5%88%86%E6%94%AF%E5%92%8C%E5%90%88%E4%BD%B5%E7%9A%84%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95)	
	- git cherry-pick
	- git rebase
	- [examples](https://github.com/yennanliu/utility_shell/blob/master/git_github/git_command.sh)

- Java 
	- Polymorphism
- Scala
	- implicit
- BQ
	- AMZ Leadership Principles
	
### 20200830
- Scala
	- Implicit
- Dev-op
	- Ansible playbook
- Invest
	- Stock exposure

### 20200829
- Java
	- abstract
	- interface
- Python
	- [Design pattern](https://refactoring.guru/design-patterns/python)
		- [example code](https://github.com/yennanliu/python-patterns)

### 20200828
- [Druid simple query](https://druid.apache.org/)
- [twitter-server](https://github.com/twitter/twitter-server)

### 20200827
- Spark
	- load parquet 

### 20200826
- Java
	- object class
	- rewrite method
	- final
- Scala 
	- UpperCass
	- option
	- find
	- Some
	- exists
	- contains
	- isDefined

### 20200825
- Git
	- `git rebase`
	- `git rebase --continue`
	- `git rebase --abort`
		- ref : [rebase step by step](http://gitforteams.com/resources/rebasing.html#:~:text=git%2Frebase%2Dapply%2Fpatch,%22git%20rebase%20%2D%2Dabort%22.)
	-  git pull = git clone + git merge
	
### 20200823
- Tech
	- [RPC](https://blog.csdn.net/yjp198713/article/details/79410521)
	- [GRPC](https://colobu.com/2017/04/06/dive-into-gRPC-streaming/#:~:text=gRPC%E6%98%AF%E4%B8%80%E4%B8%AA%E9%AB%98%E6%80%A7%E8%83%BD,%E4%B8%94%E6%94%AF%E6%8C%81%E4%BC%97%E5%A4%9A%E5%BC%80%E5%8F%91%E8%AF%AD%E8%A8%80%E3%80%82)
- Product Development
	- Agile
		- [Kanban](https://dotblogs.com.tw/mystic_pieces/2019/03/12/223533)
		- [Scrum](https://medium.com/doflowy/%E4%BB%80%E9%BA%BC%E6%98%AFscrum-%E4%B8%8D%E6%98%AF%E5%B7%A5%E7%A8%8B%E5%B8%AB%E4%B9%9F%E8%83%BD%E6%87%82%E7%9A%84scrum%E5%85%A5%E9%96%80%E6%95%99%E5%AD%B8-1cc6683575f8)
			- [Scrum guide](https://www.scrumguides.org/scrum-guide.html)
		- Lean
		- [Kanban VS scrum](http://teddy-chen-tw.blogspot.com/2013/08/scrum-kanban.html)
	- Waterfall
- Java
	- Class extends
	- Class method `rewrite`
	- `super`
- Scala
	- `super`
	- [Finatra HTTP Server](https://github.com/yennanliu/FinatraHelloWorld/blob/master/doc/progress.md)
- Python 
- Invest
	- Basic Financial statements
		- Profit and Loss Account
		- Balance Sheet
		- Cash Flow Statement
		- Statement of Stockholders Equity
	- [Apple inc. 2019 Q4 financial report](https://www.apple.com/newsroom/pdfs/Q4%20FY19%20Consolidated%20Financial%20Statements.pdf)
	- [Apple inc. financial report (yahoo finance)](https://hk.finance.yahoo.com/quote/AAPL/financials/)
### 20200822
- Java
	- [Method reload](https://github.com/yennanliu/utility_Java/blob/master/src/java/main/JavaBasics/ConstructorOverload.java) 
	- Method iteration
	- Method construct
	- [`this`](https://github.com/yennanliu/utility_Java/blob/master/src/java/main/JavaBasics/ThisDemo.java)
	- [`static` var](https://github.com/yennanliu/utility_Java/blob/master/src/java/main/JavaBasics/StaicVar.java)
	- [`static` method](https://github.com/yennanliu/utility_Java/blob/master/src/java/main/JavaBasics/StaicMethod.java)
	- `static` code
- Scala
	- [`this`](https://docs.scala-lang.org/tour/self-types.html)
	- [`implicit`](https://docs.scala-lang.org/tour/implicit-parameters.html)
- Python 
- Invest
	- [Risk VS uncertainty](https://www.motilaloswal.com/blog-details/Understanding-difference-between-risk-and-uncertainty-in-investing../1835)
	- [margin of safety](https://www.investopedia.com/terms/m/marginofsafety.asp#:~:text=Margin%20of%20safety%20is%20a,is%20the%20margin%20of%20safety.)
	- [Rate of return](https://www.investopedia.com/terms/r/rateofreturn.asp)
	- [investopedia](https://www.investopedia.com/)  
