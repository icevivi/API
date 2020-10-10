# 列表控件

列表控件用于显示一些条目的清单。如下图示：

![example](2-23-01.png)

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


- ### 属性：spacing （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int spacing const|
|修改|void setSpacing( int spacing ) const|


- ### 属性：gridWidth （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int gridWidth const|
|修改|void setGridWidth( int gridWidth ) const|


- ### 属性：gridHeight （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int gridHeight const|
|修改|void setGridHeight( int gridHeight ) const|


- ### 属性：sortingEnabled （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool sortingEnabled const|
|修改|void setSortingEnabled( bool sortingEnabled ) const|


- ### 属性：allowSelectMulti （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool allowSelectMulti const|
|修改|void setAllowSelectMulti( bool allowSelectMulti ) const|


- ### 属性：listtext （类型：QStringList 可读 ）

{{ usage }}

| |调用方法|
| - | - |
|读取|QStringList listtext const|



- ### 属性：listvalue （类型：QStringList 可读 ）

{{ usage }}

| |调用方法|
| - | - |
|读取|QStringList listvalue const|



- ### 属性：currentRow （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int currentRow const|
|修改|void setCurrentRow( int currentRow ) const|


- ### 属性：count （类型：int 可读 ）

{{ usage }}

| |调用方法|
| - | - |
|读取|int count const|



