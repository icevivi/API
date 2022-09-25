# 第一章 biForm开发基础 - 表单的属性

表单指运行时表单控件本身，在 Python  脚本中 ```this.form.属性名``` 来访问其各属性。

<h2 id=category>目录</h2>

|                     属性                      | 值类型  | 读写类型  |              说明               |
| --------------------------------------------- | ------- | -------- | ------------------------------- |
| [background](#background)                     | QColor  | 可读 可写 | 背景色                          |
| [caption](#caption)                           | QString | 可读 可写 | 标题                            |
| [createNewEnabled](#createNewEnabled)         | bool    | 可读 可写 | 是否允许使用“新建”按钮           |
| [dropEnabled](#dropEnabled)                   | bool    | 可读 可写 | 是否允许使用“删除”按钮           |
| [exportEnabled](#exportEnabled)               | bool    | 可读 可写 | 是否允许导出到PFD文件            |
| [font](#font)                                 | QFont   | 可读      | 默认字体                        |
| [foreground](#foreground)                     | QColor  | 可读      | 默认前景色                       |
| [height](#height)                             | int     | 可读 可写 | 高度                            |
| [imageFillType](#imageFillType)               | int     | 可读 可写 | 背景图片填充方式                 |
| [imageName](#imageName)                       | QString | 可读 可写 | 背景图片名称                     |
| [importEnabled](#importEnabled)               | bool    | 可读 可写 | 是否允许从PFD文件导入记录数据     |
| [isModified](#isModified)                     | bool    | 可读 可写 | 是否被修改过                     |
| [locationbarEnabled](#locationbarEnabled)     | bool    | 可读 可写 | 是否显示记录定位器               |
| [mainTable](#mainTable)                       | QString | 可读      | 主表的表名                       |
| [margin](#margin)                             | int     | 可读 可写 | 图片背景与边界的距离             |
| [name](#name)                                 | QString | 可读      | 表单的名称                       |
| [objectName](#objectName)                     | QString | 可读 可写 | 表单控件的对象名称               |
| [printEnabled](#printEnabled)                 | bool    | 可读 可写 | 是否允许打印/打印预览            |
| [printFormUUID](#printFormUUID)               | QString | 可读 可写 | 用来格式化打印的表单UUID         |
| [printPageNumber](#printPageNumber)           | bool    | 可读 可写 | 打印时是否显示页号               |
| [publishUUID](#publishUUID)                   | QString | 可读      | 运行时表单的发布UUID             |
| [PFFVersion](#PFFVersion)                     | QString | 可读      | 表单开发时使用的PFF引擎版本号     |
| [queryEnabled](#queryEnabled)                 | bool    | 可读 可写 | 是否允许使用“查询”按钮           |
| [remark](#remark)                             | QString | 可读      | 表单说明                        |
| [saveEnabled](#saveEnabled)                   | bool    | 可读 可写 | 是否允许使用“保存”按钮           |
| [showBKImageInPDF](#showBKImageInPDF)         | bool    | 可读 可写 | 背景图片在输出为PDF文件时是否显示 |
| [showBKImageInPrinter](#showBKImageInPrinter) | bool    | 可读 可写 | 背景图片在打印时是否显示          |
| [toolbarEnabled](#toolbarEnabled)             | bool    | 可读 可写 | 是否显示工具条                   |
| [transBKInPDF](#transBKInPDF)                 | bool    | 可读 可写 | PDF输出时使用透明背景            |
| [transBKInPrinter](#transBKInPrinter)         | bool    | 可读 可写 | 打印时使用透明背景               |
| [userHelp](#userHelp)                         | QString | 可读      | 用户使用说明                     |
| [UUID](#UUID)                                 | QString | 可读      | 表单的全程唯一标识（UUID）       |
| [version](#version)                           | int     | 可读      | 版本                            |
| [width](#width)                               | int     | 可读 可写 | 宽度                            |

属性的读写示例 ：

``` python 

#读取表单的标题，注意caption之后不需要用()
print(this.form.caption)
#修改表单的标题，直接对属性赋值
this.form.caption = '新标题'
#或调用函数进行修改
this.form.setCaption('新标题')

```

## 详细说明

### background

[返回目录](#category)

属性：表单的背景色。

如果设置了背景图片，这个属性就没有效果。

|      |                       调用接口                        |
| ---- | ---------------------------------------------------- |
| 读取 | QColor background() const                            |
| 修改 | void setBackground( const QColor &background ) const |

### caption

[返回目录](#category)

属性：表单的标题。

在运行时会做为对话框标题、子文档的标题、菜单项等显示。

|      |                     调用接口                     |
| ---- | ----------------------------------------------- |
| 读取 | QString caption() const                         |
| 修改 | void setCaption( const QString &caption ) const |

### createNewEnabled

[返回目录](#category)

属性：是否允许使用“新建”按钮。

在运行时状态下，点击表单工具栏上的“新建”按钮时，表示是要创建一个新的空白表单，程序会将所有控件的状态恢复到缺省状态。

|      |                         调用接口                         |
| ---- | ------------------------------------------------------- |
| 读取 | bool createNewEnabled() const                           |
| 修改 | void setCreateNewEnabled( bool createNewEnabled ) const |

### dropEnabled

[返回目录](#category)

属性：是否允许使用“删除”按钮。

|      |                    调用接口                    |
| ---- | --------------------------------------------- |
| 读取 | bool dropEnabled() const                      |
| 修改 | void setDropEnabled( bool dropEnabled ) const |

### exportEnabled

[返回目录](#category)

属性：是否允许导出到PFD文件。

导出PFD文件的功能只为有“主表”属性的表单设计，会将当前记录导出为PFD文件。非此类表单，这个属性没有什么影响。

|      |                      调用接口                      |
| ---- | ------------------------------------------------- |
| 读取 | bool exportEnabled() const                        |
| 修改 | void setExportEnabled( bool exportEnabled ) const |

### font

[返回目录](#category)

属性：默认字体。

这个属性在设计阶段，往表单上添加新控件时，会继承这个属性为新控件设置缺省字体。在运行时阶段，这个属性只读。

|      |      调用接口       |
| ---- | ------------------ |
| 读取 | QFont font() const |

### foreground

[返回目录](#category)

属性：默认前景色。

这个属性在设计阶段，往表单上添加新控件时，会继承这个属性为新控件设置缺省前景色。在运行时阶段，这个属性只读。

|      |          调用接口          |
| ---- | ------------------------- |
| 读取 | QColor foreground() const |

### height

[返回目录](#category)

属性：表单的高度。

需要注意的是，如果表单的属性“不使用缺省的框架样式”为“是”时，表单会自动调到最大以便适应主窗口的尺寸，修改这个值并不会影响表单的实际高度。

|      |              调用接口               |
| ---- | ---------------------------------- |
| 读取 | int height() const                 |
| 修改 | void setHeight( int height ) const |

### imageFillType

[返回目录](#category)

属性：背景图片填充方式。

|      |                     调用接口                      |
| ---- | ------------------------------------------------ |
| 读取 | int imageFillType() const                        |
| 修改 | void setImageFillType( int imageFillType ) const |
|      | **imageFillType 取值:**                          |
|      | pub.TEXTURE_BACKGROUND 连续填充                   |
|      | pub.LEFTTOP_CORNER 只显示在左上角                 |
|      | pub.RIGHTTOP_CORNER 只显示在右上角                |
|      | pub.LEFTBOTTOM_CORNER 只显示在左下角              |
|      | pub.RIGHTBOTTOM_CORNER 只显示在右下角             |
|      | pub.IMAGE_CENTER 在表单中央显示                   |

### imageName

[返回目录](#category)

属性：背景图片的名称。

背景图片是从图片集中选取的，所以这个属性对应图片在图片集中的名称。

|      |                       调用接口                       |
| ---- | --------------------------------------------------- |
| 读取 | QString imageName() const                           |
| 修改 | void setImageName( const QString &imageName ) const |

### importEnabled

[返回目录](#category)

属性：是否允许从PFD文件导入记录数据。只对设置了“主表”属性的表单有效。

|      |                      调用接口                      |
| ---- | ------------------------------------------------- |
| 读取 | bool importEnabled() const                        |
| 修改 | void setImportEnabled( bool importEnabled ) const |

### isModified

[返回目录](#category)

属性：数据是否被修改过。

表单上可以用于输入数据的控件，如“单行文本输入控件”、“整数编辑器”等，有一个属性“是否影响表单数据”，如果该属性值为“是”，这些控件从上次使用“保存”按钮保存过数据之后，如果进行过编辑（不一定是值发生了变化，只要进行过编辑），表单的 isModified 的值会变为 True，在“保存”后，isModified 会被置为 False。在 isModified 值为 True 时，在多文档窗口状态下，子文档窗口标题会显示“*”以表示数据被修改过，如果关闭表单，会提示是否要先保存数据。这部分是运行时引擎自动处理的，开发者也可以使用 setIsModified 主动修改这个属性的值。

|      |                   调用接口                   |
| ---- | ------------------------------------------- |
| 读取 | bool isModified() const                     |
| 修改 | void setIsModified( bool isModified ) const |

### locationbarEnabled

[返回目录](#category)

属性：是否显示记录定位器。

|      |                           调用接口                           |
| ---- | ----------------------------------------------------------- |
| 读取 | bool locationbarEnabled() const                             |
| 修改 | void setLocationbarEnabled( bool locationbarEnabled ) const |

### mainTable

[返回目录](#category)

属性：表单的数据视图中“主表”的表名。

表单的“主表”是指表单数据需要保存到数据库时，记录对应的主表。设置了这个属性之后，运行时的数据库引擎能自动提供非常丰富的封装功能。如果不希望使用这些自动提供的功能，也可以自己写程序读写数据库和展示数据。

这个属性是只读的，只能在设计阶段设置好，不允许在运行时状态下修改这个属性。

|      |          调用接口          |
| ---- | ------------------------- |
| 读取 | QString mainTable() const |

### margin

[返回目录](#category)

属性：表单背景图片与边界的距离。只在设置了背景图片时有效。背景图片绘制时，会在四周留出边界，这个属性指这个边界的宽度。

|      |                 调用接口                 |
| ---- | --------------------------------------- |
| 读取 | int margin() const                      |
| 修改 | void setMargin( int width margin) const |

### name

[返回目录](#category)

属性：表单的名称。只允许由阿拉伯字母、数字、下划线构成。

不同的表单这个属性是允许重复的，所以它并不能唯一标识一个表单，只有UUID属性才能唯一地标识一个表单。表单名称会用于设置表单控件名称和设置表单对应的 Python 模块名称。给一个表单设置一个有意义的名字，会有助于进行程序调试。

|      |       调用接口        |
| ---- | -------------------- |
| 读取 | QString name() const |

### objectName

[返回目录](#category)

属性：表单控件的对象名称。缺省状态下，与 name 属性值相同。

|      |                        调用接口                        |
| ---- | ----------------------------------------------------- |
| 读取 | QString objectName() const                            |
| 修改 | void setObjectName( const QString &objectName ) const |

### printEnabled

[返回目录](#category)

属性：是否允许打印、打印预览。

|      |                     调用接口                     |
| ---- | ----------------------------------------------- |
| 读取 | bool printEnabled() const                       |
| 修改 | void setPrintEnabled( bool printEnabled ) const |

### printFormUUID

[返回目录](#category)

属性：使用格式化打印的表单的UUID。

缺省情况下，使用表单上的“打印”和“打印预览”会直接将表单界面打印出来。但在很多应用场景下，需要以特定的格式进行打印，比如打印记账凭证，打印的格式与录入界面区别很大，因此需要另外设计一个表单用于打印，这个属性用于指定用于这种格式化打印的表单的UUID。运行时引擎会在打印时调出这个表单，按它设计好的格式进行打印。

|      |                           调用接口                           |
| ---- | ----------------------------------------------------------- |
| 读取 | QString printFormUUID() const                               |
| 修改 | void setPrintFormUUID( const QString &printFormUUID ) const |

### printPageNumber

[返回目录](#category)

属性：打印时是否显示页号。

某些情况下，因为打印纸张大小的设置，打印的内容可能需要多页打印，这个属性为 True 时，打印程序会自动在底端添加页号。

|      |                        调用接口                        |
| ---- | ----------------------------------------------------- |
| 读取 | bool printPageNumber() const                          |
| 修改 | void setPrintPageNumber( bool printPageNumber ) const |

### publishUUID

[返回目录](#category)

属性：表单在运行时环境中的UUID。

同一个表单，在运行时状态下，在不同的数据库里，以不同的身份发布（注册）的表单，会有不同的 publishUUID，可以通过这个值区别不同的表单的运行时实例。

开发者在写程序时一般较少用到这个属性，但在某些情况下可以通过这个属性值查询系统表中与这个表单相关的记录，比如这个表单所有相关的数据表的清单。

这个是只读属性，不允许修改，并且在一个数据库的实例中，经发布（注册）后的表单这个值是不变的。

|      |           调用接口           |
| ---- | --------------------------- |
| 读取 | QString publishUUID() const |

### PFFVersion

[返回目录](#category)

属性：表单开发时使用的PFF引擎版本号。V3.1.006开始引入。

这个是只读属性，不允许修改。在运行时环境（如biReader、智应软件中心等）中，低版本的PFF引擎不允许执行高版本的PFF程序。

|      |          调用接口           |
| ---- | -------------------------- |
| 读取 | QString PFFVersion() const |

| [PFFVersion](#PFFVersion)                     | QString | 可读      | 表单开发时使用的PFF引擎版本号     |

### queryEnabled

[返回目录](#category)

属性：是否允许使用“查询”按钮。

|      |                     调用接口                     |
| ---- | ----------------------------------------------- |
| 读取 | bool queryEnabled() const                       |
| 修改 | void setQueryEnabled( bool queryEnabled ) const |

### remark

[返回目录](#category)

属性：表单功能的概要说明。

虽然对这个属性的内容 biForm 并不做限制，但建议开发者用这个属性概括地描述这个表单的主要功能。在 userhelp 中进行详细的说明。这个属性的用法取决于运行时环境的设计。在 biReader 中，在使用“这是什么？”点击某个表单时，会以工具提示的方式显示这个属性的内容。

这个属性只允许在设计阶段进行设置，运行时是只读的。

|      |        调用接口         |
| ---- | ---------------------- |
| 读取 | QString remark() const |

### saveEnabled

[返回目录](#category)

属性：是否允许使用“保存”按钮。

|      |                    调用接口                    |
| ---- | --------------------------------------------- |
| 读取 | bool saveEnabled() const                      |
| 修改 | void setSaveEnabled( bool saveEnabled ) const |

### showBKImageInPDF

[返回目录](#category)

属性：PDF输出时是否显示背景图片。

|      |                         调用接口                         |
| ---- | ------------------------------------------------------- |
| 读取 | bool showBKImageInPDF() const                           |
| 修改 | void setShowBKImageInPDF( bool showBKImageInPDF ) const |

### showBKImageInPrinter

[返回目录](#category)

属性：打印/打印预览时是否显示背景图片。

|      |                             调用接口                             |
| ---- | --------------------------------------------------------------- |
| 读取 | bool showBKImageInPrinter() const                               |
| 修改 | void setShowBKImageInPrinter( bool showBKImageInPrinter ) const |

### toolbarEnabled

[返回目录](#category)

属性：是否显示缺省的工具栏。

缺省状态下，每个表单运行时都会有一个工具栏，如下图所示：

![toolbar](1-5-03.png)

在某些情况下，可能开发者并不希望表单上有这个工具栏，可以使用这个属性将之隐藏。这个属性可以在设计阶段进行设置，也可以在运行时状态下通过 Python 脚本来处理。

|      |                       调用接口                       |
| ---- | --------------------------------------------------- |
| 读取 | bool toolbarEnabled() const                         |
| 修改 | void setToolbarEnabled( bool toolbarEnabled ) const |

### transBKInPDF

[返回目录](#category)

属性：PDF输出时是否使用透明背景。

透明背景表示忽略表单的背景色，只输出控件的图像。否则会按表单的背景色输出一个矩形背景图片。

|      |                     调用接口                     |
| ---- | ----------------------------------------------- |
| 读取 | bool transBKInPDF() const                       |
| 修改 | void setTransBKInPDF( bool transBKInPDF ) const |

### transBKInPrinter

[返回目录](#category)

属性：打印/打印预览时是否使用透明背景。

透明背景表示忽略表单的背景色，只输出控件的图像。否则会按表单的背景色输出一个矩形背景图片。

|      |                         调用接口                         |
| ---- | ------------------------------------------------------- |
| 读取 | bool transBKInPrinter() const                           |
| 修改 | void setTransBKInPrinter( bool transBKInPrinter ) const |

### userHelp

[返回目录](#category)

属性：关于这个表单的用户使用说明。

这个属性用于说明表单的用途等，是为最终用户了解表单的功能而设置的。虽然它在何处使用取决于运行时环境，但它在最终用户处是可见的，开发者设置这个属性时需了解阅读的对象。

这个属性在设计阶段进行设置，运行时不允许修改。

|      |         调用接口          |
| ---- | ------------------------ |
| 读取 | QString userHelp() const |

### UUID

[返回目录](#category)

属性：表单的全程唯一标识，用于区别不同的表单。

这个是在设计阶段由 biForm 自动生成的，是只读的，不允许在运行时进行修改。

|      |       调用接口        |
| ---- | -------------------- |
| 读取 | QString UUID() const |

### version

[返回目录](#category)

属性：表单的版本号。

版本号为整数。在 biForm 中每次打包生成PFF文件时，这个属性值会自动增长。但也允许手工修改，除非有十分的理由，否则不建议手工修改版本号。这个属性在运行时是只读的。在运行时环境中，打开同一个表单的不同版本的PFF文件时，会以这个属性值来判断是否比现用的版本更新，以便决定是否进行升级。

|      |       调用接口       |
| ---- | ------------------- |
| 读取 | int version() const |

### width

[返回目录](#category)

属性：表单的宽度。

需要注意的是，如果表单的属性“不使用缺省的框架样式”为“是”时，表单会自动调到最大以便适应主窗口的尺寸，修改这个值并不会影响表单的实际宽度。

|      |             调用接口              |
| ---- | -------------------------------- |
| 读取 | int width() const                |
| 修改 | void setWidth( int width ) const |
