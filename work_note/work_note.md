
# mail包升级到1.47后，内部邮箱发送时认证失败
props.put("mail.smtp.auth", "true");后面加上(两个地方)props.setProperty("mail.smtp.ehlo", "false");


# tomcat偶报连接异常
查看mysqld的启动时间， mysqld safe

# nginx静态文件不通过代理

# uploadfile没有权限，与uploadfile在server.xml与配置文件里路径不一致造成404

# 除了eclipse自动的内存分析工具的leak， JProfiler的Biggest Objects
JProfiler -> Biggest Objects -> shwo  in Grpath可以看到java stack of http-nio-9092-exec-13 in...


# 数据库Url连接监控由service-datasourse.xml控制

# nginx超时问题502 Bad Gateway（proxy_read_timeout 90;改成proxy_read_timeout 180;）

# read-only异常（由数据库隔离级别引起）

# 线程有很多CoreRequest.mc请求，可通过nginx访问日志查看长的请求
处理隆基泰和正式(由sqlId:kq_rule_overtime_judge引起的/RedseaPlatform/getList/kq_rule_overtime_judge/CoreRequest.mc(16:14:02 - 17:59:27 超过60秒的有300563条)

# 最大可用内存，一般把sort内存设置的过大

# set session optimizer_switch='derived_merge=on', 和小表索引
猿辅导正式数据库 set session optimizer_switch='derived_merge=on'，并给小表加上索引。 一个25秒，提高到1.4秒

# 备份太慢
处理中银富登模拟环境硬盘速度太慢问题，9k/秒，一般机器几十M/s(dd if=/dev/zero of=kwxgd bs=64k count=4k oflag=dsync)

# 处理猿辅导工作流权限问题造成cpu高，线程里查看


# nginx目录权限，大的header请求和大的body返回
处理居然之家测试nginx配置目录没有权限造成报IERR_INCOMPLETE_CHUNKED_ENCODING 200，
python下报requests.exceptions.ChunkedEncodingError: 

# VPN
处理发布sql在vpn连接时，一个需要0.7秒，直接0.0?秒，针对慢的客户可以重新连接一次vpn再发布

# os.flush()行报错，由于权限问题造成 uploadfile权限

# 坏表问题
处理中标正式流程日志表坏掉问题（rename解决）

# 消息消费过多，造成数据库卡死，集团

# 数据库重启，drop表容易引起硬件硬件故障

# 集团excel样式对不齐，（onscroll时修复样式实现对齐）

# mysql提升批量操作性能，通过url的连接实现

# 集团连接池问题，修改源代码，细化到method方法，找到没有关闭的连接

# 集团nginx配置问题，访问不到druid

# RedseaPlatform大mp4可以断点续传支持ie11(上传文件file的属性修改日期属性跟chome不一样造成)

# spring session
查找新框架spring session的性能问题，一般用户首页的redis请求110次，超管是150次，原因，因为一次请求5个，从request的session 取，这样就是5x调用次数x请求数(最大一个140K)，发版系统是用ThreadLocal取用户：1x1x请求数。
晚上用抓包软件测试了一下，超管登录有200次redis请求，跟在spring写代码抓住的一样, 很多Ping的请求，估计是连接池那部分写错代码了

# 修改发版系统上传慢的问题，zip时没有使用-q(5M卡到3秒)

# 新框架在《Excel导入页面》要慢9秒，日志多20倍(100vs2000), 23次redis请求

# tomcat宕机(java线程忽然消失)
处理猿辅导测试tomcat宕机(java线程忽然消失)。查看linux系统日志/var/log/message，由于mysql占用12G内存造成linux
顺便把java进程(内存占用第二,昨天重启过一次,造成oom比重较高)kill掉。解决方法：把mysql的最大连接数2000改成1000

# 有递归的线程
处理美奥测试环境-内存溢出的线程，工作流模拟流程接口递归一千多次，造成内存溢出

# GTID模式
mysql改成GTID模式，不支持create temporary table,有3860条sql有create temporary table

# 培训报com.mysql.jdbc.MysqlIO.readFully(MysqlIO.java:2911)，
临时解决方案：加大缓存区，mysql连接后面加&tcpRcvBuf=1024000长期解决方案(需要分业务类型，长请求，短请求)：mysql连接配置socketTimeout

# 一个高频的请求打印日志过多
石药宕机问题：(现象：java新生代码还未满，老年代码已满，未打印内存溢出日志)一个高频的请求打印日志过多，一个请求2百多条日志(估计是在递归里调用的另一个有事务的方法，产生很多无用的日志)
control.MobileInterfaceControlWithCommon_OutWork:394
处理方式二，把druid的true改成false

# 处理培训socketRead0占高cpu 工作流8秒 一个方法(WfWorkformColJdbcDao:231)六千多请求，还有其它请求(200人用)，解决方法：使用缓存

# 培训环境由于root_id多个，使用了万能的map, 一百多万数据，造成内存溢出(多个接口都存在这个问题)









