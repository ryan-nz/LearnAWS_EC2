# EC2 - 实例元数据 - metadata

==========================

## 知识点

* 建立一个新的 EC2 实例
* 使用 EC2 实例元数据 - metadata

## 官网

https://docs.aws.amazon.com/zh_cn/AWSEC2/latest/UserGuide/ec2-instance-metadata.html

## EC2元数据获取方法

http://169.254.169.254/latest/meta-data/

## 实战演习

```bash
$ ssh -i ./deeplearn-ssh-key.pem ec2-user@ip
############################################################
# 获取元数据一览
$ curl http://169.254.169.254/latest/meta-data/
# 获取主机名
$ curl http://169.254.169.254/latest/meta-data/hostname
# 获取公有IP
$ curl http://169.254.169.254/latest/meta-data/public-ipv4
# 获取内网IP
$ curl http://169.254.169.254/latest/meta-data/local-ipv4
# 获取系统使用的AIM-ID
$ curl http://169.254.169.254/latest/meta-data/ami-id

############################################################
# 下载元数据脚本
$ wget https://s3.amazonaws.com/ec2metadata/ec2-metadata
$ chmod +x ec2-metadata
$ ./ec2-metadata --help
# 获取内网IP
$ ./ec2-metadata -o
# 获取公有IP
$ ./ec2-metadata -v
# 获取放置可用区
$ ./ec2-metadata -z
# 所在安全组
$ ./ec2-metadata -s
```

### 元数据类别

https://docs.aws.amazon.com/zh_cn/AWSEC2/latest/UserGuide/instancedata-data-categories.html

## 小马部落(Discord)

https://discord.gg/VSKw72P

## 小马视频频道

http://komavideo.com

## 课程文件

https://github.com/komavideo/LearnAWS_EC2
