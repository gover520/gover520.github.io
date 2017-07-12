---
layout: post
title: 在MacBook下使用protobuf
author: L.Y
---

protobuf是Google开源的一种轻便高效的结构化数据存储格式 可用于网络传输以及数据存储

## 简介
-----

公司项目中网络传输使用的一直是 [Protobuf](https://github.com/gover520/protobuf) 速度快 易于拓展
protobuf是和json相似的结构化数据存储格式 json是字符串 而protobuf更像是C++中的struct和class

这里有一篇文章是分析了protobuf和json的速度的文章 [Protobuf有没有比json快5倍](http://www.sohu.com/a/136487507_505779)


## 下载及安装
-----

### protobuf github
https://github.com/gover520/protobuf

### 下载protobuf
$ git clone https://github.com/google/protobuf.git 

### 安装automake & libtool
$ brew install automake  
$ brew install libtool

### 运行autogen.sh
$ ./autogen.sh

### 安装protobuf
$ ./configure  
$ make check  
$ make  
$ make install 


## 生成 xxx.proto 文件
-----
### proto 文件
package ly; 
message helloworld 
{ 
	required int32     id = 1;  // ID 
	required string    str = 2;  // str 
	optional int32     opt = 3;  //optional field 
}

### 编译 .proto 文件
写好 proto 文件之后就可以用 Protobuf 编译器将该文件编译成目标语言了。本例中我们将使用 C++。
假设您的 proto 文件存放在 $SRC_DIR 下面，您也想把生成的文件放在同一个目录下，则可以使用如下命令：

protoc -I=$SRC_DIR --cpp_out=$DST_DIR $SRC_DIR/addressbook.proto

命令将生成两个文件：
lm.helloworld.pb.h 定义了 C++ 类的头文件
lm.helloworld.pb.cc C++ 类的实现文件

## 使用proto

略