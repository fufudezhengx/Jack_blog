---
layout: default
title: flask-User.permissions 数值异常
---

## {{ page.title }}

疑问：有时 roles 中添加 Administrator 后 User.permissions 从 0x07 变为 0xff

回答：

	class User(db.Model,UserMixin): 
	...
	def __init__(self,**kwargs):
    super(User,self).__init__(**kwargs)
    if self.role is None:
        if self.email == current_app.config['AS_ADMIN']:
            self.role = Role.query.filter_by(permissions=0xff).first()
        if self.role is None:
            self.role = Role.query.filter_by(default=True).first()

全局配置参数 AS\_ADMIN 没有设置默认值，导致测试的时候注册用户如果没有填写邮箱  

	 self.email == current_app.config['AS_ADMIN'] 

判断为真，role.permissions被置为0xff