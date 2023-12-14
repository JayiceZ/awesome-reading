intent里要记录超时时间、min commit ts
## 读写流程
### 读
```
if 没读到intent
  太好了
else
  if intent 还没超时
    去找txn record
    if txn 不存在
      写入一个虚拟record，里面写着这个事务的start ts作为push ts。
    else if txn 存在
      检查所有intent是否写入成功
      if 所有intent写入成功
        则认为事务commit了，帮忙resolve，然后删掉record
      else if 有一个intent上是rollback
        帮忙删其余的intent和txn
      else
        等超时时间到了，如果还没成功，在没成功的intent上写入rollback标记。然后帮忙删掉成功的intent和txn
  else 超时了
    去找txn record
    if txn 不存在
      写一个rollback txn
    else if txn存在
       检查所有intent
       if 所有intent写入成功
        则认为事务commit了，帮忙resolve，然后删掉record
      else if 有一个intent上是rollback
        帮忙清理
      else
        不存在的intent上写入rollback标记。然后帮忙删掉成功的intent和txn

```

### 写
```
if 没遇到intent
  太好了
else
  if intent 还没超时
    去找txn record
    if txn 不存在
      等超时
    else if txn 存在
      检查所有intent是否写入成功
      if 所有intent写入成功
        则认为事务commit了，帮忙resolve，然后删掉record。如果最终选择的commit ts小于写的start ts，那么写可以进行，否则conflict。
      else if 有一个intent上是rollback
        帮忙删其余的intent和txn
      else
        等超时时间到了，如果还没成功，在没成功的intent上写入rollback标记。然后帮忙删掉成功的intent和txn
  else 超时了
    去找txn record
    if txn 不存在
      写一个rollback txn
    else if txn存在
       检查所有intent
       if 所有intent写入成功
        则认为事务commit了，帮忙resolve，然后删掉record
      else if 有一个intent上是rollback
        帮忙删其余的intent和txn
      else
        不存在的intent上写入rollback标记。然后帮忙删掉成功的intent和txn
```



### max read ts怎么维护
tablet级别
min commit ts = Max（commit ts from tso，max read ts+1）
防止coordinator挂了无法进行第二阶段，min commit ts要写入intent里。

这里会有时序问题
1. txnA 获取max read ts=10
2. txnB startTs=12，读了旧数据
3. txnA 写入intent
4. txnA 最终以commit ts=11来commit
5. txnB 再读，读到了新数据
破坏了SI

本质就是获取max read ts和写入intent不是原子操作，所以需要有锁，intent写入后才释放。
      
