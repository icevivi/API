# 日期时间编辑器控件

日期时间编辑器控件用于选择设定日期和时间。如下图示：

![example](2-16-01.png)

## 继承自 widgetDelegateBase 的 属性和成员函数

参考： [基类widgetDelegateBase](2-2-base)

## 日期时间编辑器控件的属性

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


