为 EC2 实例添加一块 EBS 卷(存储块)
===============================

## 知识点

* 当系统硬盘存储容量不足时，为系统提供更多的存储空间

## 官网

https://docs.aws.amazon.com/zh_cn/AWSEC2/latest/UserGuide/ebs-volumes.html

## 实战演习

+ 建立一个新的EBS卷
  - Name: koma-ebs01
+ 将EBS卷绑定到EC2实例
  - /dev/xvdb
+ 在EC2中识别EBS卷

### 挂载步骤

```bash
# 查看可用磁盘设备及其挂载点
$ lsblk
# 查看当前系统挂载
$ df -h
# 确定卷上是否存在文件系统(如果输出[data]，则说明设备上没有文件系统)
$ sudo file -s /dev/xvdb
# 查看当前文件系统类型和挂载点
$ sudo lsblk -f
# 创建一个文件系统
$ sudo mkfs -t xfs /dev/xvdb
# 确认是否创建成功
$ sudo file -s /dev/xvdb
# 如果出现“找不到 mkfs.xfs”错误，请首先安装 XFS 工具
# $ sudo yum install xfsprogs
# 建立本地文件夹，准备挂载卷
$ sudo mkdir /var/mydata
# 把EBS卷挂载到文件夹
$ sudo mount /dev/xvdb /var/mydata
# 确认挂载结果
$ df -h
# 重新启动
$ sudo reboot
```

### 自动挂载步骤

```bash
# 备份挂载设置文件
$ sudo cp /etc/fstab /etc/fstab.bak
# 使用 blkid 命令查找设备的 UUID
$ sudo blkid
# /dev/xvdb: UUID="89e8f243-691f-4751-a25d-eab16b1bf694" TYPE="xfs"
# 编辑挂载文件
$ sudo nano /etc/fstab
...
UUID=89e8f243-691f-4751-a25d-eab16b1bf694     /var/mydata           xfs    defaults,noatime  1   1
...
# 重新启动
$ sudo reboot
# 确认挂载结果
$ df -h
```

## 小马部落(Discord)

https://discord.gg/VSKw72P

## 小马视频频道

http://komavideo.com

## 课程文件

https://github.com/komavideo/LearnAWS_EC2
