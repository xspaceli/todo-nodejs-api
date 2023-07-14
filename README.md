# 前言

NodeJS 全栈开发之后端接口开发基于 Node.js+Express+Mysql 实现 RESTFUL API，接口包括：登录，注册，记住密码，修改密码，退出登录，todoList 增删改查 CRUD，查询条件筛选，点亮红星标记等。本项目场景虽然简单，但涵盖功能比较齐全，适合初学全栈开发的小伙伴。如果觉得不错的话，请大大们给个:heart:star，也期待大家一起交流学习。

[在线 DEMO 演示](http://106.55.168.13:8082/)

[NodeJS 全栈开发一个功能完善的 Express 项目实战分享](https://juejin.im/post/6844904198551666701)

# 目录结构

```
│  app.js                              // 入口文件
│  ecosystem.config.js                // pm2默认配置文件
│  package.json                       // npm包管理所需模块及配置信息
├─db
│      dbConfig.js                    // mysql数据库基础配置
├─routes
│      index.js                       // 初始化路由信息，自定义全局异常处理
│      tasks.js                       // 任务路由模块
│      users.js                       // 用户路由模块
├─services
│      taskService.js                 // 业务逻辑处理 - 任务相关接口
│      userService.js                 // 业务逻辑处理 - 用户相关接口
└─utils
        constant.js                   // 自定义常量
        index.js                      // 封装连接mysql模块
        md5.js                        // 后端封装md5方法
        user-jwt.js                   // jwt-token验证和解析函数
```

# 技术栈

- NodeJS v10
- express
- mysql v5.7
- jwt
- nodemon
- cors
- boom
- pm2

# 功能模块

- 登录（登出）
- 注册
- 记住密码
- 修改密码
- todo 增删改查
- 点亮红星标记
- 查询条件筛选

# 下载安装依赖

```
git clone https://github.com/jackchen0120/todo-nodejs-api.git
cd todo-nodejs-api
npm install 或 yarn
```

#数据库表设计
使用 MySQL，创建数据库 my_test ，创建 sys_user 用户表。
sql 复制代码-- 创建数据库
CREATE DATABASE `my_test` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;

-- 创建用户表
CREATE TABLE `sys_user` (
`id` BIGINT(20) UNSIGNED NOT NULL AUTO_INCREMENT COMMENT '唯一标识',
`username` VARCHAR(50) NOT NULL DEFAULT '' COMMENT '登录帐号，邮箱或手机号',
`password` VARCHAR(64) NOT NULL DEFAULT '' COMMENT '登录密码',
`nickname` VARCHAR(50) NULL DEFAULT '' COMMENT '昵称',
`avator` VARCHAR(50) NULL DEFAULT '' COMMENT '用户头像',
`sex` VARCHAR(20) NULL DEFAULT '' COMMENT '性别：u:未知, m:男, w:女',
`gmt_create` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
`gmt_modify` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
PRIMARY KEY (`id`) USING BTREE,
UNIQUE KEY `username_UNIQUE` (`username`)
) ENGINE=InnoDB AUTO_INCREMENT=1 COMMENT='用户表';

## MySQL 安装

请移步到我的一篇博客[前端必知必会 MySQL 的那些事儿 - NodeJS 全栈成长之路](https://juejin.im/post/5ee6010ef265da76d3188ea8)

## 开发模式

```
npm start
```

运行之后，访问地址：http://localhost:8088

## 生产环境（后台启动服务）

```
pm2 start ecosystem.config.js
```

## 获取更多实操经验及项目源码

欢迎关注个人公众号：**懒人码农**

<img src="https://img-blog.csdnimg.cn/20200531011333650.png#pic_center?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzE1MDQxOTMx,size_16,color_FFFFFF,t_70" width="200" alt="公众号二维码" />
