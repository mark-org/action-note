


docker run --name scan-mysql -p3306:3306 -e MYSQL_ROOT_PASSWORD=scan-root -d mysql

docker cp /usr/share/zoneinfo/Asia/Shanghai scan-mysql:/etc/localtime

select * from information_schema.innodb_trx;

show engine innodb status\G;
 
```sql
set autocommit = 0;
start transaction;
update test set val = '2v' where id = 1;
select sleep(10);
select 'end';
commit;
```

