# 表单的成员函数和信号

<h2 id="category">目录</h2>

- [成员函数（槽函数）](#表单的成员函数（槽）)

  - [与数据库操作相关的函数](#与数据库操作相关的函数)
  - [与按钮组操作相关的函数](#与按钮组操作相关的函数)
  - [与定时器相关的成员函数](#与定时器相关的成员函数)
  - [与布局相关的成员函数](#与布局相关的成员函数)
  - [与图像相关的成员函数](#与图像相关的成员函数)
  - [与引用列表相关的成员函数](#与引用列表相关的成员函数)
  - [与打印和输出相关的成员函数](#与打印和输出相关的成员函数)
  - [与消息提示相关的成员函数](#与消息提示相关的成员函数)
  - [其它成员函数](#其它成员函数)
  
- [信号](#表单的信号)

---

## 表单的成员函数（槽）

[返回目录](#category)

|                            函数                             |                                         接口                                         |                      说明                       |
| ----------------------------------------------------------- | ------------------------------------------------------------------------------------ | ---------------------------------------------- |
| [accept](#accept)                                           | void accept(const QVariant& v=QVariant()) const                                      | 以接受方式关闭以弹出对话框显示的这个表单并返回数据 |
| [addArg](#addArg)                                           | void addArg(const QVariant &arg)                                                     | 添加传入参数                                    |
| [addCheckBoxGroup](#addCheckBoxGroup)                       | checkBoxGroupDelegate* addCheckBoxGroup(const QString &name,bool exclusive = false)  | 添加复选按钮组                                  |
| [addDBConnection](#addDBConnection)                         | DBConnectionDelegate* addDBConnection(const QString& name)                           | 创建新的数据库连接                               |
| [addWidget](#addWidget)                                     | void addWidget(QWidget* widget,int x=0,int y=0) const                                | 添加控件                                        |
| [allobject](#allobject)                                     | QStringList allobject()                                                              | 所有子控件的名称清单                             |
| [args](#args)                                               | QVariantList args() const                                                            | 所有传入参数                                    |
| [baseSQL](#baseSQL)                                         | QString baseSQL() const                                                              | 基础SQL语句                                     |
| [baseWidget](#baseWidget)                                   | QWidget* baseWidget() const                                                          | 表单控件对象                                    |
| [broadcastTableUpdated](#broadcastTableUpdated)             | void broadcastTableUpdated(const QStringList &tableNames) const                      | 广播某些表的数据有被修改过                       |
| [buttonGroup](#buttonGroup)                                 | radioButtonGroupDelegate* buttonGroup() const                                        | 单选按钮组                                      |
| [buttonGroupCount](#buttonGroupCount)                       | int buttonGroupCount() const                                                         | 多选按钮组的数量                                 |
| [checkBoxGroup](#checkBoxGroup)                             | checkBoxGroupDelegate* checkBoxGroup(const QString &name) const                      | 返回批定名称的复选框选按钮组                     |
| [close](#close)                                             | void close() const                                                                   | 关闭这个表单                                    |
| [contextName](#contextName)                                 | QString contextName() const                                                          | 对应的python模块名                              |
| [createNew](#createNew)                                     | void createNew() const                                                               | 创建一个新的空白表单                             |
| [currentRecordIndex](#currentRecordIndex)                   | int currentRecordIndex()                                                             | 当前记录的顺序号                                 |
| [currentState](#currentState)                               | int currentState()                                                                   | 表单的当前状态                                  |
| [database](#database)                                       | DBDelegate* database()  const                                                        | 表单对应的数据库连接对象                         |
| [DBConnection](#DBConnection)                               | DBConnectionDelegate* DBConnection(const QString& name) const                        | 按名称返回数据库连接对象                         |
| [DBConnections](#DBConnections)                             | QStringList formDelegate::DBConnections() const                                      | 所有数据库连接对象的名称清单                     |
| [directPreview](#directPreview)                             | void directPreview() const                                                           | 按表单界面打印预览                               |
| [directPrinting](#directPrinting)                           | void directPrinting() const                                                          | 按表单界面打印                                  |
| [drop](#drop)                                               | void drop() const                                                                    | 删除当前记录                                    |
| [ensureWidgetVisible](#ensureWidgetVisible)                 | void ensureWidgetVisible(const QString& name) const                                  | 确保某个控件可见                                 |
| [exportAllToXLS](#exportAllToXLS)                           | void exportAllToXLS(const QString& fileName="")                                      | 导出查询出的所有记录到XLS文件                    |
| [exportCurrentToXLS](#exportCurrentToXLS)                   | void exportCurrentToXLS(const QString& fileName="")                                  | 导出当前记录到XLS文件                            |
| [exportToPFD](#exportToPFD)                                 | void exportToPFD()                                                                   | 导出为PFD文件                                   |
| [exportToXLSByFilter](#exportToXLSByFilter)                 | void exportToXLSByFilter(const QString& fileName="",const QString& filter="")        | 导出过滤后的记录到XLS文件                        |
| [findReferenceText](#findReferenceText)                     | int findReferenceText(const QString& reference, const QString& text) const           | 在引用列表中查找文本                             |
| [findReferenceValue](#findReferenceValue)                   | int findReferenceValue(const QString& reference, const QString& value) const         | 在引用列表中查找值                               |
| [finishWaiting](#finishWaiting)                             | void finishWaiting() const                                                           | 结束进度对话框                                  |
| [formatPreview](#formatPreview)                             | void formatPreview() const                                                           | 格式化打印预览                                  |
| [formatPrinting](#formatPrinting)                           | void formatPrinting() const                                                          | 格式化打印                                      |
| [getArg](#getArg)                                           | QVariant getArg(const QString& key) const                                            | 按键值获取传入参数的值                           |
| [getCurrentLastUpdated](#getCurrentLastUpdated)             | QString getCurrentLastUpdated() const                                                | 返回当前记录的 lastUpdated 的值                  |
| [getCurrentNo](#getCurrentNo)                               | QString getCurrentNo()                                                               | 返回当前记录的关键字段的值                       |
| [getCurrentUUID](#getCurrentUUID)                           | QString getCurrentUUID() const                                                       | 返回当前记录的 UUID 字段的值                     |
| [getImage](#getImage)                                       | QPixmap getImage(const QString &name)  const                                         | 从图片集里按名称获取图片                         |
| [getImageList](#getImageList)                               | QStringList getImageList()                                                           | 返回图片集里所有自定义图片的清单                  |
| [getMovie](#getMovie)                                       | QMovie* getMovie(const QString &name)  const                                         | 从图片集里按名称获取动画图片                     |
| [getReferenceCount](#getReferenceCount)                     | int getReferenceCount(const QString& reference) const                                | 返回指定引用列表中条目的数量                     |
| [getReferenceData](#getReferenceData)                       | QStringList getReferenceData(const QString& reference, int index) const              | 返回指定引用列表里某一个条目的显示文字和值        |
| [getReferenceText](#getReferenceText)                       | QString getReferenceText(const QString& reference, int index) const                  | 返回指定引用列表里某一个条目的显示文字            |
| [getReferenceValue](#getReferenceValue)                     | QString getReferenceValue(const QString& reference, int index) const                 | 返回指定引用列表里某一个条目的值                  |
| [grab](#grab)                                               | QPixmap grab() const                                                                 | 这个表单的截图                                  |
| [hide](#hide)                                               | void hide() const                                                                    | 隐藏这个表单                                    |
| [hideBalloon](#hideBalloon)                                 | void hideBalloon() const                                                             | 隐藏汽泡提示                                    |
| [hideList](#hideList)                                       | void hideList() const                                                                | 隐藏查询结果列表                                 |
| [hideListColumn](#hideListColumn)                           | void hideListColumn(const QString & fieldName) const                                 | 隐藏查询结果列表中某个字段                       |
| [hscrollto](#hscrollto)                                     | void hscrollto ( int value ) const                                                   | 垂直滚动条滚动到指定位置                         |
| [horizontalScrollBarMaxValue](#horizontalScrollBarMaxValue) | int horizontalScrollBarMaxValue() const                                              | 水平滚动条是否可见                               |
| [horizontalScrollBarVisible](#horizontalScrollBarVisible)   | bool horizontalScrollBarVisible() const                                              | 水平滚动条是否可见                               |
| [importFromPFD](#importFromPFD)                             | void importFromPFD()                                                                 | 从PFD文件导入数据                               |
| [isDebug](#isDebug)                                         | bool isDebug() const                                                                 | 是否在 debug 环境下                             |
| [isExtentTable](#isExtentTable)                             | bool isExtentTable(const QString& tablename) const                                   | 某个表是否是主表的扩展表                         |
| [isMine](#isMine)                                           | bool isMine() const                                                                  | 是否是本地发布（注册）的表单                     |
| [isNull](#isNull)                                           | bool isNull()                                                                        | 是否是空的表单对象                               |
| [jumpToBegin](#jumpToBegin)                                 | void jumpToBegin()                                                                   | 转到记录集第一条                                 |
| [jumpToEnd](#jumpToEnd)                                     | void jumpToEnd()                                                                     | 转到记录集最后一条                               |
| [jumpToIndex](#jumpToIndex)                                 | void jumpToIndex(int index)                                                          | 转到记录集指定位置                               |
| [jumpToNext](#jumpToNext)                                   | void jumpToNext()                                                                    | 转到记录集下一条                                 |
| [jumpToPrevious](#jumpToPrevious)                           | void jumpToPrevious()                                                                | 转到记录集前一条                                 |
| [jumpToRecordByKey](#jumpToRecordByKey)                     | bool jumpToRecordByKey(const QString &key)                                           | 转到匹配指定关键字的记录                         |
| [jumpToRecordByUUID](#jumpToRecordByUUID)                   | bool jumpToRecordByUUID(const QString &UUID)                                         | 转到匹配UUID的记录                              |
| [killAllTimer](#killAllTimer)                               | void killAllTimer() const                                                            | 停掉所有定时器                                  |
| [killTimer](#killTimer)                                     | bool killTimer ( int id )                                                            | 停掉指定的定时器                                 |
| [lastSavedUUID](#lastSavedUUID)                             | QString lastSavedUUID() const                                                        | 最近保存的记录的UUID                             |
| [object](#object)                                           | QObject* object(const QString &name)                                                 | 按名称返回指定的控件                             |
| [owner](#owner)                                             | QString owner() const                                                                | 表单的发布者                                    |
| [preview](#preview)                                         | void preview() const                                                                 | 打印预览                                        |
| [printing](#printing)                                       | void printing() const                                                                | 打印                                            |
| [printToPDF](#printToPDF)                                   | void printToPDF()                                                                    | 打印到PDF文件                                   |
| [query](#query)                                             | QString query(const QString& filter="",bool isSilence=false,const QString& order="") | 查询                                            |
| [queryByFilter](#queryByFilter)                             | void queryByFilter()                                                                 | 弹出设定过滤条件查询对话框进行查询                |
| [recordCount](#recordCount)                                 | int recordCount()                                                                    | 当前记录集的记录数                               |
| [refresh](#refresh)                                         | void refresh() const                                                                 | 刷新记录集                                      |
| [reject](#reject)                                           | void reject() const                                                                  | 以拒绝方式关闭做为弹出对话框的这个表单            |
| [removeCheckBoxGroup](#removeCheckBoxGroup)                 | bool removeCheckBoxGroup(const QString &name) const                                  | 删除指定名称的多选按钮组                         |
| [removeDBConnection](#removeDBConnection)                   | bool removeDBConnection(const QString& name)                                         | 删除指定名称的数据库连接                         |
| [resize](#resize)                                           | void resize(int w, int h) const                                                      | 调整大小                                        |
| [save](#save)                                               | void save()                                                                          | 保存当前记录                                    |
| [self](#self)                                               | QWidget* self()                                                                      | 返回表单控件对象                                 |
| [setAllReadOnly](#setAllReadOnly)                           | void setAllReadOnly() const                                                          | 设置所有控件为只读状态                           |
| [setArgs](#setArgs)                                         | void setArgs(const QVariantList &arg)                                                | 设置传入参数                                    |
| [setBaseWidget](#setBaseWidget)                             | void setBaseWidget(QWidget* widget) const                                            | 设置基础控件                                    |
| [setHLayout](#setHLayout)                                   | void setHLayout(const QStringList &widgetList, int left=0                            | 设置水平布局                                    |
|                                                             | 　　　　,int top=0, int right=0, int bottom=0,int spacing=0) const                    |                                                |
| [setHSplitter](#setHSplitter)                               | void setHSplitter(const QStringList &widgetList                                      | 设置水平可调布局                                 |
|                                                             | 　　　　,int left=0, int top=0, int right=0, int bottom=0,int spacing=0) const        |                                                |
| [setSubStep](#setSubStep)                                   | void setSubStep(int v) const                                                         | 设置进度对话框的子进度值                         |
| [setVLayout](#setVLayout)                                   | void setVLayout(const QStringList &widgetList, int left=0,                           | 设置垂直布局                                    |
|                                                             | 　　　　,int top=0, int right=0, int bottom=0,int spacing=0) const                    |                                                |
| [setVSplitter](#setVSplitter)                               | void setVSplitter(const QStringList &widgetList, int left=0                          | 设置垂直可调布局                                 |
|                                                             | 　　　　,int top=0, int right=0, int bottom=0,int spacing=0) const                    |                                                |
| [setWaitingMsg](#setWaitingMsg)                             | void setWaitingMsg(const QString& msg)                                               | 设置进度对话框显示的文本                         |
| [setWaitingStep](#setWaitingStep)                           | void setWaitingStep(const QString& msg,int v)                                        | 设置进度对话框显示的文本和进度值                  |
| [show](#show)                                               | void show() const                                                                    | 显示                                            |
| [showDownUp](#showDownUp)                                   | void showDownUp() const                                                              | 表单显示在下方，列表显示在上方                    |
| [showForm](#showForm)                                       | void showForm() const                                                                | 只显示表单                                      |
| [showLeftRight](#showLeftRight)                             | void showLeftRight() const                                                           | 表单显示在左侧，列表显示在右侧                    |
| [showList](#showList)                                       | void showList() const                                                                | 只显示列表                                      |
| [showListColumn](#showListColumn)                           | void showListColumn(const QString & fieldName) const                                 | 设置查询记录列表中某列显示                       |
| [showRightLeft](#showRightLeft)                             | void showRightLeft() const                                                           | 表单显示在右侧，列表显示在左侧                    |
| [showSplashMsg](#showSplashMsg)                             | void showSplashMsg(const QString& msg,bool error=false) const                        | 显示快显消息提示                                 |
| [showUpDown](#showUpDown)                                   | void showUpDown() const                                                              | 表单显示在上方，列表显示在下方                    |
| [showWaiting](#showWaiting)                                 | void showWaiting(const QString& title ) const                                        | 显示进度对话框                                  |
| [SQL_Fields](#SQL_Fields)                                   | QVariantList SQL_Fields() const                                                      | 返回基础SQL中字段的属性清单                      |
| [SQL_FromTables](#SQL_FromTables)                           | QStringList SQL_FromTables() const                                                   | 返回基础SQL中使用的表名                         |
| [startSingleShot](#startSingleShot)                         | void startSingleShot ( int interval )                                                | 启动单次定时器                                  |
| [startTimer](#startTimer)                                   | int startTimer ( int interval )                                                      | 启动定时器                                      |
| [tableAlias](#tableAlias)                                   | QString tableAlias(const QString& tablename) const                                   | 返回基础SQL中某个表的别名                        |
| [timers](#timers)                                           | QStringList timers() const                                                           | 返回所有定时器的ID值清单                         |
| [vscrollto](#vscrollto)                                     | void vscrollto ( int value ) const                                                   | 垂直滚动条滚动到指定位置                         |
| [verticalScrollBarMaxValue](#verticalScrollBarMaxValue)     | int verticalScrollBarMaxValue() const                                                | 垂直滚动条最大值                                 |
| [verticalScrollBarVisible](#verticalScrollBarVisible)       | bool verticalScrollBarVisible() const                                                | 垂直滚动条是否可见                               |

## 与数据库操作相关的函数

- ### addDBConnection

调用接口：DBConnectionDelegate* addDBConnection(const QString& name) 

[返回目录](#category)

这个函数用来创建一个新的表单级的数据库连接对象。PFF的运行时环境（比如biReader）必然会有后台数据库。目前 biReader 只连接一个数据源供自己使用。如果表单的功能需要访问其它数据源，就可以使用此函数连接创建新的数据库连接，给连接起个名字以便加以区分。需要注意的是，这些数据库连接会在表单关闭时断开。函数返回的是一个 DBConnectionDelegate 对象，关于它的接口请参考[数据库](1-8-database)。

|   内容   | 名称 |        数据类型        |      说明       |
| ------- | ---- | --------------------- | --------------- |
| 传入参数 | name | QString               | 数据库连接的名称 |
| 返回值   |      | DBConnectionDelegate* | 数据库连接对象   |

- ### baseSQL

调用接口：QString baseSQL() const

[返回目录](#category)

这个函数会返回针对主表的基础的SQL语句，即不带过滤条件的、返回所有字段的SQL语句。如果主表设置了“外键“，SQL语句中会使用 left join 关联的表，同时会返回关联表有关联的那个字段。

比如“我的书籍”使用 ```this.form.baseSQL()```返回的内容：

``` python
>>> this.form.baseSQL()
'select t0.ID,t0.fname,t0.fauthor,t0.fclass,t0.fyear,t0.fISBN,t0.UUID,t0.lastUpdated 
from RT_T_BOOK_1_S t0 '
```

另外一个表单“出纳日记账”，因为主表有设置“外键”，facctID 关联到 t_bankaccount 表的 ID 字段。其中主表 RT_T_CASH_0_S 会使用别名 t0，关联的另外一个表 RT_T_BANKACCOUNT_0_S 表会使用别名 O_t1。返回的内容如下：

``` python
>>> this.form.baseSQL()
'select t0.ID,O_t1.fname,t0.findex,t0.fdate,t0.fdebit,t0.fcredit,t0.fcontact,t0.foperator,t0.finputDate,t0.fmemo,t0.fremark,t0.UUID,t0.lastUpdated 
from RT_T_CASH_0_S t0   
     left join RT_T_BANKACCOUNT_0_S O_t1 
     on t0.facctID=O_t1.ID '
```

通常开发者并不需要使用这个函数返回的SQL语句来操作数据库。PFF的运行时引擎也有可能将来会修改这个函数的返回值的内容，而且运行时表名也是动态的，因此同一个表单，这个函数返回的内容也并不是固定的，因此不建议开发者依赖于这个函数的返回值进行数据库操作。

|   内容   | 名称 | 数据类型 |                说明                 |
| ------- | ---- | ------- | ----------------------------------- |
| 传入参数 | 无   |         |                                     |
| 返回值   |      | QString | 不带过滤条件的主表的所有字段的SQL语句 |

- ### createNew

调用接口：void createNew() const

[返回目录](#category)

这个函数用于创建一个新的空白表单，等同于在表单的工具栏上按下“新建”按钮。但如果这个按钮处于不可用的状态，或表单的属性“createNewEnabled”值为 False， 调用无效。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### currentRecordIndex

调用接口：int currentRecordIndex()

[返回目录](#category)

这个函数返回在表单查询返回的记录集中，当前记录所处的顺序号（从0开始）。这个只是在返回的记录集中的序号，并不是保存在数据库中的记录的序号。

|   内容   | 名称 | 数据类型 |          说明           |
| ------- | ---- | ------- | ---------------------- |
| 传入参数 | 无   |         |                        |
| 返回值   |      | int     | 当前记录在记录集中的序号 |

- ### currentState

调用接口：int currentState()

[返回目录](#category)

这个函数返回当前表单的状态。返回值的说明参考信号 [statusChanged](#statusChanged)。

|   内容   | 名称 | 数据类型 |    说明    |
| ------- | ---- | ------- | --------- |
| 传入参数 | 无   |         |           |
| 返回值   |      | int     | 当前状态值 |

- ### database

调用接口：DBDelegate* database()  const

[返回目录](#category)

这个函数返回当前表单后台使用的数据库连接对象。关于其调用接口，参考 [数据库](1-8-database)。

|   内容   | 名称 |   数据类型   |     说明      |
| ------- | ---- | ----------- | ------------- |
| 传入参数 | 无   |             |               |
| 返回值   |      | DBDelegate* | 数据库连接对象 |

- ### DBConnection

调用接口：DBConnectionDelegate* DBConnection(const QString& name) const

[返回目录](#category)

这个函数通过数据库连接的名称，返回数据库连接对象。只对 addDBConnection 添加的数据库连接有效，表单缺省使用的数据库直接用 database() 就可以了。

|   内容   | 名称 |        数据类型        |     说明      |
| ------- | ---- | --------------------- | ------------- |
| 传入参数 | 无   |                       |               |
| 返回值   |      | DBConnectionDelegate* | 数据库连接对象 |

- ### DBConnections

调用接口：QStringList formDelegate::DBConnections() const

[返回目录](#category)

这个函数返回这个表单所有数据库连接的名称。

|   内容   | 名称 |   数据类型   |          说明           |
| ------- | ---- | ----------- | ---------------------- |
| 传入参数 | 无   |             |                        |
| 返回值   |      | QStringList | 所有数据库连接对象的名称 |

- ### drop

调用接口：void drop() const

[返回目录](#category)

这个函数用来删除正在显示的一条主表记录，并且会同时删除与主表相关联的子表的记录。等同于点击表单上工具栏中的按钮“删除”。如果“删除”按钮处于不可用状态，或表单的属性　“dropEnabled”为False，调用无效。删除过程会调用表单的“删除前”脚本判断是否允许删除，如果不允许删除，删除过程也会被取消。删除后，将转为空白表单状态。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### getCurrentLastUpdated

调用接口：QString getCurrentLastUpdated() const

[返回目录](#category)

这个函数返回当前正在显示的那条主表记录的 lastUpdated 字段的值。如果当前表单并不是在 QUERY_RESULT 状态，则返回空字符串。如果表单没有设置“主表”属性，也返回空字符串。

|   内容   | 名称 | 数据类型 |              说明              |
| ------- | ---- | ------- | ------------------------------ |
| 传入参数 | 无   |         |                                |
| 返回值   |      | QString | 当前记录的 lastUpdated 字段的值 |

- ### getCurrentNo

调用接口：QString getCurrentNo()

[返回目录](#category)

这个函数返回当前正在显示的那条主表记录的主关键字段的值，不管是什么字段类型，都会转化为字符串。如果当前表单并不是在 QUERY_RESULT 状态，则返回空字符串。如果表单没有设置“主表”属性，也返回空字符串。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   |      | QString |      |

- ### getCurrentUUID

调用接口：QString getCurrentUUID() const

[返回目录](#category)

这个函数返回当前正在显示的那条主表记录的 UUID 字段的值。如果当前表单并不是在 QUERY_RESULT 状态，则返回空字符串。如果表单没有设置“主表”属性，也返回空字符串。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   |      | QString |      |

- ### isExtentTable

调用接口：bool isExtentTable(const QString& tablename) const

[返回目录](#category)

这个函数根据表名，返回这个表是否是主表的扩展数据表。扩展数据表的定义是：它是表单的子表（非基础表，非主表），且与主表只有一个字段关联，且这个字段是这个子表的唯一关键字段。符合这几个条件，就返回 True，否则返回 False。

|   内容   |   名称    | 数据类型 | 说明 |
| ------- | --------- | ------- | ---- |
| 传入参数 | tablename | QString | 表名 |
| 返回值   |           | bool    |      |

- ### jumpToBegin

调用接口：void jumpToBegin()

[返回目录](#category)

这个函数用于跳转到当前查询出的记录集中的第一条记录。如果当前不是 QUERY_RESULT 状态，调用无效。

|   内容   | 名称 |        数据类型        |      说明       |
| ------- | ---- | --------------------- | --------------- |
| 传入参数 |  |                | |
| 返回值   |      | void|   |

- ### jumpToEnd

调用接口：void jumpToEnd()

[返回目录](#category)

这个函数用于跳转到当前查询出的记录集中的第一条记录。如果当前不是 QUERY_RESULT 状态，调用无效。需要注意的是，运行时引擎可能会在记录集较大时，只显示一部分记录，这个函数不一定会跳转到完整的记录集的最后一条，而只是跳转到当前缓存区的最后一条，这取决于运行时引擎的处理策略。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### jumpToIndex

调用接口：void jumpToIndex(int index)

[返回目录](#category)

这个函数用于跳转到当前查询出的记录集中的指定顺序的那条记录。如果当前不是 QUERY_RESULT 状态，调用无效。如果 index 超出记录集范围，调用无效。

|   内容   | 名称  | 数据类型 |        说明        |
| ------- | ----- | ------- | ------------------ |
| 传入参数 | index | 整数     | 记录的顺序（0开始） |
| 返回值   |     无  |    |                    |

- ### jumpToNext

调用接口：void jumpToNext()

[返回目录](#category)

这个函数用于跳转到当前查询出的记录集中下一条记录。如果当前不是 QUERY_RESULT 状态，调用无效。如果已到最后一条，调用无效。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### jumpToPrevious

调用接口：void jumpToPrevious()

[返回目录](#category)

这个函数用于跳转到当前查询出的记录集中前一条记录。如果当前不是 QUERY_RESULT 状态，调用无效。如果已到第一条，调用无效。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### jumpToRecordByKey

调用接口：bool jumpToRecordByKey(const QString &key)

[返回目录](#category)

这个函数用于按关键字段的值跳转到当前查询出的记录集中匹配的记录。如果当前不是 QUERY_RESULT 状态，调用无效。如果没有找到匹配的记录，调用无效。

|   内容   | 名称 | 数据类型 |                        说明                        |
| ------- | ---- | ------- | -------------------------------------------------- |
| 传入参数 | key  | QString | 主关键字段的值，不管是何种数据类型，统一转为字符串形式 |
| 返回值   |      | bool    | 是否找到了匹配的记录                                 |

- ### jumpToRecordByUUID

调用接口：bool jumpToRecordByUUID(const QString &UUID)

[返回目录](#category)

这个函数用于按主表的UUID字段的值跳转到当前查询出的记录集中匹配的记录。如果当前不是 QUERY_RESULT 状态，调用无效。如果没有找到匹配的记录，调用无效。

|   内容   | 名称 | 数据类型 |        说明         |
| ------- | ---- | ------- | ------------------- |
| 传入参数 | UUID | QString | 主表UUID字段的值    |
| 返回值   |      | bool    | 是否找到了匹配的记录 |

- ### lastSavedUUID

调用接口：QString lastSavedUUID() const

[返回目录](#category)

这个函数用于返回最近一次点击“保存”按钮或调用 save() 保存的记录的 UUID 字段的值。在保存记录时，主表的 UUID 的值是运行时引擎自动生成的。

|   内容   | 名称 | 数据类型 |         说明          |
| ------- | ---- | ------- | --------------------- |
| 传入参数 |      |         |                       |
| 返回值   |      | QString | 主表记录的UUID字段的值 |

- ### query

调用接口：QString query(const QString& filter="",bool isSilence=false,const QString& order="")

[返回目录](#category)

对主表记录进行查询。如果表单没有设置“主表”属性，调用无效。

如果 filter 为空，则返回主表所有记录。但如果主表的可编程函数“全程过滤条件”返回的结果不为空，会在查询时加上“全程过滤条件”。

调用此函数，等同于执行一个SQL语句， 参数 filter 为 where 子句中的内容，参数 order 为 order by  子句中的内容，最后生成的SQL语句会使用 baseSQL() 函数的结果与这两个参数进行拼接，所以在这两个参数中也可以使用表的别名，或使用其它表。 

调用有效之后，表单会转到显示查询结果的界面，状态会转换为 QUERY_RESULT。

|   内容   |   名称    | 数据类型 |                                    说明                                    |
| ------- | --------- | ------- | -------------------------------------------------------------------------- |
| 传入参数 | filter    | QString | 过滤条件，对应SQL语句中 where 子句中的内容                                   |
| 传入参数 | isSilence | bool    | 是否以无消息提醒的方式进行查询，如果为 False ，在出错时可能会弹出一些消息对话框 |
| 传入参数 | order     | QString | 排序规则 ，对应SQL语句中 order by 子句中的内容                               |
| 返回值   |           | QString |                                                                            |

- ### queryByFilter

调用接口：void queryByFilter()

[返回目录](#category)

调用这个函数，会弹出“查询过滤条件设定”窗口，供用户输入查询条件之后进行查询。等同于点击工具栏上的“查询”-“按过滤条件查询”菜单项。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### recordCount

调用接口：int recordCount()

[返回目录](#category)

调用这个函数，返回当前查询的结果集中的记录的个数。如果表单没有设置“主表”属性，返回0。如果表单并不是处于 QUERY_RESULT 状态，也返回0。

|   内容   | 名称 | 数据类型 |        说明         |
| ------- | ---- | ------- | ------------------- |
| 传入参数 | 无   |         |                     |
| 返回值   |      | int     | 当前记录集的记录个数 |

- ### refresh

调用接口：void refresh() const

[返回目录](#category)

调用这个函数，重新按上一次的查询条件重新查询并显示。如果表单没有设置“主表”属性，或者表单没有处于 QUERY_RESULT 状态，则调用无效。刷新后，会转到查询记录集的第一条记录。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 |     无 |         |      |
| 返回值   |     无 |   |      |

- ### removeDBConnection

调用接口：bool removeDBConnection(const QString& name) 

[返回目录](#category)

这个函数用来移除一个表单级的数据库连接对象，移除前会关闭对应的数据库连接。

表单级的数据库连接会在表单关闭时被断开并移除，所以一般并不需要在脚本中显式地调用这个函数。开发者可以视情况决定是否要在表单运行过程中调用这个函数。

|   内容   | 名称 | 数据类型 |      说明       |
| ------- | ---- | ------- | --------------- |
| 传入参数 | name | QString | 数据库连接的名称 |
| 返回值   |      | bool    | 是否移除成功     |

- ### save

调用接口：void save()

[返回目录](#category)

调用这个函数会保存当前表单的数据，包括主表和子表的数据都会被修改，但基础表的数据不会被修改，除非脚本里使用数据库接口对基础表中的数据进行修改。

如果表单没有设置“主表”属性，则调用无效。

如果表单处于 UNSAVED_BLANK_NEW_FORM 状态，则是添加新的记录。

如果表单处于 QUERY_RESULT 状态，则是修改旧的记录。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 |    无  |         |      |
| 返回值   |      无|    |      |

- ### SQL_Fields

调用接口：QVariantList SQL_Fields() const

[返回目录](#category)

这个函数用于返回 baseSQL 中查询返回的记录集的表结构，即各个字段的定义，包括字段名称、类型、长度等。

|   内容   | 名称 |       数据类型        |           说明           |
| ------- | ---- | --------------------- | ------------------------ |
| 传入参数 |      |                       |                          |
| 返回值   |      | QVariantList（tuple） | baseSQL返回的各字段的信息 |

以“我的书籍”这个表单为例，返回的结果：

``` python
>>> this.form.SQL_Fields()
(('t0.ID', 't0.ID', '序号', '', 'Int', 10, 0), 
('t0.fname', 't0.fname', '书名', '', 'Text', 30, 0), 
('t0.fauthor', 't0.fauthor', '作者', '', 'Text', 30, 0), 
('t0.fclass', 't0.fclass', '分类', '', 'Text', 10, 0),
('t0.fyear', 't0.fyear', '出版年份', '', 'Int', 10, 0),
('t0.fISBN', 't0.fISBN', 'ISBN', '', 'Text', 20, 0), 
('t0.UUID', 't0.UUID', '记录UUID', '', 'Text', 100, 0),
('t0.lastUpdated', 't0.lastUpdated', '最后更新日期时间', '', 'DateTime', 19, 0))
```

以另一个复杂点的表单  “现金日记账”为例，返回的结果：

``` python 
>>> this.form.SQL_Fields()
(('t0.ID', 't0.ID', '序号', '', 'Int', 10, 0), 
('t0.facctID', 'O_t1.fname', '账户', '', 'Text', 100, 0), 
('t0.findex', 't0.findex', '流水号', '', 'Int', 10, 0),
('t0.fdate', 't0.fdate', '日期', '', 'Date', 10, 0),
('t0.fdebit', 't0.fdebit', '借方金额', '', 'Decimal', 20, 2), 
('t0.fcredit', 't0.fcredit', '贷方金额', '', 'Decimal', 20, 2),
('t0.fcontact', 't0.fcontact', '经手人', '', 'Text', 30, 0),
('t0.foperator', 't0.foperator', '录入人', '', 'Text', 30, 0),
('t0.finputDate', 't0.finputDate', '录入日期', '', 'Date', 10, 0), 
('t0.fmemo', 't0.fmemo', '摘要', '', 'Text', 100, 0), 
('t0.fremark', 't0.fremark', '备注', '', 'Text', 1000, 0), 
('t0.UUID', 't0.UUID', '记录UUID', '', 'Text', 100, 0), 
('t0.lastUpdated', 't0.lastUpdated', '最后更新日期时间', '', 'DateTime', 19, 0))
```

返回的 tuple 中每个元素也是一个有7个元素的 tuple，以 "('t0.facctID', 'O_t1.fname', '账户', '', 'Text', 100, 0)"为例讲解，它们分别的含义如下：

| 序号 |     值     |                                                              说明                                                              |
| ---- | ---------- | ------------------------------------------------------------------------------------------------------------------------------ |
| 0    | t0.facctID | 主表的facctID字段                                                                                                               |
| 1    | O_t1.fname | 因为设置了这个字段关联到另一个表的 ID 字段，并以 fname 字段进行显示，所以这个元素指实际查询结果里使用的字段                           |
| 2    | 账户       | 主表的facctID字段用于显示的名称                                                                                                  |
| 3    |            | 主表的facctID字段的说明                                                                                                         |
| 4    | Text       | 主表的facctID字段的类型 ，注意这里不是指数据库实体表中的字段类型，而是 biForm 中定义的数据类型，不同的DBMS具体使用的字段类型会稍有差别 |
| 5    | 100        | 主表的facctID字段的长度                                                                                                         |
| 6    | 0          | 主表的facctID字段的小数位数（如果有的话）                                                                                        |

- ### SQL_FromTables

调用接口：QStringList SQL_FromTables() const

[返回目录](#category)

这个函数返回 baseSQL() 中用到的数据表的表名清单。注意是表的“设计时”的表名，不是物理表名。关于这两个表名的区别，请参考[数据库](1-8-database)。

|   内容   | 名称 |      数据类型       |         说明          |
| ------- | ---- | ------------------ | -------------------- |
| 传入参数 |      |                    |                      |
| 返回值   |      | QStringList(tuple) | 查询用到的表的表名清单 |

以“现金日记账”为例，返回的结果：

``` python
>>> this.form.SQL_FromTables()
('t_cash', 't_bankaccount')
```

- ### tableAlias

调用接口：QString tableAlias(const QString& tablename) const

[返回目录](#category)

这个函数返回 baseSQL() 中表名 tablename 对应的表的别名。传入参数是表的“设计时”的表名，不是物理表名。关于这两个表名的区别，请参考[数据库](1-8-database)。

|   内容   |   名称    | 数据类型 |   说明   |
| ------- | --------- | ------- | ------- |
| 传入参数 | tablename | QString | 表名     |
| 返回值   |           | QString | 表的别名 |

比如在“现金日记账”这个例子中，返回的结果：
``` python
>>> this.form.tableAlias('t_cash')
't0'

>>> this.form.tableAlias('t_bankaccount')
'O_t1'
```
---

## 与按钮组操作相关的函数

按钮组包括 [单选按钮组](2-29-radiobuttongroup) 和 [多选按钮组](2-30-checkboxgroup) 。

- ### addCheckBoxGroup

调用接口：checkBoxGroupDelegate* addCheckBoxGroup(const QString &name,bool exclusive = false) 

[返回目录](#category)

这个函数添加一个多选按钮组，指定按钮组名称和是否互斥。

|   内容   |   名称    |        数据类型        |                   说明                    |
| ------- | --------- | ---------------------- | ----------------------------------------- |
| 传入参数 | name      | QString                | 多选按钮组的名称                           |
| 传入参数 | exclusive | bool                   | 组内成员是否互斥，如果是，则只有一个能被勾选 |
| 返回值   |           | checkBoxGroupDelegate* | 多选按钮组对象                             |

- ### buttonGroup

调用接口：radioButtonGroupDelegate* buttonGroup() const

[返回目录](#category)

这个函数返回这个表单的单选按钮组。

|   内容   | 名称 |          数据类型          |     说明      |
| ------- | ---- | ------------------------- | ------------- |
| 传入参数 | 无   |                           |               |
| 返回值   |      | radioButtonGroupDelegate* | 单选按钮组对象 |

- ### buttonGroupCount

调用接口：int buttonGroupCount() const 

[返回目录](#category)

这个函数返回这个表单上多选按钮组的数量。

|   内容   | 名称 | 数据类型 |      说明       |
| ------- | ---- | ------- | --------------- |
| 传入参数 | 无   | 无       |                 |
| 返回值   |      | int     | 多选按钮组的数量 |

- ### checkBoxGroup

调用接口：checkBoxGroupDelegate* checkBoxGroup(const QString &name) const

[返回目录](#category)

这个函数用名称返回对应的多选按钮组。

|   内容   | 名称 |        数据类型        |      说明       |
| ------- | ---- | ---------------------- | --------------- |
| 传入参数 | name | QString                | 多选按钮组的名称 |
| 返回值   |      | checkBoxGroupDelegate* | 多选按钮组对象   |

- ### removeCheckBoxGroup

调用接口：bool removeCheckBoxGroup(const QString &name) const

[返回目录](#category)

这个函数删除掉指定名称的多选按钮组的设置，但并不会删除复选框控件。

|   内容   | 名称 | 数据类型 |      说明       |
| ------- | ---- | ------- | --------------- |
| 传入参数 | name | QString | 多选按钮组的名称 |
| 返回值   |      | bool    | 是否删除成功     |

---

## 与定时器相关的成员函数

- ### killAllTimer

调用接口：void killAllTimer() const

[返回目录](#category)

这个函数用于停止所有这个表单的内置定时器，不包括控件的内置定时器，也不包括单次定时器。

|   内容   | 名称 |        数据类型        |      说明       |
| ------- | ---- | --------------------- | --------------- |
| 传入参数 |  无|                | |
| 返回值   |     无 | |   |

- ### killTimer

调用接口：bool killTimer ( int id )

[返回目录](#category)

这个函数用于停止指定ID值的这个表单的内置定时器，不包括控件的内置定时器。

|   内容   | 名称 | 数据类型 |         说明          |
| ------- | ---- | ------- | --------------------- |
| 传入参数 | id   | int     | 需要停止的定时器的ID值 |
| 返回值   |      | bool    | 是否停止成功          |

- ### startSingleShot

调用接口：void startSingleShot ( int interval )

[返回目录](#category)

这个函数用于启动一个单次定时器，单次定时器在超时事件触发一次后就会自动停掉。

|   内容   |   名称   | 数据类型 | 说明 |
| ------- | -------- | ------- | ---- |
| 传入参数 | interval | int     |     触发的时间间隔，以毫秒为单位 |
| 返回值   | 无       |         |      |

- ### startTimer

调用接口：int startTimer ( int interval )

[返回目录](#category)

这个函数启动一个定时器，并返回其ID值。

|   内容   |   名称   | 数据类型 |               说明               |
| ------- | -------- | ------- | -------------------------------- |
| 传入参数 | interval | int     | 定时器触发的时间间隔，以毫秒为单位 |
| 返回值   |          | int     | 定时器的ID值                     |

- ### timers

调用接口：QStringList timers() const

[返回目录](#category)

这个函数返回当前表单内置所有定时器的ID值的清单。不包括控件的内置定时器。

|   内容   | 名称 |   数据类型   |              说明              |
| ------- | ---- | ----------- | ------------------------------ |
| 传入参数 |   无   |             |                                |
| 返回值   |      | QStringList | 定时器ID值的清单（转换成字符串） |

---

## 与布局相关的成员函数

- ### hideList

调用接口：void hideList() const

[返回目录](#category)

这个函数用于隐藏记录列表。如果表单属性“视图模式”是“只使用表单模式”，调用无效。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### setHLayout

调用接口：void setHLayout(const QStringList &widgetList, int left=0, int top=0, int right=0, int bottom=0,int spacing=0) const

[返回目录](#category)

这个函数用于设置多个控件按水平方向进行布局。

|   内容   |    名称    |   数据类型   |                说明                |
| ------- | ---------- | ----------- | --------------------------------- |
| 传入参数 | widgetList | QStringList | 水平布局器中按顺序加入的控件名称清单 |
| 传入参数 | left       | int         | 左边界的宽度，缺省为0               |
| 传入参数 | top        | int         | 上边界的高度，缺省为0               |
| 传入参数 | right      | int         | 右边界的宽度，缺省为0               |
| 传入参数 | bottom     | int         | 下边界的高度，缺省为0               |
| 传入参数 | spacing    | int         | 控件间的间距，缺省为0               |
| 返回值   | 无         |             |                                   |

- ### setHSplitter

调用接口：void setHSplitter(const QStringList &widgetList, int left=0, int top=0, int right=0, int bottom=0,int spacing=0) const

[返回目录](#category)

这个函数用于设置表单上多个控件按水平方向进行布局，控件之间有调节棒可用于调节控件大小，但可调的程度会受限于控件的最大最小尺寸属性及缩放规则。

|   内容   |    名称    |   数据类型   |                说明                |
| ------- | ---------- | ----------- | --------------------------------- |
| 传入参数 | widgetList | QStringList | 水平布局器中按顺序加入的控件名称清单 |
| 传入参数 | left       | int         | 左边界的宽度，缺省为0               |
| 传入参数 | top        | int         | 上边界的高度，缺省为0               |
| 传入参数 | right      | int         | 右边界的宽度，缺省为0               |
| 传入参数 | bottom     | int         | 下边界的高度，缺省为0               |
| 传入参数 | spacing    | int         | 控件间的间距，缺省为0               |
| 返回值   | 无         |             |                                   |

- ### setVLayout

调用接口：void setVLayout(const QStringList &widgetList, int left=0, int top=0, int right=0, int bottom=0,int spacing=0) const

[返回目录](#category)

这个函数用于设置多个控件按垂直方向进行布局。

|   内容   |    名称    |   数据类型   |                说明                |
| ------- | ---------- | ----------- | --------------------------------- |
| 传入参数 | widgetList | QStringList | 水平布局器中按顺序加入的控件名称清单 |
| 传入参数 | left       | int         | 左边界的宽度，缺省为0               |
| 传入参数 | top        | int         | 上边界的高度，缺省为0               |
| 传入参数 | right      | int         | 右边界的宽度，缺省为0               |
| 传入参数 | bottom     | int         | 下边界的高度，缺省为0               |
| 传入参数 | spacing    | int         | 控件间的间距，缺省为0               |
| 返回值   | 无         |             |                                   |

- ### setVSplitter

调用接口：void setVSplitter(const QStringList &widgetList, int left=0, int top=0, int right=0, int bottom=0,int spacing=0) const

[返回目录](#category)

这个函数用于设置表单上多个控件按垂直方向进行布局，控件之间有调节棒可用于调节控件大小，但可调的程度会受限于控件的最大最小尺寸属性及缩放规则。

|   内容   |    名称    |   数据类型   |                说明                |
| ------- | ---------- | ----------- | --------------------------------- |
| 传入参数 | widgetList | QStringList | 水平布局器中按顺序加入的控件名称清单 |
| 传入参数 | left       | int         | 左边界的宽度，缺省为0               |
| 传入参数 | top        | int         | 上边界的高度，缺省为0               |
| 传入参数 | right      | int         | 右边界的宽度，缺省为0               |
| 传入参数 | bottom     | int         | 下边界的高度，缺省为0               |
| 传入参数 | spacing    | int         | 控件间的间距，缺省为0               |
| 返回值   | 无         |             |                                   |

- ### showDownUp

调用接口：void showDownUp() const

[返回目录](#category)

同时显示表单和列表，表单在下方，列表在上方。如果表单属性“视图模式”不是“表单和列表混合模式”，调用无效。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### showForm

调用接口：void showForm() const

[返回目录](#category)

这个函数调用后只显示表单。如果表单属性“视图模式”是“只使用列表模式”，调用无效。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### showLeftRight

调用接口：void showLeftRight() const

[返回目录](#category)

同时显示表单和列表，表单在左侧，列表在右侧。如果表单属性“视图模式”不是“表单和列表混合模式”，调用无效。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### showList

调用接口：void showList() const

[返回目录](#category)

这个函数调用后显示记录列表。如果表单属性“视图模式”是“只使用表单模式”，调用无效。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### showListColumn

调用接口：void showListColumn(const QString & fieldName) const

[返回目录](#category)

显示记录列表中指定列。如果表单属性“视图模式”是“只使用表单模式”，调用无效。

|   内容   |   名称    | 数据类型 | 说明 |
| ------- | --------- | ------- | ---- |
| 传入参数 | fieldName | QString |      |
| 返回值   | 无        |         |      |

- ### showRightLeft

调用接口：void showRightLeft() const

[返回目录](#category)

同时显示表单和列表，表单在右侧，列表在左侧。如果表单属性“视图模式”不是“表单和列表混合模式”，调用无效。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### showUpDown

调用接口：void showUpDown() const

[返回目录](#category)

同时显示表单和列表，表单在上方，列表在下方。如果表单属性“视图模式”不是“表单和列表混合模式”，调用无效。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

---

## 与图像相关的成员函数

- ### getImage

调用接口：QPixmap getImage(const QString &name)  const

[返回目录](#category)

从图片集中按名称返回图片对象。注意 name 可以使用自定义图片，也可以使用系统自带的图片集中的图片，比如使用“:/iconset/arrows/54.png”。如果没有名称匹配的图片，返回空图片，用 ```QPixmap::isNull()``` 可以判断是否是空图片。

|   内容   | 名称 | 数据类型 |      说明       |
| ------- | ---- | ------- | --------------- |
| 传入参数 | name | QString | 在图片集中的名称 |
| 返回值   |      | QPixmap | 图片集中的图片   |

- ### getImageList

调用接口：QStringList getImageList()

[返回目录](#category)

这个函数返回图片集中所有自定义图片的名称。注意只会返回开发者自定义的图片，系统自带的图片集不会在这里列出。

|   内容   | 名称 |   数据类型   |        说明         |
| ------- | ---- | ----------- | ------------------- |
| 传入参数 | 无   |             |                     |
| 返回值   |      | QStringList | 所有自定义图片的名称 |

- ### getMovie

调用接口：QMovie* getMovie(const QString &name)  const

[返回目录](#category)

从图片集中按名称返回动画图片对象。如果对应的图片不是动画类型，或不存在，返回0。

|   内容   | 名称 | 数据类型 |     说明      |
| ------- | ---- | ------- | ------------- |
| 传入参数 | name | QString | 动画图片的名称 |
| 返回值   |      | QMovie* | 动画对象       |

- ### grab

调用接口：QPixmap grab() const

[返回目录](#category)

对当前表单进行截图，并保存在 QPixmap 里返回。

|   内容   | 名称 | 数据类型 |    说明    |
| ------- | ---- | ------- | --------- |
| 传入参数 | 无   |         |           |
| 返回值   |      | QPixmap | 表单的截图 |

---

## 与引用列表相关的成员函数

- ### findReferenceText

调用接口：int findReferenceText(const QString& reference, const QString& text) const

[返回目录](#category)

在指定名称的引用列表里查找条目的显示文本。如果找到了，返回其所在位置（0开始），如果没找到，返回-1。搜索过程是全文匹配，区分大小写。

|   内容   |   名称    | 数据类型 |                      说明                      |
| ------- | --------- | ------- | ---------------------------------------------- |
| 传入参数 | reference | QString | 引用列表的名称                                  |
| 传入参数 | text      | QString | 需要查找的文本                                  |
| 返回值   |           | int     | 匹配的条目所处的顺序，从0开始，如果没找到，返回-1 |

- ### findReferenceValue

调用接口：int findReferenceValue(const QString& reference, const QString& value) const

[返回目录](#category)

在指定名称的引用列表里查找条目的值。如果找到了，返回其所在位置（0开始），如果没找到，返回-1。搜索过程是全文匹配，区分大小写。

|   内容   |   名称    | 数据类型 |                      说明                      |
| ------- | --------- | ------- | ---------------------------------------------- |
| 传入参数 | reference | QString | 引用列表的名称                                  |
| 传入参数 | text      | QString | 需要查找的文本                                  |
| 返回值   |           | int     | 匹配的条目所处的顺序，从0开始，如果没找到，返回-1 |

- ### getReferenceCount

调用接口：int getReferenceCount(const QString& reference) const

[返回目录](#category)

这个函数返回在引用列表里条目的数量。

|   内容   |   名称    | 数据类型 |     说明      |
| ------- | --------- | ------- | ------------- |
| 传入参数 | reference | QString | 引用列表的名称 |
| 返回值   |           | int     | 条目的数量     |

- ### getReferenceData

调用接口：QStringList getReferenceData(const QString& reference, int index) const

[返回目录](#category)

这个函数返回在引用列表里第 index 个条目的文本和值。返回值是一个列表，第一个元素是条目的文本，第二个元素是条目的值。如果 index 超出范围，返回空列表。

|   内容   |   名称    |   数据类型   |                 说明                  |
| ------- | --------- | ----------- | ------------------------------------ |
| 传入参数 | reference | QString     | 引用列表的名称                        |
| 返回值   |           | QStringList | 返回条目的数据： [条目的文本，条目的值] |

- ### getReferenceText

调用接口：QString getReferenceText(const QString& reference, int index) const

[返回目录](#category)

这个函数返回在引用列表里第 index 个条目的文本。如果 index 超出范围，返回空字符串。

|   内容   |   名称    | 数据类型 |     说明      |
| ------- | --------- | ------- | ------------- |
| 传入参数 | reference | QString | 引用列表的名称 |
| 返回值   |           | QString | 条目显示的文本 |

- ### getReferenceValue

调用接口：QString getReferenceValue(const QString& reference, int index) const

[返回目录](#category)

这个函数返回在引用列表里第 index 个条目的值。如果 index 超出范围，返回空字符串。

|   内容   |   名称    | 数据类型 |     说明      |
| ------- | --------- | ------- | ------------- |
| 传入参数 | reference | QString | 引用列表的名称 |
| 返回值   |           | QString | 条目显示的值   |

---

## 与打印和输出相关的成员函数

- ### directPreview

调用接口：void directPreview() const

[返回目录](#category)

直接按表单界面打印预览。注意只是打印“表单”，不打印“记录列表”。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### directPrinting

调用接口：void directPrinting() const

[返回目录](#category)

直接按表单界面打印。注意只是打印“表单”，不打印“记录列表”。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 |     无 |         |      |
| 返回值   |      无|    |      |

- ### exportAllToXLS

调用接口：void exportAllToXLS(const QString& fileName="")

[返回目录](#category)

将当前记录集中的所有记录以表格形式导出为 excel 文件。

|   内容   |   名称   | 数据类型 |    说明     |
| ------- | -------- | ------- | ----------- |
| 传入参数 | fileName | QString | 导出的文件名 |
| 返回值   | 无       |         |             |

- ### exportCurrentToXLS

调用接口：void exportCurrentToXLS(const QString& fileName="")

[返回目录](#category)

将当前记录集中的当前记录以表格形式导出为 excel 文件。

|   内容   |   名称   | 数据类型 |    说明     |
| ------- | -------- | ------- | ----------- |
| 传入参数 | fileName | QString | 导出的文件名 |
| 返回值   | 无       |         |             |

- ### exportToPFD

调用接口：void exportToPFD()

[返回目录](#category)

将当前记录导出为 PFD 文件。PFD 为 PFF运行时引擎支持的一种用于数据交换的文件格式。调用时会提示选择文件名。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### exportToXLSByFilter

调用接口：void exportToXLSByFilter(const QString& fileName="",const QString& filter="")

[返回目录](#category)

将当前记录集中的所有记录进行过滤筛选后，以表格形式导出为 excel 文件。

|   内容   |   名称   | 数据类型 |    说明     |
| ------- | -------- | ------- | ----------- |
| 传入参数 | fileName | QString | 导出的文件名 |
| 传入参数 | filter   | QString | 过滤条件     |
| 返回值   | 无       |         |             |

- ### formatPreview

调用接口：void formatPreview() const

[返回目录](#category)

启动格式化打印预览。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### formatPrinting

调用接口：void formatPrinting() const

[返回目录](#category)

启动格式化打印。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### importFromPFD

调用接口：void importFromPFD()

[返回目录](#category)

从PFD文件中导入数据。调用后会提示选择待导入的文件。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### preview

调用接口：void preview() const

[返回目录](#category)

启动打印预览。如果表单有设置格式化打印，就使用格式化打印，否则就是直接按表单界面进行打印预览。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### printing

调用接口：void printing() const

[返回目录](#category)

启动打印。如果表单有设置格式化打印，就使用格式化打印，否则就是直接按表单界面进行打印预览。

|   内容   | 名称 |        数据类型        |      说明       |
| ------- | ---- | --------------------- | --------------- |
| 传入参数 |  |                | |
| 返回值   |      | void|   |

- ### printToPDF

调用接口：void printToPDF()

[返回目录](#category)

启动打印输出为PDF文件的过程。注意此处是直接按表单界面输出。

|   内容   | 名称 |        数据类型        |      说明       |
| ------- | ---- | --------------------- | --------------- |
| 传入参数 |  |                | |
| 返回值   |      | void|   |

---

## 与消息提示相关的成员函数

- ### finishWaiting

调用接口：void finishWaiting() const

[返回目录](#category)

如果当前正在显示进度对话框，调用此函数后，将关闭进度对话框。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### setSubStep

调用接口：void setSubStep(int v) const

[返回目录](#category)

设置子进度的当前进度值。v的有效值是0-100。如果  v 大于或等于100，子进度条会隐藏（表示已完成）。

|   内容   | 名称 | 数据类型 |     说明      |
| ------- | ---- | ------- | ------------ |
| 传入参数 | v    | int     | 进度值，0-100 |
| 返回值   | 无   |         |              |

- ### setWaitingMsg

调用接口：void setWaitingMsg(const QString& msg) 

[返回目录](#category)

设置进度对话框中显示的文本信息。如果进度对话框没有显示，调用无效。

|   内容   | 名称 | 数据类型 |    说明     |
| ------- | ---- | ------- | ----------- |
| 传入参数 | msg  | QString | 进度提示信息 |
| 返回值   | 无   |         |             |

- ### setWaitingStep

调用接口：void setWaitingStep(const QString& msg,int v) 

[返回目录](#category)

设置进度对话框现在的执行进度和提示信息。

|   内容   | 名称 | 数据类型 |     说明      |
| ------- | ---- | ------- | ------------ |
| 传入参数 | msg  | QString | 进度提示信息  |
| 传入参数 | v    | int     | 进度值，0-100 |
| 返回值   | 无   |         |              |

- ### showSplashMsg

调用接口：void showSplashMsg(const QString& msg,bool error=false) const

[返回目录](#category)

显示快显提示信息。如果 error 为 True，显示的文本为红色。快显提示信息会在表单上显示后自动消失。如果同时多次调用这个函数，后一条消息会在前面一条消失之后才会显示。所以开发者需要注意不要在短时间内多次调用这个函数，虽然不会造成程序意外，但是过多的消息会需要较长时间才能显示完。msg中可以使用换行符。

|   内容   | 名称  | 数据类型 |           说明           |
| ------- | ----- | ------- | ------------------------ |
| 传入参数 | msg   | QString | 显示的文字                |
| 传入参数 | error | bool    | 显示的是否是有关错误的信息 |
| 返回值   | 无    |         |                          |

- ### showWaiting

调用接口：void showWaiting(const QString& title ) const

[返回目录](#category)

调用这个函数，会显示进度对话框。 title 指定显示的标题。

|   内容   | 名称  | 数据类型 |      说明       |
| ------- | ----- | ------- | --------------- |
| 传入参数 | title | QString | 对话框显示的标题 |
| 返回值   | 无    |         |                 |

---

## 其它成员函数

- ### accept

调用接口：void accept(const QVariant& v=QVariant()) const

[返回目录](#category)

PFF表单可以做为主窗口的子窗口显示，也可以做为弹出对话框显示。在其它表单中通过调用 ```pub.popupPFF``` 就会以弹出对话框方式调用本表单。这种情况下，可以在本表单关闭前，调用此函数，并将传入参数 v 传回给发起调用的表单，并关闭弹出对话框。

|   内容   | 名称 | 数据类型  |                     说明                      |
| ------- | ---- | -------- | --------------------------------------------- |
| 传入参数 | v    | QVariant | 传回给发起调用的表单的数据，可以是多种类型的数据 |
| 返回值   | 无   |          |                                               |

- ### addArg

调用接口：void addArg(const QVariant &arg) 

[返回目录](#category)

给表单添加一个传入参数。

|   内容   | 名称 | 数据类型 |                         说明                          |
| ------- | ---- | -------- | ----------------------------------------------------- |
| 传入参数 | arg  | QVariant | 一般建议的参数值使用列表，内容为键值对，如['name','bob'] |
| 返回值   | 无   |          |                                                       |

- ### addWidget

调用接口：void addWidget(QWidget* widget,int x=0,int y=0) const

[返回目录](#category)

在表单上，(x,y)处添加一个控件。

需使用 PythonQt 中的 QWidget 及其子类先创建一个控件对象后再添加到表单上。需要注意的是，调用这个函数是不会影响控件的可见状态的，还需要调用控件的 show() 才能显示。以下是示例：

``` python 

#先导入PythonQt相关模块
from PythonQt.QtGui import QLineEdit
#新建一个单行文本输入框控件
a=QLineEdit()
#添加这个控件到表单上指定位置
this.form.addWidget(a,100,100)
#调用show之后这个控件才能显示
a.show()

```

|   内容   |  名称  | 数据类型 |       说明        |
| ------- | ------ | -------- | ---------------- |
| 传入参数 | widget | QWidget* | 一个 QWidget 控件对象  |
| 返回值  | 无     |          |                  |

- ### allobject

调用接口：QStringList allobject()

[返回目录](#category)

这个函数返回表单上所有标准控件的名称清单。只有标准控件会在列表中，通过 addWidget 添加的控件不会列出。

|   内容   | 名称 |   数据类型   |              说明               |
| ------- | ---- | ----------- | ------------------------------- |
| 传入参数 |      |             |                                 |
| 返回值   |      | QStringList | 所有标准控件的 objectName 的清单 |

- ### args

调用接口：QVariantList args() const

[返回目录](#category)

当前表单的所有传入参数

|   内容   | 名称 |   数据类型    |         说明          |
| ------- | ---- | ------------ | -------------------- |
| 传入参数 | 无   |              |                      |
| 返回值   |      | QVariantList | 当前表单的所有传入参数 |

- ### baseWidget

调用接口：QWidget* baseWidget() const

[返回目录](#category)

这个函数返回这个表单的基础控件。

this.form 是表单类的Python访问代理类，this.form.self() 才是表单控件本体， this.form.baseWiget() 是在表单的滚动区域内部的表单可见区域对应的控件，baseWidget是可以通过 setBaseWidget 用其它 QWidget 替换的，this.form 和 this.form.self() 不允许替换。

虽然可以在通过这个函数返回表单的基础控件之后，对之进行控制，但不建议开发者这样做，这样可能造成一些不可预料的意外，请谨慎使用。

|   内容   | 名称 | 数据类型  | 说明 |
| ------- | ---- | -------- | ---- |
| 传入参数 |      |          |      |
| 返回值   |      | QWidget* |    表单的基础控件  |

- ### broadcastTableUpdated

调用接口：void broadcastTableUpdated(const QStringList &tableNames) const

[返回目录](#category)

在表单相关的数据表中的记录被修改后，通过调用此函数发出数据被修改的信号。这个信号主要是为某些PFF运行时环境中内部使用保留。暂时是为了向下兼容保留。

|   内容   |    名称    |   数据类型   |         说明          |
| ------- | ---------- | ----------- | -------------------- |
| 传入参数 | tableNames | QStringList | 数据被修改的表名的清单 |
| 返回值   | 无         |             |                      |

- ### close

调用接口：void close() const

[返回目录](#category)

关闭这个表单。等同于点击工具栏上“关闭”按钮，会处理关闭前需要处理的一切事务，并不是无条件直接关闭。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### contextName

调用接口：QString contextName() const

[返回目录](#category)

这个函数返回这个表单在 Python 中对应模块的模块名，即 __name__ 的值。

|   内容   | 名称 | 数据类型 |        说明         |
| ------- | ---- | ------- | ------------------- |
| 传入参数 | 无   |         |                     |
| 返回值   |      | QString | 表单所在模块的模块名 |

- ### ensureWidgetVisible

调用接口：void ensureWidgetVisible(const QString& name) const

[返回目录](#category)

确保某个控件在滚动区域的可见区域中。只对标准控件有效，name 是控件的 objectName。如果没有名称匹配的控件，调用无效。注意只是确保控件在滚动区域的可见区域中，并不会影响控件的可见状态，隐藏的控件还是会处于不可见的状态。

|   内容   | 名称 | 数据类型 |       说明       |
| ------- | ---- | ------- | ---------------- |
| 传入参数 | name | QString | 控件的objectName |
| 返回值   | 无   |         |                  |

- ### getArg

调用接口：QVariant getArg(const QString& key) const

[返回目录](#category)

从表单的传入参数中获取键值为 key 的参数。传入参数一般建议为类似 "[['key1','value1'],['key2','value2'],['key3',[1,2,3,4]]]"。如果没找到的参数，返回空的 QVariant 变量。

|   内容   | 名称 | 数据类型  |      说明       |
| ------- | ---- | -------- | --------------- |
| 传入参数 | key | QString  | 想要的参数的键值 |
| 返回值   |      | QVariant | 想要的参数的值   |

- ### hasCountLimit

调用接口：bool hasCountLimit() const

[返回目录](#category)

表单是否限制被记录数。向下兼容保留。

|   内容   | 名称 | 数据类型 |      说明       |
| ------- | ---- | ------- | --------------- |
| 传入参数 | 无   |         |                 |
| 返回值   |      | bool    | 是否被限制记录数 |

- ### hasLicense

调用接口：bool hasLicense() const

[返回目录](#category)

表单是否有授权。向下兼容保留。

|   内容   | 名称 | 数据类型 |     说明      |
| ------- | ---- | ------- | ------------- |
| 传入参数 | 无   |         |               |
| 返回值   |      | bool    | 是否有经过授权 |

- ### hasUseLimit

调用接口：bool hasUseLimit() const

[返回目录](#category)

表单是否被限制使用次数。向下兼容保留。

|   内容   | 名称 | 数据类型 |       说明        |
| ------- | ---- | ------- | ----------------- |
| 传入参数 | 无   |         |                   |
| 返回值   |      | bool    | 是否被限制使用次数 |

- ### hide

调用接口：void hide() const

[返回目录](#category)

隐藏表单区域。注意记录列表区域不会受影响。

|   内容   | 名称 |        数据类型        |      说明       |
| ------- | ---- | --------------------- | --------------- |
| 传入参数 |  |                | |
| 返回值   |      | void|   |

- ### hideBalloon

调用接口：void hideBalloon() const

[返回目录](#category)

隐藏表单上所有控件可能正在显示的汽泡提示框。

汽泡提示框用于定位于控件上提示一些消息，显示之后会自动消失。比如  ```this.buClick.showBalloon('点击一下')``` 就是在 buClick 这个控件上显示汽泡消息。hideBalloon() 会隐藏表单所有控件上可能会有的汽泡提示框。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### hideListColumn

调用接口：void hideListColumn(const QString & fieldName) const

[返回目录](#category)

隐藏记录列表中的指定字段名对应的列。

注意 fieldName 不是列表的列标题文字，而是 baseSQL() 中 select 子句中的字段名，比如 ```this.form.hideListColumn('t0.fname')``` 是对的， ```this.form.hideListColumn('书名')``` 是没有效果的。可以通过 ```this.form.SQL_Fields()``` 返回对应的列名。具体参考 [SQL_Fields](#SQL_Fields) 和 [baseSQL](#baseSQL)。

|   内容   |   名称    | 数据类型 | 说明 |
| ------- | --------- | ------- | ---- |
| 传入参数 | fieldName | QString |      |
| 返回值   | 无        |         |      |

- ### hscrollto

调用接口：void hscrollto ( int value ) const

[返回目录](#category)

水平滚动条滚动到指定位置。

|   内容   | 名称  | 数据类型 |    说明     |
| ------- | ----- | ------- | ----------- |
| 传入参数 | value | int     | 滚动的目标值 |
| 返回值   | 无    |         |             |

- ### horizontalScrollBarVisible

调用接口：bool horizontalScrollBarVisible() const

[返回目录](#category)

水平滚动条是否可见。

|   内容   | 名称 | 数据类型 |       说明        |
| ------- | ---- | ------- | ----------------- |
| 传入参数 | 无   |         |                   |
| 返回值   |     | bool    | 水平滚动条是否可见 |

- ### horizontalScrollBarMaxValue

调用接口：int horizontalScrollBarMaxValue() const

[返回目录](#category)

水平滚动条的最大值。

|   内容   | 名称 | 数据类型 |       说明        |
| ------- | ---- | ------- | ----------------- |
| 传入参数 | 无   |         |                   |
| 返回值   |      | int     | 水平滚动条的最大值 |

- ### isDebug

调用接口：bool isDebug() const

[返回目录](#category)

当前运行时环境是否是 debug 环境。

在 biForm 中试运行表单时，isDebug() 的值为 True，在其它运行时环境下（比如 biReader），通常值为 False。所以这个值是由使用 PFF 运行时引擎的主应用程序进行设置的，不允许修改。

一般用于在值为 True 时在程序中添加一些调试用的脚本进行调试。

|   内容   | 名称 | 数据类型 |       说明        |
| ------- | ---- | ------- | ---------------- |
| 传入参数 | 无   |         |                  |
| 返回值   |      | bool    | 是否是 debug 状态 |

- ### isMine

调用接口：bool isMine() const

[返回目录](#category)

当前表单是否是本地发布（注册）的。在目前发布的各PFF运行时版本中返回值都是 True。为向下兼容保留的，未来可能还会再启用。

|   内容   | 名称 | 数据类型 |          说明           |
| ------- | ---- | ------- | ---------------------- |
| 传入参数 | 无   |         |                        |
| 返回值   |      | bool    | 是否是本地发布（注册）的 |

- ### isNull

调用接口：bool isNull()

[返回目录](#category)

是否是个空的表单对象。为容错保留。正常情况下都返回 False。

|   内容   | 名称 | 数据类型 |     说明      |
| ------- | ---- | ------- | ------------- |
| 传入参数 | 无   |         |               |
| 返回值   |      | bool    | 是否是空的表单 |

- ### object

调用接口：QObject* object(const QString &name)

[返回目录](#category)

按标准控件的 objectname 返回这个表单上匹配的标准控件对象。只对标准控件有效，对通过 addWidget 添加的控件无效。

|   内容   | 名称 | 数据类型  |   说明   |
| ------- | ---- | -------- | ------- |
| 传入参数 | name | QString  | 想要查找的控件的 objectName         |
| 返回值   |      | QObject* | 控件对象 |

- ### owner

调用接口：QString owner() const

[返回目录](#category)

表单的所有者，即发布（注册）这个表单的应用程序或账号。如果是在 biReader 中使用这个PFF表单，并且是在本地注册的，返回结果会是 "BIREADER"，如果有其它的  PFF 运行时环境，可能会返回其它值。

|   内容   | 名称 | 数据类型 |        说明         |
| ------- | ---- | ------- | ------------------- |
| 传入参数 | 无   |         |                     |
| 返回值   |      | QString | 发布的应用程序或账号 |

- ### reject

调用接口：void reject() const

[返回目录](#category)

如果这个表单是以弹出对话框方式打开的，调用这个函数将以拒绝的方式关闭这个表单。以主窗口的子窗口方式打开的表单调用这个函数无效。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### resize

调用接口：void resize(int width, int height) const

[返回目录](#category)

调整表单大小。若表单已经是全屏或最大化状态，这个调用会无效。做为子窗体时，调整尺寸只会调整 baseWidget（即滚动区域内表单控件） 的尺寸，外部容器（即子窗体）的尺寸不会被改变。如果是弹出对话框会改变弹出窗口的尺寸。

|   内容   |  名称  | 数据类型 | 说明 |
| ------- | ------ | ------- | ---- |
| 传入参数 | width  | int     | 宽度 |
| 传入参数 | height | int     | 高度 |
| 返回值   | 无     |         |      |

- ### self

调用接口：QWidget* self() 

[返回目录](#category)

这个函数返回表单控件本体，包括滚动区域控件和在滚动区域内的表单可见区域。

this.form 是表单类的Python访问代理类，this.form.self() 才是表单控件本体， this.form.baseWiget() 是在表单的滚动区域内部的表单可见区域对应的控件，baseWidget是可以通过 setBaseWidget 用其它 QWidget 替换的，this.form 和 this.form.self() 不允许替换。

虽然可以在通过这个函数返回表单控件对象，对之进行控制，但不建议开发者这样做，这样可能造成一些不可预料的意外，请谨慎使用。

|   内容   | 名称 |        数据类型        |      说明       |
| ------- | ---- | --------------------- | --------------- |
| 传入参数 |  |                | |
| 返回值   |      | QWidget*|   |

- ### setAllReadOnly

调用接口：void setAllReadOnly() const

[返回目录](#category)

设置表单上所有标准控件为只读状态。只对标准控件有效，对通过 addWidget 添加的控件无效。控件若没有 readonly 属性会被忽略。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 |    无  |         |      |
| 返回值   |     无 |    |      |

- ### setArgs

调用接口：void setArgs(const QVariantList &arg) 

[返回目录](#category)

设置表单的传入参数。arg 通常使用列表类型，比如 [['name','vivian'],['values',[1,2,5,6,8]]] 这样。如果多次调用，会覆盖之前的值。

|   内容   | 名称 |   数据类型    | 说明 |
| ------- | ---- | ------------ | ---- |
| 传入参数 | arg  | QVariantList |      |
| 返回值   | 无   |              |      |

- ### setBaseWidget

调用接口：void setBaseWidget(QWidget* widget) const

[返回目录](#category)

设置表单的基础控件替换缺省生成的表单基础控件。

虽然可以在通过这个函数替换整个表单对应的控件，但一般不建议开发者这样做，如果处理不当，可能会造成一些不可预料的意外，请谨慎使用。

|   内容   |  名称  | 数据类型 |      说明      |
| ------- | ------ | -------- | -------------- |
| 传入参数 | widget | QWidget* | QWidget 的实例 |
| 返回值   | 无     |          |                |

- ### setCaption

调用接口：void setCaption(const QString &s)

[返回目录](#category)

这个函数用来设置表单标题。这项设置只在当前运行状态下有效，表单关闭后，重新打开，还是会使用表单设计时的标题或通过脚本修改的标题内容。也不会影响PFF运行时环境菜单等需要使用表单标题的地方显示的内容。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | s    | QString | 标题 |
| 返回值   | 无   |         |      |

- ### show

调用接口：void show() const

[返回目录](#category)

这个函数用来显示表单区域（不包括记录列表区域）。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### vscrollto

调用接口：void vscrollto ( int value ) const

[返回目录](#category)

垂直滚动条滚动到指定位置。

|   内容   | 名称  | 数据类型 |     说明      |
| ------- | ----- | ------- | ------------- |
| 传入参数 | value | int     | 垂直滚动条的值 |
| 返回值   | 无    |         |               |

- ### verticalScrollBarVisible

调用接口：bool verticalScrollBarVisible() const

[返回目录](#category)

垂直滚动条是否可见。

|   内容   | 名称 | 数据类型 |       说明        |
| ------- | ---- | ------- | ----------------- |
| 传入参数 | 无   |         |                   |
| 返回值   |     | bool    | 垂直滚动条是否可见 |

- ### verticalScrollBarMaxValue

调用接口：int verticalScrollBarMaxValue() const

[返回目录](#category)

垂直滚动条的最大值。

|   内容   | 名称 | 数据类型 |       说明        |
| ------- | ---- | ------- | ----------------- |
| 传入参数 | 无   |         |                   |
| 返回值   |      | int     | 垂直滚动条的最大值 |


---

## 表单的信号

[返回目录](#category)

|     信号      |                     接口                     |            说明            |
| ------------- | -------------------------------------------- | -------------------------- |
| waitingMsg    | 	void waitingMsg(const QString& msg)        | 等待消息                    |
| waitingStep   | 	void waitingStep(const QString& msg,int v) | 等待消息和完成度            |
| statusChanged | 	void statusChanged()                       | 当前状态发生改变时发出此信号 |

### waitingMsg

在调用 ```this.form.setWaitingMsg(msg)```  时会发出此信号。调用的 setWaitingMsg 函数，同时会影响等待窗口显示的消息。

### waitingStep

在调用 ```this.form.setWaitingStep(msg,v)```  时会发出此信号。调用的 setWaitingStep 函数，同时会影响等待窗口显示的消息和进度条。

### statusChanged 

表单状态发生变化时发出此信号。

表单有如下几种状态，可以在接收到这个信号时，通过 this.form.currentState 获取当前的状态值：

|      状态       |             值             |                                                          说明                                                          |
| --------------- | -------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| 错误            | pub.ERRSTATE               | 通常表单都不会处于这种状态，只是为了处理意外错误保留                                                                       |
| 未保存的空白表单 | pub.UNSAVED_BLANK_NEW_FORM | 新加载一个表单默认就处于这种状态，不管是不是用来填写数据的表单，点击“新建”按钮后，也会切换到这个状态                          |
| 保存后的表单     | pub.SAVED_FORM             | 用于填写数据的表单（设置了“主表”属性的表单），在保存一条记录后，会短暂地处于这个状态。                                       |
|                 |                            | 但保存后通常会“新建”一个新的空白表单，或加载之前保存的那条记录，表单会很快转到 UNSAVED_BLANK_NEW_FORM 或 QUERY_RESULT 状态。 |
| 查询结果        | pub.QUERY_RESULT           | 保存表单的一条记录后，如果选项设置为“保存后显示保存的记录”，就会转到这个状态。                                              |

