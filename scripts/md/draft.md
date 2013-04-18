# Outline

## what's nodejs

Node.js is a platform built on Chrome's JavaScript runtime for easily building fast, scalable network applications. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient, perfect for data-intensive real-time applications that run across distributed devices.

## why nodejs

- Web development in a dynamic language (JavaScript) on a VM that is incredibly fast (V8). It is much faster than Ruby, Python, or Perl.

- Ability to handle thousands of concurrent connections with minimal overhead on a single process.

- JavaScript is perfect for event loops with first class function objects and closures. People already know how to use it this way having used it in the browser to respond to user initiated events.

- A lot of people already know JavaScript, even people who do not claim to be programmers. It is arguably the most popular programming language.

- Using JavaScript on a web server as well as the browser reduces the impedance mismatch between the two programming environments which can communicate data structures via JSON that work the same on both sides of the equation. Duplicate form validation code can be shared between server and client, etc.


npm get and publish, don't use source code!
non-blocking, event loop
Performance is the main advantage, node.js allocates a small heap per each connection, while other server side solutions create a (2MB) thread for each incoming connection, and of course creating a thread is much slower than allocating heap memory. Among the other advantages is the event-oriented and non-blocking nature of node.js.


distributed

Platform control - Specifically as compared to a LAMP stack, I have a lot more power/control over what is happening on the server side, how a client connection is handled - requests are handled, etc. You can do all of the same stuff with Apache/PHP but it requires a lot more work, plugins, etc.

Code re-use - It's nice to know that I can potentially use any piece of code on both sides of the stack. I don't do this as often as you'd think, but I do occasionally and it makes me a little happy every time.

Fast? hard to say

node connection pool
mysql
redis
memcached
mongo db

The community is vibrant and growing

walmart is using nodejs: end-to-end

We believe that Node.js is a programming mega-event on the scale of Java or Ruby on Rails. [It is] not merely a new way of expressing existing ideas, but rather a new way of thinking about how software systems should be built.

nodejs ~ apache+php ?
wait ? why no apache?

 serve static content, access logging, rewrite URLs, terminate SSL, enforce access rules, and manage multiple sub-services.

Long Way to Go


## how to use nodejs
socket.io
grunt
mysql
redis等
heroku

git


nodejs 调试