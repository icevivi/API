# 第四章 测试和调试 - 日志系统

biForm 和 PFF 运行时环境使用同样的日志系统。

---

<h2 id=category>目录</h2>

- [哪些信息会通过日志系统输出](#哪些信息会通过日志系统输出)
 - [1. 输出内容：应用程序运行产生的日志信息](#_1-输出内容：应用程序运行产生的日志信息)
 - [2. 输出内容：Python 程序运行产生的输出](#_2-输出内容：Python-程序运行产生的输出)
- [输出方式](#输出方式)
 - [1. 输出方式：log文件](#_1-输出方式：log文件)
 - [2. 输出方式：调试窗口](#_2-输出方式：调试窗口)
 - [3. 输出方式：UDP Socket 输出](#_3-输出方式：UDP-Socket-输出)
- [脚本中如何调用](#脚本中如何调用)
- [其它日志输出方式](#其它日志输出方式)

---

## 哪些信息会通过日志系统输出

[返回目录](#category)

通过日志系统输出的内容包括：

### 1. 输出内容：应用程序运行产生的日志信息

[返回目录](#category)

biForm 和 PFF 运行时环境（如biReader）运行过程中也会输出很多日志信息，比如 biForm 中试运行一下表单可以看到类似于下面这样的一些信息：

``` log
=====标准输出=====
-*- 加载表单 于: 14:16:32 -*-
LOG|INFO    | #-------------开始加载表单： newform
LOG|INFO    | [表单状态]切换到：Blank
LOG|INFO    | ***在模块 BILIVE_RUN_FORM_4 中添加对象 newform
LOG|INFO    | ***在模块 BILIVE_RUN_FORM_4 中执行文件：
LOG|INFO    | G:/bilive_dev/bin/temp/class_eval_newform.py
LOG|INFO    | * 开始加载表单：newform
LOG|INFO    | newform::Public module
LOG|INFO    | =====* ENV info *=====
LOG|INFO    | BILIVE_RUN_FORM_4
LOG|INFO    | [表单状态]切换到：Blank
LOG|INFO    | 表单：【newform】 已加载！版本：1
LOG|INFO    | #-------------加载完成：newform
LOG|INFO    | ***修改模块名称 从 BILIVE_RUN_FORM_4 改为 BILIVE_FORM_NEWFORM_4
LOG|INFO    | ###表单 [newform] 的模块名:BILIVE_FORM_NEWFORM_4
LOG|INFO    | [Database]no such table: notable Unable to execute statement
LOG|INFO    | [SQL]select * from notable
```

有时这些信息对于调试程序也很有帮助，比如上例中如果应用程序底层执行SQL语句出错时，会输出错误信息。但其内容和格式可能不同的程序有些差异，因此开发者也不必特意研究这些日志的内容和格式。在调试程序需要查看日志文件时，这些内容通过上下文一般都比较容易理解。

### 2. 输出内容：Python 程序运行产生的输出

[返回目录](#category)

Python 脚本产生的标准输出和标准错误信息，以及调用 log 对象的接口输出的信息，都会通过我们的日志系统一起输出。

比如以下语句产生的输出都会反映到日志系统中：

``` Python

>>> dir()
['__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'base64', 'codecs', 'formclass_newform', 'gbk', 'gbkList', 'log', 'logging', 'newform', 'pub', 'sys', 'this']

>>> print('测试日志输出')
测试日志输出

>>> 一行错误代码
Traceback (most recent call last):
  File "<string>", line 1, in <module>
NameError: name '一行错误代码' is not defined

```

产生的日志内容：

``` log
LOG|INFO    | ['__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'base64', 'codecs', 'formclass_newform', 'gbk', 'gbkList', 'log', 'logging', 'newform', 'pub', 'sys', 'this']
LOG|INFO    | 测试日志输出
LOG|INFO    | Traceback (most recent call last):
LOG|INFO    |   File "<string>", line 1, in <module>
LOG|INFO    | NameError: name '一行错误代码' is not defined
```

调用 log 接口产生的日志输出请参考 [脚本中如何调用](#脚本中如何调用) 中的示例。

## 输出方式

[返回目录](#category)

有三种输出方式：

### 1. 输出方式：log文件

[返回目录](#category)

biForm 和 PFF 的运行时环境（比如 biReader），运行时都会生成日志文件，文件存放路径一般在工作区的 log 子目录下，文件名为 biForm.log（或 biReader.log）。这些文件一般在重启之后会被删除重建，所以如果需要保留上一次运行的日志文件，需要将文件复制一份，否则应用程序重启的话其中的内容都会被清除。

### 2. 输出方式：调试窗口

[返回目录](#category)

在 biForm 中的脚本编辑器和试运行窗口都有“调试”窗口，其中有“输出”分页，日志信息都会显示在这里。

在某些 PFF 运行时环境中也会提供“调试”窗口，如果有这样的功能，也会显示日志信息。目前 biReader 的社区免费版没有提供这样的功能，所以没有这项日志输出。

### 3. 输出方式：UDP Socket 输出

[返回目录](#category)

这种方式会将日志内容通过 UDP Socket 输出。

biForm 和 biReader 都支持这种输出方式，但需要注意的是，在社区免费版中没有提供这种输出方式。

日志信息缺省发送到本机，端口号是 60008。也可以修改工作目录下的 log.config 指定IP地址或其它端口号。IP地址为空时表示是本机。格式如下：

``` config
[General]
IP=
port=60008
```

输出的内容可以使用我们提供的日志跟踪程序 biLog 进行实时跟踪，需要注意 biLog 的端口设置要和 biForm 和 biReader 的端口设置一致，否则接收不到日志信息。

## 脚本中如何调用

[返回目录](#category)

开发者可以在 Python 脚本中通过内置的 log 对象输出日志信息。

比如：
``` Python
>>> log.info('普通信息')
>>> log.debug('调试信息')
>>> log.warning('警告信息')
>>> log.critical('严重警告信息')
>>> log.error('错误信息')
```

输出的内容就是：
``` log
LOG|INFO    | 普通信息
LOG|DEBUG   | 调试信息
LOG|WARNING | 警告信息
LOG|CRITICAL| 严重警告信息
LOG|ERROR   | 错误信息
```

log 输出信息的等级：

|   等级   |       调用方式        |    说明     |
| -------- | -------------------- | ----------- |
| info     | log.info(content)    | 普通信息     |
| debug    | log.debug(content)   | 程序调试信息 |
| warning  | log.warning(content) | 警告        |
| critical | log.warning(content) | 严重警告     |
| error    | log.warning(content) | 错误信息     |

当然也支持使用 Python 的格式化输出，比如：
``` Python
>>> a=12342
>>> b='数量'
>>> log.info(f'{b}:{a}')
>>> log.debug('%s : %s' % (b,a))
```

输出的内容就是：
``` log
LOG|INFO    | 数量:12342
LOG|DEBUG   | 数量 : 12342
```

## 其它日志输出方式

[返回目录](#category)

开发者也可以自己使用 Python 的 logging 模块或其它方式输出日志，不过我们建议尽量使用我们提供的日志系统，这样与其它开发者开发的程序进行集成时，能获得统一的日志输出，更方便进行调试和测试。
