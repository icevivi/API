# 基类widgetDelegateBase

biForm 中的标准控件都继承自 widgetDelegateBase，有共同的一些属性和方法。

## Python 脚本调用接口时的注意事项

本文中属性的调用方法采用 C++ 的语法，但在 biForm 中用 Python 脚本调用时，需要注意语法格式。

读取属性时，如```const QRect & geometry()```，在 Python 脚本调用时就应该是```obj.geometry```。注意不要带“()”。

修改属性时，如```void setGeometry(const QRect& rect)```，在 Python 脚本调用时，需要先导入 QRect ：

``` python

#先导入 QRect
from PythonQt.Qt import QRect
#可以调用函数对属性赋值
this.label.setGeometry(QRect(10,10,100,30))
#也可以直接对属性赋值
this.label.geometry=QRect(10,10,100,30)

```

## 外观相关的属性

- ### 属性：geometry （类型：QRect 可读 可写）

控件相对于它的上级控件（父对象）的几何尺寸

| |调用方法|
| - | - |
|读取|const QRect & geometry()|
|修改|void setGeometry(const QRect& rect)|

- ### 属性：x （类型：int 可读 可写）

控件相对于上级控件的位置坐标的 x 值。

| |调用方法|
| - | - |
|读取|int x()|
|修改|void setX(const int x)|

- ### 属性：y （类型：int 可读 可写）

控件相对于上级控件的位置坐标的 y 值。

| |调用方法|
| - | - |
|读取|int y()|
|修改|void setY(const int y)|

- ### 属性：width （类型：int 可读 可写）

控件的宽度。

| |调用方法|
| - | - |
|读取|int width()|
|修改|void setWidth(const int w)|

- ### 属性：height （类型：int 可读 可写）

控件的高度。

| |调用方法|
| - | - |
|读取|int height()|
|修改|void setHeight(const int h)|

- ### 属性：pos （类型：QPoint 可读 可写）

控件左上角相对于上级控件的位置。

| |调用方法|
| - | - |
|读取|QPoint pos()|
|修改|void setPos(const QPoint h)|

- ### 属性：size （类型：QSize 可读 可写）

控件的尺寸。

| |调用方法|
| - | - |
|读取|QSize size()|
|修改|void setSize(const QSize size)|

- ### 属性：rect （类型：QRect 只读）

控件相对于上级控件的矩形区域，等于 QRect(0,0,width(),height())。

| |调用方法|
| - | - |
|读取|const QRect rect()|
|修改|void setRect(const QSize& rect)|

- ### 属性：vAlign （类型：int 可读 可写）

垂直方向的对齐方式。

| |调用方法|
| - | - |
|读取|int vAlign()|
|修改|void setVAlign(int align)|
| |align取值：pub.ALIGNTOP 向上对齐|
| |                 pub.ALIGNBOTTOM 向下对齐|
| |                 pub.ALIGNVCENTER 垂直居中对齐|

- ### 属性：hAlign （类型：int 可读 可写）

水平方向的对齐方式。

| |调用方法|
| - | - |
|读取|int hAlign()|
|修改|void setHAlign(int align)|
| |align取值：pub.ALIGNLEFT 向左对齐|
| |                 pub.ALIGNRIGHT 向右对齐|
| |                 pub.ALIGNHCENTER 水平居中对齐|
| |                 pub.ALIGNJUSTIFY 水平分散对齐|

- ### 属性：maxwidth （类型：int 可读 可写）

最大宽度。

| |调用方法|
| - | - |
|读取|int maxwidth()|
|修改|void setMaxWidth(const int w)|

- ### 属性：maxheight （类型：int 可读 可写）

最大高度。

| |调用方法|
| - | - |
|读取|int maxheight()|
|修改|void setMaxHeight(const int h)|

- ### 属性：minwidth （类型：int 可读 可写）

最小宽度。

| |调用方法|
| - | - |
|读取|int minwidth()|
|修改|void setMinWidth(const int w)|

- ### 属性：minheight （类型：int 可读 可写）

最小高度。

| |调用方法|
| - | - |
|读取|int minheight()|
|修改|void setMinHeight(const int h)|

- ### 属性：font （类型：QFont 可读 可写）

控件的字体。

| |调用方法|
| - | - |
|读取|QFont font()|
|修改|void setFont(const QFont &font)|

- ### 属性：foreground （类型：QColor 可读 可写）

控件的前景色。

| |调用方法|
| - | - |
|读取|QColor foreground()|
|修改|void setForeground(const QColor &color)|

- ### 属性：background （类型：QColor 可读 可写）

控件的背景色。

| |调用方法|
| - | - |
|读取|QColor background()|
|修改|void setBackground(const QColor &color)|

- ### 属性：fillStyle （类型：int 可读 可写）

背景填充方式。如果设置为“填充”，则背景色有效，设置为“透明”，背景色的设置不起作用。

| |调用方法|
| - | - |
|读取|int fillStyle()|
|修改|void setFillStyle(const int style)|
| | **style的值：**|
| | &nbsp;- pub.FILLED_BACKGROUND 填充|
| | &nbsp;- pub.TRANSPARENT_BACKGROUND 透明|

- ### 属性：showBorder （类型：bool 可读 可写）

是否显示边框。

| |调用方法|
| - | - |
|读取|int showBorder()|
|修改|void setShowBorder(const int show)|

- ### 属性：borderColor （类型：QColor 可读 可写）

控件的边框颜色。

| |调用方法|
| - | - |
|读取|QColor borderColor()|
|修改|void setBorderColor(const QColor &color)|

- ### 属性：borderWidth （类型：int 可读 可写）

边框宽度。

| |调用方法|
| - | - |
|读取|int borderWidth()|
|修改|void setBorderWidth(const int w)|

- ### 属性：borderStyle （类型：int 可读 可写）

边框样式。

| |调用方法|
| - | - |
|读取|int borderStyle()|
|修改|void setBorderStyle(const int style)|



## 其它属性

- ### 属性：visible （类型：bool 可读 可写）

是否可见。

| |调用方法|
| - | - |
|读取|bool visible()|
|修改|void setVisible(bool visible)|

- ### 属性：showInForm （类型：bool 可读 可写）

表单上是否显示。

| |调用方法|
| - | - |
|读取|bool showInForm()|
|修改|void setShowInForm(bool show)|

- ### 属性：showInPDF （类型：bool 可读 可写）

PDF打印时是否显示。

| |调用方法|
| - | - |
|读取|bool showInPDF()|
|修改|void setShowInPDF(bool show)|

- ### 属性：showInPrinter （类型：bool 可读 可写）

打印机打印时是否显示。

| |调用方法|
| - | - |
|读取|bool showInPrinter()|
|修改|void setShowInPrinter(bool showInPrinter)|

- ### 属性：focus （类型：bool 可读 可写）

当前是否获得了输入焦点。

| |调用方法|
| - | - |
|读取|bool hasFocus()|
|修改|void setFocus(bool hasFocus)|

- ### 属性：acceptDrops （类型：bool 可读 可写）

是否接受DropDown事件。

| |调用方法|
| - | - |
|读取|bool acceptDrops()|
|修改|void setAcceptDrops(bool acceptDrops)|

- ### 属性：dragEnabled （类型：bool 可读 可写）

是否接受拖动。

| |调用方法|
| - | - |
|读取|bool dragEnabled()|
|修改|void setDragEnabled(bool enabled)|

- ### 属性：reloadWhenCreateNew （类型：bool 可读 可写）

在表单执行动作“新建”时，是否重新加载此控件的各项属性值。不同控件对重新加载的处理不一样，一般是恢复设计时的缺省状态。通常这个属性改为 False 时，可以在新建空白表单记录时，控件保持以前的状态或值减少输入的工作量。

| |调用方法|
| - | - |
|读取|bool reloadWhenCreateNew()|
|修改|void setReloadWhenCreateNew(bool reload)|

- ### 属性：updatesEnabled （类型：bool 可读 可写）

是否允许更新显示。通常用于要对控件进行较大影响外观的修改之前，将此值置为 False，在完成修改后再改为 True，以避免中途频繁刷新显示占用过多的系统资源或引起屏幕闪烁。

| |调用方法|
| - | - |
|读取|bool updatesEnabled()|
|修改|void setUpdatesEnabled(bool enabled)|

- ### 属性：tabOrder （类型：int 只读）

按 tab 键在控件间切换焦点时这个控件的顺序。

| |调用方法|
| - | - |
|读取|int tabOrder()|

- ### 属性：toolTip （类型：QString 可读 可写）

鼠标悬停在控件上时显示的工具提示。

| |调用方法|
| - | - |
|读取|QString toolTip()|
|修改|void setToolTip(const QString &text)|

- ### 属性：statusTip （类型：QString 可读 可写）

鼠标移动到主窗口状态栏显示的控件提示内容。

| |调用方法|
| - | - |
|读取|QString statusTip()|
|修改|void setStatusTip(const QString &text)|

- ### 属性：whatsThis （类型：QString 可读 可写）

使用 “what's this” 功能点击这个控件时，显示的“这是什么？”的内容。

| |调用方法|
| - | - |
|读取|QString whatsThis()|
|修改|void setWhatsThis(const QString &text)|

- ### 属性：tag （类型：QString 可读 可写）

备用的临时存放值的一个属性，可以按需要灵活使用。

| |调用方法|
| - | - |
|读取|QString tag()|
|修改|void setTag(const QString &text)|

- ### 属性：enabled （类型：bool 可读 可写）

是否可用。

| |调用方法|
| - | - |
|读取|int enabled()|
|修改|void setEnabled(const int enabled)|

## 槽函数（方法）

- ### QPixmap grab()

截取控件的图像，如果控件有子控件，子控件的图像也会被截取。

- ### setStyleSheet(const QString& style)

设置控件的外观样式，style 的格式，请参考Qt文档。

- ### void setFullScreen()

将控件全屏显示。

- ### void quitFullScreen()

退出全屏显示。

- ### void setSizePolicy(QSizePolicy policy)

设置尺寸规则，请参考 Qt 文档。

- ### void showBalloon(const QString& msg)

在控件上显示一个消息汽泡，msg指定要显示的文字。

- ### void showValidBalloon()

在控件上显示一个消息汽泡，显示控件的“合法性检查文本提示”的内容。

- ### void hideBalloon()

隐藏消息汽泡。

- ### bool isNull()

返回这个控件是否是一个空的 widgetDelegateBase 对象，空的表示没有绑定实际的控件。

- ### void toTop()

将这个控件提升到同一级控件中最前端，它会显示在最前端。同 raise() 是一样的效果。

- ### void toBottom()

将这个控件置于同一级控件中最底层，它会显示在其它控件最后面。同 lower() 是一样的效果。

- ### void raise()

将这个控件提升到同一级控件中最前端，它会显示在最前端。同 toTop() 是一样的效果。

- ### void lower()

将这个控件置于同一级控件中最底层，它会显示在其它控件最后面。同 toBottom() 是一样的效果。

- ### void repaint()	

重画这个控件，除非控件设置了 updatesEnabled 为 False 或控件处于隐藏状态。

- ### void show()

显示控件。

- ### void hide()

隐藏控件。

- ### int startTimer ( int interval )

启动一个定时器，interval 是时间间隔，单位是毫秒，返回定时器的标识号。

- ### bool killTimer ( int id )

停止一个定时器，id是定时器的标识号。

- ### void killAllTimer()

停止这个控件内部通过 startTimer 启动的所有定时器。

- ### QStringList timers()

返回这个控件所有定时器的标识号。

- ### void startSingleShot ( int interval )

启动一个单次定时器，interval 是时间间隔，单位是毫秒。单次定时器在触发一次超时事件后，就会停止。

- ### void setDisabled(bool disabled)

设置控件是否可用，如果 disabled 值为 True ，则不可用 ,enabled 属性值为 False , 否则为可用，enabled 属性值为 True。

