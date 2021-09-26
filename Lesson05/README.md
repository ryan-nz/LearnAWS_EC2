监控CPU使用率(stress, cloudwatch)
================================

## 知识点

* 使用 Cloudwatch 监视 EC2 的运行状态

## 官网

https://docs.aws.amazon.com/zh_cn/AWSEC2/latest/UserGuide/using-cloudwatch.html

## 实战演习

### 开启详细监控(生产环境)

EC2 -> 监控 -> 管理详细监控 -> 开启

### 建立警报状态

+ 警报通知
  - 设置SNS主题
+ 警报操作
  - 停止(生产环境不要这样做！)
+ 警报阈值
  - CPU利用率
  - 0.9
  - 平均值

#### 安装压力测试工具

```bash
$ sudo amazon-linux-extras install -y epel
$ sudo yum install -y stress
# 安装确认
$ stress --help
# 压力测试CPU
$ stress --cpu 8
# 压压看
$ stress --cpu 8 --io 4 --vm 2 --vm-bytes 128M --timeout 10s
```

## 小马部落(Discord)

https://discord.gg/VSKw72P

## 小马视频频道

http://komavideo.com

## 课程文件

https://github.com/komavideo/LearnAWS_EC2
