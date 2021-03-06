# Kafka介绍
<!-- TOC -->

- [Kafka介绍](#kafka介绍)
    - [简介](#简介)
    - [特点](#特点)
    - [kafka解决了什么问题](#kafka解决了什么问题)
    - [在哪些场景下会选择 Kafka](#在哪些场景下会选择-kafka)
        - [日志收集](#日志收集)
        - [消息系统](#消息系统)
        - [用户活动跟踪](#用户活动跟踪)
        - [运营指标](#运营指标)
        - [流式处理](#流式处理)
    - [kafka和其他消息队列的对比](#kafka和其他消息队列的对比)

<!-- /TOC -->

## 简介

Kafka是最初由Linkedin公司开发，是一个分布式、支持分区的（partition）、多副本的（replica），基于zookeeper协调的分布式消息系统

## 特点

- **高吞吐量、低延迟**：kafka每秒可以处理几十万条消息，它的延迟最低只有几毫秒，每个topic可以分多个partition,consumer group 对partition进行consume操作。

- **可扩展性**：kafka集群支持热扩展

- **持久性、可靠性**：消息被持久化到本地磁盘，并且支持
数据备份防止数据丢失

- **容错性**：允许集群中节点失败（若副本数量为n,则允许n1个节点失败）

- **高并发**：支持数千个客户端同时读写


## kafka解决了什么问题
kafka能在系统或应用程序之间构建可靠的用于传输实时数据的管道，是一种高吞吐量的分布式发布订阅消息系统

将不同的数据通过不同的topic实现发布订阅，生产者生成的数据发布到对应的topic中，订阅这个topic的消费者都可以消费这个topic中的数据。




## 在哪些场景下会选择 Kafka

### 日志收集
一个公司可以用Kafka可以收集各种服务的log，通过kafka以统一接口服务的方式开放给各种consumer，例如hadoop、HBase、Solr等


### 消息系统
解耦和生产者和消费者、缓存消息等

### 用户活动跟踪
Kafka经常被用来记录web用户或者app用户的各种活动，如浏览网页、搜索、点击等活动，这些活动信息被各个服务器发布到kafka的topic中，然后订阅者通过订阅这些topic来做实时的监控分析，或者装载到hadoop、数据仓库中做离线分析和挖掘。

### 运营指标
Kafka也经常用来记录运营监控数据。包括收集各种分布式应用的数据，生产各种操作的集中反馈，比如报警和报告。

### 流式处理
比如spark streaming和 Flink


## kafka和其他消息队列的对比
* 内容待补充


