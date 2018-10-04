# vps上挂载OneDrive
# vps上挂载OneDrive做云硬盘

------

**说明：** 国外有很多vps小鸡价格便宜，很多人买了搭建博客或者搞代理服务器，一般这种vps的磁盘空间都不大，手头有个1t的OneDrive账号就想拿来挂载到小鸡上，离线个视频啥的


## 安装rclone
[RCLONE](https://rclone.org/) 是一款能够方便的管理 GoogleDrive 与 OneDrive 等网盘以及FTP多种文件存储的管理软件，支持挂载盘符与命令MOVE、COPY、SYNC、MKDIR等操作。 

**获取参数**
首先需要在本地电脑也下载rclone用于获取 OneDrive  登录 TOKEN ， 因为过程当中会打开网页，登录 OneDrive 由于 SSH 配置是无法看到网页的
下载rclone的Windows客户端
[x64](https://downloads.rclone.org/v1.43.1/rclone-v1.43.1-windows-amd64.zip) [x32](https://downloads.rclone.org/v1.43.1/rclone-v1.43.1-windows-386.zip)
解压到能找到的目录，cmd定位到解压后的文件夹
输入命令
`rclone authorize "onedrive"`
![1](https://github.com/chain01/Cloud-hard-disk/blob/master/image/1.png)