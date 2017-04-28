---
layout: default
title: flask-SQLAlchemy 数据库迁移步骤
---

## {{ page.title }}

1. 创建迁移仓库  
	
		python hello.py db init

2. 创建迁移脚本  
	
		python hello.py db migrate -m "initial migration"  
   "initial migration"是迁移脚本的名称

3. 更新数据库  
	
		python hello.py db upgrade

修改了 model 之后  
需要先 python manage.py db migrate   
然后才 python manage.py db upgrade