
# pip install mysql-connector-python
*  cryptography is required for sha256_password or caching_sha2_password(pymysql)

# mysql
```
docker pull mysql
docker run --network scan-network --network-alias scan-mysql -v /usr/local/scan/mysql/conf:/etc/mysql/conf.d -v /usr/local/scan/mysql/data:/var/lib/mysql --name scan-mysql -p3306:3306 -e MYSQL_ROOT_PASSWORD=scan-root -d mysql
docker exec -it scan-mysql bash
```

# 日期问题
```
docker cp /usr/share/zoneinfo/Asia/Shanghai scan-mysql:/etc/localtime
```

# 配置
```
[mysqld]
log_error=/var/lib/mysql/log/mysql_error.log
```







