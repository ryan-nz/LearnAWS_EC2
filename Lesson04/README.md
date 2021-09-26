角色授权 - iam role profile
==========================

## 知识点

* 通过为 EC2 实例进行授权，扩展 EC2 访问 AWS 资源的能力

## 官网

https://docs.aws.amazon.com/zh_cn/IAM/latest/UserGuide/id_roles_use_switch-role-ec2_instance-profiles.html

## 实战演习

+ 建立 EC2 实例(Amazon Linux 2)
  - Name: ec2-for-role
+ 建立 IAM 角色，赋予 S3 的访问权限
  - Name: ec2-s3-role
+ 将角色赋予 EC2 实例
+ 通过 EC2 实例访问 S3 资源

## EC2

```bash
# 通过 AWS CLI 列出 S3 存储桶的信息
$ aws s3 ls
```

## 小马部落(Discord)

https://discord.gg/VSKw72P

## 小马视频频道

http://komavideo.com

## 课程文件

https://github.com/komavideo/LearnAWS_EC2
