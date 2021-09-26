Apache - 快速架起HTTP服务器
=========================

## 知识点

* Linux教学：使用 EC2 快速架起HTTP网站

## 官网

https://httpd.apache.org/

## 实战演习

```bash
############################################
# 系统升级
$ sudo yum update -y
# 安装 Apache HTTP 服务器
$ sudo yum install -y httpd
$ sudo yum list installed |grep httpd
# Web目录权限确认
$ ll /var/www
# 把ec2-user添加到apache组
$ sudo usermod -a -G apache ec2-user
# 设置Web目录权限
$ sudo chown -R ec2-user:apache /var/www

# 启动Apache 服务器
$ sudo systemctl start httpd.service
# 状态确认
$ sudo systemctl status httpd.service
# 安装nmap
$ sudo yum install -y nmap
$ nmap 127.0.0.1
$ ps aux|grep httpd
# 安装httpd服务
$ sudo systemctl enable httpd.service
$ sudo systemctl is-enabled httpd.service
$ sudo reboot
############################################
# 授权S3访问角色 -> KomaRoleS3FullAccess
# 确认S3存储桶访问权限
$ aws s3 ls --region ap-northeast-1
$ aws s3 sync s3://deeplearnaws-web/ /var/www/html/ --delete --region ap-northeast-1

# 动作确认
Done.
```

## Apache HTTP 服务器设置目录

```bash
$ ls /etc/httpd
```

## 小马部落(Discord)

https://discord.gg/VSKw72P

## 小马视频频道

http://komavideo.com

## 课程文件

https://github.com/komavideo/LearnAWS_EC2
