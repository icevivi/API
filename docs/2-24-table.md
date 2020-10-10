# 表格控件

表格控件用于以表格形式显示一些条目的清单。如下图示：

![example](2-24-01.png)

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


- ### 属性：gridStyle （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int gridStyle const|
|修改|void setGridStyle( int gridStyle ) const|


- ### 属性：cornerButtonEnabled （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool cornerButtonEnabled const|
|修改|void setCornerButtonEnabled( bool cornerButtonEnabled ) const|


- ### 属性：sortingEnabled （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool sortingEnabled const|
|修改|void setSortingEnabled( bool sortingEnabled ) const|


- ### 属性：showGrid （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool showGrid const|
|修改|void setShowGrid( bool showGrid ) const|


- ### 属性：wordwrap （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool wordwrap const|
|修改|void setWordwrap( bool wordwrap ) const|


- ### 属性：stretchLastColumn （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool stretchLastColumn const|
|修改|void setStretchLastColumn( bool stretchLastColumn ) const|


- ### 属性：stretchLastRow （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool stretchLastRow const|
|修改|void setStretchLastRow( bool stretchLastRow ) const|


- ### 属性：rowCount （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int rowCount const|
|修改|void setRowCount( int rowCount ) const|


- ### 属性：columnCount （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int columnCount const|
|修改|void setColumnCount( int columnCount ) const|


- ### 属性：defaultRowHeight （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int defaultRowHeight const|
|修改|void setDefaultRowHeight( int defaultRowHeight ) const|


- ### 属性：rowResizeMode （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int rowResizeMode const|
|修改|void setRowResizeMode( int rowResizeMode ) const|


- ### 属性：columnResizeMode （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int columnResizeMode const|
|修改|void setColumnResizeMode( int columnResizeMode ) const|


- ### 属性：alternatingRowColors （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool alternatingRowColors const|
|修改|void setAlternatingRowColors( bool alternatingRowColors ) const|


- ### 属性：alternateBaseColor （类型：QColor 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QColor alternateBaseColor const|
|修改|void setAlternateBaseColor( const QColor &alternateBaseColor ) const|


- ### 属性：columnHeaderVisible （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool columnHeaderVisible const|
|修改|void setColumnHeaderVisible( bool columnHeaderVisible ) const|


- ### 属性：rowHeaderVisible （类型：bool 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|bool rowHeaderVisible const|
|修改|void setRowHeaderVisible( bool rowHeaderVisible ) const|


- ### 属性：defaultColumnWidth （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int defaultColumnWidth const|
|修改|void setDefaultColumnWidth( int defaultColumnWidth ) const|


- ### 属性：rowHeaderFont （类型：QFont 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QFont rowHeaderFont const|
|修改|void setRowHeaderFont( const QFont &rowHeaderFont ) const|


- ### 属性：columnHeaderFont （类型：QFont 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QFont columnHeaderFont const|
|修改|void setColumnHeaderFont( const QFont &columnHeaderFont ) const|


- ### 属性：rowHeaderForegroundColor （类型：QColor 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QColor rowHeaderForegroundColor const|
|修改|void setRowHeaderForegroundColor( const QColor &rowHeaderForegroundColor ) const|


- ### 属性：columnHeaderForegroundColor （类型：QColor 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QColor columnHeaderForegroundColor const|
|修改|void setColumnHeaderForegroundColor( const QColor &columnHeaderForegroundColor ) const|


- ### 属性：rowHeaderBackgroundColor （类型：QColor 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|QColor rowHeaderBackgroundColor const|
|修改|void setRowHeaderBackgroundColor( const QColor &rowHeaderBackgroundColor ) const|


- ### 属性：selectionMode （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int selectionMode const|
|修改|void setSelectionMode( int selectionMode ) const|


- ### 属性：selectionBehavior （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int selectionBehavior const|
|修改|void setSelectionBehavior( int selectionBehavior ) const|


- ### 属性：horizontalScrollBarPolicy （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int horizontalScrollBarPolicy const|
|修改|void setHorizontalScrollBarPolicy( int horizontalScrollBarPolicy ) const|


- ### 属性：verticalScrollBarPolicy （类型：int 可读 可写）

{{ usage }}

| |调用方法|
| - | - |
|读取|int verticalScrollBarPolicy const|
|修改|void setVerticalScrollBarPolicy( int verticalScrollBarPolicy ) const|


---

## 可编程函数

[返回目录](#category)

- [可编程函数的详细说明](1-4-openscript?id=可编程函数)

表格控件所有可编程函数的清单：

|函数|函数名|传入参数|返回值|说明|
| - | - | - | - | - |
|[鼠标进入时](1-4-openscript?id=enter)|控件名_enter|无|无|鼠标光标进入到这个控件时调用|
|[鼠标离开时](1-4-openscript?id=leave)|控件名_leave|无|无|鼠标光标离开这个控件时调用|
|[大小改变时](1-4-openscript?id=resize)|控件名_resize|无|无|控件大小改变时调用|
|[当拖曳进入时](1-4-openscript?id=dragEnter)|控件名_dragEnter|拖曳进入的元数据|是否接受拖曳进入<br>**数据类型：布尔**|当从外部拖曳一些内容进入到这个控件时，会调用此函数。<br>不接受拖曳的控件不会调用此函数。<br>通过脚本判断是否接受拖曳，<br>如果接受，返回 True，如果在控件上放开鼠标，程序会转而调用“当拖曳放下时”函数。<br>如果不接受，返回False，程序将不会调用“当拖曳放下时”函数。<br>传入参数：<br>format:元数据的格式列表，以列表类型传入<br>data:元数据的内容，以列表类型传入<br>dx:拖入的位置X坐标<br>dy:拖入的位置Y坐标|
|[当拖曳放下时](1-4-openscript?id=drop)|控件名_drop|拖曳放下的元数据|是否接受拖曳放下<br>**数据类型：布尔**|拖曳放下时调用。允许则返回 True，否则返回 False。<br>format:元数据的格式列表，以列表类型传入<br>data:元数据的内容，以列表类型传入<br>dx:放下的位置X坐标<br>dy:放下的位置Y坐标|
|[生成元数据](1-4-openscript?id=mimedata)|控件名_mimedata|无|以列表形式生成控件的元数据<br>**数据类型：列表**|拖曳时这个控件时生成元数据的内容|
|[获得焦点](1-4-openscript?id=getfocus)|控件名_getfocus|无|无|获得输入焦点时调用|
|[失去焦点](1-4-openscript?id=lostfocus)|控件名_lostfocus|无|无|失去输入焦点时调用|
|[单次定时器超时时](1-4-openscript?id=singleshot)|控件名_singleshot|无|无|内置单次定时器超时时调用|
|[定时器超时时](1-4-openscript?id=timeout)|控件名_timeout|定时器的ID值|无|内置定时器超时时调用|



