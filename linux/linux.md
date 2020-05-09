# 负载
$w $uptime
* 其中load average分别对应过去的1分钟、5分钟、15分钟的负载均衡值
* linux 负载高，主要是CPU的使用、内存的使用、IO消耗三部分。
load:是计算机干活多少的度量(the system Load is a measure of the amount of work
that a compute system is doing),就是进程队列的长度

* 平均负载是指单位时间内，系统处于可运行状态和不可中断状态的平均进程数。
>> * 可运行状态：指正在使用cpu或者正式在等待cpu的进程, ps aux 的 STAT +R(running, runnable)
>> * 不可中断状态: 指进程正处理于内核关键流程中的进程，并且这些流程是不可被打断的，比如最长久
的是等待硬件设备的I/O响应，STAT D(Uniteruptible, Disk Sleep) 

* 最理想的就是每个cpu上刚好运行着一个进程
# 平均负载多少时合理
* cat /proc/cpuinfo |grep "model name"|wc -l (逻辑CPU)
* 当平均负载比CPU个数还大的时候，系统已经出现了过载


# rsync同步文件如何指定服务器端口
```
#rsync -avuz -e 'ssh -p 2222' user@remote-server:/path/to/remote/folder 
/path/to/local/folder

rsync -P --rsh=ssh -e 'ssh -p 22' maintain@39.96.55.160:/home/data/nginx/logs/oa.access.zip /home/deploy/bak/

```
-a --archive 归档(压缩模式)，表示以递归方式传输文件，并保持所有文件属性等同于-rltogD(无 -H,-A, -X）
-v --verboase详细模式输出
-z --compress 在传输过程中进行压缩
-u --update仅仅更新，也就是跳过所有已经存在于DST,并且文件时间晚于要备份的文件(不覆盖更新的文件)




