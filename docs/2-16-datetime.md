# 日期时间编辑器控件

日期时间编辑器控件用于选择设定日期和时间。如下图示：

![example](2-16-01.png)

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

- ### 属性：margin （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int margin const|
|修改|void setMargin( int margin ) const|


- ### 属性：wrapping （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool wrapping const|
|修改|void setWrapping( bool wrapping ) const|


- ### 属性：format （类型：QString 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QString format const|
|修改|void setFormat( const QString &format ) const|


- ### 属性：calendarpopup （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool calendarpopup const|
|修改|void setCalendarpopup( bool calendarpopup ) const|


- ### 属性：defaultVal （类型：QString 可读 ）

{{ usage }}

| |调用方法|
| - | - |
|读取|QString defaultVal const|



- ### 属性：text （类型：QString 可读 ）

{{ usage }}

| |调用方法|
| - | - |
|读取|QString text const|



- ### 属性：checkable （类型：bool 可读 ）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool checkable const|



- ### 属性：checked （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool checked const|
|修改|void setChecked( bool checked ) const|


- ### 属性：datetime （类型：QString 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QString datetime const|
|修改|void setDatetime( const QString &datetime ) const|


- ### 属性：readOnly （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool readOnly const|
|修改|void setReadOnly( bool readOnly ) const|


