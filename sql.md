for update悲观锁能否锁住一条不存在的记录
锁是针对索引加锁，如果查询条件无索引，全表扫描，全表锁

前开后闭
Innodb对于行的查询都采用Next-Key Lock,但是当查询索引时含有唯一索引时，Innodb会对Next-Key lock优化，降级为Record lock,仅锁住索引本身而非范围
数据库空表无记录 Next-Key lock锁定范围包含记录本身，因为此时数据无记录，锁定范围（-max，+max），即为全表锁
数据库表有一条记录， 锁定范围（-max，'xm') ['xm',+max) 全表锁


间隙锁死锁问题 间隙锁之间不互斥

mysql存储过程不会自动开启事物

#日志
show variables like "%log%"
redolog ib_logfile0 ib_logfile1
undolog undo001 undo002 ... 事物回滚，多版本并发控制（mvcc）