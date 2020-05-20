


docker run --name scan-mysql -p3306:3306 -e MYSQL_ROOT_PASSWORD=scan-root -d mysql

docker cp /usr/share/zoneinfo/Asia/Shanghai scan-mysql:/etc/localtime
 
 
