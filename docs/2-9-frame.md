# 框架控件

框架控件为多个控件提供容器。如下图示：

![example](2-9-01.png)

---

<h2 id="category">目录</h2>

- [继承的属性和函数](#继承的属性和函数)

- [自有属性](#框架控件的自有属性)

- [自有成员函数](#框架控件自有成员函数)

- [信号](#框架控件的信号)

- [可编程函数](#可编程函数)

---

## 继承的属性和函数

- [继承自QObject 的属性](2-1-qobject?id=属性)

- [继承自QObject 的 成员函数](2-1-qobject?id=成员函数)

- [继承自widgetDelegateBase的属性](2-2-base?id=属性)

- [继承自widgetDelegateBase的成员函数](2-2-base?id=成员函数)

---

## 框架控件的属性

[返回目录](#category)

|属性|值类型|读写类型|说明|
| - | - | - | - |
|shadow|int|可读 可写|边框样式特效|
|useScrollBar|bool|可读 |是否使用滚动条|
|viewportWidth|int|可读 可写|可见范围宽度|
|viewportHeightlineStyle|int|可读 可写|可见范围高度|

- ### 属性：shadow （类型：int 可读 可写）

边框样式特效。

| |调用方法|
| - | - |
|读取|int shadow const|
|修改|void setShadow( int shadow ) const|
| |**shadow取值：**|
| |pub.PLAIN 平的|
| |pub.RAISED 上凸|
| |pub.SUNKEN 下陷|

- ### 属性：useScrollBar （类型：bool 可读 ）

是否使用滚动条。

| |调用方法|
| - | - |
|读取|bool useScrollBar const|

- ### 属性：viewportWidth （类型：int 可读 可写）

可见范围宽度。

| |调用方法|
| - | - |
|读取|int viewportWidth const|
|修改|void setViewportWidth( int viewportWidth ) const|

- ### 属性：viewportHeight （类型：int 可读 可写）

可见范围高度。

| |调用方法|
| - | - |
|读取|int viewportHeight const|
|修改|void setViewportHeight( int viewportHeight ) const|

- ### 属性：horizontalScrollBarPolicy （类型：int 可读 可写）

水平滚动条显示策略。

| |调用方法|
| - | - |
|读取|int horizontalScrollBarPolicy const|
|修改|void setHorizontalScrollBarPolicy( int horizontalScrollBarPolicy ) const|
| |**horizontalScrollBarPolicy取值：**|
| |pub.SCROLLBAR_AS_NEEDED 需要时显示|
| |pub.SCROLLBAR_ALWAYS_OFF 一直隐藏|
| |pub.SCROLLBAR_ALWAYS_ON 一直显示|

- ### 属性：verticalScrollBarPolicy （类型：int 可读 可写）

垂直滚动条显示策略。

| |调用方法|
| - | - |
|读取|int verticalScrollBarPolicy const|
|修改|void setVerticalScrollBarPolicy( int verticalScrollBarPolicy ) const|
| |**verticalScrollBarPolicy取值：**|
| |pub.SCROLLBAR_AS_NEEDED 需要时显示|
| |pub.SCROLLBAR_ALWAYS_OFF 一直隐藏|
| |pub.SCROLLBAR_ALWAYS_ON 一直显示|

---

## 框架控件自有成员函数

[返回目录](#category)

所有属性的设置函数（参考上一节中修改属性的接口），都属于此类，都可以当做槽使用。除此之处， 框架控件还包括以下成员函数：

|函数|接口|说明|
| - | - | - | 
|buttonGroupCount|int buttonGroupCount() const|单选按钮组的数量<br>框架控件上所有下一级单选按钮自动会形成一个组。<br>框架控件只会有一个单选按钮组。|
|buttonGroup|radioButtonGroupDelegate* buttonGroup(int index = 0) const|返回指定序号的单选按钮组|
|setVLayout |void setVLayout(const QStringList& widgetList, <br>int left=0, int top=0, int right=0, int bottom=0,<br>int spacing=0) const|以垂直方向添加多个控件<br><br>**传入参数：**<br>widgetList：需要添加的控件的名称清单<br>left：左边界宽度（像素为单位）<br>top：上边界宽度（像素为单位）<br>right：右边界宽度（像素为单位）<br>bottom：下边界宽度（像素为单位）<br>spacing：控件间距（像素为单位）|
|setHLayout |void setHLayout(const QStringList &widgetList, <br>int left=0, int top=0, int right=0, int bottom=0,<br>int spacing=0) const|以水平方向添加多个控件<br>传入参数的用法与setVLayout相同|
|setVSplitter|void setVSplitter(const QStringList &widgetList,<br> int left=0, int top=0, int right=0, int bottom=0,<br>int spacing=0) const|以垂直方向添加多个控件，控件分隔可调<br>传入参数的用法与setVLayout相同|
|setHSplitter|void setHSplitter(const QStringList &widgetList, <br>int left=0, int top=0, int right=0, int bottom=0,<br>int spacing=0) const|以水平方向添加多个控件，控件分隔可调<br>传入参数的用法与setVLayout相同|

---

## 框架控件的信号

[返回目录](#category)

框架控件没有信号。

---

## 可编程函数

[返回目录](#category)

- [可编程函数的详细说明](1-4-openscript?id=控件的可编程函数)

框架控件除了继承的 widgetDelegateBase 中的可编程函数外，没有其它可编程函数。

