# 腾讯云镜像
创建或修改 /etc/docker/daemon.json
```
{
   "registry-mirrors": [
       "https://mirror.ccs.tencentyun.com"
  ]
}
```
systemctl daemon-reload
systemctl restart docker

# network
docker network create scan-network


# 安装chrome
* docker pull selenium/standalone-chrome
* docker run -d --network scan-network --network-alias scan-chrome -p 4444:4444 --shm-size=2g --name chrome selenium/standalone-chrome


# 安装python
* docker pull python
* docker run -it --name scan-python python bash

* mkdir app
* pip install selenium
* pip install Flask

* docker commit -m "selenium Flask" scan-python scan-python
* docker run -d --network scan-network --network-alias scan-python -p 5000:5000 -v /usr/local/app:/app --name flask-test scan-python python /app/app.py
* docker logs flask-test
* docker run -it --rm --network scan-network --network-alias scan-python -v /usr/local/app:/app --name chrome-test scan-python python /app/chrome.py


flask的host="0.0.0.0"
curl: (56) Recv failure: Connection reset by peer


selenum测试脚本
```
from selenium import webdriver
from selenium.webdriver.common.desired_capabilities import DesiredCapabilities

driver = webdriver.Remote(
    command_executor="http://scan-chrome:4444/wd/hub",
    desired_capabilities=DesiredCapabilities.CHROME
)

driver.get("http://www.baidu.com")
print(driver.title)

picture_url = driver.get_screenshot_as_file("/app/test.png")
print("%s：success picture！！！" % picture_url)

driver.close()
```
Flask测试脚本
```
from flask import Flask

app = Flask(__name__)


@app.route('/')
def hello_world():
    return 'Hello World!'


if __name__ == '__main__':
    app.run(host="0.0.0.0", port=5000)
```

# 删除所有容器
docker stop $(docker ps -aq)
docker rm $(docker ps -aq)








