
# request_time和upstream_response_time差别
* request_time: request processing time in seconds with a milliseconds resolution;
time elapsed between the first bytes were read from the client and the log write after the last bytes were sent to the client.
* upstream_response_time: keeps times of responses obtained from upstream servers; times are kept in seconds with a milliseconds resolution..
Several response times are separeated by commas and colons like addresses in the $upstream_addr_variable
（$upstream_addr， 后台upstream的地址，即真正提供服务的主机地址）

* $request_time >= $upstream_response_time
特别是使用POST方式传递参数时，因为Niginx会把request body缓存住，接受完毕后才会把数据一起发给后端。
（如果用户网络较差，或者传递数据较大的，$request_time会比$upstream_response_time大很多）

* 查看接口性能，查看$upstream_response_time


# HEAD请求(HEAD方法用于仅获取响应头，而不获取响应)
大部分网站宕机监控都是发送HEAD请求来查看服务器是否宕机
这种请求一般IP地址有若干个，并且每个地址间隔一定时间会发送一次HEAD请求，以确定服务器正常工作