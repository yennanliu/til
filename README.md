# til
> Today I Learned
- Collection & record regarding my daily learning. 
- Tech + product + business. 

---

## Progress
### 20201125
- Scala
	- comment -> auto generate API doc
	- var, val point to storage space
	- how scala use/re-write part of java lib as well as write itself one
	- sbt publish
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
