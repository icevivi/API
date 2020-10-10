# 复选框控件

复选框控件用于勾选某个选项，同级的一组复选框可进行多项选择。如下图示：

![example](2-13-01.png)

## 继承自 widgetDelegateBase 的 属性和成员函数

参考： [基类widgetDelegateBase](2-2-base)

## 复选框控件的属性

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


- ### 属性：checkState （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int checkState const|
|修改|void setCheckState( int checkState ) const|


- ### 属性：triState （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool triState const|
|修改|void setTriState( bool triState ) const|


- ### 属性：defaultVal （类型：QVariant 可读 ）

{{ usage }}

| |调用方法|
| - | - |
|读取|QVariant defaultVal const|



- ### 属性：checkedText （类型：QString 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QString checkedText const|
|修改|void setCheckedText( const QString &checkedText ) const|


- ### 属性：uncheckedText （类型：QString 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QString uncheckedText const|
|修改|void setUncheckedText( const QString &uncheckedText ) const|


- ### 属性：partiallyCheckedText （类型：QString 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QString partiallyCheckedText const|
|修改|void setPartiallyCheckedText( const QString &partiallyCheckedText ) const|


- ### 属性：currentText （类型：QString 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QString currentText const|
|修改|void setCurrentText( const QString &currentText ) const|


