---
layout: default
title: Python27 and Python3 both install
---

## {{ page.title }}
#### Python27 添加 Python 路径

Assuming that your Python installation is in C:\Python27\, add this to your PATH:

	C:\Python27\;C:\Python27\Scripts\
	
#### Pip 安装

download [get-pip.py](https://bootstrap.pypa.io/get-pip.py)

	> python get-pip.py 

将 pip.exe 加入系统变量 Path

	C:\Python27\Scripts

#### Virtualenv 安装

	> pip install virtualenv

#### Python3 install

安装 Python 时要勾选 *Add Python 3.6 to PATH*


#### 分别进入 Python2 和 Python3 运行环境

	> py -2
	Python 2.7.13 ...

	> py -3
	Python 3.6.1 ...

#### 创建运行不同 Python 版本的虚拟环境

	> virtualenv -p C:\Python27\python.exe venv27
	> virtualenv -p C:\Users\...\Python36-32\python.exe venv36


