# 单选按钮控件

单选按钮控件用于在多个选项中选择一项。如下图示：

![example](2-12-01.png)

---

<h2 id="category">目录</h2>

- [继承的属性和函数](#继承的属性和函数)

- [自有属性](#树形控件的自有属性)

- [自有成员函数](#树形控件自有成员函数)

- [信号](#树形控件的信号)

- [可编程函数](#可编程函数)

---

## 继承的属性和函数

- [继承自QObject 的属性](2-1-qobject?id=属性)

- [继承自QObject 的 成员函数](2-1-qobject?id=成员函数)

- [继承自widgetDelegateBase的属性](2-2-base?id=属性)

- [继承自widgetDelegateBase的成员函数](2-2-base?id=成员函数)

---

## 树形控件的属性

[返回目录](#category)

|属性|值类型|读写类型|说明|
| - | - | - | - |

- ### 属性：caption （类型：QString 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QString caption const|
|修改|void setCaption( const QString &caption ) const|


- ### 属性：checked （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool checked const|
|修改|void setChecked( bool checked ) const|


- ### 属性：value （类型：QString 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QString value const|
|修改|void setValue( const QString &value ) const|


- ### 属性：defaultVal （类型：bool 可读 ）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool defaultVal const|



