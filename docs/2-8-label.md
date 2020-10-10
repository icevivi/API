# 标签控件

标签控件用于显示文本，可以有多种格式，比如下图显示了几种不同样式的文本标签控件：

![example](2-8-01.png)

## 继承自 widgetDelegateBase 的 属性和成员函数

参考： [基类widgetDelegateBase](2-2-base)

## 标签控件的属性

- ### 属性：caption （类型：QString 可读 可写）

显示的文字。

| |调用方法|
| - | - |
|读取|QString caption const|
|修改|void setcaption( const QString &caption ) const|

- ### 属性：URL （类型：QString 可读 可写）

超链接地址。

| |调用方法|
| - | - |
|读取|QString URL const|
|修改|void setURL( const QString &URL ) const|

- ### 属性：wordWrap （类型：bool 可读 可写）

是否自动换行。

| |调用方法|
| - | - |
|读取|bool wordWrap const|
|修改|void setwordWrap( bool wordWrap ) const|



