# playground点击演示

[参考资料](https://nightlies.apache.org/flink/flink-docs-release-1.15/zh/docs/try-flink/flink-operations-playground/)

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