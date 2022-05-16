## main

Transaction::getAccountId 引用类方法，lambda功能，效果类似 data -> data.getAccountId

DataStream<Transaction> transactions = env
.addSource(new TransactionSource())
.name("transactions");
加.name可以增加调试信息，使发生错误时可以快速定位问题

## TransactionSource

@Public 用于标注稳定公开的接口，也就是说带有Public注解的类会被相同大版本的flink编译，只有大版本不同才会破坏带有注解的接口 

继承了一个可迭代的SourceFunction（FromIteratorFunction），这样只需重写构造方法，传入一个迭代对象RateLimitedIterator

## Transaction

@SuppressWarnings("unused")  消除编译器告警  

## AlertSink

@PublicEvolving 类方法的作用是稳定的，为了公开用途的，但是接口和签名是变化的  

private static final long serialVersionUID = 1L;  兼容不同的java编译器，反序列化不报错  

## TransactionIterator

100毫秒产生一个指定的随机订单

## 最终程序

检测到小于1元时开启定时器、设置flag。当不大于500元则清定时器清状态，大于500报警  
DataStream Api + ValueState实现