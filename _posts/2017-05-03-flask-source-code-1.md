---
layout: default
title: Flask 源码理解
---

## {{ page.title }}

### WSGI

全称 Web Server Gateway Interface  是一种网关协议

在python的世界里，通过WSGI约定了web服务器怎么调用web应用程序的代码，web应用程序需要符合什么样的规范，只要web应用程序和web服务器都遵守WSGI 协议，那么，web应用程序和web服务器就可以随意的组合。这也就是WSGI存在的原因。

### jinja2与Werkzeug

#### jinja2

jinja2 是是一个功能齐全的模板引擎。它有完整的unicode支持，一个可选 的集成沙箱执行环境，被广泛使用。

	>>> from jinja2 import Template
	>>> template = Template('Hello !')
	>>> template.render(name='John Doe')
	u'Hello John Doe!'

#### Werkzeug

Werkzeug是一个WSGI工具包。WSGI是一个web应用和服务器通信的协议，web应用可以通过WSGI一起工作。一个基本的”Hello World”WSGI应用看起来是这样的:

	def application(environ, start_response):
	    start_response('200 OK', [('Content-Type', 'text/plain')])
	    return ['Hello World!']

上面这小段代码就是WSGI协议的约定，它有一个可调用的start_response 。environ包含了所有进来的信息。 start_response用来表明已经收到一个响应。 通过Werkzeug，我们可以不必直接处理请求或者响应这些底层的东西，它已经为我们封装好了这些。

请求数据需要environ对象，Werkzeug允许我们以一个轻松的方式访问数据。响应对象是一个WSGI应用，提供了更好的方法来创建响应。如下所示：

	from werkzeug.wrappers import Response

	def application(environ, start_response):
	   response = Response('Hello World!', mimetype='text/plain')
	   return response(environ, start_response)

### wsgi, Werkzeug, flask之间的关系

Flask是一个基于Python开发并且依赖jinja2模板和Werkzeug WSGI服务的一个微型框架，对于Werkzeug，它只是工具包，其用于接收http请求并对请求进行预处理，然后触发Flask框架，开发人员基于Flask框架提供的功能对请求进行相应的处理，并返回给用户，如果要返回给用户复杂的内容时，需要借助jinja2模板来实现对模板的处理。将模板和数据进行渲染，将渲染后的字符串返回给用户浏览器。