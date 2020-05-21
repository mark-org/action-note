

# docker pull selenium/standalone-chrome
```
docker run -d --network test-network --network-alias chrome2 -p 4444:4444 --shm-size=2g selenium/standalone-chrome
```
--rm Automaticcally remove the container when it exits



```

from selenium import webdriver
from selenium.webdriver.common.desired_capabilities import DesiredCapabilities

driver = webdriver.Remote(
    command_executor="http://chrome2:4444/wd/hub",
    desired_capabilities=DesiredCapabilities.CHROME
)

driver.get("http://www.baidu.com")
print(driver.title)

picture_url = driver.get_screenshot_as_file("test.png")
print("%s：success picture！！！" % picture_url)

driver.close()


```


* docker-compose
```
version: "2.0"
services:
  spider:
    image: selenium_python:v1
    volumes:
      - ./spider.py:/code/spider.py  # 这里把刚刚的代码映射到这个目录
    command: python /code/spider.py  # 定义启动容器执行的命令
    depends_on:
      - chrome
  chrome:
    image: selenium/standalone-chrome:latest
    ports:
      - "4444:4444"
    shm_size: 2g
```
















