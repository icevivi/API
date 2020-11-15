# 第二章 标准控件 - 继承自 QObject 的接口

biForm中的标准控件都是通过代理控件提供接口供 Python 脚本访问，代理控件都继承自 Qt 中的 QObject，因此也继承了一些 QObject 的接口，但与 Qt 中的 QObject 的接口并不完全一样，开放的接口以本文档为准。这些接口因为在 Python 中使用 dir() 都可以看到，所以本文对之进行一些解释，但其实一般用不上这些接口，只有 connect/disconnect/help/classname/objectname 等少量接口比较常用。

因为 biForm 中的标准控件并没有开放构造函数，因此也不能将它们做为基类进行继承，有些继承自 QObject 的虚函数虽然还是有定义，但不可能有派生类，因此也不需要使用。如果需要继承 QObject，需要使用 PythonQt 中的 QObject。关于 QObject 接口的详细说明都可以从 Qt 的官方文档中找到。

---

<h2 id=category>目录</h2>

- [属性](#属性)

- [成员函数](#成员函数)

---

## 属性

|属性|值类型|读写类型|说明|
| - | - | - | - |
|objectName|QString|可读 可写|对象名称|

### objectName

[返回目录](#category)

接口：QString objectName() const
void setObjectName(const QString& name) const

这个属性为对象名称。

调用示例：

``` python

#读取属性值
print(obj.objectName)
#修改属性值
obj.objectName='newname'
#或调用成员函数修改属性值
obj.setObjectName('newname')

```

## 成员函数

[返回目录](#category)

|                     函数                      |                                                               接口                                                               |             说明             |
| --------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | ---------------------------- |
| [blockSignals](#blockSignals)                 | bool blockSignals(bool block)                                                                                                    | 阻止发送信号                  |
| [childEvent](#childEvent)                     | [virtual protected] void childEvent(QChildEvent * event)                                                                         | 下级对象的事件                |
| [children](#children)                         | const QObjectList & children() const                                                                                             | 所有下级对象                  |
| [className](#className)                       | const char * className() const                                                                                                   | 类名称                       |
| [connect](#connect)                           | bool connect( const QByteArray& signal, PyObject* callable)                                                                      | 连接信号和Python函数          |
| [connect](#connect)                           | bool connect(const QByteArray& signal, QObject* receiver, const QByteArray& slot,  Qt::ConnectionType type = Qt::AutoConnection) | 连接信号和槽                  |
| [connect](#connect)                           | bool connect(QObject* sender, const QByteArray& signal, const QByteArray& slot,  Qt::ConnectionType type = Qt::AutoConnection)   | 连接信号和槽                  |
| [customEvent](#customEvent)                   | [virtual protected] void customEvent(QEvent * event)                                                                             | 自定义事件                    |
| [delete](#delete)                             | delete()                                                                                                                         | 删除                         |
| [disconnect](#disconnect)                     | bool disconnect(const QByteArray& signal, PyObject * callable = NULL)                                                            | 断开连接信号和Python函数      |
| [disconnect](#disconnect)                     | bool disconnect(const QByteArray& signal, QObject * receiver, const QByteArray& slot)                                            | 断开连接信号和槽              |
| [dumpObjectInfo](#dumpObjectInfo)             | void dumpObjectInfo()                                                                                                            | 输出对象信息                  |
| [dumpObjectTree](#dumpObjectTree)             | void dumpObjectTree()                                                                                                            | 输出对象信息树                |
| [dynamicPropertyNames](#dynamicPropertyNames) | QList<QByteArray> dynamicPropertyNames()                                                                                         | 动态属性的名称清单            |
| [event](#event)                               | [virtual] bool event(QEvent * e)                                                                                                 | 事件                         |
| [eventFilter](#eventFilter)                   | [virtual] bool eventFilter(QObject * watched, QEvent * event)                                                                    | 事件过滤器                    |
| [findChild](#findChild)                       | T findChild(const QString &name = QString(), Qt::FindChildOptions options = Qt::FindChildrenRecursively) const                   | 查找子对象                    |
| [findChildren](#findChildren)                 | QList<T> findChildren(const QRegExp &regExp, Qt::FindChildOptions options = Qt::FindChildrenRecursively) const                   | 查找子对象清单                |
| [findChildren](#findChildren)                 | QList<T> findChildren(const QString &name = QString(), Qt::FindChildOptions options = Qt::FindChildrenRecursively) const         | 查找子对象清单                |
| [help](#help)                                 | QString help()                                                                                                                   | 打印帮助信息                  |
| [inherits](#inherits)                         | bool inherits(const char * className)                                                                                            | 判断是否继承自某个类          |
| [installEventFilter](#installEventFilter)     | void installEventFilter(QObject * filterObj)                                                                                     | 设置事件过滤器对象            |
| [isSignalConnected](#isSignalConnected)       | [protected] bool isSignalConnected(const QMetaMethod &signal) const                                                              | 判断信号是否已连接            |
| [isWidgetType](#isWidgetType)                 | bool isWidgetType()                                                                                                              | 是否是控件类型                |
| [isWindowType](#isWindowType)                 | bool isWindowType()                                                                                                              | 是否是窗体类型                |
| [killTimer](#killTimer)                       | void killTimer(int  id)                                                                                                          | 停止定时器                    |
| [metaObject](#metaObject)                     | [virtual] QMetaObject * metaObject() const                                                                                       | 元对象                       |
| [moveToThread](#moveToThread)                 | void moveToThread(QThread * targetThread)                                                                                        | 移到其它线程                  |
| [parent](#parent)                             | QObject * parent() const                                                                                                         | 找上级对象                    |
| [property](#property)                         | QVariant property(const char * name)                                                                                             | 按名称返回对应的属性          |
| [removeEventFilter](#removeEventFilter)       | void removeEventFilter(QObject * obj)                                                                                            | 移除事件过滤器的设置          |
| [sender](#sender)                             | [protected] QObject * sender() const                                                                                             | 接收到信号时返回发送信号的对象 |
| [senderSignalIndex](#senderSignalIndex)       | [protected] int senderSignalIndex() const                                                                                        | 发送信号的属性索引            |
| [setParent](#setParent)                       | void setParent(QObject* parent)                                                                                                  | 设置父级对象                  |
| [setProperty](#setProperty)                   | bool setProperty(const char * name, const QVariant &value)                                                                       | 设置属性值                    |
| [signalsBlocked](#signalsBlocked)             | bool signalsBlocked() const                                                                                                      | 信号是否被阻止                |
| [startTimer](#startTimer)                     | int  startTimer(int  interval, Qt::TimerType  timerType = Qt::CoarseTimer)                                                       | 启动定时器                    |
| [thread](#thread)                             | QThread * thread() const                                                                                                         | 返回线程对象的指针            |
| [timerEvent](#timerEvent)                     | [virtual protected] void QObject::timerEvent(QTimerEvent * event)                                                                | 定时器事件处理                |
| [tr](#tr)                                     | QString tr(const char *sourceText, const char *disambiguation = Q_OBJECT, int n = Q_OBJECT)                                      | 翻译文本                     |

### blockSignals

[返回目录](#category)

调用接口：bool blockSignals(bool block)

如果 block 为 true，这个对象发出的信号会被阻止，即不会调用任何连接。如果 block 为 false，不会进行阻止。返回的值是之前 signalsBlocked() 返回的值。

需要注意的是， destroyed() 信号不会受这个影响，还是会被发出。

被阻止的信号直接就是取消了，不会进行缓存。

### childEvent

[返回目录](#category)

调用接口：[virtual protected] void childEvent(QChildEvent *event)

标准控件用不上这个虚函数。

### children

[返回目录](#category)

调用接口：const QObjectList & children() const

这个接口用于返回容器类控件中的子控件。因为 biForm 中标准控件在 Python 中只是指向QWidget控件的代理对象 ，所以即使是容器类QWidget控件，在 Python 脚本中访问的也不是QWidget本身，因此用 children() 并不能返回这个控件的所有子控件，这个方法返回的总是空的列表。上面的 childEvent 也是同理没有什么用处。

### className

[返回目录](#category)

调用接口：const char * className() const

返回控件的类名。比如一个标签控件，返回的结果就是'labelDelegate'。

### connect

[返回目录](#category)

调用接口： bool connect( const QByteArray& signal, PyObject* callable)
　　　　　 bool connect(const QByteArray& signal, QObject* receiver, const QByteArray& slot,  Qt::ConnectionType type = Qt::AutoConnection)
　　　　　 bool connect(QObject* sender, const QByteArray& signal, const QByteArray& slot,  Qt::ConnectionType type = Qt::AutoConnection)

连接信号和槽（或python函数），callable 直接使用函数名，不需要使用引号将其转为字符串，但 slot 要用字符串形式。详细说明请参考关于信号和槽的章节。

### customEvent

[返回目录](#category)

调用接口：[virtual protected] void customEvent(QEvent *event)

标准控件用不上这个接口。

### delete

[返回目录](#category)

调用接口：delete()

删除对象。注意对于 biForm 的标准控件来讲，这里只会删除 Python 中指向标准控件对应的QWidget的代理对象，并不能真正删除掉这些控件。

### disconnect

[返回目录](#category)

调用接口： bool disconnect(const QByteArray& signal, PyObject* callable = NULL)
　　　　　 bool disconnect(const QByteArray& signal, QObject* receiver, const QByteArray& slot) 

断开信号和槽（或python函数）的连接。callable 直接使用函数名，不需要使用引号将其转为字符串，但 slot 要用字符串形式。详细说明请参考关于信号和槽的章节。

### dumpObjectInfo

[返回目录](#category)

调用接口：void dumpObjectInfo()

输出对象的调试信息，在 biForm 中没有什么用，因为输出的信息在 biForm 中不会显示出来。

### dumpObjectTree

[返回目录](#category)

调用接口：void dumpObjectTree()

导出子对象的调试信息，在 biForm 中没有什么用，因为输出的信息在 biForm 中不会显示出来。

### dynamicPropertyNames

[返回目录](#category)

调用接口：QList<QByteArray> dynamicPropertyNames()

列出所有通过 setProperty() 动态添加的属性名称。

### event

[返回目录](#category)

调用接口：[virtual] bool event(QEvent *e)

标准控件用不上这个虚函数。

### eventFilter

[返回目录](#category)

调用接口：[virtual] bool eventFilter(QObject *watched, QEvent *event)

如果这个对象被其它对象指定为事件过滤器对象，则可以通过重写这个虚函数，将接管其它对象的事件进行处理。如果之后要停止继续处理，返回 True，否则返回 False。

biForm 的标准控件用不上这个虚函数。

### findChild

[返回目录](#category)

调用接口：T findChild(const QString &name = QString(), Qt::FindChildOptions options = Qt::FindChildrenRecursively) const

按对象的名称查找子对象，如果名称为空，则所有子对象都匹配。如果存在，返回对象，否则返回0。

缺省的查找选项使用Qt::FindChildrenRecursively，是递归的 ，即会查找子对象的子对象。如果不希望递归查找，使用 Qt::FindDirectChildrenOnly，就只查找第一级子对象。

如果有多项匹配的结果，只返回一个关系最直系的。如果有多个直系的匹配，返回的结果将不确定。在这种情况下使用 findChildren() 更合适。

biForm的标准控件是一个虚拟的代理对象类，所以一般并没有子对象，children()返回总是空的，这个函数一般对标准控件没有什么用处。

### findChildren

[返回目录](#category)

调用接口：QList<T> findChildren(const QString &name = QString(), Qt::FindChildOptions options = Qt::FindChildrenRecursively) const

按名称查找所有子对象，返回所有匹配的对象的列表。传入参数name若不指定，则返回所有子对象的列表。如果没有匹配的，返回空列表。

biForm的标准控件是一个虚拟的代理对象类，所以一般并没有子对象，children()返回总是空的，这个函数一般对标准控件没有什么用处。

### findChildren

[返回目录](#category)

调用接口：QList<T> findChildren(const QRegExp &regExp, Qt::FindChildOptions options = Qt::FindChildrenRecursively) const

使用正则表达式查找所有子对象。QRegExp的用法参考Qt文档。

### help

[返回目录](#category)

调用接口：QString help()

打印这个对象的帮助信息，帮助信息列出这个对象的属性、信号、槽、枚举变量、类名等。

### inherits

[返回目录](#category)

调用接口：bool inherits(const char *className)

如果这个对象是一个继承自 className 的类，则返回 True，否则返回 False。每个类都被认为是继承它自己所属的类，也会返回 True。

### installEventFilter

[返回目录](#category)

调用接口：void installEventFilter(QObject *filterObj)

指写其它控件做为这个对象的事件过滤器，这个对象触发的事件，都会由filterObj接管，filterObj可以重写 eventFilter 对这些事件进行处理。参考 eventFilter 的解释。

如果多次调用这个函数，只有最后一个才是有效的。

### isSignalConnected

[返回目录](#category)

调用接口：[protected] bool isSignalConnected(const QMetaMethod &signal) const

如果指定信号至少连接到了一个接收者，返回 True，否则返回 False。

signal 必须是这个对象的信号，否则可能产生未知的结果。

### isWidgetType

[返回目录](#category)

调用接口：bool isWidgetType()

如果这个对象是一个 QWidget 类或子类，返回 True，否则返回 False。

但是因为 biForm 的标准控件在对应的 QWidget 上加了一层代理类，所以都是返回 False，不推荐使用。

### isWindowType

[返回目录](#category)

调用接口：bool isWindowType()

如果这个对象是一个 QWindow 类或子类，返回 True，否则返回 False。

biForm 的标准控件调用这个函数都是返回 False。

### killTimer

[返回目录](#category)

调用接口：void killTimer(int  id)

停止标识值为 id 的定时器。

需要注意的是 biForm 中的标准控件也有 bool killTimer(int id) 函数，但是是有返回值的，成功会返回 True，否则返回 False。

### metaObject

[返回目录](#category)

调用接口：[virtual] QMetaObject * metaObject() const

返回这个对象的元对象的指针。元对象包含这个类的关于类的定义的一些信息，比如类名、超类名、属性、信号和槽。具体资料可以查看 Qt 的文档。

比如可以通过 obj.metaObject().className() 返回这个对象的类名。

### moveToThread

[返回目录](#category)

调用接口：void moveToThread(QThread *targetThread)

改变这个对象和其子对象的所属线程关系。如果这个对象有父对象，就不能被移到其它线程。

如果想要移到应用程序的主线程，使用 QApplication::instance()->thread()。

如果目标线程为零，所有这个对象和其子对象的事件处理将会停止。

biForm的标准控件不建议使用这个函数来修改其线程，因为标准控件在 Python 接口中暴露的只是一个继承自 QObject 的代理类，其对应的控件都继承自QWidget，将代理对象移到其它线程并不能影响对应的控件，也无太大意义，也有可能会产生意料不到的问题。

更多信息请参考 Qt 文档。

### parent

[返回目录](#category)

调用接口：QObject * parent() const

返回父对象的指针。

### property

[返回目录](#category)

调用接口：QVariant property(const char *name) 

返回对象的属性值，传入参数 name 指定属性名称。

如果没有这个属性，返回 None。

可以通过  metaObject() 和 dynamicPropertyNames() 获取所有可用属性的信息。

### removeEventFilter

[返回目录](#category)

调用接口：void removeEventFilter(QObject *obj)

移除这个对象之前指定的事件过滤器对象。如果之前并没有指定事件过滤器对象，调用会被忽略。

所以事件过滤器对象会在这个对象被销毁时自动移除。

移除过程总是安全的，即使是在事件正在被过滤器处理的时候。

### sender

[返回目录](#category)

调用接口：[protected] QObject * sender() const

如果在槽函数里调用，将返回发出信号的对象的指针，其它情况下返回0。指针只在槽函数被调用执行期间有效。

biForm的标准控件用不上这个函数，因为它需要在派生类的槽函数里通过它获取发送信号的对象，但因为标准控件无法做为基类，所以也用不上这个函数。

### senderSignalIndex

[返回目录](#category)

调用接口：[protected] int senderSignalIndex() const

在当前执行的槽函数中，返回发送信号的对象，其信号在它的属性中的序号。如果在被调用的槽函数外部调用这个函数，返回-1。

### setObjectName

[返回目录](#category)

调用接口：void setObjectName(const QString& name)

设置这个对象名称。biForm的标准控件会由运行时引擎设置 objectName，一般如无特殊要求，不需要通过调用这个函数修改 objectName。

### setParent

[返回目录](#category)

调用接口：void setParent(QObject *parent)

设置这个对象的父对象。不建议使用这个接口修改biForm的标准控件的父对象，除非你认为必须使用这个接口并能处理好随之产生的影响。

### setProperty

[返回目录](#category)

调用接口：bool setProperty(const char *name, const QVariant &value)

设置属性。name 是属性名，value是属性值。

如果这个属性已经是类定义中指定的属性，设置成功后返回 True，否则返回 False。如果新的属性，会做为动态属性添加到属性列表中，返回值为 False。

所有属性可以通过 metaObject() 和 dynamicPropertyNames() 获取。 

动态属性的值可以通过 property() 读取，也可以通过设置值为一个不合法的 QVariant 移除。修改动态属性的值会发起 QDynamicPropertyChangeEvent 事件。

以 "_q_" 开头的属性名保留做为内部使用。

### signalsBlocked

[返回目录](#category)

调用接口：bool signalsBlocked() const

如果信息被阻止，返回 True，否则返回 False。

### startTimer

[返回目录](#category)

调用接口：int  startTimer(int  interval, Qt::TimerType  timerType = Qt::CoarseTimer)

启动一个定时器，返回其标识值，或者在启动失败时返回0。

interval 为定时器触发的时间间隔，单位是毫秒。

虚函数 timerEvent() 会在定时器事件触发时被调用。如果有多个定时器，可以用 QTimerEvent::timerId() 返回是哪个定时器触发的定时器事件。

需要注意的是 biForm 中的标准控件也有 int startTimer(int interval) 函数，但没有timerType参数，所以不会使用这个接口。

而且因为biForm 的标准控件不能加以继承，所以无法重写timerEvent虚函数，所以这里这个函数也无法使用。biForm 的标准控件有自己的定时器处理接口，参考各控件的接口文档。

### thread

[返回目录](#category)

调用接口：QThread * thread() const

返回这个对象所在的线程。

### timerEvent

[返回目录](#category)

调用接口：[virtual protected] void timerEvent(QTimerEvent *event)

biForm 的标准控件用不上这个接口。biForm 的标准控件有自己的定时器处理接口，参考各控件的接口文档。

### tr

[返回目录](#category)

调用接口：QString tr(const char * sourceText, const char * disambiguation = Q_OBJECT, int n = Q_OBJECT)

返回经过翻译的文本。这个功能用于 C++ 写的Qt程序中的字符串进行翻译，在 biForm 中并有用这种方式来进行文本的翻译，所以这个函数没有什么用，总是返回输入的字符串。 关于Qt文本翻译的详细资料请参考Qt文档。

