---
title: "记录一次habse[key-value is too large]的排错及解决办法"
date: 2019-03-01T15:21:29+08:00
---

事件起因是:数据同步程序中kafka的消费线程突然中止，于服务器上程序日志中找出如下异常信息:

_```
Caused by: IllegalArgument(message:java.lang.IllegalArgumentException: KeyValue size too large```_

经过查找相关资料，初步估计为以下原因:
    _单条内容过大，超过hbase配置的大小(我自己这边默认的是10M)_
    _```
        hbase.client.keyvalue.maxsize
    ```_
