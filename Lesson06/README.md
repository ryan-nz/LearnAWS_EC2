监控EC2内存使用率
===============

## 知识点

* 监控内存使用率
  - Cloudwatch 自定义指标

## 官网

https://docs.aws.amazon.com/zh_cn/AmazonCloudWatch/latest/monitoring/publishingMetrics.html

## 实战演习

+ 编写内存检测脚本
+ 编写脚本执行计划任务
+ 定义EC2角色，授予 *CloudWatchAgentServerPolicy* 权限
+ 设置实例详细监控

### report_mem.sh

*内存使用率收集脚本*

```bash
# 计算出内存使用率
USEDMEMORY=$(free -m | awk 'NR==2{printf "%.2f\t", $3*100/$2}')
# 通过AWS CLI向Cloudwatch发送自定义内存指标
aws cloudwatch put-metric-data --metric-name memory-usage \
    --dimensions InstanceId=i-0983a35d44b2aaaaa \
    --storage-resolution 1 \
    --namespace "Custom" \
    --value $USEDMEMORY \
    --region ap-northeast-1
```

### 定义EC2角色

+ Name: ec2-cloudwatch-mymetrics
  - CloudWatchAgentServerPolicy

### 定义任务执行

```bash
$ crontab -e
...
*/1 * * * * /home/ec2-user/report_mem.sh
...
```

### 设置实例详细监控

监控 -> 管理详细监控 -> 启用

## 小马部落(Discord)

https://discord.gg/VSKw72P

## 小马视频频道

http://komavideo.com

## 课程文件

https://github.com/komavideo/LearnAWS_EC2
