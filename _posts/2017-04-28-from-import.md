---
layout: default
title: from import 理解
---

## {{ page.title }}

see https://docs.python.org/2/tutorial/modules.html

In section 6.4.2. Intra-package References:

- If the import module in the same dir, use e.g: from . import core
- If the import module in the top dir, use e.g: from .. import core
- If the import module in the other subdir, use e.g: from ..other import core

from . import XXX默认的就是在当前程序所在文件夹里\_\_init\_\_.py程序中导入XXX，如果当前程序所在文件夹里没有\_\_init\_\_.py文件的话，就不能这样写，而应该写成from .A import XXX，A是指当前文件夹下你想导入的函数(或者其他的)的python程序名，如果你想导入的函数不在当前文件夹，那么就有可能用到 from .. import XXX(即上一个文件夹中的\_\_init\_\_.py)，或者from ..A import XXX(即上一个文件夹中的文件A)