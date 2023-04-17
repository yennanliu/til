# til
> Today I Learned
- Collection & record regarding my daily learning. 
- Tech + product + business. 

---

# PROGRESS

### 20230417
- SSL/TLS certificate
	- https://aws.amazon.com/tw/what-is/ssl-certificate/
- Cloudfront - Lambda@Edge function (Viewer request, Origin request, Origin response, Viewer response)
	- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-cloudfront-trigger-events.html

### 20230319
- Deep copy, shallow copy
	- https://youtu.be/iJmOIzo4kL0?t=268
	- https://youtu.be/PU74J-hk7xg?t=1
	<p><img src ="https://github.com/yennanliu/til/blob/master/doc/pic/shallow_copy.png" ></p>
	<p><img src ="https://github.com/yennanliu/til/blob/master/doc/pic/deep_copy.png" ></p>

### 20230316
- AWS
	- CDK
		- [update CDK online directly](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-direct.html)

### 20230315
- AWS
	- VPC subnet, CIDR
		- https://docs.aws.amazon.com/zh_tw/vpc/latest/userguide/configure-subnets.html
		- https://docs.aws.amazon.com/zh_tw/vpc/latest/userguide/vpc-subnets-commands-example.html
		- https://ithelp.ithome.com.tw/articles/10234482

### 20230314
- AWS RDS
	- VPC
		- https://docs.aws.amazon.com/zh_tw/AmazonRDS/latest/UserGuide/USER_VPC.WorkingWithRDSInstanceinaVPC.html
		- https://docs.aws.amazon.com/zh_tw/AmazonRDS/latest/UserGuide/USER_VPC.Scenarios.html
		- https://docs.aws.amazon.com/zh_tw/AmazonRDS/latest/UserGuide/CHAP_Tutorials.WebServerDB.CreateVPC.html

### 20230313
- CDK
	- Port mapping
		- https://cloud.tencent.com/developer/ask/sof/947933
		- https://stackoverflow.com/questions/69739519/cdk-fargate-map-subdomain-to-different-container-port

### 20230312
- Typescript
	- ? in attr name
		```typescript
		// typescript
		let a{name: string, age: number};
		let b{name: string, age?: number}; // age attr for b is optional
		
		// test
		b = {name: 'iori'};
		```
		- https://youtu.be/aUxOW6Rirhs?t=314
	- readonly
		- https://youtu.be/tA5AzJBevzo?t=838
	- class constructor : this
		- https://youtu.be/BA7IvQGBB-k?t=373
	- extends
		- https://youtu.be/K0MQLF-qH2g?t=512
	- override
		- https://youtu.be/K0MQLF-qH2g?t=1171
	- super
		- https://youtu.be/UDBhubQGmVs?t=26
		- https://youtu.be/UDBhubQGmVs?t=361 : important!!, super used in constructor
	- generic type
		- https://youtu.be/Al44tYBPy_0?t=512

### 20230310
- how to solve "The maximum number of addresses has been reached" for AWS VPC Elastic IP addresses?
	- Go to https://us-east-1.console.aws.amazon.com/servicequotas/home/services/ec2/quotas and search for "IP". Then, choose "EC2-VPC Elastic IPs".
	- https://stackoverflow.com/questions/71807998/how-to-resolve-the-maximum-number-of-addresses-has-been-reached-for-aws-vpc-el

### 20230309
- CDK
	- constructor
		- https://towardsthecloud.com/aws-cdk-construct
		- https://github.com/aws/aws-cdk/discussions/23839

### 20230304
- Java
	- volatile
		- `Java volatile 關鍵字作用是，使系統中所有線程對該關鍵字修飾的變量共享可見，可以禁止線程的工作內存對volatile修飾的變量進行緩存。`
		- https://www.baeldung.com/java-volatile
		- https://jenkov.com/tutorials/java-concurrency/volatile.html
		- https://zhuanlan.zhihu.com/p/151289085
		- https://blog.csdn.net/u012723673/article/details/80682208
		- https://cloud.tencent.com/developer/article/1803803
		- https://zhuanlan.zhihu.com/p/145902867
		- example
			- https://youtu.be/TpdPsCGsFVk?t=151
			```java
			// java, Singleton double check (use volatile)
			public class Singleton{
				// NOTE here
				private static volatile Singleton singleton;
				private Singleton(){};
				public static Singleton getInstance(){
					if(singleton == null){
						synchronized(Singleton.class){
							if (singleton == null){
									singleton = new Singleton();
								}
						}
					}
					
					return singleton;
				}
			}
			
			```

### 20230301
- AWS CloudFront
	```
	Amazon CloudFront 是一種內容交付網路 (CDN)，可加速向最終使用者交付靜態和動態 Web 內容。`
	CloudFront 透過稱為邊緣節點的全球資料中心網路交付內容。當最終使用者請求您使用 CloudFront 提供的內容時，該請求將被路由至距離最終使用者最近且延遲最低的邊緣節點。
	```
	- https://aws.amazon.com/tw/cloudfront/getting-started/
	- https://docs.aws.amazon.com/zh_tw/AmazonCloudFront/latest/DeveloperGuide/GettingStarted.html
	- tutorial
		- https://ithelp.ithome.com.tw/articles/10192080
			- step 1) set S3 bucket as NON public
			- step 2) go to S3 bucket set up "Bucket policy" as below
			- step 3) then create cloudfront distribution with "Originaccess control settings (recommended)"
				- https://github.com/yennanliu/til/blob/master/doc/pic/cloud-front1.png
				- [Example S3 bucket policy that allows read-only access to a CloudFront OAC](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html#private-content-oac-permission-to-access-s3)
		```json
		   {
		    "Version": "2008-10-17",
		    "Id": "PolicyForCloudFrontPrivateContent",
		    "Statement": [
			{
			    "Sid": "AllowCloudFrontServicePrincipal",
			    "Effect": "Allow",
			    "Principal": {
				"Service": "cloudfront.amazonaws.com"
			    },
			    "Action": "s3:GetObject",
			    "Resource": "arn:aws:s3:::yen-test-20230413/*",
			    "Condition": {
				"StringEquals": {
				    "AWS:SourceArn": "arn:aws:cloudfront::77777777777:distribution/EUPA2IOLE7S30"
				}
			    }
			}
		    ]
		}
		```
	- video
		- https://www.youtube.com/watch?v=Vr4N_ZA-uGo

### 20230226
- Spring boot
	- logic deletion
		- https://github.com/yennanliu/SpringPlayground/blob/main/springEcommerceGuli/backend/EcommerceGuli/gulimall-product/src/main/java/com/yen/gulimall/product/entity/CategoryEntity.java#L47
	- print SQL in log
		- https://github.com/yennanliu/SpringPlayground/blob/main/springEcommerceGuli/backend/EcommerceGuli/gulimall-product/src/main/resources/application.yml#L34
### 20230225
- Spring boot
	- Entity add field NOT exists in DB table:
		- `@TableField(exist = false)`
		- [code](https://github.com/yennanliu/SpringPlayground/blob/dev-016-be-3-layer-prod-data-query/springEcommerceGuli/backend/EcommerceGuli/gulimall-product/src/main/java/com/yen/gulimall/product/entity/CategoryEntity.java#L63)
		- https://youtu.be/5aWkhC7plsc?t=646
	```java
	// java
	@TableField(exist = false)
	private List<CategoryEntity> children;
	```

### 20230222
- Java
	- Spring @Async VS CompletableFuture
		- https://cloud.tencent.com/developer/article/1686016
		- https://spring.io/guides/gs/async-method/

### 20230214
- Java
	- Future VS Promise, CompletableFuture ... (async call)
		- https://popcornylu.gitbooks.io/java_multithread/content/async/cfuture.html
                - https://cloud.tencent.com/developer/article/1845416
                - https://www.liaoxuefeng.com/wiki/1252599548343744/1306581182447650
                - https://www.readfog.com/a/1633195577082744832
- Spring boot
	- JpaRepository
		- JpaRepository 是作為 Repository 應用的一種繼承的「抽象介面」，他允許我們可以透過介面的使用，就直接與資料庫進行映射與溝通。
 		- https://medium.com/learning-from-jhipster/20-controller-service-repository%E7%9A%84%E5%BB%BA%E7%AB%8B-1-jparepository-%E7%9A%84%E4%BD%BF%E7%94%A8-6606de7c9d41
 		- https://ithelp.ithome.com.tw/articles/10194906
- Redshift
	- data sharing
		- https://www.wellarchitectedlabs.com/sustainability/300_labs/300_optimize_data_pattern_using_redshift_data_sharing/
		- https://docs.aws.amazon.com/redshift/latest/dg/considerations.html
		- [ref code](https://github.com/yennanliu/Redshift-poc/tree/main/lab5)

### 20230212
- Map Reduce
	- Reduce
	```
	// syntax:
	// array.reduce(function(total, currentValue, currentIndex, arr), initialValue)
	// or
	// array.reduce(callback[, initialValue]);
	function(total, currentValue, index, arr): It is a required parameter used to run for each array element. It contains four parameters which are listed below:
	- total: It is the required parameter used to specify an initialValue or the previously returned value of a function.
	- currentValue: It is the needed parameter and is used to determine the value of a current element.
	- currentIndex: It is the optional parameter used to specify an array index of the current element.
	- arr: It is the optional parameter used to determine an array object the current element belongs to.
		initialValue: The optional parameter specifies the value to be passed to the function as an initial value.
	```
	```javascript
	// javascript
	// example:
	const data = [5, 10, 15, 20, 25];

	const res = data.reduce((total,currentValue) => {
	  return total + currentValue;
	});

	console.log(res); // 75
	```
	- https://appdividend.com/2022/03/08/javascript-reduce/
	- https://github.com/yennanliu/JS_Playground/blob/master/es6/map_reduce.html#L31

### 20230210
- [Implementing Stripe-like Idempotency Keys in Postgres](https://brandur.org/idempotency-keys?fbclid=IwAR0qoNeFHfGfcnLzD2ZrxGGCw9v07rf6xYzsRUgY_yaIOqpsh-dxx104TCs)

### 20230209
- LDAP (Lightweight Directory Access Protocol)
	- https://itman.pixnet.net/blog/post/26817279
	- https://www.okta.com/identity-101/what-is-ldap/
	- https://blog.poychang.net/ldap-introduction/
- Others
	- [the-technology-behind-githubs-new-code-search](https://github.blog/2023-02-06-the-technology-behind-githubs-new-code-search/)

### 20230208
- Message queue
	- TTL: time to live
		- https://youtu.be/xDK72L-XZps?t=455
		- msg survive time

### 20230207
- Distribution system
	- 分布式事務方案 (Distribution transaction)
		- 2PC (2 phase commit) (XA)
		- 3PC (3 phase commit) (automated TCC)
		- TCC (Try, Commit, and Cancel (TCC))
		- Local Messaging
		- Transactional Messaging
		- Best-effort Notification
		- Ref
			- https://youtu.be/fBGmuUdNejM
			- https://www.alibabacloud.com/blog/an-in-depth-analysis-of-distributed-transaction-solutions_597232#:~:text=Try%2C%20Commit%2C%20and%20Cancel%20(,%2C%20commit%2C%20and%20cancel%20interfaces.
			- https://medium.com/@dongfuye/the-seven-most-classic-solutions-for-distributed-transaction-management-3f915f331e15
			- https://betterprogramming.pub/a-tcc-distributed-transaction-made-easy-with-go-c0a38d2a8c44
			- https://www.dtm.pub/
		- TCC
			- <p><img src ="./doc/pic/tcc.png" ></p>
- Metadata discover
	- https://datahubproject.io/
- IntelliJ create test from a class directly
	- https://youtu.be/kyWllXOGMWQ?t=472

### 20230205
- Java
	- 本地事務隔離級別, 傳播行為
		- https://youtu.be/Z-sR0K5dVPw?t=944

### 20230203
- 驗證(Authentication)與授權(Authorization)
	```
	Authentication（驗證）：確認使用者是否真的是其所宣稱的那個人的過程。
	Authorization（授權）：根據使用者的角色來授予應有的權限。
	```
	- https://matthung0807.blogspot.com/2018/03/authenticationauthorization.html
	- https://www.ithome.com.tw/voice/134389
	- https://www.onelogin.com/learn/authentication-vs-authorization#:~:text=Authentication%20and%20authorization%20are%20two,authorization%20determines%20their%20access%20rights.

### 20230201
- Redshift
	- optimazation
		- https://zhuanlan.zhihu.com/p/398754264
		- https://blog.csdn.net/awschina/article/details/121759986
		- https://www.infoq.cn/article/yudaymzeokmbr3zgwxag
		- https://aws.amazon.com/cn/blogs/china/overview-of-ten-amazon-redshift-performance-tuning-techniques/
		- https://docs.aws.amazon.com/zh_cn/redshift/latest/dg/c-optimizing-query-performance.html
	- table design
		- https://aws.amazon.com/cn/blogs/china/amazon-redshift-table-design-databasedata/
	- `sharding, partition, ordering, design ideas` !!!
		- https://aws.amazon.com/cn/blogs/china/amazon-redshift-table-design-databasedata/

### 20230126
- Docker
	- docker container connect to local mysql (macbook)
		- https://juejin.cn/post/6965008009009315848
		- https://blog.csdn.net/JosephThatwho/article/details/103128794
		- https://www.cnblogs.com/aaabbbcccddd/p/14405804.html
- Redshift 
	- Intro
		- http://www.ilongda.com/knowledge/paper/redshift.html
		- https://www.infoq.cn/article/3e09axb8glwhswiskfix
	- WLM queue assignment rules
		- https://docs.aws.amazon.com/redshift/latest/dg/cm-c-wlm-queue-assignment-rules.html

### 20230125
- gitignore
	- negelect all files with below name (spring boot)
	-  https://youtu.be/4NLgelF5-rk?t=546
	-  https://github.com/yennanliu/SpringPlayground/blob/main/.gitignore#L36
```bash
**/mvnw
**/mvnw.cwd
**/.idea
**/.mvn
**/.iml
**/.cmd
**/target/
.idea
```

### 20230124
- Java spring boot/cloud
	- Idea intelliJ : Create multiple modules under a project
		- https://blog.csdn.net/wangmx1993328/article/details/121189232

### 20230121
- Java spring boot + RabbitMQ
	- json serialize / deserialize
		- https://youtu.be/8x4G7rRb9zo?t=624

### 20230114
- Java spring boot : multi thread pool
	- ref1
		- https://youtu.be/c134eGL062g?t=1603
		- https://youtu.be/c134eGL062g?t=2323
		- https://youtu.be/KeDhbCdmIvs?t=61
		- https://youtu.be/s9nJeXOD0C8?t=144
	- code
		- https://github.com/yennanliu/SpringPlayground/tree/main/springAdvance/springThreadPool

### 20230108
- Java
	- ThreadLocal : share data in the same thread
		- https://youtu.be/dop2UFz4am4?t=1198
		- https://kucw.github.io/blog/2018/7/java-thread-local/
- Linux
	- Access-Control list (ACL)
		- https://youtu.be/0vYydtG1Xi4?t=1517
		- `ownwer group others`
		- R: read
		- W : write
		- X : execute
		- modfiy ACL via `chmod`

### 20221213
- HTML
	- Nu HTML checker
		- https://validator.w3.org/nu/#textarea
		- https://stackoverflow.com/questions/56667637/getting-nullpointerexception-while-converting-html-to-pdf-using-java-and-itext7
- DB
	- partial index
		- https://docs.postgresql.tw/the-sql-language/index/partial-indexes
		- https://blog.csdn.net/neweastsun/article/details/113096327

### 20221211
- MySQL
	- `group_concat()` function
		- https://www.yiibai.com/mysql/group_concat.html#:~:text=GROUP_CONCAT%20%E5%87%BD%E6%95%B0%E8%BF%94%E5%9B%9E%E4%BA%8C%E8%BF%9B%E5%88%B6%E6%88%96,%E5%8F%98%E9%87%8F%E6%9D%A5%E6%89%A9%E5%B1%95%E6%9C%80%E5%A4%A7%E9%95%BF%E5%BA%A6%E3%80%82
		- https://www.footmark.com.tw/news/database/mysql/mysql-group-concat-json/
		- https://www.w3resource.com/mysql/aggregate-functions-and-grouping/aggregate-functions-and-grouping-group_concat.php
		- https://youtu.be/k9i6bOMt4rg?t=500

### 20221130
- Java
	- sort double list
		- https://stackoverflow.com/questions/16252269/how-to-sort-a-list-arraylist
		```java
		// java
		testList.sort((a, b) -> Double.compare(b, a));
		```

### 20221129
- SQL
	- compress SQL code
		- https://tool.lu/sql/
		- https://www.toolnb.com/tools-lang-zh-TW/sqlFormat.html
	- Mysql text type : TEXT, TINYTEXT, MEDIUMTEXT, LONGTEXT
		- https://www.analyticsvidhya.com/blog/2020/11/guide-data-types-mysql-data-science-beginners/#:~:text=LONGTEXT%20can%20store%20the%20maximum,LONGTEXT%20takes%204%2DBytes%20overhead.
		- https://blog.csdn.net/youcijibi/article/details/80673811
		```sql
		# mysql cmd
		alter table my_db.my_table modify sql_template LONGTEXT
		```

### 20221115
- Sringboot Java
	-  ObjectMapper : json <--> Java Object transformation
		- https://kucw.github.io/blog/2020/6/java-jackson/
		- https://tw.gitbook.net/jackson/jackson_objectmapper.html

### 20221114
- AWS S3 token expire with IAM, access key...
	- https://aws.amazon.com/premiumsupport/knowledge-center/presigned-url-s3-bucket-expiration/
	- https://stackoverflow.com/questions/57511301/load-data-from-s3-the-provided-token-has-expired

### 20221111
- Millisecond to day/hour/min..
	- https://www.calculateme.com/time/milliseconds/to-days/900000

### 20221105
- Java
	- super()
	- https://github.com/yennanliu/SpringPlayground/blob/main/courses/springBoot_springCloud_%E9%A0%82%E7%B4%9A%E9%96%8B%E7%99%BC_src_code/chapter04-efence/src/main/java/com/wudimanong/efence/exception/ServiceException.java#L11
	```java
	// java
	    public ServiceException(Integer code, String message) {
		super(message); // TODO: double check this
		this.code = code;
	    }

	```
	- Spring boot
		- @ExceptionHandler(Exception.class)
		- @ControllerAdvice
		- https://github.com/yennanliu/SpringPlayground/blob/main/courses/springBoot_springCloud_%E9%A0%82%E7%B4%9A%E9%96%8B%E7%99%BC_src_code/chapter04-efence/src/main/java/com/wudimanong/efence/exception/GlobalExceptionHandler.java#L23

### 20221105
- Java
	- generic type
		- https://www.runoob.com/java/java-generics.html
		```
		java 中泛型标记符：
		
		E - Element (在集合中使用，因为集合中存放的是元素)
		T - Type（Java 类）
		K - Key（键）
		V - Value（值）
		N - Number（数值类型）
		？ - 表示不确定的 java 类型
		```
	- stream
		- https://mycollegenotebook.medium.com/java-stream-%E7%AD%86%E8%A8%98-%E4%B8%8A-34df0e282fc8
		- https://mycollegenotebook.medium.com/java-stream-%E7%AD%86%E8%A8%98-%E4%B8%8B-d8fc2d227e16
		- https://tw511.com/a/01/22301.html

### 20221104
- Spring boot
	```java
	// java
	@Target({METHOD, FIELD, ANNOTATION_TYPE, CONSTRUCTOR, PARAMETER}) // TODO : double check it
	@Retention(RUNTIME)
	@Documented
	@Constraint(validatedBy = {EnumValue.EnumValueValidator.class})
	```
- Java
	- Class<?>
	

### 20221102
- Java
	- `Collectors.groupingBy`
	```java
	    Map<String, List<MyReport>> monthReportMap = myReport.stream()
        .collect(Collectors.groupingBy(MyReport::getOwnerGroupKey));
	```
	- https://github.com/yennanliu/JavaHelloWorld/blob/e3f4dc87ddbe034d5ae1eff09ea209478596e7fc/src/main/java/dev/StreamTest1.java#L60

### 20221029
- Java
	- parse object (whatever type) to json
		- https://youtu.be/wGtcsi65arQ?t=494
		- https://blog.csdn.net/xuexi_gan/article/details/114915890
		- https://www.runoob.com/w3cnote/fastjson-intro.html
		```java
		// java
		Map<String, List<Catelog2Vo>> result = JSON.parseObject(CatelogJSON, new TypeReference<Map<String, List<Catelog2Vo>>>() {} );
		```

### 20221028
- Java
	- `@Import` annotation
		- https://www.itread01.com/article/1532997860.html
		- https://blog.csdn.net/tuoni123/article/details/80213050
		- https://www.jianshu.com/p/6b2f672e2446
		- https://blog.csdn.net/qq_52496081/article/details/121833395
- AWS
	- S3 presignedURL max expire time
		- https://docs.aws.amazon.com/AmazonS3/latest/API/sigv4-query-string-auth.html
			- Provides the time period, in seconds, for which the generated presigned URL is valid. For example, 86400 (24 hours). This value is an integer. The minimum value you can set is 1, and the maximum is 604800 (seven days).
			- A presigned URL can be valid for a maximum of seven days because the signing key you use in signature calculation is valid for up to seven days.
		- https://stackoverflow.com/questions/24014306/aws-s3-pre-signed-url-without-expiry-date
		- https://docs.amazonaws.cn/en_us/AmazonS3/latest/userguide/ShareObjectPreSignedURL.html
		
### 20221024
- Java
	- Jshell (java REPL)
		- https://docs.oracle.com/javase/9/jshell/introduction-jshell.htm
		- https://www.tpisoftware.com/tpu/articleDetails/1089	

### 20221023
- System monitoring
	- Skywalking
		- https://dubbo.apache.org/zh/docs/v2.7/admin/ops/skywalking/#:~:text=%E5%88%86%E5%B8%83%E5%BC%8F%E8%B7%9F%E8%B8%AA-,Apache%20Skywalking%20%E7%AE%80%E4%BB%8B,%E9%97%B4%E5%85%B3%E7%B3%BB%E4%BB%A5%E5%8F%8A%E6%9C%8D%E5%8A%A1%E6%8C%87%E6%A0%87%E3%80%82
		- https://juejin.cn/post/7002389720315461640
		- https://www.jianshu.com/p/ffa7ddcda4ab
	- General
		- https://www.youtube.com/watch?v=6pquxpmk4R8&list=PLmOn9nNkQxJEwPjhNwGliP_bw3RjkgFCf&index=141
		- <p><img src ="./doc/pic/sys_metric1.png" ></p>
		- <p><img src ="./doc/pic/sys_metric2.png" ></p>

### 20221022
- Java
	- Java Collectors toMap()
		- https://www.baeldung.com/java-collectors-tomap
		- https://vimsky.com/zh-tw/examples/usage/collectors-tomap-method-in-java-with-examples.html
		- https://youtu.be/lq-xGkEm140?t=693
		```java
		// java
		data.stream().collect(Collectors.toMap( k -> k.getId(), v -> {return v.gatValue()} ))	
		```
- Nginx conf
	- <p><img src ="./doc/pic/nginx_conf.png" ></p>

### 20221019
- Java
	- x == null VS x.equals(null)
	- can also use `spring StringUtils.isEmpty` check if empty
		- https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/util/StringUtils.html

### 20221013
- Spring boot
	- Pinpoint
		- https://pinpoint-apm.github.io/pinpoint/2.1.0/main.html
		- https://blog.csdn.net/it_lihongmin/article/details/124160500
		- https://www.jianshu.com/p/03dc1377f137

### 20221004
- Spring boot
	- MapStruct
		- `XXXDTO <----> XXXVO <----> XXXBO <----> ....` transformation
		- https://www.tpisoftware.com/tpu/articleDetails/2443
		- https://springboot.io/t/topic/4162
		- https://www.itread01.com/details/MnRvMA==.html

### 20221003
- Java
	- [netty](https://netty.io/)
	- [dubbo apache](https://dubbo.apache.org/en/)

### 20220929
- sdkman
	- https://sdkman.io/

### 20220927
- Java
	- Stream map op (get collections of Stream map result)
        - <img src ="https://github.com/yennanliu/til/blob/master/doc/pic/stream_map1.png">
	- Ref
		- video
			- https://www.youtube.com/watch?v=PFtMlUlCZgY&list=PLmOn9nNkQxJEwPjhNwGliP_bw3RjkgFCf&index=81
			- https://www.youtube.com/watch?v=7JOhxs7lYbE&list=PLmOn9nNkQxJEwPjhNwGliP_bw3RjkgFCf&index=80
		- code
			- https://github.com/yennanliu/JavaHelloWorld/blob/main/src/main/java/dev/StreamMapTest.java
	```java
	// java
	List<String> brand_list = car_list.stream().map(x -> {
            String brand = x.getBrand();
            return brand;
        }).collect(Collectors.toList());
	```

### 20220919
- Spring boot
	- user-defined general exceptions
		- https://www.youtube.com/watch?v=UT9lRWUwDGQ&list=PLmOn9nNkQxJEwPjhNwGliP_bw3RjkgFCf&index=68

### 20220915
- Spring boot
	- `this` VS `self`

### 20220915
- Spring boot
	- `@Transactional` (事務性)
		- https://www.tpisoftware.com/tpu/articleDetails/2741
		- https://www.readfog.com/a/1637926921197162496
		- https://kknews.cc/zh-tw/code/9ggzjq8.html
		- https://www.marcobehler.com/guides/spring-transaction-management-transactional-in-depth
		- https://www.gushiciku.cn/pl/givy/zh-tw

### 20220914
- Mybatis plus lambda
	- https://www.796t.com/content/1541640975.html
	- https://blog.csdn.net/m0_37034294/article/details/82917234
	- https://blog.csdn.net/liuxing201122013/article/details/120874343
- Spring booot
	- `consumes, produces` in RequestMapping
		- https://medium.com/@lemonchen/requestmapping-%E8%A8%BB%E8%A7%A3%E4%B8%ADconsumes-produces-%E5%B7%AE%E5%88%A5-d0a9a79fdbb8
		- https://blog.csdn.net/jaryle/article/details/72965885
- HTTP
	- MIME TYPE
		- https://topic.alibabacloud.com/tc/a/network-what-is-mime-type_1_38_30917192.html
		- https://www.796t.com/p/616463.html
- Eng soft skill
	- [An Elegant Puzzle: Systems of Engineering Management](https://www.amazon.com/dp/1732265186/ref=as_sl_pc_as_ss_li_til?tag=danlebrero-20&linkCode=w00&linkId=a91305ee2692c674733bd592ec7c897d&creativeASIN=1732265186)
	- [Staff Engineer: Leadership beyond the management track ](https://www.amazon.com/Staff-Engineer-Leadership-beyond-management-ebook/dp/B08RMSHYGG)
	- [will larson twitter](https://twitter.com/Lethain)

### 20220912
- Spring boot
	- `Validation`, `valid`
		- https://bingdoal.github.io/backend/2021/10/spring-boot-validate-request-body-and-nest-validate/
		- https://bingdoal.github.io/backend/2021/10/spring-boot-validation-customize-validator-and-annotation/
		- https://morosedog.gitlab.io/springboot-20190403-springboot20/
	- `切面導向程式設計（Aspect Oriented Programming，AOP`
		- https://chikuwa-tech-study.blogspot.com/2021/06/spring-boot-aop-introduction.html
		- https://ithelp.ithome.com.tw/articles/10279178
		- https://medium.com/appxtech/spring-aop%E7%99%BD%E8%A9%B1%E6%96%87-%E6%B7%BA%E8%AB%87spring-aop%E7%9A%84%E5%AD%B8%E7%BF%92%E5%88%86%E4%BA%AB-1985489d008
- Scala
	- `ZIO` course
		- https://rockthejvm.com/p/zio
			- ZIO is a Scala toolkit that allows us to write powerful, concurrent, and high-performance applications in Scala using pure functional programming.
		- https://github.com/rockthejvm/zio-course

### 20220907
- Mysql
	- BLOB VS Binary
		- http://c.biancheng.net/view/2428.html
		- https://blog.csdn.net/weixin_42363501/article/details/113424096

### 20220904
- Web dev
	- 跨域請求 Cross-Origin Resource Sharing (CORS)
		- https://www.youtube.com/watch?v=VNP6inKmw5I&list=PLmOn9nNkQxJEwPjhNwGliP_bw3RjkgFCf&index=48
		- https://developer.mozilla.org/zh-TW/docs/Web/HTTP/CORS
- Java
	- load files under `/resources`
		- https://github.com/yennanliu/JavaHelloWorld/blob/main/src/main/java/dev/ParseCSVTest.java
		- https://stackoverflow.com/questions/15749192/how-do-i-load-a-file-from-resource-folder

### 20220903
- Spring boot
	- lombok `@Builder`
		- https://hackmd.io/@KaiChen/S145q3NP8
		- https://matthung0807.blogspot.com/2019/11/lombok-builder.html
		- https://walkonnet.com/archives/10611
	- JSP
- Java
	- set default val if null
		- https://youtu.be/5aWkhC7plsc?t=1099
		```java
		// sample code
		(menu1.getSort() == null ? 0);
		```

### 20220901
- PageHelper doc
	- https://pagehelper.github.io/docs/howtouse/

### 20220830
- AWS S3
	- Why is my presigned URL for an Amazon S3 bucket expiring before the expiration time that I specified?
		- https://aws.amazon.com/premiumsupport/knowledge-center/presigned-url-s3-bucket-expiration/
	- Examples: Signature Calculations in AWS Signature Version 4 (java)
		- https://docs.aws.amazon.com/AmazonS3/latest/API/sig-v4-examples-using-sdks.html#sig-v4-examples-using-sdk-java
	- How do I utilize AWS Signature v4 when generating a presigned S3 URL?
		- https://stackoverflow.com/questions/50090241/how-do-i-utilize-aws-signature-v4-when-generating-a-presigned-s3-url
	- How to check presignedURL expire time (Signature Version 4)?
		- https://stackoverflow.com/questions/46865679/amazon-s3-how-to-check-if-presigned-url-is-expired
		- `Amz-Expires is the expiration time in seconds, while X-Amz-Date is the the timestamp `

### 20220822
- Spring boot
	- cron scheduling
		- https://stackoverflow.com/questions/26147044/spring-cron-expression-for-every-day-101am
		- https://docs.spring.io/spring-framework/docs/3.2.x/spring-framework-reference/html/scheduling.html#scheduling-annotation-support
	- spring cron generator/explanation (with cron code)
 		- https://www.javainuse.com/cron
		- https://codepen.io/etienne582/pen/xxOgwzX
	```java
	* "0 0 * * * *" = the top of every hour of every day.
	* "*/10 * * * * *" = every ten seconds.
	* "0 0 8-10 * * *" = 8, 9 and 10 o'clock of every day.
	* "0 0 8,10 * * *" = 8 and 10 o'clock of every day.
	* "0 0/30 8-10 * * *" = 8:00, 8:30, 9:00, 9:30 and 10 o'clock every day.
	* "0 0 9-17 * * MON-FRI" = on the hour nine-to-five weekdays
	* "0 0 0 25 12 ?" = every Christmas Day at midnight
	```

### 20220816
- AWS S3
	- 存取控制清單(Access Control List, ACL
		- https://zh.wikipedia.org/zh-tw/%E5%AD%98%E5%8F%96%E6%8E%A7%E5%88%B6%E4%B8%B2%E5%88%97
		- https://docs.aws.amazon.com/zh_tw/AmazonS3/latest/userguide/amazon-s3-condition-keys.html
		- https://aws.amazon.com/tw/premiumsupport/knowledge-center/s3-bucket-owner-full-control-acl/
	- `Timeout waiting for connection from pool while calling S3client.getObject`
		- https://github.com/aws/aws-sdk-java/issues/1405

### 20220814
- Spring boot
	- RestTemplate
		- https://openhome.cc/Gossip/Spring/RestTemplate.html
		- https://elim168.github.io/spring/bean/30.Spring%E4%B9%8BRestTemplate%E4%BB%8B%E7%BB%8D.html#:~:text=RestTemplate%E6%98%AFSpring%20Web%E6%A8%A1%E5%9D%97,RestTemplate%E6%93%8D%E4%BD%9C%E5%B0%86%E9%9D%9E%E5%B8%B8%E6%96%B9%E4%BE%BF%E3%80%82
		- https://www.796t.com/article.php?id=38894
		- https://zhuanlan.zhihu.com/p/78261630
- Apache JMeter
	- designed to load test functional behavior and measure performance. It was originally designed for testing Web Applications but has since expanded to other test functions.
	- https://jmeter.apache.org/download_jmeter.cgi
	- https://ithelp.ithome.com.tw/articles/10203900#:~:text=%E7%B0%A1%E4%BB%8B,Mac%20OS%20X%20%E4%B8%8A%E5%9F%B7%E8%A1%8C%E3%80%82
	- https://ithelp.ithome.com.tw/articles/10186852
	- https://stackoverflow.com/questions/22610316/how-do-i-install-jmeter-on-a-mac

### 20220811
- Freemarker
	- `freemarker.template.TemplateNotFoundException: Template not found for name “xxx.ftl“`
		- https://blog.csdn.net/hdn_kb/article/details/108405971
		- https://blog.csdn.net/weixin_45196863/article/details/119428018
		- https://www.twblogs.net/a/5efdd05ee53eaf40aa871903
		- https://www.cnblogs.com/chenfeng1122/p/6884576.html
	```xml
	<!-- example V1 -->
	<!-- put below in <build></build> in pom.xml -->
	<resources>
            <resource>
                <directory>${basedir}/src/main/java</directory>
                <includes>
                    <include>**/*.*</include>
                </includes>
                <excludes>
                    <exclude>**/*.java</exclude>
                </excludes>
                <filtering>false</filtering>
            </resource>
        </resources>
	
	<!-- example V2 -->
	<resources>
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>**/*.*</include>
                </includes>
            </resource>
        </resources>
	```

### 20220809
- AWS S3
	- download s3 file by the URL in a browser
		- https://stackoverflow.com/questions/50151062/unable-to-download-a-file-from-s3-by-the-url-in-a-browser
	- presigned URL from S3 object
		- https://docs.aws.amazon.com/sdk-for-java/latest/developer-guide/examples-s3-presign.html
		- https://docs.aws.amazon.com/AmazonS3/latest/userguide/ShareObjectPreSignedURL.html

### 20220806
- Spring boot
	- 跨域訪問
		- jsoup
		- CORS (cross-origin resource sharing)
			- https://bbs.huaweicloud.com/blogs/346514

### 20220805
- FreeMarker
	- `Apache FreeMarker™ is a template engine: a Java library to generate text output (HTML web pages, e-mails, configuration files, source code, etc.) based on templates and changing data.`
	- https://freemarker.apache.org/
	- http://freemarker.foofun.cn/index.html
	- http://blog.appx.tw/2017/05/10/freemarker1/
	- http://blog.appx.tw/2017/05/11/freemarker2/
- DB
	- SQL jdbc connection pool
		- https://www.baeldung.com/java-connection-pooling
		- https://www.progress.com/tutorials/jdbc/jdbc-jdbc-connection-pooling

### 20220804
- Apollo
	- `conf ordering : Apollo VS local conf (e.g. application.yml, bootstrap.properties..)`
		- https://www.modb.pro/db/126648
		- https://blog.csdn.net/lonelymanontheway/article/details/119968760
		- Conclusion : `will load Apollo conf only if both (Apollo, local) are set`

### 20220803
- AWS
	- IAM key
		- https://docs.aws.amazon.com/zh_tw/IAM/latest/UserGuide/id_credentials_access-keys.html
- Spring cron setting (e.g. : `@Scheduled(cron = "0 0 12 * * * ")`)
	- https://blog.csdn.net/weixin_39925350/article/details/111391748
- `lombok @Accessors(chain=true)`
	https://blog.51cto.com/wangzhenjun/4314997
	- https://www.jianshu.com/p/67a15b2e4a92
	- https://blog.csdn.net/weixin_38229356/article/details/82937420
```java
// traditional
Person person = new Person();
person.setName("wang");
person.setSex("male");
person.setEmail("123@XXX.com");
person.setDate(new Date());
person.setAddr("NY");

// with @Accessors(chain = true)
Person person = new Person();
person.setName("wang").setSex("male").setEmail("123@xxx.com").setDate(new Date()).setAddr("NY");
```

### 20220802
- XXL-JOB
	- integrate with java (spring boot)
		- https://www.xuxueli.com/xxl-job/#3.3%20GLUE%E6%A8%A1%E5%BC%8F(Java)
		- https://www.796t.com/article.php?id=161562
		- https://iter01.com/663746.html
		- https://juejin.cn/post/7068110940499083271
- Java AWS S3 SDK
```java
import com.amazonaws.services.s3.AmazonS3;
import com.amazonaws.services.s3.AmazonS3ClientBuilder;
import com.amazonaws.services.s3.AmazonS3URI;
```

### 20220731
- Java
	- 自旋鎖 spinlock
		- https://learnku.com/articles/49689
		- https://codertw.com/%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80/748267/

### 20220728
- Java
	- JSONObject -> HashMap
		- https://stackoverflow.com/questions/21720759/convert-a-json-string-to-a-hashmap
- Python
	- GIL（Global Interpreter Lock）
		- https://iter01.com/596673.html
		- https://www.maxlist.xyz/2020/03/15/gil-thread-safe-atomic/
	- GIL VS regular lock, and their low level implementation
	- Mutable & Immutable Objects in Python
		- https://www.guru99.com/mutable-and-immutable-in-python.html
		- https://towardsdatascience.com/https-towardsdatascience-com-python-basics-mutable-vs-immutable-objects-829a0cb1530a
	- python multiprocessing vs multithreading
		- https://timber.io/blog/multiprocessing-vs-multithreading-in-python-what-you-need-to-know/
		- https://stackoverflow.com/questions/3044580/multiprocessing-vs-threading-python

### 20220727
- Airflow
	- Airflow as KafkaProducer, send event to kafka topic
		- https://pypi.org/project/airflow-provider-kafka/0.1.0/
		- https://stackoverflow.com/questions/46778171/stream-files-to-kafka-using-airflow
- Backend
	- Distributed lock - `Zookeeper, Redis, Mysql`
		- `Zookeeper` is better solution in general
		- https://codertw.com/%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80/717420/
		- https://www.796t.com/p/1123418.html
		- https://gitbook.cn/books/5dd75cffd251cc422ab2e7fb/index.html
		- https://blog.yowko.com/redlocknet-redis-lock/
		- https://yuanchieh.page/posts/2020/2020-01-14_redis-lock-redlock-%E5%8E%9F%E7%90%86%E5%88%86%E6%9E%90%E8%88%87%E5%AF%A6%E4%BD%9C/
		- https://redis.io/docs/reference/patterns/distributed-locks/
	- ScheduledThreadPool (Java)
		- https://blog.csdn.net/qq_35580883/article/details/78747263
		- https://www.jianshu.com/p/925dba9f5969
		- https://ithelp.ithome.com.tw/articles/10207656
		- https://www.cjavapy.com/article/2621/

### 20220726
- Spring boot form
	- https://www.writebug.com/explore/article/g5wnHnxy
	- https://github.com/forezp/SpringBootLearning
	- https://github.com/yennanliu/SpringPlayground/tree/main/ref_project/markdown-blog-main
- Mybatis
	- via `resultMap` do java attr - Db column name mapping
		- https://www.youtube.com/watch?v=gk_pm_Uaa_Y&list=PLmOn9nNkQxJEWFBs6hVmDC5m8SbbIiDwY&index=42
		- https://blog.csdn.net/weixin_40340362/article/details/93128692
		- https://www.796t.com/content/1547529875.html
		- https://xuzhongcn.github.io/mybatis/MyBatis-02.html
	- `org.apache.ibatis.binding.BindingException: Invalid bound statement (not found)` error
		- https://blog.csdn.net/weixin_43570367/article/details/103147854
		-> can try to rebuild maven project first

### 20220724
- Nginx : `Reverse Proxy web server`
	- Web Serveer VS Application Server, Forward Proxy VS Reverse Proxy, 反向代理
		- https://medium.com/starbugs/web-server-nginx-1-cf5188459108
		- https://www.maxlist.xyz/2020/06/18/flask-nginx/
		- https://zh.m.wikipedia.org/zh-hant/Nginx#:~:text=Nginx%EF%BC%88%E7%99%BC%E9%9F%B3%E5%90%8C%E3%80%8Cengine%20X,%E5%85%AC%E5%8F%B8%E4%BB%A5%E6%8F%90%E4%BE%9B%E6%94%AF%E6%8C%81%E6%9C%8D%E5%8B%99%E3%80%82
	- 前向代理（Proxy)（網路代理)
		- 也稱網路代理，是一種特殊的網路服務，允許一個終端（一般為客戶端）通過這個服務與另一個終端（一般為伺服器）進行非直接的連接。一些閘道器、路由器等網路裝置具備網路代理功能。一般認為代理服務有利於保障網路終端的隱私或安全，在一定程度上能夠阻止網路攻擊。
		- 前向代理作為客戶端的代理，將從網際網路上取得的資源返回給一個或多個的客戶端，伺服器端（如Web伺服器）只知道代理的IP位址而不知道客戶端的IP位
		- https://zh.wikipedia.org/zh-tw/%E4%BB%A3%E7%90%86%E6%9C%8D%E5%8A%A1%E5%99%A8
	- 反向代理
		- 反向代理在電腦網路中是代理伺服器的一種。伺服器根據客戶端的請求，從其關聯的一組或多組後端伺服器（如Web伺服器）上取得資源，然後再將這些資源返回給客戶端，`客戶端只會得知反向代理的IP位址，而不知道在代理伺服器後面的伺服器叢集的存在`。
		- 而反向代理是作為伺服器端（如Web伺服器）的代理使用，而不是客戶端。客戶端藉由前向代理可以間接存取很多不同網際網路伺服器（叢集）的資源
		- https://zh.wikipedia.org/zh-tw/%E5%8F%8D%E5%90%91%E4%BB%A3%E7%90%86#:~:text=%E5%8F%8D%E5%90%91%E4%BB%A3%E7%90%86%E5%9C%A8%E9%9B%BB%E8%85%A6,%E4%BC%BA%E6%9C%8D%E5%99%A8%E5%8F%A2%E9%9B%86%E7%9A%84%E5%AD%98%E5%9C%A8%E3%80%82
	- <p><img src ="./doc/pic/reverse_proxy1.png" ></p>
	- <p><img src ="./doc/pic/reverse_proxy2.png" ></p>

### 20220722
- Mybatis plus
	- queryWrapper
		- https://blog.csdn.net/m0_37034294/article/details/82917234
	- com.baomidou.mybatisplus.extension.service.impl.ServiceImpl
		- https://www.twblogs.net/a/5c8a4f2bbd9eee35cd6a9d76

### 20220719
- Java
	- time zone enum example
		- https://github.com/roth-source/roth-lang/blob/master/roth-lang/src/main/java/roth/lang/TimeZone.java
		- https://www.w3resource.com/java-exercises/datetime/java-datetime-exercise-43.php
		- https://mkyong.com/java/java-display-list-of-timezone-with-gmt/

### 20220718
- Spring boot
	- POJO、PO、DTO、VO、BO
		- brief :
			- PO (persistent object)
			- DTO (Data Transfer Object)
			- VO (value object)
			- DAO (data access object)
			- BO (business object)
		- Ref :
			- https://hackmd.io/@MonsterLee/HJyAdgRBB
			- https://www.cnblogs.com/tooyi/p/13340374.html

### 20220716
- Mybatis grammer
	- dynamic SQL
		- https://mybatis.org/mybatis-3/dynamic-sql.html
- Postman
	- HTTP request to `gray deployment`
		- TODO
- Devop
	- Using Services to Implement Simple Grayscale Release and Blue-Green Deployment
		- https://support.huaweicloud.com/intl/en-us/bestpractice-cce/cce_bestpractice_10002.html
		- https://support.huaweicloud.com/intl/en-us/bestpractice-cce/cce_bestpractice_10003.html

### 20220715
- Java
	- map Enum type to DB
		- https://vladmihalcea.com/the-best-way-to-map-an-enum-type-with-jpa-and-hibernate/
		- https://www.baeldung.com/jpa-persisting-enums-in-jpa
		- https://thorben-janssen.com/hibernate-tips-map-enum-database-column/

### 20220709
- Mybatis paging (分頁)
	- https://www.cnblogs.com/tanghaorong/p/14017180.html
	- https://tw.gitbook.net/mybatis/mybatis_pagination.html
	- https://blog.csdn.net/feinifi/article/details/88769101
	- https://juejin.cn/post/6996303139540467749
	- https://aijishu.com/a/1060000000023074
	- https://www.google.com/search?q=mybatis+%E5%88%86%E9%A0%81&rlz=1C5CHFA_enTW908TW908&oq=mybatis+%E5%88%86%E9%A0%81&aqs=chrome..69i57j0i5i30j0i8i30.3887j0j7&sourceid=chrome&ie=UTF-8
	- code
		- https://github.com/yennanliu/SpringPlayground/blob/dev-017-prod-api-group-sub-group/springEcommerceGuli/backend/EcommerceGuli/gulimall-product/src/main/java/com/yen/gulimall/product/config/MybatisConfig.java
		- https://github.com/yennanliu/SpringPlayground/tree/dev-017-prod-api-group-sub-group/springBasics/PaginationDemo

### 20220708
- Mybatis
	- #{} VS ${}
		- https://www.w3cschool.cn/mybatis/mybatis-yta93bpj.html
	- w3school
		- https://www.w3cschool.cn/mybatis/mybatis-dyr53b5w.html

### 20220705
- Mysql
	- insert update update if duplicate
		- https://www.alibabacloud.com/help/en/analyticdb-for-mysql/latest/insert-on-duplicate-key-update
		- https://www.mysqltutorial.org/mysql-insert-or-update-on-duplicate-key-update/
		- https://blog.csdn.net/u011066470/article/details/100098626

### 20220703
- Spring Boot
	- Spring Data JPA
		- https://www.gss.com.tw/blog/spring-data-jpa-1#:~:text=Spring%20Data%20JPA%20%E6%98%AFSpring,%E4%BD%A0%E5%AF%A6%E4%BD%9C%E5%85%B6%E5%8A%9F%E8%83%BD%E3%80%82
		- https://ithelp.ithome.com.tw/articles/10194906

### 20220701
- Spring Boot
	- `@Configuration` annotation
		- https://blog.csdn.net/loongkingwhat/article/details/105752446
		- https://juejin.cn/post/7034421582034370597
		- https://iter01.com/580722.html

### 20220629
- Spring boot
	- `Error creating bean with name 'dataSource' defined in class path resource`
		- https://blog.csdn.net/wcc27857285/article/details/90679424
	- `@RequestBody VS @RequestParam`
		- https://blog.csdn.net/weixin_38004638/article/details/99655322
		- https://www.gushiciku.cn/pl/pnqB/zh-tw
	- POSTMAN sends user-defined-class with `@RequestParam` via GET request
		- https://www.twblogs.net/a/5eeec3017301656afddacbd8/?lang=zh-cn

### 20220627
- Micro service
	- CircuitBreaker (服務熔斷)
		- https://martinfowler.com/bliki/CircuitBreaker.html
		- https://youtu.be/FOHjhgdc6tw?t=371
- Spring boot
	- Paging
		- https://hackmd.io/@KaiChen/HJEN-mMVw
		- https://rumenz.com/java-topic/spring-boot2/pagination-sorting-example/index.html
		- https://matthung0807.blogspot.com/2019/09/spring-data-jpa-pagination-and-sorting.html
	- Unit test
		- https://kucw.github.io/blog/2020/2/spring-unit-test-mockito/
		- https://www.tpisoftware.com/tpu/articleDetails/1256
		- https://spring.io/guides/gs/testing-web/
		- https://www.baeldung.com/spring-boot-testing
		- [ref code](https://github.com/yennanliu/LambdaHelloWorld/blob/master/lab2/simple-handler/src/test/java/com/yen/SimpleHandlerTest.java) : unit test with mockito
		- [ref code2](https://github.com/yennanliu/JavaHelloWorld/blob/main/src/test/java/MockitoDemo/MyClassTest.java)

### 20220624
- MyBatis
	- mapper.xml, java bean - JDBC table col name mapping
		- https://youtu.be/4wWM7MmfxXw?t=1171
		- https://github.com/yennanliu/SpringPlayground/blob/main/springCloud1/cloud-provider-payment8001/src/main/resources/mapper/PaymentMapper.xml
	- enable camel style (java bean <-> SQL fields)
		- https://www.cnblogs.com/gavincoder/p/10140562.html
- `Pom.xml`
	- scope (e.g. `<scope>compile</scope>`, `<scope>provided</scope>`...)
		- https://blog.csdn.net/mccand1234/article/details/60962283
		- https://blog.csdn.net/kimylrong/article/details/50353161
		- https://segmentfault.com/a/1190000038594247

### 20220622
- Mybatis
	- `Error:java: Can‘t generate mapping method with primitive return type.`
		- https://www.cnblogs.com/andjieran/p/15974630.html
		- https://www.cnblogs.com/mike-mei/p/15792360.html
- Mybatis plus
	- BaseMapper
		- https://walkonnet.com/archives/452416
		- https://blog.csdn.net/qq924862077/article/details/81774958

- mysql insert with increment id
	- https://www.fooish.com/sql/auto-increment.html

### 20220621
- Maven (pom.xml)
	- `dependencyManagement VS dependency`
		- https://youtu.be/uG_UKEa41-s?t=51
		- https://kknews.cc/zh-tw/code/bmyyy4j.html
		- https://blog.csdn.net/vtopqx/article/details/79034835
		- https://www.796t.com/content/1546777827.html
- Mybatis dynamic SQL
	- https://mybatis.org/mybatis-3/dynamic-sql.html
- spring-cloud-starter-feign
	- https://spring-cloud-wiki.readthedocs.io/zh_CN/latest/pages/feign.html#:~:text=Feign%E6%98%AF%E4%B8%80%E4%B8%AA%E5%A3%B0%E6%98%8E%E5%BC%8F,%E6%9C%8D%E5%8A%A1%E8%AF%B7%E6%B1%82%E5%8F%8A%E7%9B%B8%E5%85%B3%E5%A4%84%E7%90%86%E3%80%82
	- https://tw511.com/a/01/26332.html

### 20220617
- Spring boot
	- @RestController VS @Controller
		- 如果返回 String 或者 json 的話就直接類上用 @RestController
		- 如果想要頁面跳轉的話，就使用 @Controller
		- 如果只有在某方法上返回 json，其他方法跳轉頁面，則在類上新增 @Controller，在需要返回 String 和 json 的方法上新增 @ResponseBody 註解
		- https://www.796t.com/content/1546330804.html
		- https://blog.csdn.net/ld1170813335/article/details/78690713

### 20220615
- Spring boot/cloud
	- use user-defined modules
		- https://blog.csdn.net/liaomingwu/article/details/122442649
		- https://blog.51cto.com/u_15239532/5144312
		- https://blog.csdn.net/qq_29718835/article/details/120828561
	- Download API code example
		- https://www.callicoder.com/spring-boot-file-upload-download-rest-api-example/
		- http://www.mastertheboss.com/jboss-frameworks/resteasy/using-rest-services-to-manage-download-and-upload-of-files/
		- https://www.devglan.com/spring-boot/spring-boot-file-upload-download#:~:text=Spring%20Boot%20File%20Download%20from%20Local%20File%20System&text=It%20is%20a%20simple%20GET,as%20application%2Foctet%2Dstream.
	- Spring Boot + AWS S3 Download Bucket File
		- https://www.techgeeknext.com/cloud/aws/amazon-s3-springboot-download-file-in-s3-bucket
		- https://codezup.com/upload-download-and-delete-file-from-aws-s3-spring-boot/

### 20220614
- Deployment Strategies: `Blue-Green, Canary (AKA 灰度發布 gray deployment), Red-Black Deployment`
	- https://harness.io/blog/continuous-verification/blue-green-canary-deployment-strategies/
	- https://segmentfault.com/a/1190000040892537/en
	- https://dev.to/mostlyjason/intro-to-deployment-strategies-blue-green-canary-and-more-3a3
	- http://www.uj5u.com/qita/281580.html
	- https://codertw.com/%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80/725615/
	- Red-Black Deployment
		- https://www.gushiciku.cn/pl/gUOs/zh-tw

### 20220606
- Spring boot
	- BeanUtils.copyProperties
		- https://www.796t.com/article.php?id=20809
		- https://www.796t.com/p/588001.html
	- Mybatis plus
		- @TableLogic
			- https://blog.csdn.net/qq_39454665/article/details/116199952
			- https://blog.csdn.net/Rm_and_Rf/article/details/106927318
- AWS
	- Redshift API (java)
		- https://docs.aws.amazon.com/zh_tw/redshift/latest/mgmt/data-api.html
		- https://sdk.amazonaws.com/java/api/latest/software/amazon/awssdk/services/redshiftdata/RedshiftDataClient.html

### 20220604
- Spring boot
	- ApplicationRunner VS CommandLineRunner 
		- https://segmentfault.com/a/1190000039421968
		- https://juejin.cn/post/6844903589232508942
		- https://blog.csdn.net/qq_20919883/article/details/111412077
		- https://www.gushiciku.cn/pl/pZxA/zh-tw
		- ApplicationRunner跟CommandLineRunner是區別是在run方法裡接收的參數不同，
			- CommandLineRuner接收的參數是String... args
			- ApplicationRunner的run方法的參數是ApplicationArguments

### 20220603
- Apache Dubbo
	- https://dubbo.apache.org/zh/index.html
	- https://kknews.cc/zh-tw/tech/2nkyamy.html
	- https://www.youtube.com/watch?v=k39CmgKxO3k&list=PLmOn9nNkQxJESDPnrV6v_aiFgsehwLgku&index=31
- Spring Cloud
	- https://www.youtube.com/watch?v=P5o-6Od5cfc&list=PLmOn9nNkQxJESDPnrV6v_aiFgsehwLgku&index=34
	- https://www.gushiciku.cn/pl/pUgh/zh-tw
	- https://ithelp.ithome.com.tw/articles/10192488
	- https://zhuanlan.zhihu.com/p/369125275#:~:text=Spring%20Cloud%E6%98%AF%E4%B8%80%E4%B8%AA%E4%B8%80,%E5%92%8C%E9%9B%86%E7%BE%A4%E7%8A%B6%E6%80%81%E7%AE%A1%E7%90%86%E7%AD%89)%E3%80%82

### 20220601
- DW layer : `ODS,DM,DWD,DWS,DIM`
	- https://help.aliyun.com/apsara/enterprise/v_3_15_0_20210816/dide/enterprise-ascm-user-guide/overview-of-data-warehouse-planning-1.html
	- https://blog.51cto.com/u_15162069/2772331
	- https://blog.csdn.net/pmdream/article/details/113601956
	- https://chowdera.com/2021/12/202112310752342124.html
	- https://www.cnblogs.com/yoyo008/p/15213829.html

### 20220531
- Spring boot
	- `Consider defining a bean of type ‘xxx.mapper.UserMapper‘ in your configuration`
		- https://blog.csdn.net/cnds123321/article/details/118222109
		- https://blog.csdn.net/qq_38974638/article/details/105739795
		- https://blog.csdn.net/cnds123321/article/details/118224473
		- https://stackoverflow.com/questions/70565863/interface-not-recognized-as-a-bean-by-spring-boot
- Project management
	- PRD (business requirements document)
		-  The BRD describes the problems the project is trying to solve and the required outcomes necessary to deliver value.
		-  https://www.lucidchart.com/blog/tips-for-a-perfect-business-requirements-document#:~:text=The%20foundation%20of%20a%20successful,everyone%20on%20the%20same%20page.

### 20220530
- REST request
	- `PUT VS POST`
		- https://blog.51cto.com/u_15301829/3095822#:~:text=%E5%9C%A8http%E4%B8%AD%EF%BC%8Cput%E8%A2%AB,%E7%9A%84%EF%BC%8C%E9%82%A3%E5%B0%B1%E6%98%AF%E5%B9%82%E7%AD%89%E3%80%82
		- https://www.w3help.cc/a/202109/1093210.html
		- https://hackmd.io/@monkenWu/Sk9Q5VoV4/https%3A%2F%2Fhackmd.io%2F%40gen6UjQISdy0QDN62cYPYQ%2FHJh9zOE7V?type=book

### 20220528
- JMS (Java Message Service) VS RabbitMQ
	- https://www.oracle.com/technical-resources/articles/java/intro-java-message-service.html
	- https://openhome.cc/Gossip/EJB3Gossip/JavaMessageService.html
- RabbitMQ
	- https://www.youtube.com/watch?v=IVjsiu0OrfQ&list=PLmOn9nNkQxJESDPnrV6v_aiFgsehwLgku&index=16

### 20220527
- Postman
	- send request via raw paste
		- https://github.com/yennanliu/utility_shell/blob/master/postman/postman_cmd.sh#L1

### 20220526
- Spring boot
	- Flyway : DB migration (version control)
		- https://www.baeldung.com/database-migrations-with-flyway
		- https://iter01.com/504630.html
		- https://www.tpisoftware.com/tpu/articleDetails/2422
 
### 20220523
- Linux
	- tmux
		- https://blog.darkthread.net/blog/tmux/?fbclid=IwAR2TSuzKnqrp_6tZmD_6VZPT83valr_a16RBWD7Kg2wtdsd9FY8mBLYt_9cg

### 20220522
- Spring boot
	- webflux : sync, async request
		- https://medium.com/swlh/spring-boot-webclient-cheat-sheet-5be26cfa3e
- Data
	- data validation
		- Integrity
		- Uniqueness
		- Consistency
		- Accuracy
		- Delay

### 20220521
- Internet
	- `cert驗證機制 `
		- https://ithelp.ithome.com.tw/articles/10193095 
	- API cert ? (SSL relative)
		- API gateway
			- https://docs.aws.amazon.com/zh_tw/apigateway/latest/developerguide/getting-started-client-side-ssl-authentication.html
			- https://docs.microsoft.com/zh-tw/azure/api-management/api-management-howto-mutual-certificates-for-clients
	- DNS
		- https://aws.amazon.com/tw/route53/what-is-dns/#:~:text=DNS%EF%BC%8C%E4%B9%9F%E5%B0%B1%E6%98%AF%E7%B6%B2%E5%9F%9F,%E4%BE%8B%E5%A6%82%EF%BC%8C192.0.2.44)%E3%80%82
		- https://www.nss.com.tw/domain-name-system/

- Spring boot
	- mybatis plus
	- JPA

### 20220519
- Spring boot
	- mybatis
		- https://autoposter.pixnet.net/blog/post/121469360
- DW/DB
	- starrocks
		- https://docs.starrocks.com/zh-cn/main/quick_start/Create_table

### 20220514
- Spring boot
	- `@bean`
		- https://chikuwa-tech-study.blogspot.com/2021/05/spring-boot-bean-introduction.html
		- https://chikuwa-tech-study.blogspot.com/2021/05/spring-boot-construct-bean-programmatically.html
		- https://zhuanlan.zhihu.com/p/60256169
		- https://iter01.com/609191.html
		- https://ithelp.ithome.com.tw/articles/10268064
	- `@Autowired`
		- https://walkonnet.com/archives/464370
		- https://iter01.com/558676.html
		- http://tw511.com/20/238/8850.html
	- 透過AppConfig元件進行建立兩項Bean類別元件，當我們服務啟動的時候，會自動將Bean載入Spring IoC容器中，故我們亦可透過ApplicationContext方式取得Bean類別，亦可透過註解方式(@Autowired)獲取Bean類別

### 20220426
- CS general
	- recent backend interview questions
		- https://angelswengineer.medium.com/2021%E5%BA%95-2022%E5%88%9D-backend-software-engineer-interview-%E5%B8%B8%E8%A6%8B%E8%80%83%E9%A1%8C-92d5c6ba384c

### 20220425
- Java Spring
	- https://www.baeldung.com/spring-cloud-netflix-eureka : Introduction to Spring Cloud Netflix
	- https://netflix.github.io/ :  netflix oss
	- https://spring.io/projects/spring-cloud-netflix : Spring Cloud Netflix
- CS general topics
	- https://hexus.net/tech/tech-explained/ram/702-ddr-ii-how-it-works/ : DDR II : how it works
	- https://en.wikipedia.org/wiki/Round-robin_scheduling : round robin scheduling
	- https://en.wikipedia.org/wiki/C10k_problem : c10k problem

### 20220418
- GraphQL
	- Scala
		- Caliban
			- https://www.youtube.com/watch?v=lgxUKsOH65k
			- https://www.youtube.com/channel/UCKvhw2CPR-0S4XZ1bNlihnw

### 20220406
- GraphQL
	- Scala 
		- server
			- https://github.com/sangria-graphql/sangria
			- https://github.com/ghostdogpr/caliban
		- client
			- https://github.com/ghostdogpr/caliban
	- Python
		- https://graphql.org/code/#python
	- Ref
		- https://graphql.cn/code/#scala


### 20220401
- DB
	- Hbase
	- dynamoDB
	- column based VS row based storage

### 20220323
- GraphQL
	- intro
		- https://ithelp.ithome.com.tw/articles/10200678
		- https://graphql.cn/learn/
		- https://hackmd.io/@dennySORA/GraphQL
### 20220322
- Scala
	- make GraphQL API call with scala
		-  https://sysgears.com/articles/how-to-create-a-graphql-api-with-scala-and-sangria/
- Java
	- reflection, dynamic Proxy
		- https://dunwu.github.io/javacore/basics/java-reflection.html#_4-%E5%8A%A8%E6%80%81%E4%BB%A3%E7%90%86
- API
	- Comparing API Architectural Styles: SOAP vs REST vs GraphQL vs RPC
		- https://www.altexsoft.com/blog/soap-vs-rest-vs-graphql-vs-rpc/

### 20220321
- Java
	- JVM error handling
	- how to config different apps run with different conf in SAME JVM
		- different spring aps run in the same JVM for example
### 20220314
- webSocket
	- https://hoohoo.top/blog/gain-an-in-depth-understanding-of-websocket-protocols-common-attack-techniques-and-protection-strategies/
	- https://hackmd.io/@dez/rJRxmO2qS

### 20220313
- Hexo : tool for static personnel site
	- https://hsins.github.io/blog/2018/01/04/Built-Personal-Website-with-Hexo/

### 20220223
- Python
	- Sorting time complexity
		- quick sort : O(NlogN) ~ O(N**2)
		- merge sort : O(NlogN) ~ O(N**2)
	- arr.sort() # time complexity ? -> use quick sort by default
	- py OOP
		- https://learn.markteaching.com/%E3%80%90python-%E6%95%99%E5%AD%B8%E3%80%91oop-%E7%B9%BC%E6%89%BF-%E5%B0%81%E8%A3%9D-%E5%A4%9A%E5%9E%8B-%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95-example/
		- https://www.learncodewithmike.com/2020/01/python-class.html
		- https://june.monster/python-101-object-oriented-programming/

### 20220209
- Scala/Java
	- MockConsumer : for kafka unit test
		- https://www.baeldung.com/kafka-mockconsumer

### 20220208
- Scala
	- if, and logic in pattern match
		- https://www.codenong.com/17034404/
		- https://stackoverflow.com/questions/17034404/matching-on-class-members-error-not-found-value
		- https://alvinalexander.com/scala/how-to-use-if-then-expressions-guards-in-case-statements-scala/
- Python
	- sum() time compmexity : O(N)
	- https://blog.finxter.com/python-sum/#:~:text=Report%20Ad-,Python%20sum()%20Time%20Complexity,touch%E2%80%9D%20every%20iterable%20element%20once.
	- https://stackoverflow.com/questions/20135093/what-is-the-time-complexity-of-sum-in-python

### 20220207
- Spark
	- Shuffle system
		- https://books.japila.pl/apache-spark-internals/shuffle/
		- https://www.slideshare.net/databricks/apache-spark-at-scale-in-the-cloud

### 20220125
- Kafka
	- get offset (per topic, partition)
	- https://gist.github.com/erhwenkuo/019ada38e645b4b76862918fe5205c9c
	- https://gist.github.com/erhwenkuo/bc4020112367af7abb78357963306ce0
- Flink
	- kafka client
		- https://github.com/yennanliu/scala-kafka-client/blob/master/akka/src/main/scala/cakesolutions/kafka/akka/TrackPartitions.scala
		- https://github.com/yennanliu/KafkaHelloWorld/tree/master/src/main/scala/Consumer
		- https://github.com/yennanliu/KafkaHelloWorld/blob/master/src/main/scala/common/KafkaProducerRecord.scala

### 20220124
- Flink
	- implement `FlinkKafkaConsumer` read kafka traffic in `defined period`
		- https://blog.csdn.net/qq_42164959/article/details/109295530?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1.pc_relevant_default&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1.pc_relevant_default&utm_relevant_index=1
		
### 20220120
- Flink
	- bugs : `org.apache.flink.runtime.fs.hdfs.HadoopRecoverableFsDataOutputStream.safelyTruncateFile`
		- https://issues.apache.org/jira/browse/FLINK-18592
		- https://issues.apache.org/jira/browse/FLINK-18592
		- https://www.saoniuhuo.com/question/detail-1935177.html
		- example code
			- https://xie.infoq.cn/article/4106f684280aa60ac7cb7c269
	- kafka consumer with custom offset
		- https://nightlies.apache.org/flink/flink-docs-release-1.12/dev/connectors/kafka.html

### 20220115
- Python
	- py memory management
		- https://realpython.com/python-memory-management/
		- https://docs.python.org/zh-tw/3.7/c-api/memory.html
		- https://www.itread01.com/content/1546061954.html
- Java
	- java memory management
		- https://dzone.com/articles/java-memory-management
		- https://docs.oracle.com/cd/E13150_01/jrockit_jvm/jrockit/geninfo/diagnos/garbage_collect.html
		- https://www.geeksforgeeks.org/java-memory-management/
		- https://www.javatpoint.com/memory-management-in-java

### 20220105
- Spark
	- write to HDFS setting
		- https://spark.apache.org/docs/2.3.0/configuration.html
		- https://www.cnblogs.com/chhyan-dream/p/13492589.html
		- If you plan to read and write from HDFS using Spark, there are two Hadoop configuration files that should be included on Spark’s classpath:
		 	- hdfs-site.xml, which provides default behaviors for the HDFS client.
			- core-site.xml, which sets the default filesystem name.
		- The location of these configuration files varies across Hadoop versions, but a common location is inside of /etc/hadoop/conf. Some tools create configurations on-the-fly, but offer a mechanism to download copies of them. To make these files visible to Spark, set HADOOP_CONF_DIR in $SPARK_HOME/conf/spark-env.sh to a location containing the configuration files.

### 20211221
- Flink
	- Flink internal memory model
		- https://www.codetd.com/en/article/12787053

### 20211215
- Scala
	- package object
		- https://docs.scala-lang.org/zh-cn/tour/package-objects.html
		- https://www.jianshu.com/p/9d6facd14472
		- https://blog.csdn.net/lovehuangjiaju/article/details/47022989

### 20211208
- Spark3
	- https://spark.apache.org/docs/latest/monitoring.html : Monitoring and Instrumentation

### 20211207
- Flink
	- Rolling policy
	- file sink cycle
	- conf checks

### 20211203
- Flink
	- flink memory management ref
		- https://nightlies.apache.org/flink/flink-docs-master/docs/deployment/memory/mem_setup_tm/
		- https://nightlies.apache.org/flink/flink-docs-release-1.12/deployment/memory/mem_setup.html#configure-total-memory
		- https://www.modb.pro/db/142743
		- https://www.gushiciku.cn/pl/abdS/zh-hk
		- https://jxeditor.github.io/2020/12/14/Flink%E7%B3%BB%E7%BB%9F%E9%85%8D%E7%BD%AE%E5%8F%82%E6%95%B0%E4%B8%80%E8%A7%88/
### 20211110
- Java
	- java.lang.OutOfMemoryError: unable-to-create-new-native-thread
		- https://www.baeldung.com/java-outofmemoryerror-unable-to-create-new-native-thread

- Spark stream foreachRDD
	- https://blog.allegro.tech/2015/08/spark-kafka-integration.html
	- https://spark.apache.org/docs/latest/streaming-programming-guide.html
	- https://stackoverflow.com/questions/46015704/spark-streaming-on-yarn-there-is-insufficient-memory-for-the-java-runtime-envi

### 20211109
- Spark
	- SF : Understanding Spark serialization
		- https://stackoverflow.com/questions/40818001/understanding-spark-serialization?fbclid=IwAR3r4HcbOf0wQnPUg7UcKyTYkIMeaxUMGpgSsQJIKI6kXrGGpurCVKDfVg0
		
### 20211108
- Spark
	- Serialization issues part 1 & 2
		- https://www.waitingforcode.com/apache-spark/serialization-issues-part-1/read
		- https://www.waitingforcode.com/apache-spark/serialization-issues-part-2/read
		- https://github.com/bartosz25/spark-scala-playground
### 20211026
- Scala
	- Shapeless
		- https://jto.github.io/articles/getting-started-with-shapeless/
		- https://github.com/milessabin/shapeless

	- HList
		- https://www.baeldung.com/scala/generic-programming

- Spark
	- Spark Standalone Mode
		- https://spark.apache.org/docs/2.3.1/spark-standalone.html#cluster-launch-scripts

### 20210923
- Python
	- Deep copy VS shallow copy
		- https://www.runoob.com/w3cnote/python-understanding-dict-copy-shallow-or-deep.html
		- https://iter01.com/578999.html

### 20210912
- ETL
	- [Top 8 Best Practices for High-Performance ETL Processing Using Amazon Redshift](https://aws.amazon.com/tw/blogs/big-data/top-8-best-practices-for-high-performance-etl-processing-using-amazon-redshift/)

### 20210908
- Python
	- `if __name__ == '__main__'`
		- http://blog.castman.net/%E6%95%99%E5%AD%B8/2018/01/27/python-name-main.html
- Java
	- heap, off-heap
		- https://www.itread01.com/content/1549478361.html
	- spark tune heap, off-heap memory
		- https://www.waitingforcode.com/apache-spark/apache-spark-off-heap-memory/read
		- https://stackoverflow.com/questions/43330902/spark-off-heap-memory-config-and-tungsten
	
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
