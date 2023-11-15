---
created: 2023-11-15T20:51
updated: 2023-11-15T20:51
---
# mongodb

## noSQL

## /usr/local/etc/mongod.conf

## mongoose

### 好处

- 1. 可以为文档创建一个模式结构(schema:约束)

	- 1.限制

		- 字段个数
		- 字段类型

	- 2.先尝试类型转换，转换不了，进不来，数据进入数据库之前，进行了检验

- 2.可以对模型中的对象/文档进行验证
- 3.数据可以通过类型转换转换为对象模型
- 4.可以使用中间件来应用业务逻辑挂钩
- 5.比node原生的MongoDB驱动更容易

### 新对象

- Schema:模式对象

	- Schema对象定义约束了数据库中的文档结构

- Model:模型

	- Model对象作为集合中的所有文档的表示，相当于MongoDB数据库中的集合collection

- Document

	- Document表示集合中的具体文档，相当于集合中的一个具体的文档

		- 结合中的元素

### 是一个第三方包

- 1.下载安装Mongoose：npm i mongoose --save
- 2.项目中引入mongoose：const mongoose = require('mongoose')
- 3.连接MongoDB数据库：mongoose.connect('mongodb://localhost/test', {userMongoclient:true});

### 特点：

- 通过关系型数据的思想来设计非关系型数据库
- 基于mongodb驱动，简化操作

### 定义Schema

- 相当于集合
- 但是不能操作数据库
- 需要定义model，才能操作数据库

### Schema的静态方法

- // 静态方法
Resource.static.findByProject = function (project, cb) {
  this.find({ project }, function (err, docs) {
    cb(err, docs)
  })
}

### Schema的实例方法

- // 实例方法
Resource.methods.print = function () {
  console.log('我是一个实例方法')
  console.log(this.name) // 实例中传递的name
  // const instance = new ResourceModel({name: "xxx"})
}

## [推荐文章地址](https://cloud.tencent.com/developer/article/1683003)

