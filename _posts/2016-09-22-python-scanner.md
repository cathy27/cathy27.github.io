---
layout:     post
title:      "Python Scanner"
date:       2016-09-22 00:17
author:     "cathy27"
header-img: "img/tag-bg.jpg"
tags:
    - python
---

## 目录
{:.no_toc}

- toc
{:toc}


#### Python Scanner

代码如下，有gist链接[^1]

```python
class Scanner:
    def __init__(self):
        self.__line_split = None
        self.__pointer = None

    def next_int(self):
        try:
            next_str = self._next_str()
            ret = int(next_str)
            return ret
        except ValueError:
            return None

    def _next_str(self):
        if not self.__line_split or self.__pointer >= len(self.__line_split):
            self.__line_split = self.__next_line_str().split()
            self.__pointer = 0

        if not self.__line_split:
            return ''

        next_one = self.__line_split[self.__pointer]
        self.__pointer += 1
        return str(next_one)

    def __next_line_str(self):
        self.__line_split = None
        self.__pointer = None
        line = str(raw_input())
        return line


def main():
    scanner = Scanner()
    while True:
        n = scanner.next_int()
        if n is None:
            break

        # todo: insert code here

main()

```


#### 参考文献

[^1]: [wings27/scanner.py](https://gist.github.com/wings27/a7ffc67657d902e77f7d3ff688728efc)
