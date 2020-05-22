
# 腾讯云镜像仓库
Docker镜像用于部署容器服务，每个镜像有特定的唯一标识（镜像的Registry地址+镜像名称+镜像Tag）

* 上传镜像
```
$ sudo docker login --username=[username] ccr.ccs.tencentyun.com
$ sudo docker tag [ImageId] ccr.ccs.tencentyun.com/[namespace]/[ImageName]:[镜像版本号]
$ sudo docker push ccr.ccs.tencentyun.com/[namespace]/[ImageName]:[镜像版本号]
```

username：腾讯云账号 ID (100000775730)
namespace：开通镜像仓库时填写的命名空间。

* 下载镜像
```
$ sudo docker login --username=[username] ccr.ccs.tencentyun.com
$ sudo docker pull ccr.ccs.tencentyun.com/[namespace]/[ImageName]:[镜像版本号]
```

* 删除镜像
选择左侧导航栏中的【镜像仓库】>【我的镜像】，进入“我的镜像”页面。
在“我的镜像”页面，选择需删除镜像所在行右侧【删除】。
在弹出的“删除镜像仓库”窗口中，单击【确定】即可删除该镜像所有版本。如下图所示：


镜像地址:ccr.ccs.tencentyun.com/deng_space/my_image

docker login --username=100000775730 ccr.ccs.tencentyun.com
docker tag f70734b6a266 ccr.ccs.tencentyun.com/deng_space/my_image
docker push ccr.ccs.tencentyun.com/deng_space/my_image

docker pull ccr.ccs.tencentyun.com/deng_space/my_image3



