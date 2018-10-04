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

会在浏览器中打开登录界面，输入账户密码登录授权允许

![2](https://github.com/chain01/Cloud-hard-disk/blob/master/image/2.png)

成功会显示

![3](https://github.com/chain01/Cloud-hard-disk/blob/master/image/3.png)

控制台返回TOKEN

![4](https://github.com/chain01/Cloud-hard-disk/blob/master/image/4.png)

我们所需要的就是下面token区域中间的内容 {"access_token":" .... "expiry":"2018-10-03T12:10:29.4050602+08:00"}
因为我们是从Console控制台中复制出来的文本，所以里面会有换行符。等下是无法直接在 SSH 粘贴使用的，所以这里用到了 Notepad++ 来转换一下 

1、粘贴文本到新建的记事本

2、用 Notepad++ 打开 菜单中选择 搜索 -  替换

3、设置 查找目标为 （\r\n） 勾选下面的 （扩展（\n,\r,\t...）选项）后 全部替换


**安装rclone**

ssh连接vps

`curl https://rclone.org/install.sh | sudo bash`

成功会显示

rclone v1.43.1 has successfully installed.
Now run "rclone config" for setup. Check https://rclone.org/docs/ for more details

![5](https://github.com/chain01/Cloud-hard-disk/blob/master/image/5.png)

**初始化配置**

`rclone config`
输入n新建，输入名称（这个名称是可以随便起的，我是为了方便识别写了OneDrive）选择要挂载的云盘这里我是OneDrive所以选了17，别的云盘也可以过程自行谷歌

![6](https://github.com/chain01/Cloud-hard-disk/blob/master/image/6.png)

选择要挂载的云盘这里我是OneDrive所以选了17，别的云盘也可以过程自行谷歌

![7](https://github.com/chain01/Cloud-hard-disk/blob/master/image/7.png)

高级设置选n，商业版选b个人版选p，自动设置选n

![8](https://github.com/chain01/Cloud-hard-disk/blob/master/image/8.png)

粘贴刚才的TOKEN

![9](https://github.com/chain01/Cloud-hard-disk/blob/master/image/9.png)

选y，选q

![10](https://github.com/chain01/Cloud-hard-disk/blob/master/image/10.png)






