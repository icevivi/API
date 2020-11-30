# 第一章 biForm开发基础 - 内置对象

biForm和biReader中除了可以使用 Python 和 Qt 库外，也提供了几个内置的对象，用于控制和访问表单对象、数据库、日志输出、提供公用函数和常量等。

## 1、this对象

this对象用来指当前这个表单对象，但并不是指这个表单在运行时状态下显示的图形化控件。如果需要调用表单的图形化控件，需要使用this.form。


可以用 **this.控件名** 来引用表单上的各个控件。比如 this.button this.lineedit this.list 分别用来调用表单上这三个控件。

This对象还有两个方法：hscrollto 和 vscrollto ，在一个表单的可用区域超过所在窗口范围时，可以用它来控制的水平方向和垂直方向的滚动条。如：

``` python 

>>> this.hscrollto(20)

```

不同的表单，this各有所指。在运行时环境下，有可能同一个表单有多个实例，它们的 this 也是指向各自的实例，不会发生冲突。

如果需要在一个表单的脚本中访问另一个表单的this对象，也是可以的，比如：

``` python 

import sys
m=sys.modules['another_form_module_name'] #返回另一个表单的模块对象
print(m.this) #这里的m.this就是另一个表单的this对象了

```

但我们一般不建议使用这种方式直接访问其它表单对象。这样可能造成表单间耦合程度增加。而且因为表单的模块名在运行时是动态生成的，所以这样的语句不可能正确运行。虽然也可以通过其它方式使用动态的模块名达到访问的效果，但并不建议这样使用，除非必须用这种方式实现某些特殊的功能。

## 2、pub对象

pub对象提供了一组常用的常量和函数方便调用。其中大部分都可以通过 PythonQt.Qt 相关模块加以调用，pub只是提供比较简单的调用方式。比如 pub.currentDateTime() 返回当前日期和时间，pub.rgb(200,200,200) 返回一个QColor对象，pub.openPFF('form_UUID_XXXX') 用于打开另外的表单。详细内容请参考pub的接口说明。

## 3、log对象

biForm 中内置了一个运行时全程共用的log对象，通过调用它的接口进行日志输出。 调用方式如 ```log.debug('调试信息')```。log对象本身是 Python 的模块 logging 的 Logger 类的一个实例，详细的调用接口可以参考Python的文档。

### 3.1 log的输出方式

1. 调试时的标准输出

在biForm中进行调试时，在“命令交互”中调用 log 的接口，比如 ```log.debug('输出的内容')```，在“输出”窗口就可以看到输出的日志内容。

2. 日志文件输出

在 biForm/biReader 工作目录下会有一个 biForm.log/biReader.log 文件。每次启动应用程序时，会清空这个LOG文件，通过调用 log 输出的内容会写入这个文件。同时写入的还会有系统运行内部产生的日志信息及Python的标准输出内容。如果想分析这些日志文件，需要在退出 biForm/biReader 后，将日志文件拷贝一份，否则下次再启动应用程序时，内容会被清空。

3. UDP Socket输出

目前在社区版中不提供这类输出，在专业版和企业版中可以通过这种输出方式，将调试信息发送给本机或其它IP地址的指定端口，我们会提供专用的日志接收和跟踪工具 biLog，通过 biLog 可以实时接收到 biForm/biReader中输出的调试信息，更方便进行程序调试和运行跟踪。详细资料请参考专业版和企业版的相关文档。

### 3.2 log输出信息的等级

|   等级   |        调用方式        |    说明     |
| -------- | --------------------- | ----------- |
| info     | log.info(content)     | 普通信息     |
| debug    | log.debug(content)    | 程序调试信息 |
| warning  | log.warning(content)  | 警告        |
| critical | log.critical(content) | 严重警告     |
| error    | log.error(content)    | 错误信息     |

## 4、数据库连接对象

biReader在运行时后台必定是会有一个数据库的，因为有些系统底层功能需要使用到数据库，有些表单也需要使用数据库。

biForm将基本的数据存取都做了封装，所以很多表单数据的存取和查询，都由表单的数据库引擎完成，一般都不需要写直接写SQL语句。但也有一些情况下，还是需要直接运行SQL语句的。另外，我们也对一些常用的数据库操作进行了封装，也都通过数据库连接对象进行调用。
	
Python脚本中通过 ```this.form.database()``` 就可以返回数据库连接对象。以下是一些使用的例子：

``` Python 

db=this.form.database()

#查询记录
result = db.execute("select * from t_mytable")
print(result)

#执行修改操作
db.execute("update t_mytable set fname='new' where fname='old'")

#判断最后执行的SQL语句是否因有错不能执行
if len(db.lastErrorText())>0:
	print(db.lastErrorText())
	this.form.showSplashMsg('修改出错')

#返回最后执行的SQL语句
print(db.lastSQL())

#判断是否使用的是PortgreSQL数据库
print(db.isUsePostgreSQL)

#按表名查询数据库中是否存在这个表
print(db.hasTable('t_mytable'))

```

关于数据库连接对象详细的调用接口请参考文档：[数据库转接对象](1-8-database)。

