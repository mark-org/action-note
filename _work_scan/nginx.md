
#  begin
docker run --network scan-network --network-alias scan-nginx --name scan-nginx -p 80:80 -v /usr/local/scan/nginx/log:/var/log/nginx/ -v /usr/local/scan/nginx/conf/nginx.conf:/etc/nginx/nginx.conf -v /usr/local/scan/nginx/html:/usr/share/nginx/html  -d nginx

docker cp scan-nginx:/etc/nginx/nginx.conf /usr/local/scan/nginx/conf

docker logs scan-nginx

docker exec -it scan-nginx bash
