---
title: hello-world
date: 2021-09-27 17:42:41
tags: 
categories: 
id: 1632735761443854700

---

# 概述

本项目为 mybatis-plus 代码生成器的 demo

# 数据库准备

具体配置见 [application.properties](#application.properties) 

```sql
CREATE DATABASE IF NOT EXISTS mybatis_plus;

USE mybatis_plus;

DROP TABLE IF EXISTS `user`;
CREATE TABLE `user`  (
  `id` bigint(20) NOT NULL COMMENT '主键ID',
  `name` varchar(30) CHARACTER SET utf8 COLLATE utf8_general_ci DEFAULT NULL COMMENT '姓名',
  `age` int(11) DEFAULT NULL COMMENT '年龄',
  `email` varchar(50) CHARACTER SET utf8 COLLATE utf8_general_ci DEFAULT NULL COMMENT '邮箱',
  `create_time` datetime(0) DEFAULT NULL,
  `update_time` datetime(0) DEFAULT NULL,
  `version` int(255) DEFAULT NULL,
  `deleted` tinyint(255) DEFAULT NULL,
  PRIMARY KEY (`id`) USING BTREE
) ENGINE = InnoDB CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Compact;

INSERT INTO `user` VALUES (1, 'Jone', 18, 'test1@baomidou.com', '2021-03-26 19:34:28', '2021-03-23 19:35:02', 0, 0);
INSERT INTO `user` VALUES (2, 'Jack', 120, 'test2@baomidou.com', '2021-03-26 19:34:32', '2021-03-09 19:34:41', 0, 0);
INSERT INTO `user` VALUES (3, 'Tom', 28, 'test3@baomidou.com', '2021-03-26 19:34:35', '2021-03-02 19:34:50', 0, 0);
INSERT INTO `user` VALUES (4, 'Sandy', 21, 'test4@baomidou.com', '2021-03-24 19:34:38', '2021-03-02 19:34:53', 0, 0);
INSERT INTO `user` VALUES (5, 'Billie', 24, 'test5@baomidou.com', '2021-03-11 19:34:59', '2021-03-30 19:34:56', 0, 0);
```

# 代码编写

## 创建新项目

Spring Initializr 创建新项目

##  [pom.xml](pom.xml) 

mybatis-plus的代码生成器当然要导入mybatis-plus 依赖，这里在spring boot 下整合，所以导入下面这个：

```xml
        <!--mybatis-plus-->
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-boot-starter</artifactId>
            <version>3.0.5</version>
        </dependency>
```

这里使用 **mysql** 作为数据库，要使用其他数据库，需要更改驱动

```xml
        <!--mysql-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
        </dependency>
```

代码生成器使用了模板引擎生成代码，这里我们使用 **velocity** 

```xml
        <!-- 模板引擎 -->
        <dependency>
            <groupId>org.apache.velocity</groupId>
            <artifactId>velocity-engine-core</artifactId>
            <version>2.0</version>
        </dependency>
```

##  [application.properties](src/main/resources/application.properties) 

配置数据库如下：

```properties
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://101.34.161.147:3306/mybatis_plus?serverTimezone=GMT%2B8&characterEncoding=utf-8
spring.datasource.username=mp
spring.datasource.password=mp
```

##  [HelloWorldApplicationTests.java](src/test/java/com/example/helloworld/HelloWorldApplicationTests.java) 

运行 **codeGenerator** 生成代码



