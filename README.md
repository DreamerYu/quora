# Quora
Used the SSM framework to build a question and answer community like Quora.


## 1. Project Environment

  * **Operation System** : Ubuntu 17.04
  * **IDE** ：IntelliJ IDEA && Pycharm
  * **JDK Version** : JDK1.8
  * **Python Version** : Python 2.7
  * **Web Container** ： SpringBoot
  * **Database** ：Mysql-8.0.13 and Mybatis
  * **Dependency Tool** : Maven
  * **Version Control**: Git


---

## 2. Project Import
- **Download or Clone**

Use `Download Zip` or `git clone`

- **Import to the IDE**

Use `IDEA` to import the project, and configue `maven`, `JDK` and other tools' version.

- **Database**

On the [resources/sql](src/main/resources/sql), configure your own database account information.

- **Mail System Configuation**

On the [resources](src/main/resources/), configure the mail account, port and other properties in `mailSetting.properties`, like below:

```
##change as your mind
mail.username=demo@vip.qq.com    // name
mail.password=demo@vip.qq.com    // pwd
mail.host=smtp.qq.com            // server
mail.port=465                    // port
mail.protocol=smtps              // protocol
mail.defaultEncoding=utf8        // code
```


---


## 3. Summary

  I have leart a lot from this project and I want to summarize the important and advanced items I have learnt.

- **Velocity Templates**



---

- **Spring Boot**

	-  Create independent Spring application
	-  Enbedded Tomcat
	-  Simple Maven configuation
	-  Provide production-ready features such as indicators, health checks and external configurations
	-  No code generation and no configuration required for XML

---

- **Login and Register**

	- Used the notion of `Token`, when users login, the backend will create a token automatically and store it in the Database. And this token will be the certification of the user login status. After the expiration of token, the user will be marked by 'log out' and will need to relogin later. And the token is transported by 'Cookie' between Server and Client.

---

- **Sensitive Word Filter**


 When we meet the sensitive words we do not want to see, we have two ideas:
 - delete the sensitive words
 - replace the sensitive words to other string.

And I used the `Trie Tree` to realize this function.


---

-  **Asynchronous**

  Today's Internet is full of users and large traffic. Asynchronous programming provides a non-blocking, event-driven programming model. This programming method can make full use of the computer's multi-core to perform parallel tasks and resources efficiency. I can imagine that the application scenario is very extensive. For a very simple example, if we register a new social account on the website, the strict website will have a verification email address. Address mail. This is an asynchronous event. You can't say that the process of mail verification is directly nested in the business logic. It should be sent to a queue, and then the queue handles this kind of event. On a website There are all kinds of things that need to be handled.

----


 - **Mail System**

 I used the mail server to send the template mails like login, register and ban mail automaticlly which can reduce the people's work.

 - Process:
 	- Define the mail configuation which including server information, protocol and account info.
 	
 	- Define different HTML mail templates to build and send the mail.


----

- **Redis**

	Redis is an open source (BSD licensed), in-memory data structure store, used as a database, cache and message broker. It supports data structures such as strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs, geospatial indexes with radius queries and streams. Redis has built-in replication, Lua scripting, LRU eviction, transactions and different levels of on-disk persistence, and provides high availability via Redis Sentinel and automatic partitioning with Redis Cluster.


  The difference between Redis and sql database is that for the sparse data it is a waste of space to create a new table in the sql database. Therefore, using a no-sql database is a great idea.



----


-  **Activity Timeline**

	On the sns website, everyone will have their own timeline or fresh, interesting things to publish. So, when users submit a lot of data, we need to arrange the storage place and storage ways to store big data and optimize the database to the best. 

	- Data Storage Idea:
  		+ Data with high frequence will be stored into the No-SQL Database like Redis to be red with high speed.
  		+ Users information, comments and so on will be stored into SQL database for better safety and long time storage.
   	+ And for active users we used the `push` mode and used `pull` mode for inactive users. This can make server more balanced.


----

- **Java Unit Test**

  这里介绍的是一个阿帕奇下的一个开源工具`apache2-utils`,因为我是在`Ubuntu`系统下,直接从终端安装就好了
  I used the `apache2-utils` tools to test the website.
  This tool can be installed by `sudo apt-get install apache2-utils`

For example:
  
```
ab -n 100 -c 100 http://qq.com/
This is ApacheBench, Version 2.3 <$Revision: 1706008 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking qq.com (be patient).....done


Server Software:        squid/3.5.20
Server Hostname:        qq.com
Server Port:            80

Document Path:          /
Document Length:        160 bytes

Concurrency Level:      100
Time taken for tests:   0.107 seconds
Complete requests:      100
Failed requests:        0
Non-2xx responses:      100
Total transferred:      45222 bytes
HTML transferred:       16000 bytes
Requests per second:    930.95 [#/sec] (mean)
Time per request:       107.417 [ms] (mean)
Time per request:       1.074 [ms] (mean, across all concurrent requests)
Transfer rate:          411.13 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:       14   23   6.7     21      32
Processing:    14   28  13.5     26      76
Waiting:       14   28  13.5     26      76
Total:         29   51  17.4     52     107

Percentage of the requests served within a certain time (ms)
  50%     52
  66%     61
  75%     62
  80%     63
  90%     73
  95%     87
  98%     97
  99%    107
 100%    107 (longest request)

``` 

























