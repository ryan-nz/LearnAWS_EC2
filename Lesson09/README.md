EFS - 多台 EC2 实例间共享文件存储
==============================

## 知识点

* 建立一个 EFS 文件系统，绑定到多个 EC2 实例上，实现文件共享

## 官网

https://aws.amazon.com/cn/efs

## 实战演习

+ 建立一个 EFS 文件系统
  - Name: koma-efs01
  - 自定义: 选择可用区, 安全组
+ 向安全组中添加 NFS 端口授权
+ 确认所在 VPC 已开启DNS解析服务
  - DNS 主机名
  - DNS 解析
+ 选择刚刚建立的 EFS 文件系统，获取连接串
+ 启动 EC2 实例
  - Name: for-efs01
  - Name: for-efs02

## 执行脚本

```bash
# 安装 EC2 实用程序
$ sudo yum update -y
$ sudo yum install -y amazon-efs-utils
$ mkdir koma-efs01
$ sudo mount -t efs -o tls fs-e60ea0c6:/ koma-efs01
$ df -h
$ cd koma-efs01
$ sudo nano helo.txt
...
helo efs.
...
```

## 参考: 自动挂载 Amazon EFS 文件系统

https://docs.aws.amazon.com/zh_cn/efs/latest/ug/mount-fs-auto-mount-onreboot.html

## 小马部落(Discord)

https://discord.gg/VSKw72P

## 小马视频频道

http://komavideo.com

## 课程文件

https://github.com/komavideo/LearnAWS_EC2
