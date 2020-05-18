
# docker image
* image里面是一层层文件系统，叫做Union FS(联合文件系统)
* 联合文件系统，可以将几层目录挂载到一起，形成一个虚拟文件系统
* 虚拟文件系统的目录结构就像普通linux的目录结构一样
* docker通过这些文件再加上宿主机的内核提供了一个linux的虚拟环境 

# layer 每一层文件系统我们叫做一层layer
* 对每一层文件系统设置三种权限，只读(readonly)，读写(readwrite)和写出(whiteout-able)
* docker镜像中每一层文件系统都是只读的

# linux文件系统
由bootfs和rootfs组成，
* boot file system: bootloader和kernel. (bootloader 主要用于引导加载 kernel，
	当 kernel 被加载到内存中后 bootfs 会被 umount 掉)
* root file system: /dev /proc/ /bin /etc等标准目录和文件。

# 目前支持五种镜像层次的存储driver：aufs、device mapper、btrfs、vfs、overlay。


# win Settings -> Resources -> Disk image location
C:\ProgramData\DockerDesktop\vm-data
DockerDesktop.vhdx



# Docker镜像保存为文件及从文件导入镜像的方法
* docker save -o 要保存的文件名  要保存的镜像
* docker load < 文件名 (docker load --input 文件)




