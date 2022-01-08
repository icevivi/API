# 第二章 标准控件 - 树形控件的节点

树形控件中每一个节点是一个 treeItemDelegate 对象。它可以有多列。在调用树形控件的接口时经常需要用到它。

---

<h2 id="category">目录</h2>

- [创建](#创建)

- [属性](#属性)

- [成员函数](#成员函数)

---

## 创建

[返回目录](#category)

如果需要往树形控件里添加新的项目，需要先创建一个 treeItemDelegate 对象，再调用树形控件的接口添加到指定的位置。

调用接口：

|                                         调用接口                                          |                                    示例代码                                     |                          说明                          |
| ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------ |
treeItemDelegate* treeItem(  )  const;
	treeItemDelegate* treeItem ( const QStringList & strings )  const;
	treeItemDelegate* treeItem ( treeWidgetDelegate * parent)  const;
	treeItemDelegate* treeItem ( treeWidgetDelegate * parent, const QStringList & strings)  const;
	treeItemDelegate* treeItem ( treeWidgetDelegate * parent, treeItemDelegate * preceding )  const;

	treeItemDelegate* treeItem ( treeItemDelegate * parent ) const;
	treeItemDelegate* treeItem ( treeItemDelegate * parent, const QStringList & strings)  const;
	treeItemDelegate* treeItem ( treeItemDelegate * parent, treeItemDelegate * preceding )  const;


如以下代码所示：

``` python 

#创建一个新的树形控件项目
item=pub.treeItem()
#设置这个项目第一列显示的文字
item.setText(0,'上海')
#将它添加到树形控件中，做为顶级节点
this.tree.addTopLevelItem(item)

#添加后还可以继续修改其属性，修改会影响到树形控件中的显示
item.setText(1,'是')

#也可以创建时就设置好文字，注意要用列表做为传入参数
#如果列表中元素数量超出列数，超出部分会被忽略，如果不足，对应列显示空字符串
item2=pub.treeItem(['天津','是'])
this.tree.addTopLevelItem(item2)

#如果传入参数是一个字符串，会被拆成一个一个字符分别填入每列
item3=pub.treeItem('天津')
#下面这句执行后，该行第一列是“天”，第二列是“津”。
this.tree.addTopLevelItem(item3)

```

## 属性

[返回目录](#category)

|属性|值类型|读写类型|说明|
| - | - | - | - |
|columnCount|int|可读 |列数量|
|childCount|int|可读 |子节点的数量|
|isSelected|bool|可读 可写|是否被选中|
|tag|QVariant|可读 可写|保留用做存储额外的数据|

- ### 属性：columnCount （类型：int 可读 ）

列的数量。

|      |         调用方法         |
| ---- | ----------------------- |
| 读取 | int columnCount() const |

- ### 属性：childCount （类型：int 可读 ）

下级节点的数量。只计算最近的一级，下级的下级不计算在内。

|      |        调用方法         |
| ---- | ---------------------- |
| 读取 | int childCount() const |

- ### 属性：isSelected （类型：bool 可读 可写）

是否被选中。

|      |                 调用方法                 |
| ---- | --------------------------------------- |
| 读取 | bool isSelected() const                 |
| 修改 | void setSelected( bool selected ) const |

- ### 属性：tag （类型：QVariant 可读 可写）

保留用做存储额外的数据。

|      |                  调用方法                   |
| ---- | ------------------------------------------ |
| 读取 | QVariant tag() const                       |
| 修改 | void setTag( const QVariant &value ) const |

---

## 成员函数

[返回目录](#category)

|函数|接口|说明|
| - | - | - | 
|addChild|	void addChild ( treeItemDelegate * child )  const|添加下级项目|
|background|	QColor background (int column) const			|返回指定列的背景色|
|child|	treeItemDelegate * child ( int index ) const|获取指定序号的下级项目|
|clone|	treeItemDelegate * clone () const|对这个项目进行克隆|
|font|	QFont font (int column) const	|返回指定列的字体|
|foreground|	QColor foreground (int column) const	|返回指定列的前景色|
|indexOfChild|	int indexOfChild ( treeItemDelegate * child ) const |返回下级项目的序号|
|insertChild|	void insertChild ( int index, treeItemDelegate * child )  const|在指定位置插入下级项目|
|isDisabled|	bool isDisabled () const |是否不可用|
|isDragEnabled|	bool isDragEnabled() const|是否允许拖拽|
|isDropEnabled|	bool isDropEnabled() const|是否允许拖拽放下|
|isEnabled|	bool isEnabled() const|是否可用|
|isExpanded|	bool isExpanded () const |是否可以展开|
|isFirstColumnSpanned|	bool isFirstColumnSpanned () const |首列是否合并了其它列|
|isHidden|	bool isHidden () const |是否隐藏|
|isNull|	bool isNull() const	|是否为空|
|parent|	treeItemDelegate * parent () const |上级对象|
|removeChild|	void removeChild ( treeItemDelegate * child )  const|移除指定的下级项目|
|setBackground|	void setBackground ( int column, const QColor & brush )  const|设置指定列的背景色|
|setDisabled|	void setDisabled ( bool disabled )  const|设置是否不可用|
|setDragEnabled|	void setDragEnabled( bool v)  const|设置是否允许拖拽|
|setDropEnabled|	void setDropEnabled( bool v)  const|设置是否允许拖拽放下|
|setEnabled|	void setEnabled( bool v)  const|设置是否可用|
|setExpanded|	void setExpanded ( bool expand )  const|设置是否可展开|
|setFirstColumnSpanned|	void setFirstColumnSpanned ( bool span ) const|设置是否将首列合并所有列|
|setFont|	void setFont ( int column,const QFont & font )	 const|设置字体|
|setForeground|	void setForeground ( int column, const QColor & brush )  const|设置指定列的前景色|
|setHidden|	void setHidden ( bool hide )  const|设置是否隐藏|
|setIcon|	void setIcon (int column , const QString & iconfile ) const|设置指定列的图标，指定文件名|
|setIcon|	void setIcon (int column ,  const QPixmap & icon )	 const|设置指定列的图标对应的图像|
|setSelected|	void setSelected ( bool select )		 const|设置是否选中|
|setSizeHint|	void setSizeHint ( int column, const QSize & size )  const|设置指定列的提示尺寸，如果不指定提示尺寸，则将基于项目的数据计算提示尺寸|
|setStatusTip|	void setStatusTip (  int column,const QString & statusTip ) const|设置指定列的工具栏提示文字|
|setText|	void setText ( int column, const QString & text ) const|设置指定列显示的文字|
|setTextHAlignment|	void setTextHAlignment ( int column, int alignment ) const|设置指定列的水平对齐方式<br>pub.ALIGNLEFT 向左对齐<br>pub.ALIGNRIGHT 向右对齐<br>pub.ALIGNHCENTER 水平居中对齐<br>pub.ALIGNJUSTIFY 水平分散对齐）|
|setTextList|	void setTextList(const QStringList &list) const|按字符串列表设置每一列显示的文字|
|setTextVAlignment|	void setTextVAlignment ( int column, int alignment ) const|设置指定列的垂直对齐方式<br>pub.ALIGNTOP 向上对齐<br>pub.ALIGNBOTTOM 向下对齐<br>pub.ALIGNVCENTER 垂直居中对齐|
|setToolTip|	void setToolTip (  int column,const QString & toolTip )		 const|设置指定列的工具提示|
|setWhatsThis|	void setWhatsThis (  int column,const QString & whatsThis )  const|设置指定列的“这是什么”提示文本|
|sizeHint|	QSize sizeHint ( int column ) const |返回指定列的提示尺寸|
|sortChildren|	void sortChildren ( int column, bool ascorder = true )  const|对指定的下级项目进行排序|
|statusTip|	QString statusTip (int column) const	|返回指定列的状态栏提示文本|
|takeChild|	treeItemDelegate * takeChild ( int index )  const|取出指定序号的下级项目|
|text|	QString text (int column) const	|获取指定列的显示文本|
|textAlignment|	int textAlignment ( int column ) const |返回指定列的对齐方式|
|textHAlignment|	int textHAlignment ( int column ) const |返回指定列的水平对齐方式|
|textList|	QStringList textList() const|返回所有列显示的文本|
|textVAlignment|	int textVAlignment ( int column ) const |返回指定列的垂直对齐方式|
|toolTip|	QString toolTip (int column) const|返回指定列的工具提示文本|
|whatsThis|	QString whatsThis (int column) const|返回指定列的“这是什么”提示文本|


