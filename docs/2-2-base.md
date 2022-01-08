# 第二章 标准控件 - 基类widgetDelegateBase

biForm 中的标准控件都继承自 widgetDelegateBase，有共同的一些属性和成员函数。

## Python 脚本调用接口时的注意事项

本文中属性的调用方法采用 C++ 的语法，但在 biForm 中用 Python 脚本调用时，需要注意语法格式。

读取属性时，如```const QRect & geometry()```，在 Python 脚本调用时就应该是```obj.geometry```。注意不要带“()”。

修改属性时，如```void setGeometry(const QRect& rect)```，在 Python 脚本调用时，需要先导入 QRect 。

各类调用参考以下示例：

``` python

#先导入 QRect
from PythonQt.Qt import QRect
#label是表单上一个名称为 label 的标签控件
#调用成员函数对属性赋值
this.label.setGeometry(QRect(10,10,100,30))
#也可以直接对属性赋值
this.label.geometry=QRect(10,10,100,30)
#读取属性值
print(this.label.width)
#调用成员函数
this.label.setWidth(10)
this.label.showBalloon('这是一个标签控件')

```

---

<h2 id=category>目录</h2>

- [属性](#属性)

 - [外观相关属性](#外观相关属性)

 - [其他属性](#其他属性)

- [成员函数](#成员函数)

---

## 属性

|        属性         |  值类型  | 读写类型  |           说明           |
| ------------------- | -------- | -------- | ------------------------ |
| acceptDrops         | bool     | 可读 可写 | 是否允许从外部拖拽放下     |
| affectFormData      | bool     | 可读      | 控件的修改是否影响表单数据 |
| background          | QColor   | 可读 可写 | 背景色                    |
| borderColor         | QColor   | 可读 可写 | 边框颜色                  |
| borderStyle         | int      | 可读 可写 | 边框样式                  |
| borderWidth         | int      | 可读 可写 | 边框宽度                  |
| dragEnabled         | bool     | 可读 可写 | 是否允许拖动内容          |
| enabled             | bool     | 可读 可写 | 是否可用                  |
| font                | QFont    | 可读 可写 | 字体                     |
| foreground          | QColor   | 可读 可写 | 前景色                    |
| fillStyle           | int      | 可读 可写 | 填充类型                  |
| focus               | bool     | 可读 可写 | 是否获得输入焦点          |
| geometry            | QRect    | 可读 可写 | 位置尺寸                  |
| hAlign              | int      | 可读 可写 | 水平方向对齐方式          |
| height              | int      | 可读 可写 | 高度                     |
| maxheight           | int      | 可读 可写 | 最大高度                  |
| maxwidth            | int      | 可读 可写 | 最大宽度                  |
| minheight           | int      | 可读 可写 | 最小高度                  |
| minwidth            | int      | 可读 可写 | 最小宽度                  |
| pos                 | QPoint   | 可读 可写 | 位置                     |
| rect                | QRect    | 只读      | 边框矩形尺寸              |
| reloadWhenCreateNew | bool     | 可读 可写 | 表单新建时是否重新加载     |
| showBorder          | bool     | 可读 可写 | 是否显示边框              |
| visibleOnForm       | bool     | 可读 可写 | 表单上是否可见            |
| visibleOnPDF        | bool     | 可读 可写 | PDF输出时是否可见         |
| visibleWhenPrint    | bool     | 可读 可写 | 打印时是否可见            |
| size                | QSize    | 可读 可写 | 尺寸                     |
| statusTip           | QString  | 可读 可写 | 状态栏提示文本            |
| tabOrder            | int      | 只读      | tab键顺序                 |
| tag                 | QVariant | 可读 可写 | 备用属性                  |
| toolTip             | QString  | 可读 可写 | 工具提示                  |
| updatesEnabled      | bool     | 可读 可写 | 是否允许刷新              |
| vAlign              | int      | 可读 可写 | 垂直方向对齐方式          |
| visible             | bool     | 可读 可写 | 是否可见                  |
| whatsThis           | QString  | 可读 可写 | “这是什么”提示文本        |
| width               | int      | 可读 可写 | 宽度                     |
| x                   | int      | 可读 可写 | x方向位置                 |
| y                   | int      | 可读 可写 | y方向位置                 |

### 外观相关属性

- ### 属性：geometry （类型：QRect 可读 可写）

[返回目录](#category)

控件相对于它的上级控件（父对象）的坐标信息，等于 QRect(x(),y(),width(),height()) 。所以可以用```geometry.x()```和```geometry.y()```返回其左上角的坐标值，用```geometry.width()```和```geometry.height()```返回其宽度和高度。

| |调用方法|
| - | - |
|读取|QRect geometry() const|
|修改|void setGeometry(const QRect& rect) const|

- ### 属性：x （类型：int 可读 可写）

[返回目录](#category)

控件相对于上级控件的位置坐标的 x 值。

| |调用方法|
| - | - |
|读取|int x() const|
|修改|void setX(int x) const|

- ### 属性：y （类型：int 可读 可写）

[返回目录](#category)

控件相对于上级控件的位置坐标的 y 值。

| |调用方法|
| - | - |
|读取|int y() const|
|修改|void setY(int y) const|

- ### 属性：font （类型：QFont 可读 可写）

[返回目录](#category)

控件的字体。

| |调用方法|
| - | - |
|读取|QFont font() const|
|修改|void setFont(const QFont &font) const|

- ### 属性：foreground （类型：QColor 可读 可写）

[返回目录](#category)

控件的前景色。

| |调用方法|
| - | - |
|读取|QColor& foreground() const|
|修改|void setForeground(const QColor &color) const|

- ### 属性：width （类型：int 可读 可写）

[返回目录](#category)

控件的宽度。

| |调用方法|
| - | - |
|读取|int width() const|
|修改|void setWidth(int w) const|

- ### 属性：height （类型：int 可读 可写）

[返回目录](#category)

控件的高度。

| |调用方法|
| - | - |
|读取|int height() const|
|修改|void setHeight(int h) const|

- ### 属性：pos （类型：QPoint 可读 可写）

[返回目录](#category)

控件左上角相对于上级控件的位置。```pos.x()``` 和 ```pos.y()``` 返回控件的x和y坐标。注意如果控件在其它容器控件内，容器最左上角的坐标为（0，0）。

| |调用方法|
| - | - |
|读取|QPoint pos() const|
|修改|void setPos(const QPoint& pos) const |

- ### 属性：size （类型：QSize 可读 可写）

[返回目录](#category)

控件的大小。通过 ```size.width()``` 和 ```size.height()``` 可获取控件的宽度和高度。

| |调用方法|
| - | - |
|读取|QSize size() const|
|修改|void setSize(const QSize& size) const|

- ### 属性：rect （类型：QRect 只读）

[返回目录](#category)

控件相对于上级控件的矩形区域，等于 QRect(0,0,width(),height())。因此```rect.x()```和```rect.y()```返回值总为零， ```rect.width()``` 和 ```rect.height()``` 返回控件的宽度和高度。

| |调用方法|
| - | - |
|读取|QRect rect() const|

- ### 属性：vAlign （类型：int 可读 可写）

[返回目录](#category)

垂直方向的对齐方式。

| |调用方法|
| - | - |
|读取|int vAlign() const|
|修改|void setVAlign(int align) const|
| |**align取值：**|
| |pub.ALIGNTOP 向上对齐|
| |pub.ALIGNBOTTOM 向下对齐|
| |pub.ALIGNVCENTER 垂直居中对齐|

- ### 属性：hAlign （类型：int 可读 可写）

[返回目录](#category)

水平方向的对齐方式。

| |调用方法|
| - | - |
|读取|int hAlign() const|
|修改|void setHAlign(int align) const|
| |**align取值：**|
| |pub.ALIGNLEFT 向左对齐|
| |pub.ALIGNRIGHT 向右对齐|
| |pub.ALIGNHCENTER 水平居中对齐|
| |pub.ALIGNJUSTIFY 水平分散对齐|

- ### 属性：maxwidth （类型：int 可读 可写）

[返回目录](#category)

最大宽度。

| |调用方法|
| - | - |
|读取|int maxwidth() const|
|修改|void setMaxWidth(int w) const|

- ### 属性：maxheight （类型：int 可读 可写）

[返回目录](#category)

最大高度。

| |调用方法|
| - | - |
|读取|int maxheight() const|
|修改|void setMaxHeight(int h) const|

- ### 属性：minwidth （类型：int 可读 可写）

[返回目录](#category)

最小宽度。

| |调用方法|
| - | - |
|读取|int minwidth()|
|修改|void setMinWidth(int w) const|

- ### 属性：minheight （类型：int 可读 可写）

[返回目录](#category)

最小高度。

| |调用方法|
| - | - |
|读取|int minheight() const|
|修改|void setMinHeight(int h) const|

- ### 属性：background （类型：QColor 可读 可写）

[返回目录](#category)

控件的背景色。如果 fillStyle 设置为“填充”，则背景色有效，设置为“透明”，背景色的设置不起作用。

| |调用方法|
| - | - |
|读取|QColor background() const|
|修改|void setBackground(const QColor &color) const|

- ### 属性：fillStyle （类型：int 可读 可写）

[返回目录](#category)

背景填充方式。如果设置为“填充”，则背景色有效，设置为“透明”，背景色的设置不起作用。

| |调用方法|
| - | - |
|读取|int fillStyle() const|
|修改|void setFillStyle(int style) const|
| |**style的值：**|
| |- pub.FILLED_BACKGROUND 填充|
| |- pub.TRANSPARENT_BACKGROUND 透明|

- ### 属性：showBorder （类型：bool 可读 可写）

[返回目录](#category)

是否显示边框。

| |调用方法|
| - | - |
|读取|bool showBorder() const|
|修改|void setShowBorder(bool show) const|

- ### 属性：borderColor （类型：QColor 可读 可写）

[返回目录](#category)

边框颜色。

| |调用方法|
| - | - |
|读取|QColor borderColor() const|
|修改|void setBorderColor(const QColor &color) const|

- ### 属性：borderWidth （类型：int 可读 可写）

[返回目录](#category)

边框宽度。

| |调用方法|
| - | - |
|读取|int borderWidth() const|
|修改|void setBorderWidth(int w) const|

- ### 属性：borderStyle （类型：int 可读 可写）

[返回目录](#category)

边框样式。

|      |               调用方法                |
| ---- | ------------------------------------ |
| 读取 | int borderStyle() const              |
| 修改 | void setBorderStyle(int style) const |
|      | **style取值：**                      |
|      | pub.SOLIDLINE 实线                   |
|      | pub.DASHLINE 破折线                  |
|      | pub.DOTLINE 点划线                   |
|      | pub.DASHDOTLINE 破折-点线             |
|      | pub.DASHDOTDOTLINE 破折-点-点线       |

### 其它属性

- ### 属性：affectFormData（类型：bool 可读 )

[返回目录](#category)

这个属性用来表示控件的修改（输入类控件输入新的内容等）是否会影响表单后台数据表中的记录的值。

为 True 时也只是表示它的值可能会影响，并不是绝对的。用户在表单上对控件进行操作时，若要关闭表单或在记录之间跳转时，如果这个属性值为 True ，后台程序会判断是否有过修改以便提示是否需要保存数据。

|      |           调用方法           |
| ---- | --------------------------- |
| 读取 | bool affectFormData() const |

- ### 属性：enabled （类型：bool 可读 可写）

[返回目录](#category)

是否可用。

| |调用方法|
| - | - |
|读取|bool enabled() const|
|修改|void setEnabled(bool enabled) const|

- ### 属性：visible （类型：bool 可读 可写）

[返回目录](#category)

是否可见。

| |调用方法|
| - | - |
|读取|bool visible() const|
|修改|void setVisible(bool visible) const|

- ### 属性：visibleOnForm （类型：bool 可读 可写）

[返回目录](#category)

表单上是否显示。

| |调用方法|
| - | - |
|读取|bool visibleOnForm() const|
|修改|void setVisibleOnForm(bool show) const|

- ### 属性：visibleOnPDF （类型：bool 可读 可写）

[返回目录](#category)

PDF打印时是否显示。

|      |                调用方法                |
| ---- | ------------------------------------- |
| 读取 | bool visibleOnPDF() const             |
| 修改 | void setVisibleOnPDF(bool show) const |

- ### 属性：visibleWhenPrint （类型：bool 可读 可写）

[返回目录](#category)

打印机打印时是否显示。

|      |                  调用方法                  |
| ---- | ----------------------------------------- |
| 读取 | bool visibleWhenPrint() const             |
| 修改 | void setVisibleWhenPrint(bool show) const |

- ### 属性：focus （类型：bool 可读 可写）

[返回目录](#category)

当前是否获得了输入焦点。

| |调用方法|
| - | - |
|读取|bool hasFocus() const|
|修改|void setFocus(bool hasFocus) const|

- ### 属性：acceptDrops （类型：bool 可读 可写）

[返回目录](#category)

是否接受鼠标拖入事件。

| |调用方法|
| - | - |
|读取|bool acceptDrops() const|
|修改|void setAcceptDrops(bool acceptDrops) const|

- ### 属性：dragEnabled （类型：bool 可读 可写）

[返回目录](#category)

是否接受拖动。

| |调用方法|
| - | - |
|读取|bool dragEnabled() const|
|修改|void setDragEnabled(bool enabled) const|

- ### 属性：reloadWhenCreateNew （类型：bool 可读 可写）

[返回目录](#category)

在表单执行动作“新建”时，是否重新加载此控件的各项属性值。不同控件对重新加载的处理不一样，一般是恢复设计时的缺省状态。通常这个属性改为 False 时，可以在新建空白表单记录时，控件保持以前的状态或值减少输入的工作量。

| |调用方法|
| - | - |
|读取|bool reloadWhenCreateNew() const|
|修改|void setReloadWhenCreateNew(bool reload) const|

- ### 属性：updatesEnabled （类型：bool 可读 可写）

[返回目录](#category)

是否允许更新显示。通常用于要对控件进行较大影响外观的修改之前，将此值置为 False，在完成修改后再改为 True，以避免中途频繁刷新显示占用过多的系统资源或引起屏幕闪烁。

| |调用方法|
| - | - |
|读取|bool updatesEnabled() const|
|修改|void setUpdatesEnabled(bool enabled) const|

- ### 属性：tabOrder （类型：int 只读）

[返回目录](#category)

按 tab 键在控件间切换焦点时这个控件的顺序。

| |调用方法|
| - | - |
|读取|int tabOrder() const|

- ### 属性：toolTip （类型：QString 可读 可写）

[返回目录](#category)

鼠标悬停在控件上时显示的工具提示。

| |调用方法|
| - | - |
|读取|QString toolTip() const|
|修改|void setToolTip(const QString &text) const|

- ### 属性：statusTip （类型：QString 可读 可写）

[返回目录](#category)

鼠标移动到主窗口状态栏显示的控件提示内容。

| |调用方法|
| - | - |
|读取|QString statusTip() const|
|修改|void setStatusTip(const QString &text) const|

- ### 属性：whatsThis （类型：QString 可读 可写）

[返回目录](#category)

使用 “这是什么？” 功能点击这个控件时，显示的文本内容。

| |调用方法|
| - | - |
|读取|QString whatsThis() const|
|修改|void setWhatsThis(const QString &text) const|

- ### 属性：tag （类型：QVariant 可读 可写）

[返回目录](#category)

备用的临时存放值的一个属性，可以按需要灵活使用。

| |调用方法|
| - | - |
|读取|QVariant tag() const|
|修改|void setTag(const QVariant &text) |

## 成员函数

成员函数在 biForm 中都可以当做槽函数使用。

|                  函数                  |                      接口                      |           说明           |
| ------------------------------------- | ---------------------------------------------- | ------------------------ |
| [baseMetaObject](#baseMetaObject)     | QMetaObject* baseMetaObject() const;	         | 返回基类对象的QMetaObject |
| [grab](#grab)                         | QPixmap grab() const                           | 截取控件图像              |
| [hide](#hide)                         | void hide() const                              | 隐藏                     |
| [hideBalloon](#hideBalloon)           | void hideBalloon() const                       | 隐藏汽泡控件              |
| [isNull](#isNull)                     | bool isNull() const                            | 是否为空                  |
| [killAllTimer](#killAllTimer)         | void killAllTimer() const                      | 关闭所有定时器            |
| [killTimer](#killTimer)               | bool killTimer ( int id ) const                | 关闭指定的定时器          |
| [lower](#lower)                       | void lower() const                             | 置于底层                  |
| [quitFullScreen](#quitFullScreen)     | void quitFullScreen()                          | 退出全屏                  |
| [raiseToTop](#raiseToTop)             | void raiseToTop() const                        | 置于顶层                  |
| [repaint](#repaint)                   | void repaint()                                 | 重画画                   |
| [setDisabled](#setDisabled)           | void setDisabled(bool disabled) const          | 设置可用状态              |
| [setFullScreen](#setFullScreen)       | void setFullScreen()                           | 全屏                     |
| [setSizePolicy](#setSizePolicy)       | void setSizePolicy(QSizePolicy policy) const   | 设置尺寸缩放规则          |
| [setStyleSheet](#setStyleSheet)       | setStyleSheet(const QString& styleSheet) const | 设置样式表                |
| [show](#show)                         | void show() const                              | 显示                     |
| [showBalloon](#showBalloon)           | void showBalloon(const QString& msg) const     | 显示汽泡提示文本          |
| [showValidBalloon](#showValidBalloon) | void showValidBalloon() const                  | 显示有效性汽泡提示        |
| [startSingleShot](#startSingleShot)   | void startSingleShot ( int interval ) const    | 启动单次定时器            |
| [startTimer](#startTimer)             | int startTimer ( int interval ) const          | 启动一个新的定时器        |
| [timers](#timers)                     | QStringList timers() const                     | 所有定时器的标识号清单     |
| [toBottom](#toBottom)                 | void toBottom() const                          | 置于底层                  |
| [toTop](#toTop)                       | void toTop() const                             | 置于顶层                  |

- ### baseMetaObject

调用方法：QMetaObject* baseMetaObject() const;

[返回目录](#category)

返回 widgetDelegateBase 类的 metaObject ，而不是子类的 metaObject 。以便可以通过 QMetaObject 类提供的接口，读取 widgetDelegateBase 包含的属性、方法、枚举等接口。

- ### grab

调用方法：QPixmap grab() const

[返回目录](#category)

截取控件的图像。如果控件有子控件，子控件的图像也会被截取。

- ### setStyleSheet

调用方法：void setStyleSheet(const QString& styleSheet) const

[返回目录](#category)

设置控件的外观样式。styleSheet有类似于CSS的语法，请参考Qt文档。

- ### setFullScreen

调用方法：void setFullScreen()

[返回目录](#category)

将控件全屏显示。

- ### quitFullScreen

调用方法：void quitFullScreen()

[返回目录](#category)

退出全屏显示。

- ### setSizePolicy

调用方法：void setSizePolicy(QSizePolicy policy) const

[返回目录](#category)

设置大小变动的规则，请参考 Qt 文档。

- ### showBalloon

调用方法：void showBalloon(const QString& msg) const

[返回目录](#category)

在控件上显示一个消息汽泡，msg指定要显示的文字。

- ### showValidBalloon

调用方法：void showValidBalloon() const

[返回目录](#category)

在控件上显示一个消息汽泡，显示控件的“合法性检查文本提示”的内容。

- ### hideBalloon

调用方法：void hideBalloon() const

[返回目录](#category)

隐藏消息汽泡。

- ### isNull

调用方法：bool isNull() const

[返回目录](#category)

返回这个控件是否是一个空的 widgetDelegateBase 对象，空的表示没有绑定实际的控件。

- ### toTop

调用方法：void toTop() const

[返回目录](#category)

将这个控件提升到同一级控件中最前端，它会显示在最前端。同 raiseToTop() 是一样的效果。

- ### toBottom

调用方法：void toBottom() const

[返回目录](#category)

将这个控件置于同一级控件中最底层，它会显示在其它控件最后面。同 lower() 是一样的效果。

- ### raiseToTop

调用方法：void raiseToTop() const

[返回目录](#category)

将这个控件提升到同一级控件中最前端，它会显示在最前端。同 toTop() 是一样的效果。

- ### lower

调用方法：void lower() const

[返回目录](#category)

将这个控件置于同一级控件中最底层，它会显示在其它控件最后面。同 toBottom() 是一样的效果。

- ### repaint

调用方法：void repaint()	 const

[返回目录](#category)

重画这个控件，除非控件设置了 updatesEnabled 为 False 或控件处于隐藏状态。

- ### show

调用方法：void show() const

[返回目录](#category)

显示控件。

- ### hide

调用方法：void hide() const

[返回目录](#category)

隐藏控件。

- ### startTimer

调用方法：int startTimer ( int interval ) const

[返回目录](#category)

启动一个定时器，interval 是时间间隔，单位是毫秒，返回定时器的标识号。

- ### killTimer

调用方法：bool killTimer ( int id ) const

[返回目录](#category)

停止一个定时器，id是定时器的标识号。

- ### killAllTimer

调用方法：void killAllTimer() const

[返回目录](#category)

停止这个控件内部通过 startTimer 启动的所有定时器。

- ### timers

调用方法：QStringList timers() const

[返回目录](#category)

返回这个控件所有定时器的标识号。

- ### startSingleShot

调用方法：void startSingleShot ( int interval ) const

[返回目录](#category)

启动一个单次定时器，interval 是时间间隔，单位是毫秒。单次定时器在触发一次超时事件后，就会停止。

- ### setDisabled

调用方法：void setDisabled(bool disabled) const

[返回目录](#category)

设置控件是否可用，如果 disabled 值为 True ，则不可用 ,enabled 属性值为 False , 否则为可用，enabled 属性值为 True。

