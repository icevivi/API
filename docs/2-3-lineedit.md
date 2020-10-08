# 单行文本输入控件

单行文本控件用于输入文字。可以有多种格式，比如下图显示了几种不同样式：

![example](2-3-01.png)

## 继承

- [继承自QObject 的属性](2-1-qobject?id=属性)

|属性|值类型|读写类型|说明|
| - | - | - | - |
|objectName|QString|可读 可写|对象名称|

- [继承自QObject 的 成员函数](2-1-qobject?id=成员函数)

|函数|接口|说明|
| - | - | - |
|blockSignals|bool blockSignals(bool block)|阻止发送信号|
|childEvent|[virtual protected] void childEvent(QChildEvent *event)|下级对象的事件|
|children|const QObjectList & children() const|所有下级对象|
|className|const char * className() const|类名称|
|connect|bool connect( const QByteArray& signal, PyObject* callable)|连接信号和Python函数|
|connect|bool connect(const QByteArray& signal, QObject* receiver, const QByteArray& slot,  Qt::ConnectionType type = Qt::AutoConnection)|连接信号和槽|
|connect|bool connect(QObject* sender, const QByteArray& signal, const QByteArray& slot,  Qt::ConnectionType type = Qt::AutoConnection)|连接信号和槽|
|customEvent|[virtual protected] void customEvent(QEvent *event)|自定义事件|
|delete|delete()|删除|
|disconnect|bool disconnect(const QByteArray& signal, PyObject* callable = NULL)|断开连接信号和Python函数|
|disconnect|bool disconnect(const QByteArray& signal, QObject* receiver, const QByteArray& slot) |断开连接信号和槽|
|dumpObjectInfo|void dumpObjectInfo()|输出对象信息|
|dumpObjectTree|void dumpObjectTree()|输出对象信息树|
|dynamicPropertyNames|QList<QByteArray> dynamicPropertyNames()|动态属性的名称清单|
|event|[virtual] bool event(QEvent *e)|事件|
|eventFilter|[virtual] bool eventFilter(QObject *watched, QEvent *event)|事件过滤器|
|findChild|T findChild(const QString &name = QString(), Qt::FindChildOptions options = Qt::FindChildrenRecursively) const|查找子对象|
|findChildren|QList<T> findChildren(const QRegExp &regExp, Qt::FindChildOptions options = Qt::FindChildrenRecursively) const|查找子对象清单|
|findChildren|QList<T> findChildren(const QString &name = QString(), Qt::FindChildOptions options = Qt::FindChildrenRecursively) const|查找子对象清单|
|help|QString help()|打印帮助信息|
|inherits|bool inherits(const char *className)|判断是否继承自某个类|
|installEventFilter|void installEventFilter(QObject *filterObj)|设置事件过滤器对象|
|isSignalConnected|[protected] bool isSignalConnected(const QMetaMethod &signal) const|判断信号是否已连接|
|isWidgetType|bool isWidgetType()|是否是控件类型|
|isWindowType|bool isWindowType()|是否是窗体类型|
|killTimer|void killTimer(int  id)|停止定时器|
|metaObject|[virtual] QMetaObject * metaObject() const|元对象|
|moveToThread|void moveToThread(QThread *targetThread)|移到其它线程|
|parent|QObject * parent() const|找上级对象|
|property|QVariant property(const char *name) |按名称返回对应的属性|
|removeEventFilter|void removeEventFilter(QObject *obj)|移除事件过滤器的设置|
|sender|[protected] QObject * sender() const||
|senderSignalIndex|[protected] int senderSignalIndex() const|发送信号的属性索引|
|setParent|void setParent(QObject *parent)|设置上级对象|
|setProperty|bool setProperty(const char *name, const QVariant &value)|设置属性值|
|signalsBlocked|bool signalsBlocked() const|信号是否被阻止|
|startTimer|int  startTimer(int  interval, Qt::TimerType  timerType = Qt::CoarseTimer)|启动定时器|
|thread|QThread * thread() const|返回线程对象的指针|
|timerEvent|[virtual protected] void timerEvent(QTimerEvent *event)|定时器超时事件|
|tr|QString tr(const char *sourceText, const char *disambiguation = Q_OBJECT, int n = Q_OBJECT)|翻译文本|

- [继承自widgetDelegateBase的属性](2-2-base?id=属性)

|属性|值类型|读写类型|说明|
| - | - | - | - |
|background|QColor|可读 可写|背景色|
|borderColor|QColor|可读 可写|边框颜色|
|borderStyle|int|可读 可写|边框样式|
|borderWidth|int|可读 可写|边框宽度|
|dragEnabled|bool|可读 可写|是否允许拖动内容|
|enabled|bool|可读 可写|是否可用|
|fillStyle|int|可读 可写|填充类型|
|focus|bool|可读 可写|是否获得输入焦点|
|font|QFont|可读 可写|字体|
|foreground|QColor|可读 可写|前景色|
|geometry|QRect|可读 可写|位置尺寸|
|hAlign|int|可读 可写|水平方向对齐方式|
|height|int|可读 可写|高度|
|maxheight|int|可读 可写|最大高度|
|maxwidth|int|可读 可写|最大宽度|
|minheight|int|可读 可写|最小高度|
|minwidth|int|可读 可写|最小宽度|
|pos|QPoint|可读 可写|位置|
|rect|QRect|只读 |边框矩形尺寸|
|reloadWhenCreateNew|bool|可读 可写|表单新建时是否重新加载|
|showBorder|bool|可读 可写|是否显示边框|
|showOnForm|bool|可读 可写|表单上是否可见|
|showOnPDF|bool|可读 可写|PDF输出时是否可见|
|showWhenPrint|bool|可读 可写|打印时是否可见|
|size|QSize|可读 可写|尺寸|
|statusTip|QString|可读 可写|状态栏提示文本|
|tabOrder|int|只读 |tab键顺序|
|tag|QVariant|可读 可写|备用属性|
|toolTip|QString|可读 可写|工具提示|
|updatesEnabled|bool|可读 可写|是否允许刷新|
|vAlign|int|可读 可写|垂直方向对齐方式|
|visible|bool|可读 可写|是否可见|
|whatsThis|QString|可读 可写|“这是什么”提示文本|
|width|int|可读 可写|宽度|
|x|int|可读 可写|x方向位置|
|y|int|可读 可写|y方向位置|

- [继承自widgetDelegateBase的成员函数](2-2-base?id=成员函数)

## 单行文本输入控件自有的属性

- ### 属性：caption （类型：QString 可读 可写）

标题显示的文字。

| |调用方法|
| - | - |
|读取|QString caption const|
|修改|void setCaption( const QString &caption ) const|

- ### 属性：editorFont （类型：QFont 可读 可写）

文本编辑控件的字体。注意 font 属性指标题的字体，editorFont才是输入文字的控件的字体。

| |调用方法|
| - | - |
|读取|QFont editorFont const|
|修改|void setEditorFont( const QFont &editorFont ) const|

- ### 属性：editorBackColor （类型：QColor 可读 可写）

文本输入控件的背景色，只在填充属性为“填充”时有效。

| |调用方法|
| - | - |
|读取|QColor editorBackColor const|
|修改|void setEditorBackColor( const QColor &editorBackColor ) const|

- ### 属性：editorForeColor （类型：QColor 可读 可写）

文本输入控件的前景色。

| |调用方法|
| - | - |
|读取|QColor editorForeColor const|
|修改|void setEditorForeColor( const QColor &editorForeColor ) const|

- ### 属性：editorBorderColor （类型：QColor 可读 可写）

文本输入控件边框颜色。

| |调用方法|
| - | - |
|读取|QColor editorBorderColor const|
|修改|void setEditorBorderColor( const QColor &editorBorderColor ) const|

- ### 属性：margin （类型：int 可读 可写）

边界宽度。

| |调用方法|
| - | - |
|读取|int margin const|
|修改|void setMargin( int margin ) const|

- ### 属性：maxLength （类型：int 可读 可写）

输入文本最大长度。

| |调用方法|
| - | - |
|读取|int maxLength const|
|修改|void setMaxLength( int maxLength ) const|

- ### 属性：editorBorderStyle （类型：int 可读 可写）

文本编辑器边框类型。

| |调用方法|
| - | - |
|读取|int editorBorderStyle const|
|修改|void setEditorBorderStyle( int editorBorderStyle ) const|
| |**editorBorderStyle取值：**|
| |pub.NOFRAME 没有边框|
| |pub.UNDERLINE 下划线|
| |pub.RECTANGLE 矩形边框|

- ### 属性：captionPosition （类型：int 可读 ）

标题所在位置。

| |调用方法|
| - | - |
|读取|int captionPosition const|

- ### 属性：shadow （类型：int 可读 可写）

输入框边框特效样式。

| |调用方法|
| - | - |
|读取|int shadow const|
|修改|void setShadow( int shadow ) const|
| |**shadow取值：**|
| |pub.PLAIN 平的|
| |pub.RAISED 上凸|
| |pub.SUNKEN 下陷|

- ### 属性：editorFillStyle （类型：int 可读 可写）

输入框背景填充样式。设置为“透明”时，背景色无效。

| |调用方法|
| - | - |
|读取|int editorFillStyle const|
|修改|void setEditorFillStyle( int editorFillStyle ) const|
| |**editorFillStyle的值：**|
| |- pub.FILLED_BACKGROUND 填充|
| |- pub.TRANSPARENT_BACKGROUND 透明|

- ### 属性：isPWD （类型：bool 可读 可写）

是否是密码输入控件。密码输入控件会显示特殊字符替代输入的文字。

| |调用方法|
| - | - |
|读取|bool isPWD const|
|修改|void setIsPWD( bool isPWD ) const|

- ### 属性：inputMask （类型：QString 可读 可写）

输入掩码。详细用法参考Qt文档。

| |调用方法|
| - | - |
|读取|QString inputMask const|
|修改|void setInputMask( const QString &inputMask ) const|

- ### 属性：text （类型：QString 可读 可写）

输入的文字。

| |调用方法|
| - | - |
|读取|QString text const|
|修改|void setText( const QString &text ) const|

- ### 属性：displaytext （类型：QString 可读 ）

输入框显示的文字。

| |调用方法|
| - | - |
|读取|QString displaytext const|

- ### 属性：defaultVal （类型：QString 可读 可写）

缺省文本。

| |调用方法|
| - | - |
|读取|QString defaultVal const|
|修改|void setDefaultVal( const QString &defaultVal ) const|

- ### 属性：editorVAlign （类型：int 可读 可写）

输入框文本垂直方向对齐方式。

| |调用方法|
| - | - |
|读取|int editorVAlign const|
|修改|void setEditorVAlign( int editorVAlign ) const|
| |**editorVAlign取值：**|
| |pub.ALIGNTOP 向上对齐|
| |pub.ALIGNBOTTOM 向下对齐|
| |pub.ALIGNVCENTER 垂直居中对齐|

- ### 属性：editorHAlign （类型：int 可读 可写）

输入框文本水平方向对齐方式。

| |调用方法|
| - | - |
|读取|int editorHAlign const|
|修改|void setEditorHAlign( int editorHAlign ) const|
| |**editorHAlign取值：**|
| |pub.ALIGNLEFT 向左对齐|
| |pub.ALIGNRIGHT 向右对齐|
| |pub.ALIGNHCENTER 水平居中对齐|
| |pub.ALIGNJUSTIFY 水平分散对齐|

- ### 属性：readOnly （类型：bool 可读 可写）

是否只读。只读的文本输入控件可以通过脚本修改其中的文字，但不允许用户修改。

| |调用方法|
| - | - |
|读取|bool readOnly const|
|修改|void setReadOnly( bool readOnly ) const|

