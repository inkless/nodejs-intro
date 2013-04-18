title: Overview
class: big
build_lists: true

![Node Logo](images/node-logo-light.png)

今天我们会覆盖这些东西:

- What is node.js ?
- Why node.js ?
- When can we use node.js ?

---

title: What is node.js ?
subtitle: 什么是 node.js ？
class: segue dark nobackground

---

title: What is node.js
class: big
build_lists: true

		Node.js is a platform built on Chrome's JavaScript runtime for easily building 
		fast, scalable network applications. Node.js uses an event-driven, non-blocking 
		I/O model that makes it lightweight and efficient, perfect for data-intensive 
		real-time applications that run across distributed devices.

- 基于V8引擎
- 快速，可扩展的网络应用
- 事件驱动
- 非阻塞的I/O模型
- ~ Apache + php

---

title: What is node.js ?
subtitle: 一个简单的Demo

<pre class="prettyprint" data-lang="javascript">
var http = require('http');
http.createServer(function (req, res) {
	res.writeHead(200, {'Content-Type': 'text/plain'});
	res.end('Hello World\n');
}).listen(1337, "127.0.0.1");
console.log('Server running at http://127.0.0.1:1337/');
</pre>

---

title: Why node.js ?
subtitle: 为什么使用 node.js ？
class: segue dark nobackground

---

title: Why node.js ?
subtitle: Pros
class: big
build_lists: true

- Yes, JavaScript!
- Event driven And non-blockong I/O
- Long connection
- npm
- Vibrant community
- Funny Debugger

---

title: Why node.js ?
subtitle: Yes, JavaScript!

<pre class="prettyprint" data-lang="javascript">
var replaceTmpl = function(str, conf) {
	return("" + str).replace(/\$(\w+)\$/g, function(a, b) {
		return typeof conf[b] != "undefined" ? conf[b] : "$" + b + "$"
	});
};
var ret = replaceTmpl("pre_$str$_suffix", {str: "HELLO"});
console.log(ret);
</pre>

- 无处不在的 JavaScript
- 前后端代码的复用！

---

title: Why node.js ?
subtitle: Event driven And non-blockong I/O

<pre class="prettyprint" data-lang="javascript">
process.on('uncaughtException', function(err) {
	console.log('got an error: %s', err.message);
	process.exit(1);
});

setTimeout(function() {
	throw new Error('fail');
}, 100);
</pre>

---

title: Why node.js ?
subtitle: Event driven And non-blockong I/O

	当同时有好几个请求的时候，Node会通知操作系统(通过 epoll, kqueue, /dev/poll, or select) 如果有新连接来了
	吼一声，然后它就睡觉去了。。。只有当新连接来了，操作系统会把它拽醒，它才执行一下回调。于是每个请求对它来说，
	就是小菜一碟。而不像其它大多数的 Web Server都会分配一个线程(2MB)去处理。

<pre class="prettyprint" data-lang="javascript">
var http = require('http');
http.createServer(function (req, res) {
	res.writeHead(200, {'Content-Type': 'text/plain'});
	res.end('Hello World\n');
}).listen(1337, "127.0.0.1");
console.log('Server running at http://127.0.0.1:1337/');
</pre>

---

title: Why node.js ?
subtitle: Event driven And non-blockong I/O

- 单线程
- no lock at all...
- so never dead locking...
	
---

title: Why node.js ?
subtitle: npm
class: big
build_lists: true

- node package modules
- 简单至极的package 管理
- 简单至极的package 发布
- 306 501	 downloads in the last day
- 8 506 657	 downloads in the last week
- 31 897 375	 downloads in the last month

---

title: Why node.js ?
subtitle: Vibrant Community
class: big
build_lists: true

- 好活跃啊
- 好活跃啊
- 好活跃啊
- 好活跃啊

---

title: Why node.js ?
subtitle: Funny Debugger

![](images/node-inspector.png)

---

title: And Then?

---

title: Why node.js ?
subtitle: Compare with Apache+php
class: segue dark nobackground

---
title: Why node.js ?
subtitle: Compare with Apache+php

/usr/sbin/ab -n 10000 -c 10 http://localhost:8080/

![](images/chart4.png)

---

title: Why node.js ?
subtitle: Compare with Apache+php

/usr/sbin/ab -n 100000 -c 1000 http://localhost:8080/

![](images/chart1s.png)

---

title: Why node.js ?
subtitle: Compare with Apache+php

![](images/chart2r.png)

---

title: Why node.js ?
subtitle: Storage
class: segue dark nobackground

---

title: Why node.js ?
subtitle: Storage

	支持各种常用的存储系统

- mysql
- memcache
- mongodb
- redis

---

title: Why node.js ?
subtitle: MySQL

	以最常用的 mysql 为例子，https://github.com/felixge/node-mysql

<pre class="prettyprint" data-lang="javascript">
var mysql      = require('mysql');
var connection = mysql.createConnection({
  host     : 'localhost',
  user     : 'me',
  password : 'secret',
});
connection.connect();
connection.query('SELECT 1 + 1 AS solution', function(err, rows, fields) {
  if (err) throw err;
  console.log('The solution is: ', rows[0].solution);
});
connection.end();
</pre>

---

title: Why node.js ?
subtitle: Connection Pool

	类似于 Java 的 Connection Pool，nodejs也有 Connection Pool

- mysql
- memcache
- mongodb
- redis

---

title: Why node.js ?
subtitle: MySQL Pool

	以最常用的 mysql 为例子

<pre class="prettyprint" data-lang="javascript">
var mysql = require('mysql');
var pool  = mysql.createPool({
  host     : 'example.org',
  user     : 'bob',
  password : 'secret'
});
pool.getConnection(function(err, connection) {
  // Use the connection
  connection.query( 'SELECT something FROM sometable', function(err, rows) {
    // And done with the connection.
    connection.end();
    // Don't use the connection here, it has been returned to the pool.
  });
});
</pre>

---

title: Node.js 真的这么好么？
class: segue dark quote nobackground

---

title: When can we use node.js ?
subtitle: node.js的应用场景
class: segue dark nobackground

---

title: When can we use node.js ?
class: big
build_lists: true

- Server push向客户端 / 长连接
- 较简单逻辑的Server，try it!
- 高并发平行代码
- Command-line Tools

---

title: When can we use node.js ?
subtitle: socket.io
build_lists: true

- Real Long Connection
- 兼容所有浏览器
- 100% javascript，前后端长一个样。。。

---
title: When can we use node.js ?
subtitle: socket.io

<pre class="prettyprint" data-lang="javascript">
var io = require('socket.io').listen(9090);

io.sockets.on('connection', function (socket) {
  socket.emit('news', { hello: 'world' });
  socket.on('my other event', function (data) {
    console.log(data);
  });
});
</pre>

<pre class="prettyprint" data-lang="html">
&lt;script src="/socket.io/socket.io.js">&lt;/script>
&lt;script>
  var socket = io.connect('http://localhost');
  socket.on('news', function (data) {
    console.log(data);
    socket.emit('my other event', { my: 'data' });
  });
&lt;/script>
</pre>
---

title: When can we use node.js ?
subtitle: Grunt.js
build_lists: true

- JavaScript Tast Runner
- 各种自动化，压缩，打包，单元测试，语法检查，部署，等等
