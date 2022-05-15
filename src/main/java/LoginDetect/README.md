## 依赖

```xml
<dependency>
    <groupId>org.apache.flink</groupId>
    <artifactId>flink-cep</artifactId>
    <version>${flink.version}</version>
    <scope>provided</scope>
</dependency>
```

## 程序说明

LoginDetect 基本CEP实现  
LoginDetectPro CEP循环模式实现，可以乱序    
LoginDetectNFA 用CEP状态机实现，按处理时间实现的，不能乱序    

这种场景最佳是LoginDetectPro， CEP状态机只是一个例子