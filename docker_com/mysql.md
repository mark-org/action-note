
# mysql
```
docker run --name scan-mysql -e MYSQL_ROOT_PASSWORD=scan-root -d mysql


docker run --name scan-mysql -p3306:3306 -e MYSQL_ROOT_PASSWORD=scan-root -d mysql

docker exec -it scan-mysql bash

docker logs scan-mysql


```

