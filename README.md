# spark-code
spark的源码分析

spark是UC Berkeley AMP lab开源的通用并行计算框架，提供了一种粗粒度的数据并行计算范式。

它的基本编程模型是这样的：
  a）：存储中的数据（包括磁盘、hadoop等）被吸入RDD空间，转为RDD；
  b）：这些RDD经过变换算子的转换生成新的RDD，在这个过程中，数据的计算并没有真实发生，而只是不断地记录到元数据中，形成了DAG；
  c）：上述变换直到遇上行动算子，此时执行evaluate，将此前积累的算子一次性执行；
  d）：行动算子产生数据，从RDD空间退出；
  
Spark与hadoop的MR模型相比，具有如下的一些特点：
  1、中间数据不落盘，迭代运算的效率更高；
  2、提供了多种的数据集操作类型，比如map、filter、flatMap、union、join等transformation，以及count、collect等action
  3、不适用于异步细粒度更新；

