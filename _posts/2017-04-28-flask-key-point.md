---
layout: default
title: flask-要点注意
---

## {{ page.title }}

- flask login is\_authenticated change  
  Flask-Login 0.3 [contains a breaking change](https://github.com/maxcountryman/flask-login/blob/master/CHANGES#L25-L26) which changed *is\_active, is\_anonymous*, and *is_authenticated* from functions to properties.

- flask database default 参数必须在 db.session.commit() 后生效

- SQLALCHEMY_DATABASE_URI 不是URL
  二者的区别在于，URI表示请求服务器的路径，定义这么一个资源。而URL同时说明要如何访问这个资源（http://）。

- import bootstrap 格式  
  from flask.ext.bootstrap import Bootstrap 必须修改为：  
 from flask_bootstrap import Bootstrap