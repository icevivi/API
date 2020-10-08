# 单行文本输入控件

单行文本控件用于输入文字。可以有多种格式，比如下图显示了几种不同样式：

![example](2-3-01.png)

---
## 目录

- [继承的属性和函数](id=继承的属性和函数)

- [自有属性](id=单行文本输入控件自有属性)

- [自有成员函数](id=单行文本输入控件自有成员函数)

- [信号](id=单行文本输入控件的信号)

- [可编辑函数](id=可编辑函数)
---

## 继承的属性和函数

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
|sender|[protected] QObject * sender() const|接收到信号时返回发送信号的对象|
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

|函数|接口|说明|
| - | - | - |
|grab|QPixmap grab() const|截取控件图像|
|hide|void hide() const|隐藏|
|hideBalloon|void hideBalloon() const|隐藏汽泡控件|
|isNull|bool isNull() const|是否为空|
|killAllTimer|void killAllTimer() const|关闭所有定时器|
|killTimer|bool killTimer ( int id ) const|关闭写时器|
|lower|void lower() const|置于底层|
|quitFullScreen|void quitFullScreen()|退出全屏|
|raise|void raise() const|置于顶层|
|repaint|void repaint()|重画画|
|setDisabled|void setDisabled(bool disabled) const|设置可用状态|
|setFullScreen|void setFullScreen()|全屏|
|setSizePolicy|void setSizePolicy(QSizePolicy policy) const|设置尺寸缩放规则|
|setStyleSheet|setStyleSheet(const QString& styleSheet) const|设置样式表|
|show|void show() const|显示|
|showBalloon|void showBalloon(const QString& msg) const|显示汽泡提示文本|
|showValidBalloon|void showValidBalloon() const|显示有效性汽泡提示|
|startSingleShot|void startSingleShot ( int interval ) const|启动单次定时器|
|startTimer|int startTimer ( int interval ) const|启动定时器|
|timers|QStringList timers() const|所有定时器的标识号清单|
|toBottom|void toBottom() const|置于底层|
|toTop|void toTop() const|置于顶层|

## 单行文本输入控件自有属性

|属性|值类型|读写类型|说明|
| - | - | - | - |
|caption|QString|可读 可写|标题文本|
|captionPosition|int|可读 |标题位置|
|defaultVal|QString|可读 可写|缺省值|
|displaytext|QString|可读 |显示文本|
|editorBackColor|QColor|可读 可写|编辑器背景色|
|editorBorderColor|QColor|可读 可写|编辑器边框颜色|
|editorBorderStyle|int|可读 可写|编辑器边框样式|
|editorFillStyle|int|可读 可写|编辑器填充样式|
|editorFont|QFont|可读 可写|编辑器字体|
|editorForeColor|QColor|可读 可写|编辑器前景色|
|editorHAlign|int|可读 可写|编辑器水平对齐方式|
|editorVAlign|int|可读 可写|编辑器垂直对齐方式|
|inputMask|QString|可读 可写|输入掩码|
|isPWD|bool|可读 可写|是否显示密码格式|
|margin|int|可读 可写|边界宽度|
|maxLength|int|可读 可写|输入文字最大长度|
|readOnly|bool|可读 可写|是否只读|
|shadow|int|可读 可写|边框特效样式|
|text|QString|可读 可写|输入的文本|

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

## 单行文本输入控件自有成员函数

|函数|接口|说明|
| - | - | - |
|clear|void clear()  const|清除输入的文本|
|copy|void copy() const|复制选中的文本|
|cut|void cut()  const|剪切选中的文本|
|paste|void paste()  const|从剪切板粘贴文本|
|redo|void redo()  const|重复上一步撤消的操作|
|undo|void undo()  const|撤消上一步操作|
|selectAll|void selectAll() const|选择所有文本|
|setText |void setText ( const QString & text ) const|设置输入框内的文本|
|setIsPWD|void setIsPWD(bool isPWD) const|设置是否显示密码|
|setDefaultVal|void setDefaultVal(const QString &text) const|设置缺省值|
|setInputMask|void setInputMask(const QString &mask) const|设置输入掩码|
|setEditorVAlign|void setEditorVAlign(int valign) const|设置编辑器垂直方向对齐方式（valign取值：pub.ALIGNTOP 向上对齐；pub.ALIGNBOTTOM 向下对齐；pub.ALIGNVCENTER 垂直居中对齐）|
|setEditorHAlign|void setEditorHAlign(int halign) const|设置编辑器水平方向对齐方式（halign取值：pub.ALIGNLEFT 向左对齐；pub.ALIGNRIGHT 向右对齐；pub.ALIGNHCENTER 水平居中对齐；pub.ALIGNJUSTIFY 水平分散对齐）|
|setReadOnly|void setReadOnly(bool readonly) const|设置是否只读|
|setIntValidator|void setIntValidator(intValidatorDelegate* validator) const|设置整数输入校验器|
|setDoubleValidator|void setDoubleValidator(doubleValidatorDelegate* validator) const|设置双精度小数输入校验器|

## 单行文本输入控件的信号

|信号|接口|说明|
| - | - | - |
|cursorPositionChanged|void cursorPositionChanged ( int oldp, int newp ) |光标位置发生改变时发出此信号。|
|editingFinished|void editingFinished () |编辑完成时发出此信号 。通常是在按下回车键或控件失去焦点时标识着编辑已完成。如果设置了校验器或输入掩码，只在符合输入规范（返回QValidator::Acceptable）时才会触发此信号。|
|returnPressed|void returnPressed ()	 |输入回车键时发出此信号。如果设置了校验器或输入掩码，只在符合输入规范（返回QValidator::Acceptable）时才会触发此信号。|
|selectionChanged|void selectionChanged () 	 |选择的文本范围发生变化时发出此信号。|
|textChanged|void textChanged ( const QString & text ) |文本被修改时发出此信号。与textEdited不同，通过程序修改文本内容也会发出此信号。|
|textEdited|void textEdited ( const QString & text )  |文本被操作者编辑修改时发出此信号。通过程序修改文本内容不会发出此信号。|

## 可编程函数

在 biForm 中，每个控件的属性编辑器里，有一个分类“脚本”，是开放给开发者的，可由开发者写入自己的 Python 代码，它们运行时都是以 Python 函数的形式存在。

?> PFF运行时引擎调用这些函数时，都是返回为可变数据类型（QVariant），然后再按使用的场合转换成相应的数据类型。比如“缺省值”的返回值会用于赋值给文本输入控件的字符串属性text，所以运行时引擎会尝试将返回值转换为字符串型，如果不能转换成功，会转换为空字符串。虽然运行时引擎支持这种转换，但建议尽量在程序中使用合适的数据类型，以避免转换出现不可预期的结果。

?> 这些函数可以直接在其它脚本处通过函数名进行调用，比如控件名为 lineedit，可以在其它地方使用 v=lineedit_validator() 调用其“校验规则”函数，从而可以复用这段程序。这种调用不会影响到 lineedit 控件的行为。但我们一般不建议开发者这样使用，因为函数名与控件名相关，如果需要修改控件名，相关的脚本都要进行修改。如果一定需要复用这部分程序，更好的做法是在表单的“公用模块”里定义表单级的公用函数后再在各处进行调用。

单行文本输入控件开放了以下几个可编写 Python 脚本的函数：

- ### 可编程函数：缺省值

|内容|说明|
| - | - |
|函数名|控件名_default|
|传入参数|无|
|返回值|输入框中文本内容的初始值|
|建议的返回值类型|字符串型|
|使用规则|控件初始化后、新建空白表单后输入框中的文本会还原成初始值。|

- ### 可编程函数：显示格式

|内容|说明|
| - | - |
|函数名|控件名_format|
|传入参数|输入框中的文本|
|返回值|转换格式后要显示的文本|
|建议的返回值类型|字符串型|
|使用规则|单行文本输入框中输入的内容和显示的内容可以不一样，这个函数用来将输入的内容转换格式后显示，将在用户结束输入后调用此函数，通过程序修改文本内容也会调用此函数。|

- ### 可编程函数：校验规则

|内容|说明|
| - | - |
|函数名|控件名_validator|
|传入参数|输入框中的文本|
|返回值|输入值是否合法|
|建议的返回值类型|布尔型|
|使用规则|如果输入值满足要求，返回True，否则返回False。这个函数会在完成输入后被调用。手工输入和程序修改都会调用此函数。|

- ### 可编程函数：鼠标进入时

|内容|说明|
| - | - |
|函数名|控件名_enter|
|传入参数|无|
|返回值|无|
|建议的返回值类型|无|
|使用规则|鼠标光标进入到这个控件时调用此函数。|

- ### 可编程函数：鼠标离开时

|内容|说明|
| - | - |
|函数名|控件名_leaver|
|传入参数|无|
|返回值|无|
|建议的返回值类型|无|
|使用规则|鼠标光标离开这个控件时调用此函数。|

- ### 可编程函数：大小改变时

|内容|说明|
| - | - |
|函数名|控件名_resize|
|传入参数|无|
|返回值|无|
|建议的返回值类型||
|使用规则|控件大小改变时调用此函数。|

- ### 可编程函数：拖曳进入时

|内容|说明|
| - | - |
|函数名|控件名_dargEnter|
|传入参数1|format:元数据的格式列表，以列表类型传入|
|传入参数2|data:元数据的内容|
|传入参数3|dx:鼠标位置x坐标值|
|传入参数4|dy:鼠标位置y坐标值|
|返回值|是否接受拖曳进入|
|建议的返回值类型|布尔|
|使用规则|当从外部拖曳一些内容进入到这个控件时，会调用此函数。不接受拖曳的控件不会调用此函数。通过脚本判断是否接受拖曳，如果接受，返回 True，否则返回False。返回 True 之后，程序将会调用“当拖曳放下时”函数。|


- ### 可编程函数：拖曳放下时

|内容|说明|
| - | - |
|函数名|控件名_drop|
|传入参数1|format:元数据的格式列表，以列表类型传入|
|传入参数2|data:元数据的内容|
|传入参数3|dx:鼠标位置x坐标值|
|传入参数4|dy:鼠标位置y坐标值|
|返回值|是否接受拖曳进入|
|建议的返回值类型|布尔|
|使用规则|当从外部拖曳放下一些内容到这个控件时调用此函数。当接受拖曳放下时，返回 True，否则返回 False。|

- ### 可编程函数：生成元数据

|内容|说明|
| - | - |
|函数名|控件名_mimedata|
|传入参数|无|
|返回值|这个控件的元数据|
|建议的返回值类型|列表|
|使用规则|这个函数会在拖曳这个控件时调用。返回的值必须是一个列表，类似于 [['text/plain','the drag text']]，列表中每个元素有两个子元素，第一个是数据的格式，第二个是数据的内容。|

- ### 可编程函数：获得焦点时

|内容|说明|
| - | - |
|函数名|控件名_getfocus|
|传入参数|无|
|返回值|无|
|建议的返回值类型|无|
|使用规则|在控件获得输入焦点时调用此函数。|

- ### 可编程函数：失去焦点时

|内容|说明|
| - | - |
|函数名|控件名_lostfocus|
|传入参数|无|
|返回值|无|
|建议的返回值类型|无|
|使用规则|在控件失去输入焦点时调用这个函数。|

- ### 可编程函数：单次定时器超时时

|内容|说明|
| - | - |
|函数名|控件名_singleshot|
|传入参数|无|
|返回值|无|
|建议的返回值类型|无|
|使用规则|在调用 ```控件名.startSingleShot(毫秒值)``` 后，时间点到达后会调用此函数，单次定时器只会调用一次就会停止。|

- ### 可编程函数：定时器超时时

|内容|说明|
| - | - |
|函数名|控件名_timeout|
|传入参数|timerid：定时器的ID值|
|返回值|无|
|建议的返回值类型|无|
|使用规则|在调用 ```控件名.startTimer(毫秒值)``` 后，时间点到达后会调用此函数。定时器会重复超时，重复调用此函数，直到使用 killTimer 将定时器停止。|


