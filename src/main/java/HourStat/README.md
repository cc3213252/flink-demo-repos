## 依赖

flink-table-api-java
flink-table-api-java-bridge
flink-table-planner_${scala.binary.version}
flink-connector-kafka  
flink-csv

## 环境搭建（单机环境）

### mysql

```sql
CREATE TABLE spend_report(
    account_id BIGINT,
    log_ts     TIMESTAMP(3),
    amount     BIGINT,
    PRIMARY KEY (account_id, log_ts)
);
```

### kafka

启动kafka：  
bin/zookeeper-server-start.sh config/zookeeper.properties  
bin/kafka-server-start.sh config/server.properties  

创建topic:  
bin/kafka-topics.sh --create --topic transactions --bootstrap-server localhost:9092  

查看topic:
bin/kafka-topics.sh --bootstrap-server localhost:9092 --list

删除topic:
bin/kafka-topics.sh --bootstrap-server localhost:9092 --delete --topic transactions

发送数据：  
bin/kafka-console-producer.sh --topic transactions --bootstrap-server localhost:9092  
1,100,2022-05-16 09:00:00
2,200,2022-05-16 09:10:00
1,100,2022-05-16 09:05:00

bin/kafka-console-consumer.sh --topic transactions --from-beginning --bootstrap-server localhost:9092


