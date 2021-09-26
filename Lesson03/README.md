# 实例用户数据 - userdata (初始化Script)

=====================

## 知识点

* 启动 EC2 实例时设置启动脚本 - userdata

## 实现效果

* 从系统 AMI 启动 EC2 时自动运行初始化脚本，安装必要的软件包。

## 实战演习

### 启动 AMI EC2 实例， 设置启动脚本 - userdata

```bash
#!/bin/bash
yum update -y
yum install -y httpd
yum install -y nmap
systemctl start httpd
systemctl enable httpd
usermod -a -G apache ec2-user
chown -R ec2-user:apache /var/www
cd /var/www/html
echo "<h1>你好，AWS EC2.</h1>" > index.html
touch /home/ec2-user/.hushlogin
chown -R ec2-user:ec2-user /home/ec2-user/.hushlogin
```

### 查看用户数据

```bash
#!/bin/bash
nmap 127.0.0.1
curl http://169.254.169.254/latest/user-data/
```

## 小马部落(Discord)

https://discord.gg/VSKw72P

## 小马视频频道

http://komavideo.com

## 课程文件

https://github.com/komavideo/LearnAWS_EC2
