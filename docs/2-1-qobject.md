# QObject控件

biForm中的控件都继承自 Qt 中的 QObject，QObject 提供的接口的帮助文档都可以从 Qt 的官方文档中找到，我们这里就不一一详细解释。一般在 biForm 中使用标准控件，也很少用到这些接口，本文只重点讲几个可能用得到的接口。

### bool blockSignals(bool block)

如果 block 为 true，这个对象发出的信号会被阻止，即不会调用任何连接。如果 block 为 false，不会进行阻止。返回的值是之前 signalsBlocked() 返回的值。

需要注意的是， destroyed() 信号不会受这个影响，还是会被发出。

被阻止的信号直接就是取消了，不会进行缓存。

### [virtual protected] void childEvent(QChildEvent *event)

标准控件用不上这个接口。

### const QObjectList & children() const

这个接口用于返回容器类控件中的子控件。因为 biForm 中标准控件在 Python 中只是指向QWidget控件的代理对象 ，所以即使是容器类QWidget控件，在 Python 脚本中访问的也不是QWidget本身，因此用 children() 并不能返回这个控件的所有子控件，这个方法返回的总是空的列表。上面的 childEvent 也是同理没有什么用处。

### const char * className() const

返回控件的类名，比如一个标签控件，返回的结果就是'labelDelegate'。

### connect

连接信号和槽，具体参考关于信号和槽的章节。

### customEvent


### delete
disconnect
dumpObjectInfo
dumpObjectTree
dynamicPropertyNames
event
eventFilter
findChild
findChildren
help
inherits
installEventFilter
isSignalConnected
isWidgetType
isWindowType
metaObject
moveToThread
parent
property
removeEventFilter
sender
senderSignalIndex
setObjectName
setParent
setProperty
signalsBlocked
thread
timerEvent
tr

