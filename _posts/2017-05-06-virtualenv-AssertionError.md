---
layout: default
title: Bug | virtualenv AssertionError
---

## {{ page.title }}

	> virtualenv _testenv

	Traceback (most recent call last):
	...
	AssertionError: Filename C:\Users\...\Python\Python35\Lib\os.py does not start with any of these prefixes: ['C:\\users\\...\\python\\python35', 'C:\\users\\...\\python\\python35']

Windows:

	virtualenv -p <PATH TO PYTHON.EXE> venv

Linux/Mac:

	virtualenv -p </user/path/to/python> venv

### How to get python location

	>>> import sys
	>>> print(sys.executable)
	/usr/bin/python