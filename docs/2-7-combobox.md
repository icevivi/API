# 下拉列表框控件

下拉列表框提供一个弹出的下拉列表供选择。如下图示：

![example](2-7-01.png)

---

<h2 id="category">目录</h2>

- [继承的属性和函数](#继承的属性和函数)

- [自有属性](#下拉列表框的自有属性)

- [自有成员函数](#下拉列表框自有成员函数)

- [信号](#下拉列表框的信号)

- [可编程函数](#可编程函数)

---

## 继承的属性和函数

- [继承自QObject 的属性](2-1-qobject?id=属性)

- [继承自QObject 的 成员函数](2-1-qobject?id=成员函数)

- [继承自widgetDelegateBase的属性](2-2-base?id=属性)

- [继承自widgetDelegateBase的成员函数](2-2-base?id=成员函数)

---

## 下拉列表框的属性

[返回目录](#category)

|属性|值类型|读写类型|说明|
| - | - | - | - |
|count|int|可读 ||
|currentData|QString|可读 可写||
|currentIndex|int|可读 可写||
|currentText|QString|可读 可写||
|defaultVal|QString|可读 ||
|editable|bool|可读 可写||
|reference|QString|可读 可写||
|textList|QStringList|可读 ||
|valueList|QStringList|可读 ||

- ### 属性：count （类型：int 可读）

下拉列表中项目的数量。

| |调用方法|
| - | - |
|读取|int count const|

- ### 属性：currentData （类型：QString 可读 可写）

当前项的数据。“数据”与“文本”不同，是内部保存的数据，可以与“文本”有不一样的内容。需要注意的是，调用 setCurrentData 时，并不是影响下拉列表中当前项的数据，而是从下拉列表的项目中查找到相同的数据（第一个匹配的），并将该项设置为当前项。如果找不到，就忽略。

| |调用方法|
| - | - |
|读取|QString currentData const|
|修改|void setCurrentData( const QString &data ) const|

- ### 属性：currentIndex （类型：int 可读 可写）

当前项的索引（从0开始编号）。

| |调用方法|
| - | - |
|读取|int currentIndex const|
|修改|void setCurrentIndex( int index ) const|

- ### 属性：currentText （类型：QString 可读 可写）

当前项显示的文本。需要注意的是，调用 setCurrentText 时，并不是影响下拉列表中当前项显示的文本，而是从下拉列表的项目中查找到相同的文本（第一个匹配的），并将该项设置为当前项。如果找不到，就忽略。

| |调用方法|
| - | - |
|读取|QString currentText const|
|修改|void setCurrentText( const QString &text ) const|

- ### 属性：defaultVal （类型：QString 可读）

下拉列表框创建之后，将第一个匹配这个初始值的项目做为当前项。

| |调用方法|
| - | - |
|读取|QString defaultVal const|

- ### 属性：editable （类型：bool 可读 可写）

是否允许编辑。允许编辑的下拉列表可以直接输入文字。

| |调用方法|
| - | - |
|读取|bool editable const|
|修改|void setEditable( bool editable ) const|

- ### 属性：reference （类型：QString 可读 可写）

设置下拉列表对应的“引用列表”的名称。“引用列表”是一组“文本-数据”对，在表单设计阶段就可以进行设置。设置为“引用列表”的下拉列表框，会按其“文本-数据”的对应关系创建所有下拉列表中的项目。

| |调用方法|
| - | - |
|读取|QString reference const|
|修改|void setReference( const QString &text ) const|

- ### 属性：textList （类型：QStringList 可读 ）

以字符串列表的形式返回所有项目的显示文本。

| |调用方法|
| - | - |
|读取|QStringList textList const|

- ### 属性：valueList （类型：QStringList 可读 ）

以字符串列表的形式返回所有项目的数据。

| |调用方法|
| - | - |
|读取|QStringList valueList const|

---

## 下拉列表框自有成员函数

[返回目录](#category)

所有属性的设置函数（参考上一节中修改属性的接口），都属于此类，都可以当做槽使用。除此之处， 框架控件还包括以下成员函数：

|函数|接口|说明|
| - | - | - | 
|addItem|	void addItem(const QString  &t,const QString &v)	const|添加项目（添加到最后）|
|addItems|	void addItems(const QStringList  &t,const QStringList &v)	const|批量添加项目（添加到最后）|
|addList|	void addList(const QVariantList &v)	const|以“文本，数据”列表形式添加多个项目|
|clear|	void clear() const|清除所有项目|
|clearEditText|	void clearEditText ()	const|清除编辑的文本|
|findData|	int findData( const QString & data)	const|在项目中搜索数据|
|findText|	int findText( const QString & text)	const|在项目中搜索文本|
|insertItem|	void insertItem(int x,const QString  &t,const QString &v)	const|在指定位置插入项目|
|insertItems|	void insertItems(int x,const QStringList  &t,const QStringList &v)	const|在指定位置插入项目|
|insertList|	void insertList(int index,const QVariantList &v)	const|在指定位置插入列表（多项）|
|itemData|	QString itemData(int x)	const|返回指定项目的数据|
|itemText|	QString itemText(int x)	const|返回指定项目的文本|
|reloadReferenceList|	void reloadReferenceList()	const|重新加载“引用列表”中的列表|
|removeItem|	void removeItem(int x)	const|移除指定位置的项目|
|setEditText|	void setEditText ( const QString & text ) const|设置编辑文本|
|setItemList|	void setItemList(const QStringList &t,const QStringList &v) const|设置项目的文字和数据（清除原来所有项目）|
|setList|	void setList(const QVariantList &v) const|以“文本，数据”列表的形式设置列表|
|showPopup|	void showPopup()	const|显示下拉列表|

---

## 下拉列表框的信号

[返回目录](#category)

|信号|接口|说明|
| - | - | - | 
|activated|void activated ( int index ) |在用户选择了某项时发出此信号，即使选择并没有发生变化，index是所选项在列表中的顺序（从0开始）|
|activated|void activated ( const QString & text ) |在用户选择了某项时发出此信号，即使选择并没有发生变化，index是所选项显示的文本|
|currentIndexChanged|void currentIndexChanged ( int index )|选择其它项目时，发出此信号，index是所选项在列表中的顺序| 
|currentIndexChanged|void currentIndexChanged ( const QString & text ) |选择其它项目时，发出此信号，text是所选项显示的文字|
|editTextChanged|void editTextChanged ( const QString & text )|编辑的文本发生变化时发出此信号，text是编辑的最新内容|
|highlighted|void highlighted ( int index ) |在用户高亮某个项目时发出此信号，index是所选项在列表中的顺序|
|highlighted|void highlighted ( const QString & text ) |在用户高亮某个项目时发出此信号，text是该项目显示的文字|

---

## 可编程函数

[返回目录](#category)

- [可编程函数的详细说明](1-4-openscript?id=控件的可编程函数)

下拉列表框所有可编程函数的清单：

|函数|函数名|传入参数|返回值|说明|
| - | - | - | - | - |
|[缺省值](1-4-openscript?id=default) | 控件名_default | 无 |缺省显示的文本<br>**数据类型：字符串**| 返回控件的初始值。<br>下拉列表控件创建后，第一个匹配这个缺省值的项目会被设为当前项目。|
|[校验规则](1-4-openscript?id=validator)|控件名_validator|输入的文本|输入值是否合法<br>**数据类型：布尔**|如果输入值满足要求，返回True，否则返回False。<br>这个函数会在完成输入后被调用。<br>手工输入和程序修改都会调用此函数。|
|[鼠标进入时](1-4-openscript?id=enter)|控件名_enter|无|无|鼠标光标进入到这个控件时调用|
|[鼠标离开时](1-4-openscript?id=leave)|控件名_leave|无|无|鼠标光标离开这个控件时调用|
|[大小改变时](1-4-openscript?id=resize)|控件名_resize|无|无|控件大小改变时调用|
|[当拖曳进入时](1-4-openscript?id=dragEnter)|控件名_dragEnter|拖曳进入的元数据|是否接受拖曳进入<br>**数据类型：布尔**|当从外部拖曳一些内容进入到这个控件时，会调用此函数。<br>不接受拖曳的控件不会调用此函数。<br>通过脚本判断是否接受拖曳，<br>如果接受，返回 True，如果在控件上放开鼠标，程序会转而调用“当拖曳放下时”函数。<br>如果不接受，返回False，程序将不会调用“当拖曳放下时”函数。<br><br>**传入参数：**<br>format:元数据的格式列表，以列表类型传入<br>data:元数据的内容，以列表类型传入<br>dx:拖入的位置X坐标<br>dy:拖入的位置Y坐标|
|[当拖曳放下时](1-4-openscript?id=drop)|控件名_drop|拖曳放下的元数据|是否接受拖曳放下<br>**数据类型：布尔**|拖曳放下时调用。允许则返回 True，否则返回 False。<br><br>**传入参数：**<br>format:元数据的格式列表，以列表类型传入<br>data:元数据的内容，以列表类型传入<br>dx:放下的位置X坐标<br>dy:放下的位置Y坐标|
|[获得焦点](1-4-openscript?id=getfocus)|控件名_getfocus|无|无|获得焦点时调用|
|[失去焦点](1-4-openscript?id=lostfocus)|控件名_lostfocus|无|无|失去焦点时调用|
|[单次定时器超时时](1-4-openscript?id=singleshot)|控件名_singleshot|无|无|内置单次定时器超时时调用|
|[定时器超时时](1-4-openscript?id=timeout)|控件名_timeout|定时器的ID值|无|内置定时器超时时调用|

