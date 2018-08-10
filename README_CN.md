# 基于 spark1.6 的版本源码
 
## Spark名词:
1. Application
2. Job
3. Stage
4. Task
5. PipeLine
6. Shuffle

## 抽离开发逻辑和计算实施
1. 开发逻辑:RDD编程模型
2. 计算实施:Driver&Executor(SparkEnv)

## RDD是什么
1. RDD(弹性分布式数据集),虽然叫做数据集,但是自身不存储数据,不是数据结构
2. RDD保存数据位置信息,保存自存储位置演变过来时的计算逻辑
3. RDD算子的概念:创建算子,转换算子,控制算子,执行算子
4. RDD转换的过程体现两类依赖关系,窄依赖,shuffle依赖
5. 窄依赖比较简单,表示,数据计算的过程可以在一台节点完成
6. shuffle依赖比较复杂,本身表示数据需要移动,出主机,重分区的概念
7. shuffle过程实现的细节,包含write端和read端
8. 根据加工数据的逻辑(不同转换算子内置),shuffle分为3类write,框架优化的体现点


## Spark计算框架(Driver&Executor)
1. 资源层:Standalone(Master&Worker),YARN(ResourceManager&NodeManager)
2. SubmitSparkApplication
3. 申请启动Driver
4. 粗粒度资源申请Executor
5. Driver计算调度(DAGScheduler&TaskScheduler)
6. Driver&Executor维护的SparkEnv(MemoryManager,MapOutputTracker,CacheManager,BlockManager,ShuffleManager,)

## SparkSql


## SparkStreaming