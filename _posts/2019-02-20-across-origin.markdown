---
layout: post
title: 跨域总结
date: '2019-02-20 10:00'
---

# 跨域

## 定义

### 描述

- 一种约定
- 浏览器最基本的安全功能
- 不同域之间相互请求资源

	- 为了阻止用户读取到另一个域名下的内容

### 构成

- 协议
- 域名
- 端口号

## 限制内容

### 存储类

- Cookie
- LocalStorage
- IndexedDB

### DOM节点？

### AJAX请求

### 例外

- 三个标签

	- <img>
	- <link>
	- <script>

## 问题

### 跨域ajax有没有发出去请求？

- 跨域并不是请求发不出去，请求能发出去，服务器也能收到请求并正常返回结果，只是结果被浏览器拦截了。
- 跨域并不能完全阻止CSRF，因为请求毕竟发出去了

### 后端有没有跨域，如果做安全限制？

## 解决方案

### JSONP

- 定义

	- 利用<script>标签没有跨域限制的漏洞，网页可以从其他来源动态获取JSON数据。
	- JSONP请求一定需要对方的服务器支持

- 实现过程

	- 准备回调函数和参数

		- 声明一个回调函数，函数的形参为要获取的目标数据

	- 请求

		- 创建一个<script>标签，把跨域的API接口地址赋值给script的src属性
		- 在该地址中向服务器传递该函数名，如（?callback=show）

	- 服务器处理

		- 解析回调函数名和参数
		- 逻辑处理
		- 把结果和回调函数拼装
		- 返回给客服端

	- 客户端处理返回

		- 调用回调函数，对数据进行操作
		- 清理script缓存

- 代码示例

	- 客户端
	- 服务端

### CORS

- 关键实现者

	- 后端

- 开启方式

	- 设置Access-Control-Allow-Origin

		- 表示哪些域名可以访问资源
		- 通配符表示所有网站都可以访问

- 请求分类

	- 简单请求

		- 条件

			- 满足Method

				- GET
				- POST
				- HEAD

			- 满足Content-Type

				- text/plain
				- multipart/form-data
				- application/x-www-form-urlencoded

	- 复杂请求

		- 条件

			- 不满足简单请求的其它请求

		- 查询请求

			- option方法
			- 通过该请求来查询服务端是否允许跨域请求

### postMessage

- 定义

	- Subtopic 1该方法允许来自不同源的脚本采用异步方式进行有限的通信，可以实现跨文本档、多窗口、跨域消息传递

- 解决以下场景的跨域数据传递

	- 页面和其打开的新窗口的数据传递
	- 多窗口之间的消息传递
	- 页面与嵌套iframe消息传递

- 示例

	- 页面A，发消息
	- 页面B，收消息

### websocket

- 定义

	- Websocket是HTML5的一个持久化的协议
	- 实现了浏览器和服务器的全双工通信

		- 全双工

	- 也是跨域的解决方案
	- 和HTTP都是应用层协议，都基于TCP协议

- 建立过程

	- 建立连接：借助HTTP协议
	- 建立好之后，和HTTP就无关了。WebSocket 的 server 与 client 都能主动向对方发送或接收数据

### Node中间件代理

- 实现原理

	- 同源策略是浏览器需要遵循的标准
	- 如果是服务器向服务器请求，就无需遵循同源策略

- 示例

	- 客户端
	- 代理服务器
	- 目标服务器

### Nginx反向代理

- 原理同Node中间件代理
- Nginx示例

### window.name + iframe

### location.hash + iframe

### ducument.domain + iframe

## 对比

### JSONP 和 AJAX

- 相同

	- 都是客服端向服务器发送请求，从客户端获取数据的方式。

- 不同

	- JSONP

		- 非同源策略
		- 仅支持get方法，有局限性
		- 不安全：容易遭受XSS攻击

	- AJAX

		- 同源策略

## 参考

### https://juejin.im/post/5c23993de51d457b8c1f4ee1

