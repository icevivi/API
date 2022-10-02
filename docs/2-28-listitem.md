# 第二章 标准控件 - 列表控件的条目

列表控件中每一项条目对应 listItemDelegate 对象。

---

<h2 id="category">目录</h2>

- [创建](#创建)

- [属性](#属性)

- [成员函数](#成员函数)

---

## 创建

[返回目录](#category)

有时列表控件的调用接口会需要 listItemDelegate* 做为传入参数，可能会需要创建一个新的对象。我们使用 pub 内置对象来创建这个类的一个实例。

调用接口：

|                                                         调用接口                                                         |                                           说明                                            |
| ----------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| listItemDelegate* listItem( listWidgetDelegate * parent = 0)  const                                                     | 创建一个列表条目对象实例，可以指定对应的列表控件，或者不指定，这个返回的对象显示的文本为空字符串 |
| 	listItemDelegate* listItem( const QString & text, listWidgetDelegate * parent = 0) const                              | 指定显示的文本，创建一个新的列表条目对象实例                                                 |
| 	listItemDelegate* listItem(  const QString & iconfile, const QString & text, listWidgetDelegate * parent = 0 )  const | 指定图标文件和显示的文本，创建一个新的列表条目对象实例                                        |
| 	listItemDelegate* listItem(  const QPixmap & icon, const QString & text, listWidgetDelegate * parent = 0 )  const     | 指定图标图像和显示的文本，创建一个新的列表条目对象实例                                        |
	
如以下代码所示：

``` python 

#创建一个显示文本为空字符串的条目 
item = pub.listItem(this.listWidget)

#设置它显示的文本
item.text = '这是一个列表条目'

#用文件设置图标
item = pub.listItem('d:\abc.png','这是一个列表条目') 

#也可以使用 Qt 的 QPixmap 
#先导入 Qt 模块
from PythonQt import Qt
#指定图标图像
item = pub.listItem(Qt.QPixmap('c:\abc.png'),'这是一个列表条目')

#从表单的图片集中取 QPixmap
item = pub.listItem(pub.getImage('abc.png'),'这是一个列表条目') 

```

## 属性

[返回目录](#category)

|    属性     |  值类型  | 读写类型  |    读取    |    赋值函数    |                                                                 说明                                                                  |
| ---------- | -------- | -------- | ---------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| checkState | int      | 可读 可写 | checkState | setCheckState | 勾选状态，与selected不同，这个是表示条目有勾选框时的勾选状态<br>取值： pub.UNCHECKED 未选中;pub.PARTIALLYCHECKED 部分选中;pub.CHECKED 选中 |
| data       | QString  | 可读 可写 | data       | setData       | 条目内部存储的值                                                                                                                       |
| font       | QFont    | 可读 可写 | font       | setFont       | 单元格的字体                                                                                                                          |
| isSelected | bool     | 可读 可写 | isSelected | setSelected   | 是否被选中 ，只表示这个条目是否被选择，与勾选状态不同                                                                                    |
| tag        | QVariant | 可读 可写 | tag        | setTag        | 备用的属性，可以用来存储额外的数据                                                                                                      |
| text       | QString  | 可读 可写 | text       | setText       | 条目显示的文字                                                                                                                         |
| toolTip    | QString  | 可读 可写 | toolTip    | setToolTip    | 单元格的工具提示                                                                                                                       |
| statusTip  | QString  | 可读 可写 | statusTip  | setStatusTip  | 单元格的状态栏提示                                                                                                                     |
| whatsThis  | QString  | 可读 可写 | whatsThis  | setWhatsThis  | 使用“这是什么？”时显示的帮助信息                                                                                                        |

## 成员函数

[返回目录](#category)

|       函数        |                          接口                          |                 说明                 |
| ----------------- | ------------------------------------------------------ | ----------------------------------- |
| background        | QColor background () const                             | 背景色                               |
| clone             | listItemDelegate * clone() const                       | 克隆这个单元格对象                    |
| foreground        | QColor foreground () const                             | 前景色                               |
| isCheckable       | bool isCheckable() const                               | 是否可以勾选                         |
| isChecked         | bool isChecked() const                                 | 如果允许勾选 ，是否在选中的状态       |
| isDragEnabled     | bool isDragEnabled() const                             | 是否允许拖拽                         |
| isDropEnabled     | bool isDropEnabled() const                             | 是否允许拖入放下                     |
| isEnabled         | bool isEnabled() const                                 | 是否可用                             |
| isHidden          | bool isHidden () const                                 | 是否隐藏                             |
| isNull            | bool isNull() const                                    | 是否是一个没有指向有效的单元格的空对象 |
| isSelectable      | bool isSelectable() const                              | 是否允许选择                         |
| setBackground     | void setBackground ( const QColor & brushcolor ) const | 设置背景色                           |
| setCheckable      | void setCheckable( bool v)                             | 设置是否允许勾选                     |
| setDragEnabled    | void setDragEnabled(bool v) const                      | 设置是否允许拖拽                     |
| setDropEnabled    | void setDropEnabled(bool v) const                      | 设置是否允许拖入放下                  |
| setEditable       | void setEditable( bool v) const                        | 设置是否允许编辑                     |
| setEnabled        | void setEnabled( bool v) const                         | 设置是否可用                         |
| setForeground     | void setForeground ( const QColor & brushcolor ) const | 设置前景色                           |
| setHidden         | void setHidden ( bool hide ) const                     | 设置是隐藏还是显示                    |
| setIcon           | void setIcon ( const QPixmap & icon ) const            | 设置图标（按图片设置）                |
| setIcon           | void setIcon ( const QString & iconfile ) const        | 设置图标（按文件名设置）              |
| setSelectable     | void setSelectable( bool v) const                      | 设置是否允许选择                     |
| setSizeHint       | void setSizeHint ( const QSize & size ) const          | 设置建议的尺寸                       |
| setTextHAlignment | void setTextHAlignment ( int alignment ) const         | 设置水平对齐方式                     |
| setTextVAlignment | void setTextVAlignment ( int alignment ) const         | 设置垂直对齐方式                     |
| sizeHint          | sizeHint QSize sizeHint () const                       | 建议的尺寸                           |
| textAlignment     | int textAlignment () const                             | 对齐方式                             |
| textHAlignment    | int textHAlignment () const                            | 水平方向对齐方式                     |
| textVAlignment    | int textVAlignment () const                            | 垂直方面对齐方式                     |
