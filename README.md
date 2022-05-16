## Flink Demo repos

基于flink 1.15.0的一些例子，用java 11


| 例子                                                 | 内容         | 使用技术 | 
|----------------------------------------------------| ----------- | ------- | 
| [FraudDetect](src/main/java/FraudDetect/README.md) | 一笔小额交易后紧跟一笔大额交易涉嫌欺诈 | DataStream API结合状态    | 
| [LoginDetect](src/main/java/LoginDetect/README.md) | 连续三次登陆失败报警 | CEP基本、循环模式及状态机实现     |
| [HourStat](src/main/java/HourStat/README.md)       | 统计每个账户每小时金额 | table api， kafka接收存mysql |


