# 表单的成员函数和信号

<h2 id="category">目录</h2>

- [成员函数（槽函数）](#表单的成员函数（槽）)

  - [与数据库操作相关的函数](#与数据库操作相关的函数)
 
- [信号](#表单的信号)

---

## 表单的成员函数（槽）

[返回目录](#category)

|                      函数                       |                                                          接口                                                          | 说明 |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ---- |
| [accept](#accept)                               | void accept(const QVariant& v=QVariant()) const                                                                        |      |
| [addArg](#addArg)                               | void addArg(const QVariant &arg)                                                                                       |      |
| [addCheckBoxGroup](#addCheckBoxGroup)           | checkBoxGroupDelegate* addCheckBoxGroup(const QString &name,bool exclusive = false)                                    |      |
| [addDBConnection](#addDBConnection)             | DBConnectionDelegate* addDBConnection(const QString& name)                                                             |      |
| [addWidget](#addWidget)                         | void addWidget(QWidget* widget,int x=0,int y=0) const                                                                  |      |
| [allobject](#allobject)                         | QStringList allobject()                                                                                                |      |
| [args](#args)                                   | QVariantList args() const                                                                                              |      |
| [baseSQL](#baseSQL)                             | QString baseSQL() const                                                                                                |      |
| [baseWidget](#baseWidget)                       | QWidget* baseWidget() const                                                                                            |      |
| [broadcastTableUpdated](#broadcastTableUpdated) | void broadcastTableUpdated(const QStringList &tableNames) const                                                        |      |
| [buttonGroup](#buttonGroup)                     | radioButtonGroupDelegate* buttonGroup() const                                                                          |      |
| [buttonGroupCount](#buttonGroupCount)           | int buttonGroupCount() const                                                                                           |      |
| [checkBoxGroup](#checkBoxGroup)                 | checkBoxGroupDelegate* checkBoxGroup(const QString &name) const                                                        |      |
| [close](#close)                                 | void close() const                                                                                                     |      |
| [contextName](#contextName)                     | QString contextName() const                                                                                            |      |
| [createNew](#createNew)                         | void createNew() const                                                                                                 |      |
| [currentRecordIndex](#currentRecordIndex)       | int currentRecordIndex()                                                                                               |      |
| [currentState](#currentState)                   | int currentState()                                                                                                     |      |
| [database](#database)                           | DBDelegate* database()  const                                                                                          |      |
| [DBConnection](#DBConnection)                   | DBConnectionDelegate* DBConnection(const QString& name) const                                                          |      |
| [directPreview](#directPreview)                 | void directPreview() const                                                                                             |      |
| [directPrinting](#directPrinting)               | void directPrinting() const                                                                                            |      |
| [drop](#drop)                                   | void drop() const                                                                                                      |      |
| [ensureWidgetVisible](#ensureWidgetVisible)     | void ensureWidgetVisible(const QString& name) const                                                                    |      |
| [exportAllToXLS](#exportAllToXLS)               | void exportAllToXLS(const QString& fileName="")                                                                        |      |
| [exportCurrentToXLS](#exportCurrentToXLS)       | void exportCurrentToXLS(const QString& fileName="")                                                                    |      |
| [exportToPFD](#exportToPFD)                     | void exportToPFD()                                                                                                     |      |
| [exportToXLSByFilter](#exportToXLSByFilter)     | void exportToXLSByFilter(const QString& fileName="",const QString& filter="")                                          |      |
| [findReferenceText](#findReferenceText)         | int findReferenceText(const QString& reference, const QString& text) const                                             |      |
| [findReferenceValue](#findReferenceValue)       | int findReferenceValue(const QString& reference, const QString& value) const                                           |      |
| [finishWaiting](#finishWaiting)                 | void finishWaiting() const                                                                                             |      |
| [formatPreview](#formatPreview)                 | void formatPreview() const                                                                                             |      |
| [formatPrinting](#formatPrinting)               | void formatPrinting() const                                                                                            |      |
| [getArg](#getArg)                               | QVariant getArg(const QString& key) const                                                                              |      |
| [getCurrentLastUpdated](#getCurrentLastUpdated) | QString getCurrentLastUpdated() const                                                                                  |      |
| [getCurrentNo](#getCurrentNo)                   | QString getCurrentNo()                                                                                                 |      |
| [getCurrentUUID](#getCurrentUUID)               | QString getCurrentUUID() const                                                                                         |      |
| [getImage](#getImage)                           | QPixmap getImage(const QString &name)  const                                                                           |      |
| [getImageList](#getImageList)                   | QStringList getImageList()                                                                                             |      |
| [getMovie](#getMovie)                           | QMovie* getMovie(const QString &name)  const                                                                           |      |
| [getReferenceCount](#getReferenceCount)         | int getReferenceCount(const QString& reference) const                                                                  |      |
| [getReferenceData](#getReferenceData)           | QStringList getReferenceData(const QString& reference, int index) const                                                |      |
| [getReferenceText](#getReferenceText)           | QString getReferenceText(const QString& reference, int index) const                                                    |      |
| [getReferenceValue](#getReferenceValue)         | QString getReferenceValue(const QString& reference, int index) const                                                   |      |
| [grab](#grab)                                   | QPixmap grab() const                                                                                                   |      |
| [hasCountLimit](#hasCountLimit)                 | bool hasCountLimit() const                                                                                             |      |
| [hasLicense](#hasLicense)                       | bool hasLicense() const                                                                                                |      |
| [hasUseLimit](#hasUseLimit)                     | bool hasUseLimit() const                                                                                               |      |
| [hide](#hide)                                   | void hide() const                                                                                                      |      |
| [hideBalloon](#hideBalloon)                     | void hideBalloon() const                                                                                               |      |
| [hideList](#hideList)                           | void hideList() const                                                                                                  |      |
| [hideListColumn](#hideListColumn)               | void hideListColumn(const QString & fieldName) const                                                                   |      |
| [hscrollto](#hscrollto)                         | void hscrollto ( int value ) const                                                                                     |      |
| [importFromPFD](#importFromPFD)                 | void importFromPFD()                                                                                                   |      |
| [isDebug](#isDebug)                             | bool isDebug() const                                                                                                   |      |
| [isDraft](#isDraft)                             | bool isDraft() const                                                                                                   |      |
| [isExtentTable](#isExtentTable)                 | bool isExtentTable(const QString& tablename) const                                                                     |      |
| [isInbox](#isInbox)                             | bool isInbox() const                                                                                                   |      |
| [isMine](#isMine)                               | bool isMine() const                                                                                                    |      |
| [isNull](#isNull)                               | bool isNull()                                                                                                          |      |
| [jumpToBegin](#jumpToBegin)                     | void jumpToBegin()                                                                                                     |      |
| [jumpToEnd](#jumpToEnd)                         | void jumpToEnd()                                                                                                       |      |
| [jumpToIndex](#jumpToIndex)                     | void jumpToIndex(int index)                                                                                            |      |
| [jumpToNext](#jumpToNext)                       | void jumpToNext()                                                                                                      |      |
| [jumpToPrevious](#jumpToPrevious)               | void jumpToPrevious()                                                                                                  |      |
| [jumpToRecordByKey](#jumpToRecordByKey)         | bool jumpToRecordByKey(const QString &key)                                                                             |      |
| [jumpToRecordByUUID](#jumpToRecordByUUID)       | bool jumpToRecordByUUID(const QString &UUID)                                                                           |      |
| [killAllTimer](#killAllTimer)                   | void killAllTimer() const                                                                                              |      |
| [killTimer](#killTimer)                         | bool killTimer ( int id )                                                                                              |      |
| [lastSavedUUID](#lastSavedUUID)                 | QString lastSavedUUID() const                                                                                          |      |
| [object](#object)                               | QObject* object(const QString &name)                                                                                   |      |
| [owner](#owner)                                 | QString owner() const                                                                                                  |      |
| [preview](#preview)                             | void preview() const                                                                                                   |      |
| [printing](#printing)                           | void printing() const                                                                                                  |      |
| [printToPDF](#printToPDF)                       | void printToPDF()                                                                                                      |      |
| [query](#query)                                 | QString query(const QString& filter="",bool isSilence=false,const QString& order="")                                   |      |
| [queryByFilter](#queryByFilter)                 | void queryByFilter()                                                                                                   |      |
| [recordCount](#recordCount)                     | int recordCount()                                                                                                      |      |
| [refresh](#refresh)                             | void refresh() const                                                                                                   |      |
| [reject](#reject)                               | void reject() const                                                                                                    |      |
| [removeCheckBoxGroup](#removeCheckBoxGroup)     | bool removeCheckBoxGroup(const QString &name) const                                                                    |      |
| [resize](#resize)                               | void resize(int w, int h) const                                                                                        |      |
| [save](#save)                                   | void save()                                                                                                            |      |
| [self](#self)                                   | QWidget* self()                                                                                                        |      |
| [sendData](#sendData)                           | QString sendData(const QString& filter="",const QString& toJID="",const QString& title="",const QString& msg="") const |      |
| [setAllReadOnly](#setAllReadOnly)               | void setAllReadOnly() const                                                                                            |      |
| [setArgs](#setArgs)                             | void setArgs(const QVariantList &arg)                                                                                  |      |
| [setBaseWidget](#setBaseWidget)                 | void setBaseWidget(QWidget* widget) const                                                                              |      |
| [setHLayout](#setHLayout)                       | void setHLayout(const QStringList &widgetList, int left=0, int top=0, int right=0, int bottom=0,int spacing=0) const   |      |
| [setHSplitter](#setHSplitter)                   | void setHSplitter(const QStringList &widgetList, int left=0, int top=0, int right=0, int bottom=0,int spacing=0) const |      |
| [setSubStep](#setSubStep)                       | void setSubStep(int v) const                                                                                           |      |
| [setVLayout](#setVLayout)                       | void setVLayout(const QStringList &widgetList, int left=0, int top=0, int right=0, int bottom=0,int spacing=0) const   |      |
| [setVSplitter](#setVSplitter)                   | void setVSplitter(const QStringList &widgetList, int left=0, int top=0, int right=0, int bottom=0,int spacing=0) const |      |
| [setWaitingMsg](#setWaitingMsg)                 | void setWaitingMsg(const QString& msg)                                                                                 |      |
| [setWaitingStep](#setWaitingStep)               | void setWaitingStep(const QString& msg,int v)                                                                          |      |
| [show](#show)                                   | void show() const                                                                                                      |      |
| [showDownUp](#showDownUp)                       | void showDownUp() const                                                                                                |      |
| [showForm](#showForm)                           | void showForm() const                                                                                                  |      |
| [showLeftRight](#showLeftRight)                 | void showLeftRight() const                                                                                             |      |
| [showList](#showList)                           | void showList() const                                                                                                  |      |
| [showListColumn](#showListColumn)               | void showListColumn(const QString & fieldName) const                                                                   |      |
| [showRightLeft](#showRightLeft)                 | void showRightLeft() const                                                                                             |      |
| [showSplashMsg](#showSplashMsg)                 | void showSplashMsg(const QString& msg,bool error=false) const                                                          |      |
| [showUpDown](#showUpDown)                       | void showUpDown() const                                                                                                |      |
| [showWaiting](#showWaiting)                     | void showWaiting(const QString& title ) const                                                                          |      |
| [SQL_Fields](#SQL_Fields)                       | QVariantList SQL_Fields() const                                                                                        |      |
| [SQL_FromTables](#SQL_FromTables)               | QStringList SQL_FromTables() const                                                                                     |      |
| [startSingleShot](#startSingleShot)             | void startSingleShot ( int interval )                                                                                  |      |
| [startTimer](#startTimer)                       | int startTimer ( int interval )                                                                                        |      |
| [tableAlias](#tableAlias)                       | QString tableAlias(const QString& tablename) const                                                                     |      |
| [timers](#timers)                               | QStringList timers() const                                                                                             |      |
| [vscrollto](#vscrollto)                         | void vscrollto ( int value ) const                                                                                     |      |

## 与数据库操作相关的函数

- ### addDBConnection

调用接口：DBConnectionDelegate* addDBConnection(const QString& name) 

这个函数用来创建一个新的表单级的数据库连接对象。PFF的运行时环境（比如biReader）必然会有后台数据库。目前 biReader 只连接一个数据源供自己使用。如果表单的功能需要访问其它数据源，就可以使用此函数连接创建新的数据库连接，给连接起个名字以便加以区分。需要注意的是，这些数据库连接会在表单关闭时断开。函数返回的是一个 DBConnectionDelegate 对象，关于它的接口请参考[数据库](1-8-database)。

|   内容   | 名称 |        数据类型        |      说明       |
| ------- | ---- | --------------------- | --------------- |
| 传入参数 | name | QString               | 数据库连接的名称 |
| 返回值   |      | DBConnectionDelegate* | 数据库连接对象   |

- ### baseSQL

调用接口：QString baseSQL() const

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

这个函数用于创建一个新的空白表单，等同于在表单的工具栏上按下“新建”按钮。但如果这个按钮处于不可用的状态，或表单的属性“createNewEnabled”值为 False， 调用无效。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### currentRecordIndex

调用接口：int currentRecordIndex()

这个函数返回在表单查询返回的记录集中，当前记录所处的顺序号（从0开始）。这个只是在返回的记录集中的序号，并不是保存在数据库中的记录的序号。

|   内容   | 名称 | 数据类型 |          说明           |
| ------- | ---- | ------- | ---------------------- |
| 传入参数 | 无   |         |                        |
| 返回值   |      | int     | 当前记录在记录集中的序号 |

- ### currentState

调用接口：int currentState()

这个函数返回当前表单的状态。返回值的说明参考信号 [statusChanged](#statusChanged)。

|   内容   | 名称 | 数据类型 |    说明    |
| ------- | ---- | ------- | --------- |
| 传入参数 | 无   |         |           |
| 返回值   |      | int     | 当前状态值 |

- ### database

调用接口：DBDelegate* database()  const

这个函数返回当前表单后台使用的数据库连接对象。关于其调用接口，参考 [数据库](1-8-database)。

|   内容   | 名称 |   数据类型   |     说明      |
| ------- | ---- | ----------- | ------------- |
| 传入参数 | 无   |             |               |
| 返回值   |      | DBDelegate* | 数据库连接对象 |

- ### DBConnection

调用接口：DBConnectionDelegate* DBConnection(const QString& name) const

这个函数通过数据库连接的名称，返回数据库连接对象。只对 addDBConnection 添加的数据库连接有效，表单缺省使用的数据库直接用 database() 就可以了。

|   内容   | 名称 |        数据类型        |     说明      |
| ------- | ---- | --------------------- | ------------- |
| 传入参数 | 无   |                       |               |
| 返回值   |      | DBConnectionDelegate* | 数据库连接对象 |

- ### drop

调用接口：void drop() const

这个函数用来删除正在显示的一条主表记录，并且会同时删除与主表相关联的子表的记录。等同于点击表单上工具栏中的按钮“删除”。如果“删除”按钮处于不可用状态，或表单的属性　“dropEnabled”为False，调用无效。删除过程会调用表单的“删除前”脚本判断是否允许删除，如果不允许删除，删除过程也会被取消。删除后，将转为空白表单状态。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### getCurrentLastUpdated

调用接口：QString getCurrentLastUpdated() const

这个函数返回当前正在显示的那条主表记录的 lastUpdated 字段的值。如果当前表单并不是在 QUERY_RESULT 状态，则返回空字符串。如果表单没有设置“主表”属性，也返回空字符串。

|   内容   | 名称 | 数据类型 |              说明              |
| ------- | ---- | ------- | ------------------------------ |
| 传入参数 | 无   |         |                                |
| 返回值   |      | QString | 当前记录的 lastUpdated 字段的值 |

- ### getCurrentNo

调用接口：QString getCurrentNo()

这个函数返回当前正在显示的那条主表记录的主关键字段的值，不管是什么字段类型，都会转化为字符串。如果当前表单并不是在 QUERY_RESULT 状态，则返回空字符串。如果表单没有设置“主表”属性，也返回空字符串。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   |      | QString |      |

- ### getCurrentUUID

调用接口：QString getCurrentUUID() const

这个函数返回当前正在显示的那条主表记录的 UUID 字段的值。如果当前表单并不是在 QUERY_RESULT 状态，则返回空字符串。如果表单没有设置“主表”属性，也返回空字符串。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   |      | QString |      |

- ### isExtentTable

调用接口：bool isExtentTable(const QString& tablename) const

这个函数根据表名，返回这个表是否是主表的扩展数据表。扩展数据表的定义是：它是表单的子表（非基础表，非主表），且与主表只有一个字段关联，且这个字段是这个子表的唯一关键字段。符合这几个条件，就返回 True，否则返回 False。

|   内容   |   名称    | 数据类型 | 说明 |
| ------- | --------- | ------- | ---- |
| 传入参数 | tablename | QString | 表名 |
| 返回值   |           | bool    |      |

- ### jumpToBegin

调用接口：void jumpToBegin()

这个函数用于跳转到当前查询出的记录集中的第一条记录。如果当前不是 QUERY_RESULT 状态，调用无效。

|   内容   | 名称 |        数据类型        |      说明       |
| ------- | ---- | --------------------- | --------------- |
| 传入参数 |  |                | |
| 返回值   |      | void|   |

- ### jumpToEnd

调用接口：void jumpToEnd()

这个函数用于跳转到当前查询出的记录集中的第一条记录。如果当前不是 QUERY_RESULT 状态，调用无效。需要注意的是，运行时引擎可能会在记录集较大时，只显示一部分记录，这个函数不一定会跳转到完整的记录集的最后一条，而只是跳转到当前缓存区的最后一条，这取决于运行时引擎的处理策略。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### jumpToIndex

调用接口：void jumpToIndex(int index)

这个函数用于跳转到当前查询出的记录集中的指定顺序的那条记录。如果当前不是 QUERY_RESULT 状态，调用无效。如果 index 超出记录集范围，调用无效。

|   内容   | 名称  | 数据类型 |        说明        |
| ------- | ----- | ------- | ------------------ |
| 传入参数 | index | 整数     | 记录的顺序（0开始） |
| 返回值   |     无  |    |                    |

- ### jumpToNext

调用接口：void jumpToNext()

这个函数用于跳转到当前查询出的记录集中下一条记录。如果当前不是 QUERY_RESULT 状态，调用无效。如果已到最后一条，调用无效。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### jumpToPrevious

调用接口：void jumpToPrevious()

这个函数用于跳转到当前查询出的记录集中前一条记录。如果当前不是 QUERY_RESULT 状态，调用无效。如果已到第一条，调用无效。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### jumpToRecordByKey

调用接口：bool jumpToRecordByKey(const QString &key)

这个函数用于按关键字段的值跳转到当前查询出的记录集中匹配的记录。如果当前不是 QUERY_RESULT 状态，调用无效。如果没有找到匹配的记录，调用无效。

|   内容   | 名称 | 数据类型 |                        说明                        |
| ------- | ---- | ------- | -------------------------------------------------- |
| 传入参数 | key  | QString | 主关键字段的值，不管是何种数据类型，统一转为字符串形式 |
| 返回值   |      | bool    | 是否找到了匹配的记录                                 |

- ### jumpToRecordByUUID

调用接口：bool jumpToRecordByUUID(const QString &UUID)

这个函数用于按主表的UUID字段的值跳转到当前查询出的记录集中匹配的记录。如果当前不是 QUERY_RESULT 状态，调用无效。如果没有找到匹配的记录，调用无效。

|   内容   | 名称 | 数据类型 |        说明         |
| ------- | ---- | ------- | ------------------- |
| 传入参数 | UUID | QString | 主表UUID字段的值    |
| 返回值   |      | bool    | 是否找到了匹配的记录 |

- ### lastSavedUUID

调用接口：QString lastSavedUUID() const

这个函数用于返回最近一次点击“保存”按钮或调用 save() 保存的记录的 UUID 字段的值。在保存记录时，主表的 UUID 的值是运行时引擎自动生成的。

|   内容   | 名称 | 数据类型 |         说明          |
| ------- | ---- | ------- | --------------------- |
| 传入参数 |      |         |                       |
| 返回值   |      | QString | 主表记录的UUID字段的值 |

- ### query

调用接口：QString query(const QString& filter="",bool isSilence=false,const QString& order="")

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

调用这个函数，会弹出“查询过滤条件设定”窗口，供用户输入查询条件之后进行查询。等同于点击工具栏上的“查询”-“按过滤条件查询”菜单项。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   |         |      |
| 返回值   | 无   |         |      |

- ### recordCount

调用接口：int recordCount()

调用这个函数，返回当前查询的结果集中的记录的个数。如果表单没有设置“主表”属性，返回0。如果表单并不是处于 QUERY_RESULT 状态，也返回0。

|   内容   | 名称 | 数据类型 |        说明         |
| ------- | ---- | ------- | ------------------- |
| 传入参数 | 无   |         |                     |
| 返回值   |      | int     | 当前记录集的记录个数 |

- ### refresh

调用接口：void refresh() const

调用这个函数，重新按上一次的查询条件重新查询并显示。如果表单没有设置“主表”属性，或者表单没有处于 QUERY_RESULT 状态，则调用无效。刷新后，会转到查询记录集的第一条记录。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 |     无 |         |      |
| 返回值   |     无 |   |      |

- ### save

调用接口：void save()

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

这个函数用于返回 baseSQL 中查询返回的记录集的表结构，即各个字段的定义，包括字段名称、类型、长度等。

|   内容   | 名称 |       数据类型        |           说明           |
| ------- | ---- | --------------------- | ------------------------ |
| 传入参数 |      |                       |                          |
| 返回值   |      | QVariantList（tuple） | baseSQL返回的各字段的信息 |

以“我的书籍”这个表单为例，返回的结果：

``` python
>>> this.form.SQL_Fields()
(('t0.ID', 't0.ID', '序号', '', 'Int', 10, 0), ('t0.fname', 't0.fname', '书名', '', 'Text', 30, 0), ('t0.fauthor', 't0.fauthor', '作者', '', 'Text', 30, 0), ('t0.fclass', 't0.fclass', '分类', '', 'Text', 10, 0), ('t0.fyear', 't0.fyear', '出版年份', '', 'Int', 10, 0), ('t0.fISBN', 't0.fISBN', 'ISBN', '', 'Text', 20, 0), ('t0.UUID', 't0.UUID', '记录UUID', '', 'Text', 4635076, 1713441720), ('t0.lastUpdated', 't0.lastUpdated', '最后更新日期时间', '', 'DateTime', 4635076, 1713441720))
```

以另一个复杂点的表单  “现金日记账”为例，返回的结果：

``` python 
>>> this.form.SQL_Fields()
(('t0.ID', 't0.ID', '序号', '', 'Int', 10, 0), ('t0.facctID', 'O_t1.fname', '账户', '', 'Text', 100, 0), ('t0.findex', 't0.findex', '流水号', '', 'Int', 10, 0), ('t0.fdate', 't0.fdate', '日期', '', 'Date', 10, 0), ('t0.fdebit', 't0.fdebit', '借方金额', '', 'Decimal', 20, 2), ('t0.fcredit', 't0.fcredit', '贷方金额', '', 'Decimal', 20, 2), ('t0.fcontact', 't0.fcontact', '经手人', '', 'Text', 30, 0), ('t0.foperator', 't0.foperator', '录入人', '', 'Text', 30, 0), ('t0.finputDate', 't0.finputDate', '录入日期', '', 'Date', 10, 0), ('t0.fmemo', 't0.fmemo', '摘要', '', 'Text', 100, 0), ('t0.fremark', 't0.fremark', '备注', '', 'Text', 1000, 0), ('t0.UUID', 't0.UUID', '记录UUID', '', 'Text', 4635076, 1713441720), ('t0.lastUpdated', 't0.lastUpdated', '最后更新日期时间', '', 'DateTime', 4635076, 1713441720))
```

返回的 tuple 中每个元素也是一个有7个元素的 tuple，以 "('t0.facctID', 'O_t1.fname', '账户', '', 'Text', 100, 0)"为例讲解，它们分别的含义如下：

| 序号 |     值     |                                                 说明                                                 |
| ---- | ---------- | ---------------------------------------------------------------------------------------------------- |
| 0    | t0.facctID | 主表的facctID字段                                                                                     |
| 1    | O_t1.fname | 因为设置了这个字段关联到另一个表的 ID 字段，并以 fname 字段进行显示，所以这个元素指实际查询结果里使用的字段 |
| 2    | 账户       | 主表的facctID字段用于显示的名称                                                                        |
| 3    |            | 主表的facctID字段的说明                                                                               |
| 4    | Text       | 主表的facctID字段的类型                                                                               |
| 5    | 100        | 主表的facctID字段的长度                                                                               |
| 6    | 0          | 主表的facctID字段的小数位数（如果有的话）                                                               |

- ### SQL_FromTables

调用接口：QStringList SQL_FromTables() const

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

