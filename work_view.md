

# JAVA 打印线程
```
jstack -F PID > /tmp/java_thread0.txt

# docker环境 加上docker run --cap-add=SYS_PTRACE 
```

# LINUX 打印线程
```
ps -mp PID -o THREAD,tid,time | sort -k2r > /tmp/linux_thread0.txt
```

# 下载文件
```
rsync -P --rsh=ssh -e 'ssh -p 22' maintain@39.96.55.160:/tmp/java_thread0.txt /home/deploy/bak/
scp -P 2294 redsea@192.168.101.222:/tmp/java_thread0.txt /home/deploy/bak
```

# linux
```
# 启动时间
ps -eo lstart,etime,command | grep mysqld
```

# mysql
```
-- mysql5.7 启用内存监控
update performance_schema.setup_instruments set enabled = 'yes' where name like 'memory%';

-- 内存分配
select * from performance_schema.memory_...
-- thread_handling = one-thread-per-connection
show variables like '%thread_cache_size%' -- 默认为9
-- 通过设置tmp_table_size选项来增加一张临时表的大小，例如做高级GROUP BY操作生成的临时表 默认为16M
show variables like '%max_heap_table_size%'

-- 查看连接
show status like '%thread%'
show status like '%connect%'

show full PROCESSLIST
select * from `performance_schema`.threads

-- 事务
select * from information_schema.INNODB_TRX
-- 锁
select * from information_schema.INNODB_LOCKS


```

# java打印内存
```
# 打印内存信息
jmap -dump:format=b,file=e.hprof PID

# 查看java进程活跃对象个数[C is a char[] [S is a short[] [I is a int[] [B is a byte[] [[I is a int[][]
jmap -histo:live PID | head -20

# 1000ms统计一次gc情况统计100次；
jstat -gcutil pid 1000 100
# 比例 S0:年轻代中第一个survivor S1: E ：年轻代中Eden O ：old代 P ：perm代
```








