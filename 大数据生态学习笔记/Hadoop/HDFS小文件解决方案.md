# HDFS小文件解决方案

<!-- TOC -->

- [HDFS小文件解决方案](#hdfs小文件解决方案)
    - [问题](#问题)
    - [小文件存储弊端](#小文件存储弊端)
    - [解决方法1](#解决方法1)
    - [解决方法2](#解决方法2)
    - [解决方法3](#解决方法3)

<!-- /TOC -->


## 问题
前面说了hdfs不适合存储大量小文件，有没有什么解决方案？


## 小文件存储弊端
每个文件均按块存储，每个块的元数据存储在NameNode的内存中，
因此HDFS存储小文件会非常低效

**因为大量的小文件会耗尽NameNode中的大部分内存**

但是要注意：**`存储小文件所需要的磁盘容量和数据块的大小无关`**

例如：
一个1MB的文件设置为128MB的块存储，实际上使用的是1MB的磁盘空间，不是128MB


## 解决方法1
**`Hadoop Archive`**

是一个高效的将小文件放入HDFS块中的文件存档工具，它能够将多个小文件打包成一个HAR文件，对NameNode而言是一个整体，这样就减少了NameNode的内存使用

## 解决方法2
**Sequence File**

由一系列的二进制Key/Value组成，如果key为文件名，value为文件内容，则可以将大批小文件合并成一个大文件


## 解决方法3
**CombineFileInputFormat**

是一种新的inputformat, 用于将多个文件合并成一个单独的split, 另外它会考虑数据的存储位置


