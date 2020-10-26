1. 确定技术点

   并发模型和网络模型
      多进程tcp 并发模型

   确定细节功能，注册要注册什么，注册后是否直接登录
      注册 ： 用户名密码， 加密存储，注册后直接登录
      历史记录 ： 最近的前10个

   一级界面，二级界面如何切换

     见 demo

2. mysql数据库设计  dict

    words ：  id    word   mean
    user :  id  name  passwd

    create table user (id int primary key auto_increment,name varchar(32) not null,passwd char(128) not null);

    hist :  id  name  word   time

    create table hist (id int primary key auto_increment,name varchar(32) not null,word varchar(32) not null,time datetime default now());


3. 结构设计，功能模块划分

   如何封装，客户端和服务端工作流程，有几个功能模块

   *  函数封装
   *  功能模块： 通信，登录，注册，查询，历史记录

4. 通信搭建

5. 注册
      客户端 ： 输入用户名密码
               发送请求
               接收反馈

      服务端 ： 接收请求，判断请求类型
               判定用户可否注册
               给客户端反馈


   登录
       客户端 : 输入用户名密码
               发送请求
               等待反馈

       服务端 ： 接收请求
                验证信息
                发送结果

   查询
       客户端 ： 输入单词
                发送请求 （套接字）
                接收结果

       服务器 ：　接收请求
       　　　　　　查找单词
       　　　　　　插入历史记录
       　　　　　　发送给客户端

   历史记录

协议 ： 登录   L
       注册   R
       查单词  Q
       历史记录  H
       退出   E

cookie：
    import  getpass

    pwd = getpass.getpass()
    功能: 隐藏输入内容