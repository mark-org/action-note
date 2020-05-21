
# rsync
$ rsync main.c machineB:/home/userB

# rsync有三种工作方式
(1).本地文件系统上实现同步。命令行语法格式为上述"Local"段的格式 Local:  rsync [OPTION...] SRC... [DEST]
(2).本地主机使用远程shell和远程主机通信。命令行语法格式为上述"Access via remote shell"段的格式。
Pull: rsync [OPTION...] [USER@]HOST:SRC... [DEST]
Push: rsync [OPTION...] SRC... [USER@]HOST:DEST
(3).本地主机通过网络套接字连接远程主机上的rsync daemon。命令行语法格式为上述"Access via rsync daemon"段的格式。
Pull: rsync [OPTION...] [USER@]HOST::SRC... [DEST]
      rsync [OPTION...] rsync://[USER@]HOST[:PORT]/SRC... [DEST]
Push: rsync [OPTION...] SRC... [USER@]HOST::DEST
      rsync [OPTION...] SRC... rsync://[USER@]HOST[:PORT]/DEST
	  
	  
但是，还有第四种工作方式：通过远程shell也能临时启动一个rsync daemon，这不同于方式(3)，它不要求远程主机上事先启动rsync服务，
而是临时派生出rsync daemon，它是单用途的一次性daemon，仅用于临时读取daemon的配置文件，当此次rsync同步完成，
远程shell启动的rsync daemon进程也会自动消逝。
此通信方式的命令行语法格式同"Access via rsync daemon"，但要求options部分必须明确指定"--rsh"选项或其短选项"-e"。


-t 判断时间戳、大小是否同步(不判断内容)，速度快
-I 确保数据的一致性，代价便是速度上会变慢
-z 压缩再传输
-r recursive（递归的、循环的）


