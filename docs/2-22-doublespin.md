# 双精度小数编辑器控件

双精度小数编辑器控件用于输入小数值。如下图示：

![example](2-22-01.png)

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


- ### 属性：minimum （类型：double 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|double minimum const|
|修改|void setMinimum( double minimum ) const|


- ### 属性：maximum （类型：double 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|double maximum const|
|修改|void setMaximum( double maximum ) const|


- ### 属性：wrapping （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool wrapping const|
|修改|void setWrapping( bool wrapping ) const|


- ### 属性：singlestep （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int singlestep const|
|修改|void setSinglestep( int singlestep ) const|


- ### 属性：prefix （类型：QString 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QString prefix const|
|修改|void setPrefix( const QString &prefix ) const|


- ### 属性：suffix （类型：QString 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QString suffix const|
|修改|void setSuffix( const QString &suffix ) const|


- ### 属性：decimals （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int decimals const|
|修改|void setDecimals( int decimals ) const|


- ### 属性：defaultVal （类型：double 可读 ）

{{ usage }}

| |调用方法|
| - | - |
|读取|double defaultVal const|



- ### 属性：text （类型：QString 可读 ）

{{ usage }}

| |调用方法|
| - | - |
|读取|QString text const|



- ### 属性：cleanText （类型：QString 可读 ）

{{ usage }}

| |调用方法|
| - | - |
|读取|QString cleanText const|



- ### 属性：value （类型：double 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|double value const|
|修改|void setValue( double value ) const|


- ### 属性：readOnly （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool readOnly const|
|修改|void setReadOnly( bool readOnly ) const|


- ### 属性：showSeperator （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool showSeperator const|
|修改|void setShowSeperator( bool showSeperator ) const|


