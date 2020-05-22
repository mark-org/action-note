
# network
docker network create scan-network


# 安装chrome
* docker pull selenium/standalone-chrome
* docker run -d --network scan-network --network-alias scan-chrome -p 4444:4444 --shm-size=2g selenium/standalone-chrome


# 安装python
* docker pull pythone
* docker run -it python scan-python bash

* mkdir app
* pip install selenium
* pip install Flask

* docker commit -m "selenim Flask" scan-python scan-python
* docker run -d --network scan-network --network-alias scan-python -p 5000:5000 -v /usr/local/app:/app python /app/


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

picture_url = driver.get_screenshot_as_file("test.png")
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
    app.run()
```

