# 第八周分布式缓存、分布式事务

### 1、使用 redis benchmark 工具, 测试 10 20 50 100 200 1k 5k 字节 value 大小，redis get set 性能。
```
byte:10
====== SET ======
  100000 requests completed in 0.80 seconds
  50 parallel clients
  10 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no

99.59% <= 0.4 milliseconds
100.00% <= 0.8 milliseconds
124688.28 requests per second

====== GET ======
  100000 requests completed in 0.79 seconds
  50 parallel clients
  10 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no

99.87% <= 0.4 milliseconds
100.00% <= 1.7 milliseconds
126742.72 requests per second


byte:20
====== SET ======
  100000 requests completed in 0.78 seconds
  50 parallel clients
  20 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no

99.04% <= 0.3 milliseconds
100.00% <= 0.4 milliseconds
127877.23 requests per second

====== GET ======
  100000 requests completed in 0.78 seconds
  50 parallel clients
  20 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no

99.09% <= 0.3 milliseconds
99.93% <= 0.4 milliseconds
127877.23 requests per second


byte:50
====== SET ======
  100000 requests completed in 0.79 seconds
  50 parallel clients
  50 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no

98.22% <= 0.3 milliseconds
99.69% <= 0.4 milliseconds
100.00% <= 0.5 milliseconds
126103.41 requests per second

====== GET ======
  100000 requests completed in 0.79 seconds
  50 parallel clients
  50 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no

98.87% <= 0.3 milliseconds
99.87% <= 0.4 milliseconds
100.00% <= 0.6 milliseconds
127226.46 requests per second


byte:100
====== SET ======
  100000 requests completed in 0.82 seconds
  50 parallel clients
  100 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no

95.16% <= 0.3 milliseconds
99.42% <= 0.4 milliseconds
100.00% <= 0.7 milliseconds
121359.23 requests per second

====== GET ======
  100000 requests completed in 0.79 seconds
  50 parallel clients
  100 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no


99.91% <= 0.4 milliseconds
100.00% <= 0.5 milliseconds
126103.41 requests per second


byte:200
====== SET ======
  100000 requests completed in 0.80 seconds
  50 parallel clients
  200 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no

99.83% <= 0.4 milliseconds
100.00% <= 0.5 milliseconds
125313.29 requests per second

====== GET ======
  100000 requests completed in 0.80 seconds
  50 parallel clients
  200 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no

99.89% <= 0.4 milliseconds
125000.00 requests per second


byte:1000
====== SET ======
  100000 requests completed in 0.81 seconds
  50 parallel clients
  1000 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no

99.64% <= 0.4 milliseconds
100.00% <= 1.9 milliseconds
100.00% <= 2 milliseconds
124223.60 requests per second

====== GET ======
  100000 requests completed in 0.80 seconds
  50 parallel clients
  1000 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no

100.00% <= 0 milliseconds
124688.28 requests per second


byte:5000
====== SET ======
  100000 requests completed in 0.84 seconds
  50 parallel clients
  5000 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no
  
99.71% <= 0.4 milliseconds
100.00% <= 0.5 milliseconds
119474.31 requests per second

====== GET ======
  100000 requests completed in 0.84 seconds
  50 parallel clients
  5000 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no
  
99.54% <= 0.4 milliseconds
100.00% <= 1.4 milliseconds
118623.96 requests per second


byte:10000
====== SET ======
  100000 requests completed in 0.87 seconds
  50 parallel clients
  10000 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no

99.73% <= 0.4 milliseconds
115473.45 requests per second

====== GET ======
  100000 requests completed in 0.89 seconds
  50 parallel clients
  10000 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no

99.66% <= 0.4 milliseconds
100.00% <= 2 milliseconds
112866.82 requests per second


byte:100000
====== SET ======
  100000 requests completed in 2.81 seconds
  50 parallel clients
  100000 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no

0.00% <= 0.5 milliseconds
0.00% <= 0.6 milliseconds
0.29% <= 0.7 milliseconds
7.06% <= 0.8 milliseconds
9.36% <= 0.9 milliseconds
10.51% <= 1.0 milliseconds
12.13% <= 1.1 milliseconds
24.07% <= 1.2 milliseconds
59.44% <= 1.3 milliseconds
82.79% <= 1.4 milliseconds
88.99% <= 1.5 milliseconds
93.09% <= 1.6 milliseconds
96.15% <= 1.7 milliseconds
97.97% <= 1.8 milliseconds
98.86% <= 1.9 milliseconds
99.33% <= 2 milliseconds
99.94% <= 3 milliseconds
100.00% <= 3 milliseconds
35637.92 requests per second

====== GET ======
  100000 requests completed in 6.32 seconds
  50 parallel clients
  100000 bytes payload
  keep alive: 1
  host configuration "save": 900 1 300 10 60 10000
  host configuration "appendonly": no
  multi-thread: no

2.77% <= 1 milliseconds
4.40% <= 2 milliseconds
61.70% <= 3 milliseconds
98.55% <= 4 milliseconds
99.99% <= 5 milliseconds
100.00% <= 5 milliseconds
15815.28 requests per second
```
### 分析 
依次使用下面命令针对 10, 20, 50, 100, 200, 1000, 5000, 10000, 100000 字节的数据进行测试  
```
redis-benchmark -n 100000 -d {byte} -t set,get
```
从 10 ~ 10k字节 响应的95值基本都在0.4毫秒内，  
我们知道39字节内用的是embstr编码而之后使用的是raw编码，但在该benchmark场景下体会不到太多区别， 
只有当数据到100k时，响应时间则随着数据量而提高，这里则应该是数据量大导致的redis 内部的数据IO操作耗时升高产生的  


### 2、写入一定量的 kv 数据, 根据数据大小 1w-50w 自己评估, 结合写入前后的 info memory 信息 , 分析上述不同 value 大小下，平均每个 key 的占用内存空间。
依次用如下命令插入随机KEY，每次测试前flushdb一下，验证 10,20,50,100 来分析内存消耗

```
redis-benchmark -n 100000 -d {byte} -r 100000 -t set
```

计算方式 (插入后内存-插入前内存)/插入次数-key的容量  

10字节  
(7734944 - 1136928)/100000 -  16 = 49 字节

20字节  
(8761680 - 1136928)/100000 - 16 = 60 字节

50字节  
(10762080 - 1136928)/100000 - 16 = 80 字节

100字节  
(13782048-1136928)/100000 - 16 = 110 字节

1000字节  
(70608800-1136928)/100000 - 16 = 678 字节
### 分析   

根据20字节和10字节基本可以推断每个k-v的对象需要额外的40字节左右的容量来维护，  

根据50字节和100字节和1000字节的情况看当单个value容量变大时，redis有进行容量方面的优化，越大的容量看起来越接近真实的字节数，甚至有下降的趋势  




