
# CPU高
```
# tomcat 线程
jstack -F PID > /tmp/java_thread0.txt

# linux 线程
ps -mp PID -o THREAD,tid,time | sort -k2r > /tmp/linux_thread0.txt
```

# rsync -P --rsh=ssh -e 'ssh -p 22' maintain@39.96.55.160:/home/data/nginx/logs/oa.access.zip /home/deploy/bak/

# scp -P 2294 redsea@192.168.101.222:/tmp/1592thread.txt /home/deploy/bak

# 开启时间 ps -eo lstart,etime,command

# ssh -p 2262 redsea@192.168.101.207

# zip -9 z.zip t.txt  （-1 compress faster，-9 compress better）

```
# 在文件/usr/local/nginx/conf/vhosts/oa.conf的location ~ ^/favicon.ico$ {上面加上以下代码
location ~ ^/RedseaPlatform/.*\.(js|css|png)$ {
	root /usr/local/webapps/;
}
```
# 硬盘IO性能
*写入dd if=/dev/zero of=kwxgd bs=64k count=4k oflag=dsync  
*读dd if=kwxgd of=/dev/null bs=64k count=4k oflag=dsync
dd if=kwxgd bs=64k | dd of=/dev/null


