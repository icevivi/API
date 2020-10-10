# 按钮控件

按钮控件用于响应鼠标点击事件。比如下图各种样式：

![example](2-5-01.png)


---

<h2 id="category">目录</h2>

- [继承的属性和函数](#继承的属性和函数)

- [自有属性](#按钮控件的自有属性)

- [自有成员函数](#按钮控件自有成员函数)

- [信号](#按钮控件的信号)

- [可编程函数](#可编程函数)

---

## 继承的属性和函数

- [继承自QObject 的属性](2-1-qobject?id=属性)

- [继承自QObject 的 成员函数](2-1-qobject?id=成员函数)

- [继承自widgetDelegateBase的属性](2-2-base?id=属性)

- [继承自widgetDelegateBase的成员函数](2-2-base?id=成员函数)

---

## 按钮控件的自有属性

[返回目录](#category)

|属性|值类型|读写类型|说明|
| - | - | - | - |
|caption|QString|可读 可写|标题文字|
|icon|QPixmap|可读 可写|图标|
|iconsize|int|可读 可写|图标尺寸|
|isFlat|bool|可读 可写|是否不显示按钮边框|

- ### 属性：caption （类型：QString 可读 可写）

按钮上显示的文字。

| |调用方法|
| - | - |
|读取|QString caption const|
|修改|void setCaption( const QString &caption ) const|

- ### 属性：icon （类型：QPixmap 可读 可写）

设置按钮的图标。

| |调用方法|
| - | - |
|读取|QPixmap icon const|
|修改|void seticon( const QPixmap &icon ) const|

- ### 属性：iconSize （类型：int 可读 可写）

设置图标的尺寸。比如置为24时，图标的尺寸就是 24X24 像素。

| |调用方法|
| - | - |
|读取|int iconSize const|
|修改|void setIconSize( int iconSize ) const|

- ### 属性：isFlat （类型：bool 可读 可写）

是否不显示按钮边框。

| |调用方法|
| - | - |
|读取|bool isFlat const|
|修改|void setFlat( bool isFlat ) const|

---

## 按钮控件自有成员函数

[返回目录](#category)

所有属性的设置函数（参考上一节中修改属性的接口），都属于此类，都可以当做槽使用。除此之处，另外还包括以下几个成员函数：

|函数|接口|说明|
| - | - | - |
|click| void click() const|点击控钮|
|setShortcut|void setShortcut(int k1,int k2=0,int k3=0,int k4=0)	const|设置快捷键<br>k1、k2、k3、k4可以用于组成一组按键序列。详细说明请参考 Qt 中关于QKeySequence的文档。|

---

## 按钮控件的信号

[返回目录](#category)

|信号|接口|说明|
| - | - | - | 
|clicked|void clicked ( bool checked = false ) |鼠标被点击时发出此信号|
|pressed|void pressed () |鼠标按下时发出此信号|
|released|void released () |鼠标抬起时发出此信号|

---

## 可编程函数

[返回目录](#category)

- [可编程函数的详细说明](1-4-openscript?id=控件的可编程函数)

按钮控件所有可编程函数的清单：

|函数|函数名|传入参数|返回值|说明|
| - | - | - | - | - |
|[点击时](1-4-openscript?id=clicked)|控件名_clicked|无|无|鼠标点击这个按钮时调用|
|[鼠标进入时](1-4-openscript?id=enter)|控件名_enter|无|无|鼠标光标进入到这个控件时调用|
|[鼠标离开时](1-4-openscript?id=leave)|控件名_leave|无|无|鼠标光标离开这个控件时调用|
|[大小改变时](1-4-openscript?id=resize)|控件名_resize|无|无|控件大小改变时调用|
|[当拖曳进入时](1-4-openscript?id=dragEnter)|控件名_dragEnter|拖曳进入的元数据|是否接受拖曳进入<br>**数据类型：布尔**|当从外部拖曳一些内容进入到这个控件时，会调用此函数。<br>不接受拖曳的控件不会调用此函数。<br>通过脚本判断是否接受拖曳，<br>如果接受，返回 True，如果在控件上放开鼠标，程序会转而调用“当拖曳放下时”函数。<br>如果不接受，返回False，程序将不会调用“当拖曳放下时”函数。<br><br>**传入参数：**<br>format:元数据的格式列表，以列表类型传入<br>data:元数据的内容，以列表类型传入<br>dx:拖入的位置X坐标<br>dy:拖入的位置Y坐标|
|[当拖曳放下时](1-4-openscript?id=drop)|控件名_drop|拖曳放下的元数据|是否接受拖曳放下<br>**数据类型：布尔**|拖曳放下时调用。允许则返回 True，否则返回 False。<br><br>**传入参数：**<br>format:元数据的格式列表，以列表类型传入<br>data:元数据的内容，以列表类型传入<br>dx:放下的位置X坐标<br>dy:放下的位置Y坐标|
|[获得焦点](1-4-openscript?id=getfocus)|控件名_getfocus|无|无|获得焦点时调用|
|[失去焦点](1-4-openscript?id=lostfocus)|控件名_lostfocus|无|无|失去焦点时调用|
|[单次定时器超时时](1-4-openscript?id=singleshot)|控件名_singleshot|无|无|内置单次定时器超时时调用|
|[定时器超时时](1-4-openscript?id=timeout)|控件名_timeout|定时器的ID值|无|内置定时器超时时调用|

