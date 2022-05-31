## 参考资料

https://nightlies.apache.org/flink/flink-docs-release-1.15/zh/docs/try-flink/table_api/

## 例子说明

SpendReport 最简单的Table api实现的，从kafka到mysql，按小时统计每个账户的累计金额  
SpendReportUdf 增加了自定义UDF，时间按小时取整  
SpendReportWindow 增加了滚动窗口  

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
3,100,2022-05-16 09:05:00

bin/kafka-console-consumer.sh --topic transactions --from-beginning --bootstrap-server localhost:9092


## 问题

运行测试用例报：Failed to get job status so we assume that the job has terminated  

SpendReportWindow测试没效果

## 官网例子

apache/data-generator 这个镜像用例生成数据  

docker中jobmanager无法启动