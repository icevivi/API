# 图片控件

图片控件用于显示图片。如下图示：

![example](2-18-01.png)

---

<h2 id="category">目录</h2>

- [继承的属性和函数](#继承的属性和函数)

- [自有属性](#图像控件的自有属性)

- [自有成员函数](#图像控件自有成员函数)

- [信号](#图像控件的信号)

- [可编程函数](#可编程函数)

---

## 继承的属性和函数

- [继承自QObject 的属性](2-1-qobject?id=属性)

- [继承自QObject 的 成员函数](2-1-qobject?id=成员函数)

- [继承自widgetDelegateBase的属性](2-2-base?id=属性)

- [继承自widgetDelegateBase的成员函数](2-2-base?id=成员函数)

---

## 图像控件的自有属性

[返回目录](#category)

|属性|值类型|读写类型|说明|
| - | - | - | - |
|image|QPixmap |可读 可写|当前图像|
|defaultVal|QString |可读 |缺省值|
|palette|QPalette|可读 可写|调色板|
|URL|QString |可读 可写|超链接地址|
|imageFillStyle|int |可读 可写|图片填充方式|

- ### 属性：image （类型：QPixmap 可读 可写）

当前图像。

| |调用方法|
| - | - |
|读取|QPixmap image const|
|修改|void setImage( const QPixmap &image ) const|

- ### 属性：defaultVal （类型：QString 可读 ）

初始设置的图像来源，具体指表单的图片集中某个图片的名称。

| |调用方法|
| - | - |
|读取|QString defaultVal const|

- ### 属性：palette （类型：QPalette 可读 可写）

调色板。

| |调用方法|
| - | - |
|读取|QPalette palette const|
|修改|void setPalette( const QPalette &palette ) const|

- ### 属性：URL （类型：QString 可读 可写）

超链接地址。

| |调用方法|
| - | - |
|读取|QString URL const|
|修改|void setURL( const QString &URL ) const|

- ### 属性：imageFillStyle （类型：int 可读 可写）

图像填充方式。

| |调用方法|
| - | - |
|读取|int imageFillStyle const|
|修改|void setImageFillStyle( int imageFillStyle ) const|
||**imageFillStyle取值**|
||pub.NOT_SCALED 保持原样|
||pub.SCALED_CONTENTS 按控件大小缩放图片|
||pub.TEXTURE_IMAGE 连续填充|

---

## 图像控件自有成员函数

[返回目录](#category)

所有属性的设置函数（参考上一节中修改属性的接口），都属于此类，都可以当做槽使用。除此之处， 图像控件还有以下成员函数。 

|函数|接口|说明|
| - | - | - |
|setMovie|void setMovie(QMovie * v) const|设置动画<br>只显示动画图片，不能播放声音。通常用于显示gif文件<br>关于 QMovie 的用法请参考 Qt 文档|
|movie|QMovie* movie() const|当前设置的动画|
|setImageFromImageset|void setImageFromImageset(const QString & v)const |从表单的图片集中按名称取出图像进行设置|
|setMovieFromImageset|void setMovieFromImageset(const QString & v)const  |从表单的图片集中按名称取出动画进行设置|

---

## 图像控件的信号

[返回目录](#category)

|信号|接口|说明|
| - | - | - | 
|linkActivated|void linkActivated ( const QString & link ) |设置了URL之后，点击链接时发出此信号|

---

## 可编程函数

[返回目录](#category)

- [可编程函数的详细说明](1-4-openscript?id=控件的可编程函数)

图像控件除了继承的 widgetDelegateBase 中的可编程函数外，还包括以下可编程函数：

|函数|函数名|传入参数|返回值|说明|
| - | - | - | - | - |
|[缺省值](1-4-openscript?id=default) | 控件名_default | 无 | 图像控件的图像来源的初始值。具体指使用表单的图片集中的某个图片的名称。|


