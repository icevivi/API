# 第二章 标准控件 - 表格控件的单元格

表格控件中每一个单元格是一个 tableCellDelegate 对象，多个连续的单元格，则是 tableRangeDelegate 对象。在调用表格的接口时需要用到这两种对象类型。

---

<h2 id="category">目录</h2>

- [单元格的创建](#创建单元格)

- [单元格的属性](#单元格的属性)

- [单元格的成员函数](#单元格的成员函数)

- [单元格范围](#单元格范围)

- [单元格范围的属性](#单元格范围的属性)

---

## 创建单元格

[返回目录](#category)

有时表格控件的调用接口会需要 tableCellDelegate* 做为传入参数，可能会需要创建一个新的对象。我们使用 pub 内置对象来创建这个类的一个实例。

调用接口：

|                                         调用接口                                          |                                    示例代码                                     |                          说明                          |
| ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------ |
| tableCellDelegate* tableCell(  ) const                                                   | cell=pub.tableCell()                                                            | 创建的单元格对象的文本为空字符串，也未指定图标            |
| tableCellDelegate* tableCell( const QString & text) const                                | cell=pub.tableCell('姓名')                                                      | 指定单元显示的文本                                      |
| tableCellDelegate* tableCell( const QString & iconFileName, const QString & text ) const | cell=pub.tableCell('d:\abc.png','姓名')                                         | 指定图标文件和显示的文本                                 |
| tableCellDelegate* tableCell( const QPixmap & icon, const QString & text ) const         | cell=pub.tableCell(pub.getImage('abc.png'),'姓名')                              | 指定图标和显示的文本，这个示例显示从表单的图片集中获取图片 |
|                                                                                          | from PythonQt import Qt <br>cell=pub.tableCell(Qt.QPixmap('c:\abc.png'),'姓名') | 也可以用 PythonQt 的接口创建 QPixmap                    |

使用 tableCellDelegate 对象，可以参考以下示例所示：

``` python 

#创建一个 tableCellDelegate 对象，并将单元格(0,0)设置为这个对象
newcell=pub.tableCell('姓名')
this.table.setCell(0,0,cell)

#不用 tableCellDelegate ，也可以直接设置单元格显示的文字
#比如下一句this.table.cell(0,0)会返回一个 tableCellDelegate 对象的指针
this.table.cell(0,0).text = '姓名'

```

## 单元格的属性

[返回目录](#category)

属性调用示例：
``` python 

#得到单元格对象
cell=this.table.cell(0,0)
#读取属性
print(cell.toolTip)
#写属性
cell.toolTip='这是一本书'
#或者调用为属性赋值的函数
cell.setToolTip('这是一本书')

```

|    属性     |  值类型  | 读写类型  |    读取    |   赋值函数    |               说明               |
| ---------- | -------- | -------- | ---------- | ------------ | -------------------------------- |
| column     | int      | 可读      | column     |              | 单元格所在列                     |
| font       | QFont    | 可读 可写 | font       | setFont      | 单元格的字体                     |
| isSelected | bool     | 可读 可写 | isSelected | setSelected  | 是否被选中                       |
| row        | int      | 可读      | row        |              | 单元格所在行                     |
| text       | QString  | 可读 可写 | text       | setText      | 单元格显示的文字                  |
| value      | QVariant | 可读 可写 | value      | setValue     | 单元格内部存储的值                |
| toolTip    | QString  | 可读 可写 | toolTip    | setToolTip   | 单元格的工具提示                  |
| statusTip  | QString  | 可读 可写 | statusTip  | setStatusTip | 单元格的状态栏提示                |
| whatsThis  | QString  | 可读 可写 | whatsThis  | setWhatsThis | 使用“这是什么？”时显示的帮助信息   |
| tag        | QVariant | 可读 可写 | tag        | setTag       | 备用的属性，可以用来存储额外的数据 |

---

## 单元格的成员函数

[返回目录](#category)

|       函数        |                          接口                          |                 说明                 |
| ----------------- | ------------------------------------------------------ | ----------------------------------- |
| isNull            | bool isNull() const	                                 | 是否是一个没有指向有效的单元格的空对象 |
| textVAlignment    | int textVAlignment () const		                     | 垂直方面对齐方式                     |
| textHAlignment    | int textHAlignment () const		                     | 水平方向对齐方式                     |
| textAlignment     | int textAlignment () const		                     | 对齐方式                             |
| background        | QColor background () const			                 | 背景色                               |
| clone             | tableCellDelegate * clone() const                      | 克隆这个单元格对象                    |
| isEditable        | bool isEditable() const	                             | 是否要编辑                           |
| isDragEnabled     | bool isDragEnabled() const                             | 是否允许拖拽                         |
| isDropEnabled     | bool isDropEnabled() const                             | 是否允许拖入放下                     |
| isEnabled         | bool isEnabled() const	                             | 是否可用                             |
| foreground        | QColor foreground () const                             | 前景色                               |
| isSelectable      | bool isSelectable() const                              | 是否允许选择                         |
| setBackground     | void setBackground ( const QColor & brushcolor ) const | 设置背景色                           |
| isCheckable       | bool isCheckable() const                               | 是否可以勾选                         |
| setCheckable      | void setCheckable( bool v)                             | 设置是否允许勾选                     |
| isChecked         | bool isChecked() const                                 | 如果允许勾选 ，是否在选中的状态       |
| setSelectable     | void setSelectable( bool v) const                      | 设置是否允许选择                     |
| setEditable       | void setEditable( bool v) const                        | 设置是否允许编辑                     |
| setDragEnabled    | void setDragEnabled(bool v) const                      | 设置是否允许拖拽                     |
| setDropEnabled    | void setDropEnabled(bool v) const                      | 设置是否允许拖入放下                  |
| setEnabled        | void setEnabled( bool v) const                         | 设置是否可用                         |
| setForeground     | void setForeground ( const QColor & brushcolor ) const | 设置前景色                           |
| setIcon           | void setIcon ( const QString & iconfile ) const        | 设置图标（按文件名设置）              |
| setIcon           | void setIcon ( const QPixmap & icon ) const            | 设置图标（按图片设置）                |
| sizeHint          | sizeHint QSize sizeHint () const						 | 建议的尺寸                           |
| setSizeHint       | void setSizeHint ( const QSize & size )	const        | 设置建议的尺寸                       |
| setTextVAlignment | void setTextVAlignment ( int alignment ) const         | 设置垂直对齐方式                     |
| setTextHAlignment | void setTextHAlignment ( int alignment ) const         | 设置水平对齐方式                     |

## 单元格范围

表格控制的接口中有时会用到 tableRangeDelegate 类。在 biForm 中并不需要直接创建一个与表格控件无关的 tableRangeDelegate 对象，只在使用表格控件的这些接口时，会返回 tableRangeDelegate 对象，以下几个调用接口会创建这一类对象。

相关表格控件的调用接口：

|                                   调用接口                                   |                                              说明                                              |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| tableRangeDelegate* selectedRange(int index) const                          | 与selectedRangesCount配套使用,通过 index 返回选中的单元格中第 index 个连续区域对应的单元格区域对象 |
| tableRangeDelegate* range( int top, int left, int bottom, int right ) const | 设置左上角和右下角对应的行和列来创建一个单元格区域对象                                            |

如以下代码所示：

``` python 

#假设选择了不连续的两个区域，返回第二个选中的区域
range=this.table.selectedRange(1)

#指定范围
range = this.table.range(0,1,5,3)

#设置这块区域为被选中的状态
this.table.setRangeSelected(range,True)

#删除掉这几个区域中所有单元格，第二个参数为 True 表示删除后下方单元格上移
this.table.removeRange(range,True,False)

#删除掉这几个区域中所有单元格，第三个参数为 True 表示删除后右方单元格左移
this.table.removeRange(range,False,True)

```

使用 tableRangeDelegate 类做为传入参数的几个函数：

|                                           调用接口                                            |                                说明                                 |
| -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| void setRangeSelected ( const tableRangeDelegate* range, bool select ) const                 | 设置这个单元格区域是否被选中                                          |
| void removeRange(tableRangeDelegate* range,bool downToUp=false,bool rightToLeft=false) const | 删除这个区域内所有单元格，可以选择下方单元格移或右方单元格左移来填补空位 |

## 单元格范围的属性

[返回目录](#category)

|    属性     |  值类型  | 读写类型  |               说明               |
| ----------- | -------- | -------- | -------------------------------- |
| bottomRow   | int      | 可读     | 最下方的单元格所在行              |
| columnCount | int      | 可读     | 列数                             |
| leftColumn  | int      | 可读     | 最左方的单元格所在列              |
| rightColumn | int      | 可读     | 最右方的单元格所在列              |
| rowCount    | int      | 可读     | 行数                             |
| topRow      | int      | 可读     | 最上方的单元格所在行              |
| tag         | QVariant | 可读 可写 | 备用的属性，可以用来存储额外的数据 |

