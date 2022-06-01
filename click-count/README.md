# playground点击演示

[参考资料](https://nightlies.apache.org/flink/flink-docs-release-1.15/zh/docs/try-flink/flink-operations-playground/)

## 例子说明

统计页面点击次数，15秒统计一次，显示统计的起始时间、结束时间  
点击事件程序产生，发送到kafka，开滚动窗口聚合统计，存到kafka  
提供了一键部署，检查点，恢复点，扩容实验，负压效果

fromSource用法，好处是规则的builder，简单的是用addSource  
sinkTo用法，规则的builder，简单的是用addSink  
产生数据： 15毫秒产生6条数据， 时间相同，页码依次循环，聚合时15秒统计一次，点击数1000

## 操作步骤

mkdir -p /tmp/flink-checkpoints-directory
mkdir -p /tmp/flink-savepoints-directory

cd docker/ClickCount/  
docker-compose build  
docker-compose up -d
docker-compose down -v  
docker-compose up -d taskmanager  

查看flink：  
localhost:8081  

查看日志：  
docker-compose logs -f jobmanager  
docker-compose logs -f taskmanager  

flink命令行：  
docker-compose run --no-deps client flink --help  
docker-compose run --no-deps client flink list  

查看kafka：  
docker-compose exec kafka kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic input   
docker-compose exec kafka kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic output

## TODO

时区问题  
kafka状态不正常，日志没报错，无法创建topic  