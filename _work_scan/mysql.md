
# pip install mysql-connector-python

# mysql
docker pull mysql

docker run --network scan-network -v c/Docker/mysql/conf:/etc/mysql/conf.d -v c/Docker/mysql/data:/var/lib/mysql --name scan-mysql -p3306:3306 -e MYSQL_ROOT_PASSWORD=scan-root -d mysql

docker run --network scan-network --name scan-mysql -p3306:3306 -e MYSQL_ROOT_PASSWORD=scan-root -d mysql


docker exec -it scan-mysql bash

# 日期问题
docker cp /usr/share/zoneinfo/Asia/Shanghai scan-mysql:/etc/localtime

# cryptography is required for sha256_password or caching_sha2_password
