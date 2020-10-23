# 数据库

biForm 中有两种数据库连接对象，分别在不同的场合下适用。

|         类         |                                                                   说明                                                                   |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| FormDBDelegate     | 通过 this.form.database() 访问，提供表单对应的后台数据库连接的接口，为应用程序级的永久连接                                                   |
| DatabaseConnection | 通过 this.form.addDBConnect() 添加新的数据库连接，为表单提供除它自身的数据库连接之外的其它数据库连接的访问接口，可以视之为表单运行时的临时性连接 |

在 PFF 的运行时环境中，目前 biReader 缺省地只连接到一个数据源，所以每个表单的 ```this.form.database()``` 都返回的是同一个连接。但并不代表开发者可以将这个连接做成公用变量加以共享。在不同的 PFF 运行时环境，有可能不同的表单使用不同的数据源。所以建议只将这个数据库连接在本表单内部使用。

表单的数据库连接 FormDBDelegate 在表单关闭时，不会断开连接。但通过 addDBConnect() 添加的 DatabaseConnection，在表单关闭时会断开连接。

FormDBDelegate不需要显式地创建连接，也不允许修改连接参数、断开或重新连接。

DatabaseConnection需要显式地调用 this.form.addDBConnect() 创建新的连接，设置连接参数并进行连接。在合适的时候，最好调用 close() 将之关闭。表单销毁时所有已打开的连接也会被关闭。

<h2 id=category>目录</h2>

- [FormDBDelegate的成员函数](#FormDBDelegate的成员函数)

- [DatabaseConnection的属性](#DatabaseConnection的属性)

- [DatabaseConnection的成员函数](#DatabaseConnection的成员函数)

---

## FormDBDelegate的成员函数

这些成员函数也都可以当做槽函数使用。

|                    调用接口                    |                                          说明                                           |               成员函数                |
| --------------------------------------------- | --------------------------------------------------------------------------------------- | ------------------------------------- |
| [isUseSQLite](#isUseSQLite)                   | bool isUseSQLite() const                                                                | 是否是使用的 SQLite 数据库             |
| [SQLiteDBName](#SQLiteDBName)                 | QString SQLiteDBName() const                                                            | 使用的 SQLite 数据库文件名（不带路径）  |
| [SQLiteDBFileName](#SQLiteDBFileName)         | QString SQLiteDBFileName() const                                                        | 使用的 SQLite 数据库文件名（带路径）    |
| [isUseMSSQL](#isUseMSSQL)                     | bool isUseMSSQL() const                                                                 | 是否使用的 MicroSoft SQL Server 数据库 |
| [MSSQLServerName](#MSSQLServerName)           | QString MSSQLServerName() const                                                         | 连接的 MSSQL 服务器名或地址            |
| [MSSQLUser](#MSSQLUser)                       | QString MSSQLUser() const                                                               | 连接 MSSQL 所用账号                    |
| [MSSQLDatabase](#MSSQLDatabase)               | QString MSSQLDatabase() const                                                           | 连接的 MSSQL 数据库名                  |
| [isUsePostgreSQL](#isUsePostgreSQL)           | bool isUsePostgreSQL() const                                                            | 是否使用的 PostgreSQL 数据库           |
| [PostgreSQLServer](#PostgreSQLServer)         | QString PostgreSQLServer() const                                                        | 连接的 PostgreSQL 服务器名或地址       |
| [PostgreSQLPort](#PostgreSQLPort)             | QString PostgreSQLPort() const                                                          | 连接 PostgreSQL 使用的端口号           |
| [PostgreSQLUser](#PostgreSQLUser)             | QString PostgreSQLUser() const                                                          | 登录 PostgreSQL 的账号                 |
| [PostgreSQLDatabase](#PostgreSQLDatabase)     | QString PostgreSQLDatabase() const                                                      | PostgreSQL 数据库名                   |
| [isUseSybase](#isUseSybase)                   | bool isUseSybase() const                                                                | 是否使用 Sybase 数据库                 |
| [SybaseServerName](#SybaseServerName)         | QString SybaseServerName() const                                                        | Sybase 数据服务器名                    |
| [SybaseUser](#SybaseUser)                     | QString SybaseUser() const                                                              | 登录 Sybase 账号                      |
| [SybaseDatabase](#SybaseDatabase)             | QString SybaseDatabase() const                                                          | Sybase 数据库名                       |
| [MSSQLUseSystemLogin](#MSSQLUseSystemLogin)   | bool MSSQLUseSystemLogin() const                                                        | 是否使用系统账号登录MSSQL Server       |
| [transaction](#transaction)                   | bool transaction()                                                                      | 启动事务处理                           |
| [commit](#commit)                             | bool commit ()                                                                          | 提交事务                              |
| [rollback](#rollback)                         | bool rollback ()                                                                        | 事务回滚                              |
| [isNull](#isNull)                             | bool isNull() const                                                                     | 是否是空的数据库连接                   |
| [getNextNumber](#getNextNumber)               | QString getNextNumber(const QString &tablename,                                         | 按规则生成指定表指定字段的下一个编号    |
|                                               | 　　　const QString & fieldName,                                                        |                                       |
|                                               | 　　　const QString &startStr,                                                          |                                       |
|                                               | 　　　const QString &endStr, int len,                                                   |                                       |
|                                               | 　　　int addVal =1,const QChar &fillWith= QLatin1Char('0'))                            |                                       |
| [getNextNumber](#getNextNumber)               | QString getNextNumber(const QString &tablename,const QString &startStr,                 | 按规则生成指定表的关键字段的下一个编号   |
|                                               | 　　　const QString &endStr, int len,                                                   |                                       |
|                                               | 　　　int addVal =1,const QChar &fillWith= QLatin1Char('0'))                            |                                       |
| [getMaxValue](#getMaxValue)                   | QVariant getMaxValue(const QString &tablename,const QString &fieldname)                 | 获取指定表指定字段的最大值              |
| [getMaxValue](#getMaxValue)                   | QVariant getMaxValue(const QString &tablename,int fieldindex = 0)                       | 获取指定表第几个字段的最大值            |
| [getMinValue](#getMinValue)                   | QVariant getMinValue(const QString &tablename,int fieldindex = 0)                       | 获取指定表第几个字段的最小值            |
| [getMinValue](#getMinValue)                   | QVariant getMinValue(const QString &tablename,const QString &fieldname)                 | 获取指定表指定字段的最小值              |
| [getCount](#getCount)                         | int getCount(const QString &tablename,const QString &filter = "" )                      | 获取指定表指定过滤条件的记录总数        |
| [data](#data)                                 | QVariantList data(const QString &tablename,const QStringList &fieldname= QStringList()  | 查询指定表的记录集（格式1）             |
|                                               | 　　　,const QString &filter = "",                                                      |                                       |
|                                               | 　　　int sortIndex = -1, bool isASC = true)                                            |                                       |
| [getBLOB](#getBLOB)                           | QVariant getBLOB(const QString &tablename,const QString &fieldname                      | 获取BLOB字段的内容                     |
|                                               | 　　　,const QString &filter) const                                                     |                                       |
| [updateBLOB](#updateBLOB)                     | bool updateBLOB(const QString &tablename,const QString &fieldname                       | 修改BLOB字段的内容                     |
|                                               | 　　　,const QString & filter,const QString &data) const                                |                                       |
| [updateBLOB](#updateBLOB)                     | bool updateBLOB(const QString &tablename,const QString &fieldname                       | 修改BLOB字段的内容（图片格式）          |
|                                               | 　　　,const QString & filter,const QPixmap &pixmap) const                              |                                       |
| [data2](#data2)                               | QVariantList data2(const QString &tablename,const QStringList &fieldname= QStringList() | 查询指定表的记录集（格式2）             |
|                                               | 　　　,const QString &filter = "",                                                      |                                       |
|                                               | 　　　int sortIndex = -1, bool isASC = true)                                            |                                       |
| [keydata](#keydata)                           | QVariantList keydata(const QString &tablename,const QVariantList &keyvalue              | 按表的主关键字的值返回符合条件的记录集   |
|                                               | 　　　,const QStringList &fieldname = QStringList())                                    |                                       |
| [getFieldName](#getFieldName)                 | QString getFieldName(const QString &tablename, int index) const                         | 获取表的第几个字段的字段名              |
| [getFieldIndex](#getFieldIndex)               | int getFieldIndex(const QString &tablename,const QString &fieldname) const              | 获取表的某个字段在表结构中的顺序        |
| [getFieldList](#getFieldList)                 | QStringList getFieldList(const QString &tablename) const                                | 获取指定表所有字段的清单                |
| [getPrimaryKey](#getPrimaryKey)               | QStringList getPrimaryKey(const QString &tablename) const                               | 获取表主关键字段的清单                 |
| [getRealTableName](#getRealTableName)         | QString getRealTableName(const QString &tablename) const                                | 获取表的实体表名                       |
| [tablesName](#tablesName)                     | QStringList tablesName(bool includeBaseTable = false) const                             | 获取本表单所有数据表的表名清单          |
| [baseTablesName](#baseTablesName)             | QStringList baseTablesName() const                                                      | 获取本表单所有基础表的表名清单          |
| [mainTable](#mainTable)                       | QString mainTable() const                                                               | 获取本表单的主表名称                   |
| [hasTable](#hasTable)                         | bool hasTable(const QString& tablename) const                                           | 按表名查询是否存在某个表                |
| [dropTable](#dropTable)                       | bool dropTable(const QString& tablename)                                                | 按表名删除某个表                       |
| [getFieldDisplayNames](#getFieldDisplayNames) | QStringList getFieldDisplayNames(const QString &tablename) const                        | 获取指定表的所有字段的显示名称          |
| [getFieldDisplayName](#getFieldDisplayName)   | QString getFieldDisplayName(const QString &tablename,int index) const                   | 获取指定表的第几个字段的显示名称        |
| [getFieldDisplayName](#getFieldDisplayName)   | QString getFieldDisplayName(const QString &tablename,const QString& fieldname) const    | 获取指定表的某个字段的名称              |
| [getTableDisplayName](#getTableDisplayName)   | QString getTableDisplayName(const QString &tablename) const                             | 获取某个表的显示名称                   |
| [fieldIsTextType](#fieldIsTextType)           | bool fieldIsTextType(const QString& tablename ,const QString& fieldname) const          | 判断某个表的某个字段是否是字符类字段    |
| [getFieldType](#getFieldType)                 | QString getFieldType(const QString& tablename, const QString& fieldname) const          | 获取某个表某个字段的数据类型            |
| [execute](#execute)                           | QVariantList execute(const QString &sql)                                                | 执行SQL语句，并返回结果                |
| [execBatch](#execBatch)                       | bool execBatch(const QString &sql,const QVariantList &values,bool intrasaction=true)    | 批量执行SQL语句                        |
| [deleteData](#deleteData)                     | bool deleteData(const QString &tablename,const QString &filter = "" )                   | 删除记录                              |
| [deleteKeyData](#deleteKeyData)               | bool deleteKeyData(const QString &tablename,const QVariantList &keyvalue)               | 按指定关键字段的值删除记录              |
| [addData](#addData)                           | bool addData(const QString &tablename,                                                  | 添加数据                              |
|                                               | 　　　const QStringList &fieldname,const QVariantList &value) ;                         |                                       |
| [lastErrorText](#lastErrorText)               | QString lastErrorText() const                                                           | 最后执行的SQL语句的错误信息             |
| [lastSQL](#lastSQL)                           | QString lastSQL() const                                                                 | 最后执行的SQL语句                      |
| [baseQuerySql](#baseQuerySql)                 | QString baseQuerySql(bool onlyPk=false) const                                           | 表单的基础SQL语句                      |
| [baseQueryFieldsList](#baseQueryFieldsList)   | QStringList baseQueryFieldsList() const                                                 | 表单的基础查询语句的字段清单            |

- ### isUseSQLite

调用接口： bool isUseSQLite() const 

[返回目录](#category)

是否使用的 SQLite 数据库。

|   内容   | 名称 | 数据类型 |          说明           |
| ------- | ---- | ------- | ----------------------- |
| 传入参数 | 无   |         |                         |
| 返回值   |      | bool    | 是否使用的 SQLite 数据库 |

- ### SQLiteDBName

调用接口： QString SQLiteDBName() const 

[返回目录](#category)

返回使用的 SQLite 数据库文件名（不带路径）

|   内容   | 名称 | 数据类型 |    说明     |
| ------- | ---- | ------- | ----------- |
| 传入参数 | 无   |         |             |
| 返回值   |      | QString | 数据库文件名 |

- ### SQLiteDBFileName

调用接口： QString SQLiteDBFileName() const 

[返回目录](#category)

使用的 SQLite 数据库的文件名（ 带路径）。  

|   内容   | 名称 | 数据类型 |         说明          |
| ------- | ---- | ------- | -------------------- |
| 传入参数 | 无   |         |                      |
| 返回值   |      | QString | 数据库文件全路径文件名 |

- ### isUseMSSQL

调用接口： bool isUseMSSQL() const 

[返回目录](#category)

是否使用的 MicroSoft SQL Server 数据库。

|   内容   | 名称 | 数据类型 |                 说明                  |
| ------- | ---- | ------- | ------------------------------------- |
| 传入参数 | 无   |         |                                       |
| 返回值   |      | bool    | 是否使用的 MicroSoft SQL Server 数据库 |

- ### MSSQLServerName

调用接口： QString MSSQLServerName() const 

[返回目录](#category)

连接的 MSSQL 服务器名或地址。

|   内容   | 名称 | 数据类型 |            说明            |
| ------- | ---- | ------- | -------------------------- |
| 传入参数 | 无   |         |                            |
| 返回值   |      | QString  | 连接的 MSSQL 服务器名或地址 |

- ### MSSQLUser

调用接口： QString MSSQLUser() const 

[返回目录](#category)

返回连接 MSSQL 所用账号。如果是使用  Windows 账号登录，这个函数返回空字符串。

|   内容   | 名称 | 数据类型 |        说明        |
| ------- | ---- | ------- | ------------------ |
| 传入参数 |      |         |                    |
| 返回值   |      | QString | 连接 MSSQL 所用账号 |

- ### MSSQLDatabase

调用接口： QString MSSQLDatabase() const 

[返回目录](#category)

连接的 MSSQL 数据库名。

|   内容   | 名称 | 数据类型 |         说明         |
| ------- | ---- | ------- | -------------------- |
| 传入参数 | 无   |         |                      |
| 返回值   |      | QString | 连接的 MSSQL 数据库名 |

- ### isUsePostgreSQL

调用接口： bool isUsePostgreSQL() const 

[返回目录](#category)

是否使用的 PostgreSQL 数据库。

|   内容   | 名称 | 数据类型 |            说明             |
| ------- | ---- | ------- | --------------------------- |
| 传入参数 | 无   |         |                             |
| 返回值   |      | bool    | 是否使用的 PostgreSQL 数据库 |

- ### PostgreSQLServer

调用接口： QString PostgreSQLServer() const 

[返回目录](#category)

连接的 PostgreSQL 服务器名或地址。

|   内容   | 名称 | 数据类型 |              说明               |
| ------- | ---- | ------- | ------------------------------- |
| 传入参数 | 无   |         |                                 |
| 返回值   |      | QString | 连接的 PostgreSQL 服务器名或地址 |

- ### PostgreSQLPort

调用接口： QString PostgreSQLPort() const 

[返回目录](#category)

连接 PostgreSQL 使用的端口号 。

|   内容   | 名称 | 数据类型 |            说明             |
| ------- | ---- | ------- | --------------------------- |
| 传入参数 | 无   |         |                             |
| 返回值   |      | QString | 连接 PostgreSQL 使用的端口号 |

- ### PostgreSQLUser

调用接口： QString PostgreSQLUser() const 

[返回目录](#category)

登录 PostgreSQL 的账号。

|   内容   | 名称 | 数据类型 |          说明          |
| ------- | ---- | ------- | --------------------- |
| 传入参数 | 无   |         |                       |
| 返回值   |      | QString | 登录 PostgreSQL 的账号 |

- ### PostgreSQLDatabase

调用接口： QString PostgreSQLDatabase() const 

[返回目录](#category)

PostgreSQL 数据库名。

|   内容   | 名称 | 数据类型 |        说明         |
| ------- | ---- | ------- | ------------------ |
| 传入参数 | 无   |         |                    |
| 返回值   |      | QString | PostgreSQL 数据库名 |

- ### isUseSybase

调用接口： bool isUseSybase() const 

[返回目录](#category)

是否使用 Sybase 数据库。

|   内容   | 名称 | 数据类型 |         说明          |
| ------- | ---- | ------- | --------------------- |
| 传入参数 | 无     |         |                       |
| 返回值   |      | bool    | 是否使用 Sybase 数据库 |

- ### SybaseServerName

调用接口： QString SybaseServerName() const 

[返回目录](#category)

Sybase 数据服务器名。

|   内容   | 名称 | 数据类型 |        说明        |
| ------- | ---- | ------- | ------------------ |
| 传入参数 | 无   |         |                    |
| 返回值   |      | QString | Sybase 数据服务器名 |

- ### SybaseUser

调用接口： QString SybaseUser() const 

[返回目录](#category)

连接 Sybase 的账号。

|   内容   | 名称 | 数据类型 |      说明       |
| ------- | ---- | ------- | --------------- |
| 传入参数 | 无   |         |                 |
| 返回值   |      | QString | 登录 Sybase 账号 |

- ### SybaseDatabase

调用接口： QString SybaseDatabase() const 

[返回目录](#category)

连接的 Sybase 数据库名。

|   内容   | 名称 | 数据类型 | 说明 |
| ------- | ---- | ------- | ---- |
| 传入参数 | 无   | |      |
| 返回值   |      | QString         |      Sybase 数据库名|

- ### MSSQLUseSystemLogin

调用接口： bool MSSQLUseSystemLogin() const 

[返回目录](#category)

是否使用 Windows 系统账号登录MSSQL Server  。

|   内容   | 名称 | 数据类型 |                   说明                   |
| ------- | ---- | ------- | ---------------------------------------- |
| 传入参数 | 无   |         |                                          |
| 返回值   |      | bool    | 是否使用 Windows 系统账号登录MSSQL Server |

- ### transaction

调用接口： bool transaction() 

[返回目录](#category)

启动事务处理。如果启动成功，返回 True，否则返回  False。如果启动失败，可以通过 lastErrorText() 查看数据库驱动引擎返回的错误信息。

在调用此函数之后的执行的SQL语句都属于此事务。直到调用 commit() 或 rollback() 。

需要注意的是，有的数据库不支持事务处理，此函数调用也会返回  True。

如果是使用表单运行时数据引擎保存、修改、删除数据，可不需要显式地进行事务处理操作。只建议在需要开发人员通过脚本执行SQL语句处理复杂事务时使用。

|   内容   | 名称 | 数据类型 |        说明         |
| ------- | ---- | ------- | ------------------- |
| 传入参数 | 无   |         |                     |
| 返回值   |      | bool    | 启动事务处理是否成功 |

- ### commit

调用接口： bool commit () 

[返回目录](#category)

提交事务。提交成功返回 True，否则返回 False。

|   内容   | 名称 | 数据类型 |      说明       |
| ------- | ---- | ------- | --------------- |
| 传入参数 | 无     |         |                 |
| 返回值   |      | bool    | 事务提交是否成功 |

- ### rollback

调用接口： bool rollback () 

[返回目录](#category)

事务加滚，如果成功返回 True，否则返回 False。

|   内容   | 名称 | 数据类型 |      说明       |
| ------- | ---- | ------- | --------------- |
| 传入参数 | 无   |         |                 |
| 返回值   |      | bool    | 事务回滚是否成功 |

- ### isNull

调用接口： bool isNull() const 

[返回目录](#category)

是否是空的数据库连接对象。一般正常情况下不会返回 True，只为容错留用。

|   内容   | 名称 | 数据类型 |          说明           |
| ------- | ---- | ------- | ---------------------- |
| 传入参数 | 无   |         |                        |
| 返回值   |      | bool    | 是否是空的数据库连接对象 |

- ### getNextNumber

调用接口： QString getNextNumber(const QString &tablename, const QString & fieldName, const QString &startStr, const QString &endStr, int len, int addVal =1,const QChar &fillWith= QLatin1Char('0')) 

[返回目录](#category)

按规则生成指定表指定字段的下一个编号。程序会查找数据表里指定字段中，格式与传入参数相同的最大值，在最大值基础上加上 addval ，做为返回值。

比如 ```this.form.database().getNextNumber('t_bill','fnumber','a','x',8,1)``` ，对应表 t_bill 的字段 fnumber 已有记录格式为'a00000000x'的最大值，如果是'a00000010x'，这个函数会返回'a00000011x'，如果原来没有匹配的记录，返回'a00000001x'。

|   内容   |   名称    | 数据类型 |                    说明                     |
| ------- | --------- | ------- | ------------------------------------------- |
| 传入参数 | tablename | QString | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 传入参数 | fieldName | QString | 字段名                                      |
| 传入参数 | startStr  | QString | 前缀                                        |
| 传入参数 | endStr    | QString | 后缀                                        |
| 传入参数 | len       | QString | 长度                                        |
| 传入参数 | addVal    | QString | 在最大值基础上增加的值                       |
| 传入参数 | fillWith  | QChar   | 如果位数不足，在前面填充的字符                |
| 返回值   |           | QString | 下一个编号                                  |

- ### getNextNumber

调用接口： QString getNextNumber(const QString &tablename,const QString &startStr, const QString &endStr, int len, int addVal =1,const QChar &fillWith= QLatin1Char('0')) 

[返回目录](#category)

按规则生成指定表的关键字段的下一个编号。

|   内容   |   名称    | 数据类型 |                    说明                     |
| ------- | --------- | ------- | ------------------------------------------- |
| 传入参数 | tablename | QString | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 传入参数 | startStr  | QString | 前缀                                        |
| 传入参数 | endStr    | QString | 后缀                                        |
| 传入参数 | len       | QString | 长度                                        |
| 传入参数 | addVal    | QString | 在最大值基础上增加的值                       |
| 传入参数 | fillWith  | QChar   | 如果位数不足，在前面填充的字符                |
| 返回值   |           | QString | 下一个编号                                  |

- ### getMaxValue

调用接口： QVariant getMaxValue(const QString &tablename,const QString &fieldname) 

[返回目录](#category)

获取指定表指定字段的最大值。如果表名或字段名不存在，返回“0”。如果字段类型是整数或小数，返回对应的数据类型，否则都返回字符串型。

|   内容   |    名称    | 数据类型  |                    说明                     |
| ------- | --------- | -------- | ------------------------------------------- |
| 传入参数 | tablename | QString  | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 传入参数 | fieldname | QString  | 字段名                                      |
| 返回值   |           | QVariant | 最大值                                      |

- ### getMaxValue

调用接口： QVariant getMaxValue(const QString &tablename,int fieldindex = 0) 

[返回目录](#category)

获取指定表第几个字段的最大值。如果表名或字段名不存在，返回“0”。如果字段类型是整数或小数，返回对应的数据类型，否则都返回字符串型。

|   内容   |    名称    | 数据类型  |                    说明                     |
| ------- | ---------- | -------- | ------------------------------------------- |
| 传入参数 | tablename  | QString  | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 传入参数 | fieldindex | int      | 字段的顺序（从0开始）                        |
| 返回值   |            | QVariant | 最大值                                      |

- ### getMinValue

调用接口： QVariant getMinValue(const QString &tablename,int fieldindex = 0) 

[返回目录](#category)

获取指定表第几个字段的最小值。如果表名或字段名不存在，返回“0”。如果字段类型是整数或小数，返回对应的数据类型，否则都返回字符串型。

|   内容   |    名称    | 数据类型  |                    说明                     |
| ------- | ---------- | -------- | ------------------------------------------- |
| 传入参数 | tablename  | QString  | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 传入参数 | fieldindex | int      | 字段的顺序（从0开始）                        |
| 返回值   |            | QVariant | 最小值                                      |


- ### getMinValue

调用接口： QVariant getMinValue(const QString &tablename,const QString &fieldname) 

[返回目录](#category)

获取指定表指定字段的最小值。如果表名或字段名不存在，返回“0”。如果字段类型是整数或小数，返回对应的数据类型，否则都返回字符串型。

|   内容   |    名称    | 数据类型  |                    说明                     |
| ------- | --------- | -------- | ------------------------------------------- |
| 传入参数 | tablename | QString  | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 传入参数 | fieldname | int      | 字段的顺序（从0开始）                        |
| 返回值   |           | QVariant | 最小值                                      |

- ### getCount

调用接口： int getCount(const QString &tablename,const QString &filter ="" ) 

[返回目录](#category)

获取指定表指定过滤条件的记录总数。比如 ```this.form.database().getCount('t_book',"fname='001'")```。

|   内容   |   名称    | 数据类型 |                          说明                          |
| ------- | --------- | ------- | ------------------------------------------------------ |
| 传入参数 | tablename | QString | 表名，可以使用设计时的表名，也可以使用实体表名            |
| 传入参数 | filter    | QString | 过滤条件，等同于SQL语句中where子句的内容(不带where关键字) |
| 返回值   |           | int     | 记录数                                                 |

- ### data

调用接口： QVariantList data(const QString &tablename,const QStringList &fieldname= QStringList() ,const QString &filter = "", int sortIndex = -1, bool isASC = true) 

[返回目录](#category)

查询指定表的记录集（格式1）。返回值是 tuple 对象，其中每个元素对应一条记录，每条记录也是一个 tuple 对象，每个元素为各个字段的值，如下例所示：

``` python

>>> db=this.form.database()

>>> db.data('t_book',['ID','fname'])
((1, '数学'), (2, '人生'), (3, '诗集'))

>>> db.data('t_book',('ID','fname'))
((1, '数学'), (2, '人生'), (3, '诗集'))

```

|   内容   |   名称    |   数据类型    |                          说明                          |
| ------- | --------- | ------------ | ------------------------------------------------------ |
| 传入参数 | tablename | QString      | 表名，可以使用设计时的表名，也可以使用实体表名            |
| 传入参数 | fieldname | QStringList  | 需要查询的字段清单，用 list 和 tuple 都可以              |
| 传入参数 | filter    | QString      | 过滤条件，等同于SQL语句中where子句的内容(不带where关键字) |
| 传入参数 | sortIndex | int          | 排序的字段，缺省值 -1 表示不排序                         |
| 传入参数 | isASC     | bool         | 排序方式，True 表示升序，False 表示降序                  |
| 返回值   |           | QVariantList | 符合条件的记录集                                        |

- ### getBLOB

调用接口： QVariant getBLOB(const QString &tablename,const QString &fieldname  ,const QString &filter) const 

[返回目录](#category)

获取指定表、指定的BLOB字段的内容。

如果查询出多条符合 filter 的记录，也只会返回第一条记录的内容。所以需要注意 filter 最好定位到确定的一条记录，否则会增加数据传输负担。

如果表名、字段名无效，或指定字段不是BLOB型字段，或没有符合条件的记录，返回 None。

|   内容   |   名称    | 数据类型  |                          说明                          |
| ------- | --------- | -------- | ------------------------------------------------------ |
| 传入参数 | tablename | QString  | 表名，可以使用设计时的表名，也可以使用实体表名            |
| 传入参数 | fieldname | int      | 字段的顺序（从0开始）                                   |
| 传入参数 | filter    | QString  | 过滤条件，等同于SQL语句中where子句的内容(不带where关键字) |
| 返回值   |           | QVariant | BLOB字段的内容                                          |

- ### updateBLOB

调用接口： bool updateBLOB(const QString &tablename,const QString &fieldname ,const QString & filter,const QString &data) const 

[返回目录](#category)

修改指定表、指定BLOB字段的内容。如果传入参数都为空，返回 False。否则按执行是否成功返回结果。

|   内容   |   名称    | 数据类型 |                          说明                          |
| ------- | --------- | ------- | ------------------------------------------------------ |
| 传入参数 | tablename | QString  | 表名，可以使用设计时的表名，也可以使用实体表名            |
| 传入参数 | fieldname | int      | 字段的顺序（从0开始）                                   |
| 传入参数 | filter    | QString  | 过滤条件，等同于SQL语句中where子句的内容(不带where关键字) |
| 传入参数 | data      | QString  | BLOB字段的内容                                          |
| 返回值   |           | bool    | 修改是否成功                                            |

- ### updateBLOB

调用接口： bool updateBLOB(const QString &tablename,const QString &fieldname  ,const QString & filter,const QPixmap &pixmap) const 

[返回目录](#category)

|   内容   |   名称    | 数据类型 |                          说明                          |
| ------- | --------- | ------- | ------------------------------------------------------ |
| 传入参数 | tablename | QString  | 表名，可以使用设计时的表名，也可以使用实体表名            |
| 传入参数 | fieldname | int      | 字段的顺序（从0开始）                                   |
| 传入参数 | filter    | QString  | 过滤条件，等同于SQL语句中where子句的内容(不带where关键字) |
| 传入参数 | pixmap    | QPixmap  | 需要用BLOB字段保存数据的图片对象                         |
| 返回值   |           | bool    | 修改是否成功                                            |

- ### data2

调用接口： QVariantList data2(const QString &tablename,const QStringList &fieldname= QStringList() ,const QString &filter = "",  int sortIndex = -1, bool isASC = true) 

[返回目录](#category)

查询指定表的记录集（格式2）。返回值是 tuple 对象，其中每个元素对应一个字段每条记录的值。如下例所示：

``` python

>>> db=this.form.database()

>>> db.data2('t_book',['ID','fname'])
((1, 2, 3),('数学', '人生', '诗集'))

>>> db.data2('t_book',('ID','fname'))
((1, 2, 3),('数学', '人生', '诗集'))

```

|   内容   |   名称    |   数据类型    |                          说明                          |
| ------- | --------- | ------------ | ------------------------------------------------------ |
| 传入参数 | tablename | QString      | 表名，可以使用设计时的表名，也可以使用实体表名            |
| 传入参数 | fieldname | QStringList  | 需要查询的字段清单，用 list 和 tuple 都可以              |
| 传入参数 | filter    | QString      | 过滤条件，等同于SQL语句中where子句的内容(不带where关键字) |
| 传入参数 | sortIndex | int          | 排序的字段，缺省值 -1 表示不排序                         |
| 传入参数 | isASC     | bool         | 排序方式，True 表示升序，False 表示降序                  |
| 返回值   |           | QVariantList | 符合条件的记录集                                        |

- ### keydata

调用接口： QVariantList keydata(const QString &tablename,const QVariantList &keyvalue ,const QStringList &fieldname = QStringList()) 

[返回目录](#category)

按表的主关键字的值返回符合条件的记录集 。

|   内容   |   名称    |   数据类型   |                    说明                     |
| ------- | --------- | ------------ | ------------------------------------------- |
| 传入参数 | tablename | QString      | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 传入参数 | fieldname | QStringList  | 需要查询的字段清单，用 list 和 tuple 都可以   |
| 返回值   |           | QVariantList | 符合条件的记录集                             |

- ### getFieldName

调用接口： QString getFieldName(const QString &tablename, int index) const 

[返回目录](#category)

获取表的第几个字段的字段名。

|   内容   |   名称    | 数据类型 |                    说明                     |
| ------- | --------- | ------- | ------------------------------------------- |
| 传入参数 | tablename | QString | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 传入参数 | index     | int     | 字段在表结构中的序号（0开始）                 |
| 返回值   |           | QString | 字段名                                      |

- ### getFieldIndex

调用接口： int getFieldIndex(const QString &tablename,const QString &fieldname) const 

[返回目录](#category)

获取表的某个字段在表结构中的顺序。

|   内容   |   名称    | 数据类型 |                    说明                     |
| ------- | --------- | ------- | ------------------------------------------- |
| 传入参数 | tablename | QString | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 传入参数 | fieldname | QString | 需要查询的字段名                             |
| 返回值   |           | int     | 在表结构中的顺序（0开始）                    |

- ### getFieldList

调用接口： QStringList getFieldList(const QString &tablename) const 

[返回目录](#category)

获取指定表所有字段的清单。

|   内容   |   名称    |   数据类型   |                    说明                     |
| ------- | --------- | ----------- | ------------------------------------------- |
| 传入参数 | tablename | QString     | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 返回值   |           | QStringList | 所有字段的清单                               |

- ### getPrimaryKey

调用接口： QStringList getPrimaryKey(const QString &tablename) const 

[返回目录](#category)

获取表主关键字段的清单 .

|   内容   |   名称    |   数据类型   |                    说明                     |
| ------- | --------- | ----------- | ------------------------------------------- |
| 传入参数 | tablename | QString     | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 返回值   |           | QStringList | 关键字段的字段名清单                         |

- ### getRealTableName

调用接口： QString getRealTableName(const QString &tablename) const 

[返回目录](#category)

获取表的实体表名 。

|   内容   |   名称    | 数据类型 |         说明          |
| ------- | --------- | ------- | -------------------- |
| 传入参数 | tablename | QString | 表名，使用设计时的表名 |
| 返回值   |           |         | 实体表名              |

- ### tablesName

调用接口： QStringList tablesName(bool includeBaseTable = false) const 

[返回目录](#category)

获取本表单所有数据表的表名清单。注意返回的是设计时表名。

|   内容   |       名称       |   数据类型   |             说明             |
| ------- | ---------------- | ----------- | ---------------------------- |
| 传入参数 | includeBaseTable | bool        | 是否包括基础表                |
| 返回值   |                  | QStringList | 所有表的表名清单（设计时表名） |

- ### baseTablesName

调用接口： QStringList baseTablesName() const 

[返回目录](#category)

获取本表单所有基础表的表名清单 。注意返回的是设计时表名。

|   内容   | 名称 |   数据类型   |               说明               |
| ------- | ---- | ----------- | -------------------------------- |
| 传入参数 | 无   |             |                                  |
| 返回值   |      | QStringList | 所有基础表的表名清单（设计时表名） |

- ### mainTable

调用接口： QString mainTable() const 

[返回目录](#category)

获取本表单的主表名称。

|   内容   | 名称 | 数据类型 |                  说明                   |
| ------- | ---- | ------- | --------------------------------------- |
| 传入参数 | 无   |         |                                         |
| 返回值   |      | QString | 表单的主表，返回设计时的表名，不是实体表名 |

- ### hasTable

调用接口： bool hasTable(const QString& tablename) const 

[返回目录](#category)

按表名查询是否存在某个表  。

|   内容   |   名称    | 数据类型 |                     说明                      |
| ------- | --------- | ------- | --------------------------------------------- |
| 传入参数 | tablename | QString | 表名，注意只能使用实体表名，不能使用设计时的表名 |
| 返回值   |           | bool    | 是否存在这个表                                 |

- ### dropTable

调用接口： bool dropTable(const QString& tablename) 

[返回目录](#category)

按表名删除某个表。删除成功返回 True，否则返回 False。

|   内容   |   名称    | 数据类型 |                    说明                     |
| ------- | --------- | ------- | ------------------------------------------- |
| 传入参数 | tablename | QString | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 返回值   |           | bool    | 是否删除成功                                 |

- ### getFieldDisplayNames

调用接口： QStringList getFieldDisplayNames(const QString &tablename) const 

[返回目录](#category)

获取指定表的所有字段的显示名称 。

|   内容   |   名称    | 数据类型 |                    说明                     |
| ------- | --------- | ------- | ------------------------------------------- |
| 传入参数 | tablename | QString | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 返回值   |           |         | 所有字段的显示名称的添单                     |

- ### getFieldDisplayName

调用接口： QString getFieldDisplayName(const QString &tablename,int index) const 

[返回目录](#category)

获取指定表的第几个字段的显示名称 。

|   内容   |   名称    | 数据类型 |                    说明                     |
| ------- | --------- | ------- | ------------------------------------------- |
| 传入参数 | tablename | QString | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 传入参数 | index     | int     | 需要查询的字段在表中的顺序（0开始）           |
| 返回值   |           | QString | 字段的显示名称                               |

- ### getFieldDisplayName

调用接口： QString getFieldDisplayName(const QString &tablename,const QString& fieldname) const 

[返回目录](#category)

获取指定表的某个字段的名称 。

|   内容   |   名称    | 数据类型 |                    说明                     |
| ------- | --------- | ------- | ------------------------------------------- |
| 传入参数 | tablename | QString | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 传入参数 | fieldname | QString | 需要查询的字段                               |
| 返回值   |           | QString | 字段的显示名称                               |

- ### getTableDisplayName

调用接口： QString getTableDisplayName(const QString &tablename) const 

[返回目录](#category)

获取某个表的显示名称。

|   内容   |   名称    | 数据类型 |                    说明                     |
| ------- | --------- | ------- | ------------------------------------------- |
| 传入参数 | tablename | QString | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 返回值   |           | QString | 表的显示名称                                 |

- ### fieldIsTextType

调用接口： bool fieldIsTextType(const QString& tablename ,const QString& fieldname) const 

[返回目录](#category)

判断某个表的某个字段是否是字符类字段 。如果是，返回 True，否则返回 False。

|   内容   |   名称    | 数据类型 |                    说明                     |
| ------- | --------- | ------- | ------------------------------------------- |
| 传入参数 | tablename | QString | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 传入参数 | fieldname | QString | 需要查询的字段                               |
| 返回值   |           | bool    | 是否是字符型字段                             |

- ### getFieldType

调用接口： QString getFieldType(const QString& tablename, const QString& fieldname) const 

[返回目录](#category)

获取某个表某个字段的类型 。

|   内容   |   名称    | 数据类型 |                    说明                     |
| ------- | --------- | ------- | ------------------------------------------- |
| 传入参数 | tablename | QString | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 传入参数 | fieldname | QString | 需要查询的字段                               |
| 返回值   |           | QString | 字段的类型                                  |

- ### execute

调用接口： QVariantList execute(const QString &sql) 

[返回目录](#category)

执行SQL语句，并返回结果。Select 语句会返回查询到的记录集，返回记录集的格式同 data 函数。其它语句返回空的 tuple 。可用 lastErrorText() 函数了解执行中产生的错误信息，如果得到空字符串，表示执行成功。

比如：

``` python 

>>> db=this.form.database()

>>> db.execute("select fname from "+db.getRealTableName('t_book'))
(('数学',), ('人生',), ('诗集',))

>>> db.execute("select ID,fname from "+db.getRealTableName('t_book'))
((1,'数学'), (2,'人生'), (3,'诗集'))

>>> db.execute("delete from "+db.getRealTableName('t_book'))
()

>>> db.lastErrorText()
''

```

|   内容   | 名称 |   数据类型    |       说明       |
| ------- | ---- | ------------ | ---------------- |
| 传入参数 | sql  | QString      | 需要执行的SQL语句 |
| 返回值   |      | QVariantList | 执行的结果        |

- ### execBatch

调用接口： bool execBatch(const QString &sql,const QVariantList &values,bool intransaction=true) 

[返回目录](#category)

批量执行SQL语句。传入参数 sql 中可使用占位符，在 values 中列出多组对应的值，以便使用这些值批量执行这个 SQL 语句。

|   内容   |     名称      |   数据类型    |           说明           |
| ------- | ------------- | ------------ | ----------------------- |
| 传入参数 | sql           | QString      | 使用占位符的待执行SQL语句 |
| 传入参数 | values        | QVariantList | 代替占位符的数据清单      |
| 传入参数 | intransaction | bool         | 是否使用事务处理          |
| 返回值   |               | bool         | 是否执行成功             |

- ### deleteData

调用接口： bool deleteData(const QString &tablename,const QString &filter = "") 

[返回目录](#category)

删除指定表中符合过滤条件的所有记录。

|   内容   |   名称    | 数据类型 |                    说明                     |
| ------- | --------- | ------- | ------------------------------------------- |
| 传入参数 | tablename | QString | 表名，可以使用设计时的表名，也可以使用实体表名 |
| 传入参数 | filter    | QString | 过滤条件                                    |
| 返回值   |           | bool    | 是否成功删除                                 |

- ### deleteKeyData

调用接口： bool deleteKeyData(const QString &tablename,const QVariantList &keyvalue) 

[返回目录](#category)

删除指定表中关键字段值符合条件的记录。

|   内容   |   名称    |   数据类型   |                           说明                           |
| ------- | --------- | ------------ | -------------------------------------------------------- |
| 传入参数 | tablename | QString      | 表名，可以使用设计时的表名，也可以使用实体表名              |
| 传入参数 | keyvalue  | QVariantList | 需要删除的记录的关键字段的值的清单，用 list 和 tuple 都可以 |
| 返回值   |           | bool         | 是否成功删除                                              |

- ### addData

调用接口： bool addData(const QString &tablename,  const QStringList &fieldname,const QVariantList &value) ; 

[返回目录](#category)

往指定表里添加数据。这个函数只用于添加一条记录。如果需要一次添加多条记录，使用 execBatch() 函数。如果记录较多，用 execBatch 速度较快，但需要提前按格式准备好数据。

|   内容   |   名称    |   数据类型   |                         说明                          |
| ------- | --------- | ------------ | ----------------------------------------------------- |
| 传入参数 | tablename | QString      | 表名，可以使用设计时的表名，也可以使用实体表名           |
| 传入参数 | fieldname | QStringList  | 需要查询的字段清单，用 list 和 tuple 都可以             |
| 传入参数 | value     | QVariantList | 需要添加的数据，数据的格式与 data() 返回的结果格式相同。 |
| 返回值   |           | bool         | 是否添加成功                                          |

- ### lastErrorText

调用接口： QString lastErrorText() const 

[返回目录](#category)

返回最后执行的SQL语句的错误信息。如果语句执行成功无错，返回空字符串。

运行时环境后台的数据库引擎执行产生的错误不会通过这个函数反馈给开发者。只有通过 this.form.database 调用的几个函数产生的错误才能通过这个函数了解执行情况。

在程序中如果需要调用 ```this.form.database.execute()``` ，可以通过这个函数了解刚才执行的SQL语句是否执行有错。比如：

``` python 

>>> db=this.form.database()

>>> db.execute("select notexistfield from notexisttable")
()

>>> db.lastErrorText()
'no such table: notexisttable Unable to execute statement'

>>> db.execute("select notexistfield from "+db.getRealTableName('t_book'))
()

>>> db.lastErrorText()
'no such column: notexistfield Unable to execute statement'

>>> db.execute("select fname from "+db.getRealTableName('t_book'))
(('数学',), ('人生',), ('诗集',))

>>> db.lastErrorText()
''

```

|   内容   | 名称 | 数据类型 |            说明            |
| ------- | ---- | ------- | ------------------------- |
| 传入参数 | 无     |         |                           |
| 返回值   |      | QString | 最后执行的SQL语句的错误信息 |

- ### lastSQL

调用接口： QString lastSQL() const 

[返回目录](#category)

返回最后执行的SQL语句。

|   内容   | 名称 | 数据类型 |       说明       |
| ------- | ---- | ------- | ---------------- |
| 传入参数 | 无   |         |                  |
| 返回值   |      | QString | 最后执行的SQL语句 |

- ### baseQuerySql

调用接口： QString baseQuerySql(bool onlyPk=false) const 

[返回目录](#category)

返回表单主表的基础SQL语句。

``` python

>>> db=this.form.database()
>>> db.baseQuerySql()
'select t0.ID,t0.fname,t0.fauthor,t0.fclass,t0.fyear,t0.fISBN,t0.UUID,t0.lastUpdated from RT_T_BOOK_0_S t0 '

```

|   内容   | 名称 | 数据类型 |       说明       |
| ------- | ---- | ------- | ---------------- |
| 传入参数 | 无   |         |                  |
| 返回值   |      | QString | 主表的查询SQL语句 |

- ### baseQueryFieldsList

调用接口： QStringList baseQueryFieldsList() const 

[返回目录](#category)

表单的基础查询语句的字段清单。需要注意的是返回的是字段的显示名称，而不是数据表中字段名称  。比如：

``` python

>>> db=this.form.database()
>>> db.baseQueryFieldsList()
('序号', '书名', '作者', '分类', '出版年份', 'ISBN', '记录UUID', '最后更新日期时间')

```

|   内容   | 名称 |   数据类型   |            说明            |
| ------- | ---- | ----------- | -------------------------- |
| 传入参数 | 无   |             |                            |
| 返回值   |      | QStringList | 表单的基础查询语句的字段清单 |

---

## DatabaseConnection的属性

|      属性      |  类型   | 读写状态  |             说明             |
| -------------- | ------- | -------- | ---------------------------- |
| objectName     | QString | 可读 可写 | 对象名称                     |
| server         | QString | 可读      | 连接的服务器名或IP地址        |
| port           | QString | 可读      | 连接使用的端口号              |
| user           | QString | 可读      | 连接使用的登录账号            |
| database       | QString | 可读      | 连接的数据库名                |
| useSystemLogin | bool    | 可读      | 是否使用 windows 系统账号登录 |
| useTDS         | bool    | 可读      | 是否使用TDS连接              |
| useSqlite      | bool    | 可读      | 是否使用的 SQLite 数据库      |
| useMSSQL       | bool    | 可读      | 是否使用的 MSSQL 数据库       |
| usePostgreSQL  | bool    | 可读      | 是否使用的 PostgreSQL 数据库  |
| SqliteName     | QString | 可读      | 使用的 SQLite 数据库名        |
| name           | QString | 可读      | 连接的名称                   |
| isOpen         | bool    | 可读      | 是否已连接                   |

## DatabaseConnection的成员函数

|                        属性                         |             说明              |
| -------------------------------------------------- | ----------------------------- |
| [close](#close)                                    | 关闭连接                      |
| [connectLocalMSSQL](#connectLocalMSSQL)            | 连接到本地 MSSQL Server 数据库 |
| [connectMSSQL](#connectMSSQL)                      | 连接到 MSSQL Server 数据库    |
| [connectSqlite](#connectSqlite)                    | 连接到 SQLite 数据库           |
| [connectTDS](#connectTDS)                          | 使用 TDS 连接到 Sybase 数据库  |
| [execBatch](#execbatchDatabaseConnection)        | 批量执行 SQL 语句              |
| [open](#open)                                      | 打开连接                      |
| [lastErrorText](#lasterrortextDatabaseConnection) | 最后执行的SQL语句的错误信息     |
| [lastSQL](#lastsqlDatabaseConnection)              | 最后执行的SQL语句              |
| [execute](#executeDatabaseConnection)              | 执行SQL语句                   |

- ### close

调用接口：bool close() 

[返回目录](#DatabaseConnection的成员函数)

关闭这个数据库连接。

|   内容   | 名称 | 数据类型 |    说明     |
| ------- | ---- | ------- | ----------- |
| 传入参数 | 无   |         |             |
| 返回值   |      | bool    | 关闭是否成功 |

- ### connectLocalMSSQL

调用接口：bool connectLocalMSSQL(const QString& database,const QString& user="",const QString& password="");

[返回目录](#DatabaseConnection的成员函数)

连接到本地的 MSSQL Server 数据库。是否能连接取决于运行时环境是否有提供 MSSQL Server 的数据库驱动程序，比如 biReader 的 Linux 版本没有提供这个驱动，调用这个函数就不能连接成功。

|   内容   |   名称   | 数据类型 |    说明     |
| ------- | -------- | ------- | ----------- |
| 传入参数 | database | QString | 数据库名     |
| 传入参数 | user     | QString | 登录的账号   |
| 传入参数 | password | QString | 登录的密码   |
| 返回值   |          | bool    | 是否连接成功 |

- ### connectMSSQL

调用接口：bool connectMSSQL(const QString& server,const QString& database,const QString& user="",const QString& password="");

[返回目录](#DatabaseConnection的成员函数)

连接到 MSSQL Server 数据库。是否能连接取决于运行时环境是否有提供 MSSQL Server 的数据库驱动程序，比如 biReader 的 Linux 版本没有提供这个驱动，调用这个函数就不能连接成功。

|   内容   |   名称   | 数据类型 |        说明         |
| ------- | -------- | ------- | ------------------- |
| 传入参数 | server   | QString | 数据库服务名或IP地址 |
| 传入参数 | database | QString | 数据库名            |
| 传入参数 | user     | QString | 登录的账号          |
| 传入参数 | password | QString | 登录的密码          |
| 返回值   |          | bool    | 是否连接成功         |

- ### connectSqlite

调用接口：bool connectSqlite(const QString& dbname);

[返回目录](#DatabaseConnection的成员函数)

连接到 SQLite 数据库。

|   内容   |  名称  | 数据类型 |             说明             |
| ------- | ------ | ------- | --------------------------- |
| 传入参数 | dbname | QString | SQLite 数据库文件全路径文件名 |
| 返回值   |        | bool    | 是否连接成功                 |

- ### connectTDS

调用接口：bool connectTDS(const QString& server,const  QString& database,const QString& user="",const QString& password="");

[返回目录](#DatabaseConnection的成员函数)

使用TDS连接到 Sybase 数据库。是否能连接取决于运行时环境是否有提供 TDS 的数据库驱动程序，比如 biReader 的 Linux 版本没有提供这个驱动，调用这个函数就不能连接成功。

|   内容   |   名称   | 数据类型 |        说明         |
| ------- | -------- | ------- | ------------------- |
| 传入参数 | server   | QString | 数据库服务名或IP地址 |
| 传入参数 | database | QString | 数据库名            |
| 传入参数 | user     | QString | 登录的账号          |
| 传入参数 | password | QString | 登录的密码          |
| 返回值   |          | bool    | 是否连接成功         |

- ### execBatch

调用接口：bool execBatch(const QString &sql,QVariantList values, bool intransaction);

[返回目录](#DatabaseConnection的成员函数)

批量执行SQL语句。用法参考 [execBatch](#execBatch)。

|   内容   |     名称      |    数据类型    |           说明           |
| ------- | ------------- | ------------- | ----------------------- |
| 传入参数 | sql           | QString       | 待执行的SQL语句          |
| 传入参数 | values        | QVariantListg | 替代SQL语句中占位符的数据 |
| 传入参数 | intransaction | bool          | 是否启动事务             |
| 返回值   |               | bool          | 是否执行成功             |

- ### open

调用接口：bool open() ;

[返回目录](#DatabaseConnection的成员函数)

连接数据库。

|   内容   | 名称 | 数据类型 |    说明     |
| ------- | ---- | ------- | ----------- |
| 传入参数 | 无   |         |             |
| 返回值   |      | bool    | 是否连接成功 |

- ### lasterrortext(DatabaseConnection)

调用接口：QString lastErrorText() const;

[返回目录](#DatabaseConnection的成员函数)

最后执行的SQL语句返回的错误信息。

|   内容   | 名称 | 数据类型 |   说明   |
| ------- | ---- | ------- | ------- |
| 传入参数 | 无   |         |         |
| 返回值   |      | QString | 错误信息 |

- ### lastSQL(DatabaseConnection)

调用接口：QString lastSQL() const;

[返回目录](#DatabaseConnection的成员函数)

这个函数返回最后执行的SQL语句的内容。只处理通过脚本接口执行的SQL语句，数据库引擎内部执行的SQL语句不能通过这个接口查询。

|   内容   | 名称 | 数据类型 |          说明          |
| ------- | ---- | ------- | ---------------------- |
| 传入参数 | 无   |         |                        |
| 返回值   |      | QString | 最后执行的SQL语句的内容 |

- ### execute(DatabaseConnection)

调用接口：QVariantList execute(const QString & sql)

[返回目录](#DatabaseConnection的成员函数)

执行SQL语句，可以是多条SQL语句，如果最后一条是 select 语句，会返回查询的结果，返回数据的格式参考 [FormDBDelegate::data()](#data)。

执行是否成功，可以使用 lastErrorText() 查看报错信息。可以用 lastSQL() 跟踪最后执行的SQL语句的内容。

|   内容   | 名称 |   数据类型    |       说明       |
| ------- | ---- | ------------ | ---------------- |
| 传入参数 | sql  | QString      | 需要执行的SQL语句 |
| 返回值   |      | QVariantList |                  |
