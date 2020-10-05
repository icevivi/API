# 继承自 QObject 的接口

biForm中的标准控件都继承自 Qt 中的 QObject，QObject 接口的详细说明都可以从 Qt 的官方文档中找到。

biForm中标准控件的接口继承自QObject的部分与 Qt 中的 QObject 的接口并不完全一样，有些接口也不推荐在使用标准控件时使用。

### bool blockSignals(bool block)

如果 block 为 true，这个对象发出的信号会被阻止，即不会调用任何连接。如果 block 为 false，不会进行阻止。返回的值是之前 signalsBlocked() 返回的值。

需要注意的是， destroyed() 信号不会受这个影响，还是会被发出。

被阻止的信号直接就是取消了，不会进行缓存。

### [virtual protected] void childEvent(QChildEvent *event)

标准控件用不上这个虚函数。如果是想用 Python 脚本定义一个类继承 Qt 中 QObject 或其派生类，可以重写这个虚函数以处理子控件的添加、删除、修改等事件。

### const QObjectList & children() const

这个接口用于返回容器类控件中的子控件。因为 biForm 中标准控件在 Python 中只是指向QWidget控件的代理对象 ，所以即使是容器类QWidget控件，在 Python 脚本中访问的也不是QWidget本身，因此用 children() 并不能返回这个控件的所有子控件，这个方法返回的总是空的列表。上面的 childEvent 也是同理没有什么用处。

### const char * className() const

返回控件的类名。比如一个标签控件，返回的结果就是'labelDelegate'。

### bool connect( const QByteArray& signal, PyObject* callable)
### bool connect(const QByteArray& signal, QObject* receiver, const QByteArray& slot,  Qt::ConnectionType type = Qt::AutoConnection)
### bool connect(QObject* sender, const QByteArray& signal, const QByteArray& slot,  Qt::ConnectionType type = Qt::AutoConnection)

连接信号和槽（或python函数），具体参考关于信号和槽的章节。

### [virtual protected] void customEvent(QEvent *event)

子类可以通过重写这个虚函数处理自定义事件，传入参数是一个类型设置为QEvent::User的QEvent对象指针。

### delete()

删除对象。注意对于 biForm 的标准控件来讲，这里只会删除 Python 中指向标准控件对应的QWidget的指针，并不能真正删除掉这些控件。

### bool disconnect(const QByteArray& signal, PyObject* callable = NULL)
### bool disconnect(const QByteArray& signal, QObject* receiver, const QByteArray& slot) 

断开信号和槽（或python函数）的连接，具体参考关于信号和槽的章节。

### void dumpObjectInfo()

导出对象的调试信息，在 biForm 中没有什么用。

### void dumpObjectTree()

导出子对象的调试信息，在 biForm 中没有什么用。

### QList<QByteArray> dynamicPropertyNames()

列出所有通过 setProperty() 动态添加的属性名称。

### [virtual] bool QObject::event(QEvent *e)

这个虚函数用于接收一个对象的所有事件并进行处理。如果事件在此处被处理了返回 True。对于在此处不进行处理的事件，需要调用上级控件的事件处理以确保所有事件都会被处理。

### [virtual] bool eventFilter(QObject *watched, QEvent *event)

如果这个对象被其它对象指定为事件过滤器对象，则可以通过重写这个虚函数，将接管其它对象的事件进行处理。如果之后要停止继续处理，返回 True，否则返回 False。

### T findChild(const QString &name = QString(), Qt::FindChildOptions options = Qt::FindChildrenRecursively) const

按对象的名称查找子对象，如果名称为空，则所有子对象都匹配。如果存在，返回对象，否则返回0。

缺省的查找选项使用Qt::FindChildrenRecursively，是递归的 ，即会查找子对象的子对象。如果不希望递归查找，使用 Qt::FindDirectChildrenOnly，就只查找第一级子对象。

如果有多项匹配的结果，只返回一个关系最直系的。如果有多个直系的匹配，返回的结果将不确定。在这种情况下使用 findChildren() 更合适。

biForm的标准控件是一个虚拟的代理对象类，所以一般并没有子对象，children()返回总是空的，这个函数一般对标准控件没有什么用处。

### QList<T> findChildren(const QString &name = QString(), Qt::FindChildOptions options = Qt::FindChildrenRecursively) const

按名称查找所有子对象，返回所有匹配的对象的列表。传入参数name若不指定，则返回所有子对象的列表。如果没有匹配的，返回空列表。

biForm的标准控件是一个虚拟的代理对象类，所以一般并没有子对象，children()返回总是空的，这个函数一般对标准控件没有什么用处。

### QList<T> findChildren(const QRegExp &regExp, Qt::FindChildOptions options = Qt::FindChildrenRecursively) const

使用正则表达式查找所有子对象。QRegExp的用法参考Qt文档。

### QString help()

打印这个对象的帮助信息，帮助信息列出这个对象的属性、信号、槽、枚举变量、类名等。

### bool inherits(const char *className)

如果这个对象是一个继承自 className 的类，则返回 True，否则返回 False。每个类都被认为是继承它自己所属的类，也会返回 True。

### void installEventFilter(QObject *filterObj)

指写其它控件做为这个对象的事件过滤器，这个对象触发的事件，都会由filterObj接管，filterObj可以重写 eventFilter 对这些事件进行处理。参考 eventFilter 的解释。

如果多次调用这个函数，只有最后一个才是有效的。

### [protected] bool isSignalConnected(const QMetaMethod &signal) const

如果指定信号至少连接到了一个接收者，返回 True，否则返回 False。

signal 必须是这个对象的信号，否则可能产生未知的结果。

### bool isWidgetType()

如果这个对象是一个 QWidget 类或子类，返回 True，否则返回 False。

但是因为 biForm 的标准控件在对应的 QWidget 上加了一层代理类，所以都是返回 False，不推荐使用。

### bool isWindowType()

如果这个对象是一个 QWindow 类或子类，返回 True，否则返回 False。

biForm 的标准控件调用这个函数都是返回 False，不推荐使用。

### void killTimer(int  id)

停止标识值为 id 的定时器。

需要注意的是 biForm 中的标准控件也有 bool killTimer(int id) 函数，但是是有返回值的，成功会返回 True，否则返回 False。

### [virtual] QMetaObject * metaObject() const

返回这个对象的元对象的指针。元对象包含这个类的关于类的定义的一些信息，比如类名、超类名、属性、信号和槽。具体资料可以查看 Qt 的文档。

比如可以通过 obj.metaObject().className() 返回这个对象的类名。

### void QObject::moveToThread(QThread *targetThread)

改变这个对象和其子对象的所属线程关系。如果这个对象有父对象，就不能被移到其它线程。

如果想要移动应用程序的主线程，使用 QApplication::instance()->thread()。

如果目标线程为零，所有这个对象和其子对象的事件处理将会停止。

更多信息请参考 Qt 文档。

### QObject * parent() const

返回父对象的指针。

### QVariant property(const char *name) 

返回对象的属性值，传入参数 name 指定属性名称。

如果没有这个属性，返回 None。

可以通过  metaObject() 和 dynamicPropertyNames() 获取所有可用属性的信息。

### void removeEventFilter(QObject *obj)

移除这个对象之前指定的事件过滤器对象。如果之前并没有指定事件过滤器对象，调用会被忽略。

所以事件过滤器对象会在这个对象被销毁时自动移除。

移除过程总是安全的，即使是在事件正在被过滤器处理的时候。

### [protected] QObject * sender() const

如果在槽函数里调用，将返回发出信号的对象的指针，其它情况下返回0。指针只在槽函数被调用执行期间有效。

### [protected] int senderSignalIndex() const

在当前执行的槽函数中，返回发送信号的对象，其信号在它的属性中的序号。如果在被调用的槽函数外部调用这个函数，返回-1。

### void setObjectName(const QString& name)

设置这个对象名称。

### void setParent(QObject *parent)

设置这个对象的父对象。

### bool setProperty(const char *name, const QVariant &value)

设置属性。name 是属性名，value是属性值。

如果这个属性已经是类定义中指定的属性，设置成功后返回 True，否则返回 False。如果新的属性，会做为动态属性添加到属性列表中，返回值为 False。

所有属性可以通过 metaObject() 和 dynamicPropertyNames() 获取。 

动态属性的值可以通过 property() 读取，也可以通过设置值为一个不合法的 QVariant 移除。修改动态属性的值会发起 QDynamicPropertyChangeEvent 事件。

以 "_q_" 开头的属性名保留做为内部使用。

### bool signalsBlocked() const

如果信息被阻止，返回 True，否则返回 False。

### int  startTimer(int  interval, Qt::TimerType  timerType = Qt::CoarseTimer)

启动一个定时器，返回其标识值，或者在启动失败时返回0。

interval 为定时器触发的时间间隔，单位是毫秒。

虚函数 timerEvent() 会在定时器事件触发时被调用。如果有多个定时器，可以用 QTimerEvent::timerId() 返回是哪个定时器触发的定时器事件。

需要注意的是 biForm 中的标准控件也有 int startTimer(int interval) 函数，但没有timerType参数，所以不会使用这个接口。

### QThread * thread() const

返回这个对象所在的线程。

### [virtual protected] void timerEvent(QTimerEvent *event)

子类可以重写这个虚函数，处理这个对象的定时器事件。

QTimer对象提供关于定时器更高级的接口和信息。

biForm 的标准控件有自己的定时器处理接口，不建议使用这个虚函数。如果需要继承 QObject，也建议使用 QTimer 处理定时器进行处理。

### QString tr(const char *sourceText, const char *disambiguation = Q_OBJECT, int n = Q_OBJECT)

返回经过翻译的文本。关于Qt文本翻译的详细资料请参考Qt文档。

