# SUSTech CS309OOAD-单服游戏大厅服务器
 一个基于netty实现的简易java单服服务器，用作课程项目吃豆人的服务器部分。实现了大部分网游功能，包括独立的玩家系统，英雄系统，道具系统，房间对战系统（游戏内状态同步未实现），英雄召唤，全球聊天等功能。代码风格稚嫩，bug有些还没修复，仅供学习参考。

## 写在前面

本单服服务器在王广帅的心悦单服游戏服务器的框架基础上搭建

## 简单的介绍

#### 技术栈：

1.netty

2.lombok（请记得安装idea中对应的插件）

3.mysql数据库

4.mybatisplus（请记得安装idea中对应的插件）

5.springboot

### 使用说明

检查完没有编译错误后，可以直接mvn clean package 打包成jar包部署到服务器。

消息类的设计可以参考game-server下的messages包以及gamehandle包下的各种demo。

每个消息对应的处理方法请在对应Handler里添加，记得加上GameMapping注解，签名参数要对应。

如果与其他语言的客户端通信，请保证消息header格式一样，并自行对应压缩和加密过程（我们的项目中与C#进行通信，那边对应的轮子不好找，故注释掉了）。

### 一些警告

1.暂时关闭了排行榜系统（实现有一些bug），如果需要加入请在ServerBootMain中加上@EnableScheduling，实现定时更新功能

2.房间系统实现有一点bug，主要在断线的时候出现，后来临近ddl乱改导致堆屎山

3.道具系统的typeId设计出了点问题，但是不影响我们的使用，逻辑有一些错误，如有需要可以自行修改。

4.远程开关服功能暂未测试

5.实际运行中出现的空指针bug，可以直接去对应地方作判断，因为我们有一些逻辑在客户端预判断好了

6.断线的监听器其实没有必要清理掉玩家的缓存，可以自行去除这些逻辑，依靠Scheduler检测长时间无心跳的玩家，我们暂时关闭了这个功能，所以在断线时清除玩家缓存。

7.待续

## 结尾

如有对服务器内部实现的改进，欢迎直接联系作者，也欢迎直接联系框架作者王广帅。
