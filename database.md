[TOC]



# 1.Transaction
## 1.1 论文
- [A Critique of ANSI SQL Isolation Levels](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr-95-51.pdf)
  - [TiDB的解读](https://cn.pingcap.com/blog/take-you-through-the-isolation-level-of-tidb-1/)
- write snapshot isolation
  - [Eric Fu大佬的概括](https://zhuanlan.zhihu.com/p/103456520)
- Making Snapshot Isolation Serializable
  - [Eric Fu大佬的概括](https://zhuanlan.zhihu.com/p/103553619)
- [PostgreSQL的SSI实现](https://arxiv.org/pdf/1208.4179.pdf)
- [MaaT: Effective and scalable coordination of distributed
transactions in the cloud](http://www.nawab.me/Uploads/MaaT_VLDB2014.pdf)
- [Calvin: Fast Distributed Transactions for Partitioned Database Systems,](https://cs.yale.edu/homes/thomson/publications/calvin-sigmod12.pdf)
- [An Evaluation of the Advantages and Disadvantages of Deterministic Database Systems](http://www.vldb.org/pvldb/vol7/p821-ren.pdf)
- [Fast Serializable Multi-Version Concurrency Control
for Main-Memory Database Systems](https://db.in.tum.de/~muehlbau/papers/mvcc.pdf)
- 
## 1.2 实现优化
- [CockroachDB的Follower Read](https://www.scienjus.com/an-epic-read-on-follower-reads/)
- [CockroachDB和TiDB如何避免幻读](https://www.zenlife.tk/two-tso-or-one-tso.md)
- [CockroachDB事务剖析](https://zhuanlan.zhihu.com/p/571445272)
- Parallel Commit
  - [TiDB parallel commit详解](https://nan01ab.github.io/2021/06/Distributed-Txn(4).html)
  - [TiDB parallel commit设计文档](https://github.com/tikv/sig-transaction/blob/master/design/async-commit/parallel-commit-known-issues-and-solutions.md)
  - [TiDB parallel commit设计讨论](https://docs.google.com/document/d/1-yn5zyn8NpqXRii9sA5wDcNHL3L0BYVaEFyD-YChX1g/edit#heading=h.4qyuf3giaj3x)
- []


# 2.Concurrency Control
- [并发控制协议: 2PL / TS / OCC](https://zhuanlan.zhihu.com/p/294657612)
- [MVCC & SI: Protocol](https://zhuanlan.zhihu.com/p/298576970)
- [MVOCC MV2PL MVTO](https://marsishandsome.github.io/2019/06/Multi_Version_Concurrency_Control)
- [HyPer MVCC论文:Fast Serializable Multi-Version Concurrency Control for Main-Memory Database Systems,](https://db.in.tum.de/~muehlbau/papers/mvcc.pdf)
  - [概述1](https://zhuanlan.zhihu.com/p/374241128)
  - [概述2](https://zhuanlan.zhihu.com/p/417271938)
- [Yingjun Wu的MVCC论文](https://www.vldb.org/pvldb/vol10/p781-Wu.pdf)
  - [MrCroxx大佬的翻译](https://blog.mrcroxx.com/posts/paper-reading/wu-vldb2017/)
- [MySQL undolog、MVCC](https://www.alibabacloud.com/blog/598966)


# 3. Time
- [5种分布式时钟](http://yang.observer/2020/12/16/hlc/)
- [阿莱克西斯大佬对TrueTime和commit-wait的解释](https://zhuanlan.zhihu.com/p/44254954)
- [TiDB的分布式TSO优化 解决跨AZ PD性能渣的问题](https://cn.pingcap.com/blog/preliminary-study-on-cross-center-deployment-capability-of-tidb5.0/)



# 4. Storage Engine
-  [RocksDB有哪些好的文章和资料](https://www.zhihu.com/question/270732348/answer/356254676?utm_source=wechat_session&utm_medium=social&utm_oi=1012352443086028800&utm_content=group3_Answer&utm_campaign=shareopn).
-  [TerarkDB doc](https://bytedance.feishu.cn/docs/doccnZmYFqHBm06BbvYgjsHHcKc).
-  [分布式存储的七个方面问题](https://zhuanlan.zhihu.com/p/369581725?utm_source=wechat_session&utm_medium=social&utm_oi=1012352443086028800).
-  [八股文之DPDK](https://zhuanlan.zhihu.com/p/387069915?utm_source=wechat_session&utm_medium=social&utm_oi=1012352443086028800).

# 5. Distributed Application


# 6. OLAP
-  [ClickHouse 源码阅读 —— SQL的前世今生](https://zhuanlan.zhihu.com/p/181283645?utm_source=wechat_session&utm_medium=social&utm_oi=1012352443086028800).
