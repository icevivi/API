# 第二章 标准控件 - 多行文本输入控件

多行文本控件用于输入文字。可以有多种格式，比如下图显示了几种不同样式：

![example](2-4-01.png)

---

<h2 id="category">目录</h2>

- [继承的属性和函数](2-4-multilineedit?id=继承的属性和函数)

- [自有属性](2-4-multilineedit?id=多行文本输入控件的自有属性)

- [自有成员函数](2-4-multilineedit?id=多行文本输入控件自有成员函数)

- [信号](2-4-multilineedit?id=多行文本输入控件的信号)

- [可编程函数](2-4-multilineedit?id=可编程函数)

---

## 继承的属性和函数

- [继承自QObject 的属性](2-1-qobject?id=属性)

- [继承自QObject 的 成员函数](2-1-qobject?id=成员函数)

- [继承自widgetDelegateBase的属性](2-2-base?id=属性)

- [继承自widgetDelegateBase的成员函数](2-2-base?id=成员函数)

---

## 多行文本输入控件的自有属性

[返回目录](#category)

|         属性          |          值类型          | 读写类型  |                 说明                 |
| --------------------- | ------------------------ | -------- | ----------------------------------- |
| acceptRichText        | bool                     | 可读 可写 | 是否接受富文本                       |
| autoFormatting        | QTextEdit.AutoFormatting | 可读 可写 | 自动格式                             |
| caption               | QString                  | 可读 可写 | 标题文字                             |
| captionPosition       | int                      | 可读 可写 | 标题位置                             |
| cursorWidth           | int                      | 可读 可写 | 光标宽度，缺省值为1                   |
| defaultVal            | QString                  | 可读 可写 | 缺省文本                             |
| document              | QTextDocument *          | 可读 可写 | 底层的document对象                   |
| documentTitle         | QString                  | 可读 可写 | 文档标题                             |
| editorBackColor       | QColor                   | 可读 可写 | 文本输入框背景色                     |
| editorBorderColor     | QColor                   | 可读 可写 | 文本输入框边框颜色                    |
| editorBorderStyle     | int                      | 可读 可写 | 文本输入框边框样式                    |
| editorFillStyle       | int                      | 可读 可写 | 文本输入框背景填充类型                |
| editorFont            | QFont                    | 可读 可写 | 文本输入框字体                       |
| editorForeColor       | QColor                   | 可读 可写 | 文本输入框前景色                     |
| editorHAlign          | int                      | 可读 可写 | 文本输入框水平方向对齐方式            |
| editorVAlign          | int                      | 可读 可写 | 文本输入框垂直方向对齐方式            |
| html                  | QString                  | 可读 可写 | 当前HTML格式的文本                   |
| lineWrapColumnOrWidth | int                      | 可读 可写 | 换行的宽度或栏位                     |
| lineWrapMode          | QTextEdit.LineWrapMode   | 可读 可写 | 整行换行模式                         |
| margin                | int                      | 可读 可写 | 边界宽度                             |
| maxLength             | int                      | 可读 可写 | 输入文本最大长度                     |
| overwriteMode         | bool                     | 可读 可写 | 是否为改写模式                       |
| placeholderText       | QString                  | 可读 可写 | 占位文字（没有内容时显示的灰色的文字） |
| plainText             | QString                  | 可读 可写 | 当前普通文本                         |
| readOnly              | bool                     | 可读 可写 | 是否只读                             |
| shadow                | int                      | 可读 可写 | 文本输入框边框特效样式                |
| spacing               | int                      | 可读 可写 | 标题和编辑器的间距                    |
| tabChangesFocus       | bool                     | 可读 可写 | 按TAB是否切换控件焦点                 |
| tabStopDistance       | double                   | 可读 可写 | TAB符宽度                            |
| textInteractionFlags  | Qt.TextInteractionFlags  | 可读 可写 | 文本交互模式                         |
| undoRedoEnabled       | bool                     | 可读 可写 | 是否允许UNDO REDO                    |
| wordWrapMode          | int                      | 可读 可写 | 文本输入框单词换行模式                |

**调用属性的方法示例：**

``` Python

#读取属性，注意不要使用()
result = this.textedit.caption

#修改属性有两种方法
#方法一：
this.textedit.caption='备注'

#方法二：
this.textedit.caption('备注')

```

- ### acceptRichText （类型：bool 可读 可写）

是否接受富文本输入。

|      |                  调用方法                  |
| ---- | ----------------------------------------- |
| 读取 | bool acceptRichText() const               |
| 修改 | void setAcceptRichText( bool set )  const |

- ### autoFormatting（类型：QTextEdit.AutoFormatting 可读 可写）

是否使用自动格式化。
使用前先导入 Qt namespace 模块 ： ```from PythonQt.Qt import QTextEdit```。

|      |                            调用方法                            |
| ---- | ------------------------------------------------------------- |
| 读取 | QTextEdit::AutoFormatting autoFormatting() const              |
| 修改 | void setAutoFormatting( QTextEdit::AutoFormatting set ) const |
|      | **autoFormatting的值：**                                      |
|      | - QTextEdit.AutoNone 不使用自动格式化                          |
|      | - QTextEdit.AutoBulletList 自动使用清单格式                    |
|      | - QTextEdit.AutoAll 使用所有格式                              |

- ### 属性：caption （类型：QString 可读 可写）

标题显示的文本。

|      |                     调用方法                     |
| ---- | ----------------------------------------------- |
| 读取 | QString caption() const                         |
| 修改 | void setCaption( const QString &caption ) const |

- ### 属性：captionPosition （类型：int 可读 可写 ）

标题所在位置。

|      |                   调用方法                    |
| ---- | -------------------------------------------- |
| 读取 | int captionPosition() const                  |
| 修改 | void setCaptionPosition( int position) const |
|      | 值的含义：                                    |
|      | pub.ATTOP 在上方                             |
|      | pub.ATLEFT 在左侧                            |
|      | pub.ATBOTTOM 在下方                          |
|      | pub.ATRIGHT 在右侧                           |
|      | pub.NOCAPTION 无标题                         |

- ### cursorWidth（类型：int 可读 可写）

输入光标宽度（像素值），缺省值为1。

|      |                调用方法                |
| ---- | -------------------------------------- |
| 读取 | int cursorWidth() const                |
| 修改 | void setCursorWidth( int width ) const |

- ### 属性：defaultVal （类型：QString 可读 可写）

缺省的文本内容。

|      |                        调用方法                        |
| ---- | ----------------------------------------------------- |
| 读取 | QString defaultVal() const                            |
| 修改 | void setDefaultVal( const QString &defaultVal ) const |

- ### document （类型：QTextDocument* 可读 可写）

底层的 QTextDocument 对象，用于进行更复杂的文档操作。

|      |                      调用方法                      |
| ---- | ------------------------------------------------- |
| 读取 | QTextDocument* document() const                   |
| 修改 | void setDocument( QTextDocument* document ) const |

- ### documentTitle （类型：QString 可读 可写）

文档标题。

|      |                       调用方法                       |
| ---- | --------------------------------------------------- |
| 读取 | QString documentTitle() const                       |
| 修改 | void setDocumentTitle(const QString& title )  const |

- ### 属性：editorBackColor （类型：QColor 可读 可写）

文本编辑器的背景色，在填充类型设为“透明”时无效。

|      |                            调用方法                             |
| ---- | -------------------------------------------------------------- |
| 读取 | QColor editorBackColor() const                                 |
| 修改 | void setEditorBackColor( const QColor &editorBackColor ) const |

- ### 属性：editorBorderColor （类型：QColor 可读 可写）

文本编辑器的边框颜色。

|      |                              调用方法                               |
| ---- | ------------------------------------------------------------------ |
| 读取 | QColor editorBorderColor() const                                   |
| 修改 | void setEditorBorderColor( const QColor &editorBorderColor ) const |

- ### 属性：editorBorderStyle （类型：int 可读 可写）

文本输入框边框样式。

|      |                         调用方法                          |
| ---- | -------------------------------------------------------- |
| 读取 | int editorBorderStyle() const                            |
| 修改 | void setEditorBorderStyle( int editorBorderStyle ) const |
|      | **editorBorderStyle取值：**                              |
|      | pub.NOFRAME 没有边框                                      |
|      | pub.UNDERLINE 下划线                                     |
|      | pub.RECTANGLE 矩形边框                                    |

- ### 属性：editorFillStyle （类型：int 可读 可写）

文本输入框背景填充样式。设置为“透明”时，背景色无效。

|      |                       调用方法                        |
| ---- | ---------------------------------------------------- |
| 读取 | int editorFillStyle() const                          |
| 修改 | void setEditorFillStyle( int editorFillStyle ) const |
|      | **editorFillStyle的值：**                            |
|      | pub.FILLED_BACKGROUND 填充                           |
|      | pub.TRANSPARENT_BACKGROUND 透明                      |

- ### 属性：editorFont （类型：QFont 可读 可写）

文本编辑器的字体。

|      |                       调用方法                       |
| ---- | --------------------------------------------------- |
| 读取 | QFont editorFont() const                            |
| 修改 | void setEditorFont( const QFont &editorFont ) const |

- ### 属性：editorForeColor （类型：QColor 可读 可写）

文本编辑器的前景色。

|      |                            调用方法                             |
| ---- | -------------------------------------------------------------- |
| 读取 | QColor editorForeColor() const                                 |
| 修改 | void setEditorForeColor( const QColor &editorForeColor ) const |

- ### 属性：editorHAlign （类型：int 可读 可写）

文本输入框水平方向对齐方式。

|      |                    调用方法                     |
| ---- | ---------------------------------------------- |
| 读取 | int editorHAlign() const                       |
| 修改 | void setEditorHAlign( int editorHAlign ) const |
|      | **editorHAlign取值：**                         |
|      | pub.ALIGNLEFT 向左对齐                          |
|      | pub.ALIGNRIGHT 向右对齐                         |
|      | pub.ALIGNHCENTER 水平居中对齐                   |
|      | pub.ALIGNJUSTIFY 水平分散对齐                   |

- ### 属性：editorVAlign （类型：int 可读 可写）

文本输入框垂直方向对齐方式。

|      |                    调用方法                     |
| ---- | ---------------------------------------------- |
| 读取 | int editorVAlign() const                       |
| 修改 | void setEditorVAlign( int editorVAlign ) const |
|      | **editorVAlign取值：**                         |
|      | pub.ALIGNTOP 向上对齐                           |
|      | pub.ALIGNBOTTOM 向下对齐                        |
|      | pub.ALIGNVCENTER 垂直居中对齐                   |

- ### 属性：html （类型：QString 可读 可写）

输入的HTML格式的文本内容。

|      |                  调用方法                  |
| ---- | ----------------------------------------- |
| 读取 | QString html() const                      |
| 修改 | void setHtml( const QString &html ) const |

- ### lineWrapMode （类型：QTextEdit.LineWrapMode 可读 可写）

整行换行模式。会按单词间的空格进行换行以保持单词的完整性，如果需要在单词内换行，使用wordWrapMode属性。
如果设置为  FixedPixelWidth 或 FixedColumnWidth，还需要使用 setLineWrapColumnOrWidth() 设置对应的值。
固定列数为字符的数量。
使用前先导入 Qt namespace 模块 ： ```from PythonQt.Qt import QTextEdit```。

|      |                          调用方法                          |
| ---- | --------------------------------------------------------- |
| 读取 | QTextEdit::LineWrapMode lineWrapMode() const              |
| 修改 | void setLineWrapMode( QTextEdit::LineWrapMode set ) const |
|      | **lineWrapMode的值：**                                    |
|      | QTextEdit.NoWrap 不使用自动格式化                          |
|      | QTextEdit.WidgetWidth 按控件宽度换行                       |
|      | QTextEdit.FixedPixelWidth 指定固定像素值                   |
|      | QTextEdit.FixedColumnWidth 使用固定列数                    |

- ### 属性：margin （类型：int 可读 可写）

边界宽度（像素为单位）。

|      |              调用方法               |
| ---- | ---------------------------------- |
| 读取 | int margin() const                 |
| 修改 | void setMargin( int margin ) const |

- ### 属性：maxLength （类型：int 可读 可写）

可输入文本的最大长度。

|      |                 调用方法                  |
| ---- | ---------------------------------------- |
| 读取 | int maxLength() const                    |
| 修改 | void setMaxLength( int maxLength ) const |

- ### overwriteMode （类型：bool 可读 可写）

是否为改写模式。
如果值为“是”，则用户输入的字符会覆盖输入位置处原来输入的文字。

|      |                 调用方法                  |
| ---- | ---------------------------------------- |
| 读取 | bool overwriteMode() const               |
| 修改 | void setOverwriteMode( bool mode ) const |

- ### placeholderText（类型：QString 可读 可写）

占位文字（没有内容时显示的灰色的文字） ，缺省情况下为空字符串。

|      |                       调用方法                       |
| ---- | --------------------------------------------------- |
| 读取 | int placeholderText() const                         |
| 修改 | void setPlaceholderText( const QString& set ) const |

- ### 属性：plainText （类型：QString 可读 可写）

输入的普通文本内容。

|      |                       调用方法                       |
| ---- | --------------------------------------------------- |
| 读取 | QString plainText() const                           |
| 修改 | void setPlainText( const QString &plainText ) const |

- ### 属性：readOnly （类型：bool 可读 可写）

是否只读。

|      |                 调用方法                 |
| ---- | --------------------------------------- |
| 读取 | bool readOnly() const                   |
| 修改 | void setReadOnly( bool readOnly ) const |

- ### 属性：shadow （类型：int 可读 可写）

文本输入框边框样式。

|      |              调用方法               |
| ---- | ---------------------------------- |
| 读取 | int shadow() const                 |
| 修改 | void setShadow( int shadow ) const |
|      | **shadow取值：**                   |
|      | pub.PLAIN 平的                     |
|      | pub.RAISED 上凸                    |
|      | pub.SUNKEN 下陷                    |

- ### 属性：spacing （类型：bool 可读 可写）

标题和输入框的间距（像素值）。

|      |               调用方法                |
| ---- | ------------------------------------ |
| 读取 | int spacing() const                  |
| 修改 | void setSpacing( int spacing ) const |

- ### tabChangesFocus （类型：bool 可读 可写）

按tab键时是否切换控件焦点。

|      |                  调用方法                   |
| ---- | ------------------------------------------ |
| 读取 | bool tabChangesFocus() const               |
| 修改 | void setTabChangesFocus( bool set )  const |

- ### tabStopDistance （类型：double 可读 可写）

TAB键宽度（像素值），缺省为80像素。

|      |                   调用方法                   |
| ---- | ------------------------------------------- |
| 读取 | double tabStopDistance() const              |
| 修改 | void setTabStopDistance( double set ) const |

- ### textInteractionFlags（类型：Qt.TextInteractionFlags 可读 可写）

设置交互方式。几个值可以使用二进制或运算进行组合。
使用前先导入 Qt namespace 模块 ： ```from PythonQt.Qt import Qt```。

|      |                                                  调用方法                                                   |
| ---- | ----------------------------------------------------------------------------------------------------------- |
| 读取 | int textInteractionFlags() const                                                                            |
| 修改 | void setTextInteractionFlags( Qt.TextInteractionFlags flags ) const                                         |
|      | **Qt.TextInteractionFlags取值**                                                                             |
|      | Qt.NoTextInteraction = 0 不设置                                                                             |
|      | Qt.TextSelectableByMouse = 1 文本可以使用鼠标选择                                                            |
|      | Qt.TextSelectableByKeyboard = 2 文本可以使用键盘进行选择                                                     |
|      | Qt.LinksAccessibleByMouse = 4 链接可以使用鼠标点击                                                           |
|      | Qt.LinksAccessibleByKeyboard = 8 链接可以使用键盘（TAB后回车）激活                                            |
|      | Qt.TextEditable = 16 文本可编辑                                                                             |
|      | Qt.TextEditorInteraction 等于 TextSelectableByMouse \| TextSelectableByKeyboard \| TextEditable             |
|      | Qt.TextBrowserInteraction 等于 TextSelectableByMouse \| LinksAccessibleByMouse \| LinksAccessibleByKeyboard |

- ### undoRedoEnabled （类型：bool 可读 可写）

是否允许undo和redo。

|      |                  调用方法                   |
| ---- | ------------------------------------------ |
| 读取 | bool isUndoRedoEnabled() const             |
| 修改 | void setUndoRedoEnabled( bool set )  const |

- ### 属性：wordWrapMode （类型：int 可读 可写）

换行模式。
可以直接使用 int 值，也可以使用 QTextOption.WrapMode 或 pub 中的常量。
使用 QTextOption.WrapMode 需要先```from PythonQt.Qt import QTextOption```

|      |                                              调用方法                                              |
| ---- | -------------------------------------------------------------------------------------------------- |
| 读取 | int wordWrapMode() const                                                                           |
| 修改 | void setWordWrapMode( int wordWrapMode ) const                                                     |
|      | **wordWrapMode的值：**                                                                             |
|      | pub.NOWRAP 或 QTextOption.NoWrap 不换行                                                             |
|      | pub.WORD_WRAP 或 QTextOption.WordWrap 换单词换行                                                    |
|      | pub.MANUAL_WRAP 或 QTextOption.ManualWrap 手动换行                                                  |
|      | pub.WRAP_ANYWHERE 或 TextOption.WrapAnywhere 随时换行                                               |
|      | pub.WRAP_ATWORD_BOUNDARY_OR_ANYWHERE 或 QTextOption.WrapAtWordBoundaryOrAnywhere 单词边界或随时换行 |

---

## 多行文本输入控件自有成员函数

[返回目录](#category)

所有性的设置函数（参考上一节中修改属性的接口），都属于此类，都可以当做槽使用。除此之处，另外还包括以下几个成员函数：

|           函数            |                                    接口                                     |              说明              |
| ------------------------- | --------------------------------------------------------------------------- | ------------------------------ |
| append                    | void append(const QString & text) const                                     | 在最后添加文本                  |
| clear                     | void clear() const                                                          | 清除所有内容                    |
| copy                      | void copy() const                                                           | 复制选中的文本                  |
| cut                       | void cut() const                                                            | 剪切                           |
| insertHtml                | void insertHtml(const QString &text) const                                  | 插入HTML文本                   |
| insertPlainText           | void insertPlainText(const QString &text) const                             | 插入普通文本                    |
| paste                     | void paste() const                                                          | 粘贴                           |
| redo                      | void redo() const                                                           | 重做上一步操作                  |
| selectAll                 | void selectAll() const                                                      | 选择所有                       |
| setText                   | void setText(const QString & text) const                                    | 设置文本                       |
| setTitleStyleSheet        | void setTitleStyleSheet(const QString& style) const                         | 设置标题的外观样式              |
| setEditorStyleSheet       | void setEditorStyleSheet(const QString& style) const                        | 设置编辑器的外观样式            |
| undo                      | void undo() const                                                           | 撤消上一步操作                  |
| zoomIn                    | void zoomIn(int range = 1) const                                            | 放大，range指定字号增加的点数   |
| zoomOut                   | void zoomOut(int range =1) const                                            | 缩小，range指定字号减少的点数   |
| alignment                 | Qt.Alignment alignment() const                                              | 当前格式的对齐方式              |
| anchorAt                  | QString anchorAt(const QPoint &pos) const                                   | 某个坐标点对应的锚点            |
| canPaste                  | bool canPaste() const                                                       | 是否可以粘贴                    |
| createStandardContextMenu | QMenu * createStandardContextMenu()                                         | 创建标准上下文菜单              |
| createStandardContextMenu | QMenu * createStandardContextMenu(const QPoint &position)                   | 指定某个坐标点创建标准上下文菜单 |
| currentCharFormat         | QTextCharFormat currentCharFormat() const                                   | 当前文本格式                    |
| currentFont               | QFont currentFont() const                                                   | 当前字体                       |
| cursorForPosition         | QTextCursor cursorForPosition(const QPoint &pos) const                      | 当前坐标点的输入光标对象        |
| cursorRect                | QRect cursorRect(const QTextCursor &cursor) const                           | 输入光标对象的坐标范围          |
| cursorRect                | QRect cursorRect() const                                                    | 当前坐标范围                    |
| ensureCursorVisible       | void ensureCursorVisible()                                                  | 确保当前输入光标可见            |
| extraSelections           | QList <QTextEdit.ExtraSelection> extraSelections() const                    | 额外选择范围清单                |
| find                      | bool find(const QString &exp                                                | 搜索文本                       |
|                           | 　　　　,QTextDocument.FindFlags options = QTextDocument.FindFlags())       |                                |
| find                      | bool find(const QRegExp &exp                                                | 使用正则表达式搜索文本          |
|                           | 　　　　,QTextDocument.FindFlags options = QTextDocument.FindFlags())       |                                |
| fontFamily                | QString fontFamily() const                                                  | 当前格式使用的字体集            |
| fontItalic                | bool fontItalic() const                                                     | 当前格式是否使用斜体            |
| fontPointSize             | double fontPointSize() const                                                | 当前格式使用的字号              |
| fontUnderline             | bool fontUnderline() const                                                  | 当前格式是否使用下划线          |
| fontWeight                | int fontWeight() const                                                      | 当前格式的加粗程度              |
| loadResource              | QVariant loadResource(int type, const QUrl &name)                           | 从URL加载内容                  |
| mergeCurrentCharFormat    | void mergeCurrentCharFormat(const QTextCharFormat &modifier)                | 合并格式                       |
| moveCursor                | void moveCursor(QTextCursor.MoveOperation operation                         | 移动输入光标                    |
|                           | 　　　　,QTextCursor.MoveMode mode = QTextCursor.MoveAnchor)                |                                |
| overwriteMode             | bool overwriteMode() const                                                  | 是否为覆盖输入模式              |
| print                     | void print(QPagedPaintDevice * printer) const                               | 打印                           |
| setCurrentCharFormat      | void setCurrentCharFormat(const QTextCharFormat &format)                    | 设置当前字符格式                |
| setExtraSelections        | void setExtraSelections(const QList <QTextEdit.ExtraSelection> &selections) | 设置额外选择范围清单            |
| setTextCursor             | void setTextCursor(const QTextCursor &cursor)                               | 设置输入光标对象                |
| setUndoRedoEnabled        | void setUndoRedoEnabled(bool enable)                                        | 是否允许 undo redo             |
| textBackgroundColor       | QColor textBackgroundColor() const                                          | 当前格式的文本背景颜色          |
| textColor                 | QColor textColor() const                                                    | 当前格式的文本颜色              |
| textCursor                | QTextCursor textCursor() const                                              | 返回输入光标对象                |
| scrollToAnchor            | void scrollToAnchor(const QString &name)                                    | 滚动到锚点                     |
| setEditorAlignment        | void setEditorAlignment(Qt.Alignment align)                                 | 设置编辑框当前格式的对齐方式     |
| setTitleAlignment         | void setTitleAlignment(Qt.Alignment align) const                            | 设置标题的对齐方式              |
| setCurrentFont            | void setCurrentFont(const QFont &font ) const                               | 设置当前格式的字体              |
| setFontFamily             | void setFontFamily(const QString &fontFamily)                               | 设置当前格式的字体集            |
| setFontItalic             | void setFontItalic(bool italic)                                             | 设置当前格式的字体是否使用斜体   |
| setFontPointSize          | void setFontPointSize(double s)                                             | 设置当前格式的字号              |
| setFontUnderline          | void setFontUnderline(bool underline)                                       | 设置当前格式的字体下划线        |
| setFontWeight             | void setFontWeight(int weight)                                              | 设置当前格式的字体加粗程度       |
| setTextBackgroundColor    | void setTextBackgroundColor(const QColor &c)                                | 设置当前格式的背景颜色          |
| setTextColor              | void setTextColor(const QColor &c)                                          | 设置当前格式的文本颜色          |
| appendTextToEnd           | void appendTextToEnd(const QString& text,bool moveCursor=true)              | 设置当前光标处文本颜色          |
|                           | 　　　　,bool makeCusorVisible = true)                                       | 在文档结尾追加文本              |
| insertTextToStart         | void insertTextToStart(const QString& text                                  | 在文档开头插入文本              |
|                           | 　　　　,bool moveCursor = true, bool makeCusorVisible = true)               |                                |
| moveCursorToEnd           | void moveCursorToEnd(bool makeCusorVisible=true)                            | 移动输入光标到文档最后          |
| moveCursorToStart         | void moveCursorToStart(bool makeCusorVisible = true)                        | 移动输入光标到文档开头          |
| lineCount                 | int lineCount()                                                             | 行数                           |
| getTextOfLine             | QString getTextOfLine(int lineNumber)                                       | 返回指定行的文本                |
| getTextOfLastLine         | QString getTextOfLastLine()                                                 | 返回最后一行的文本              |
	
### 枚举类型和Qt类说明

 - **Qt.Alignment 枚举类型**
使用前先导入 Qt namespace 模块 ： ```from PythonQt.Qt import Qt```。

 - **QTextCursor.MoveOperation 枚举类型**
使用前先导入 Qt namespace 模块 ： ```from PythonQt.Qt import QTextCursor```。

|            枚举变量            | 值  |                              说明                              |
| ----------------------------- | --- | ------------------------------------------------------------- |
| QTextCursor.NoMove            | 0   | 不移动                                                         |
| QTextCursor.Start             | 1   | 移动到文档开始位置                                              |
| QTextCursor.StartOfLine       | 3   | 移动到本行开始位置                                              |
| QTextCursor.StartOfBlock      | 4   | 移动到文本块开始位置                                            |
| QTextCursor.StartOfWord       | 5   | 移动到单词开始位置                                              |
| QTextCursor.PreviousBlock     | 6   | 移动到前一个文本块                                              |
| QTextCursor.PreviousCharacter | 7   | 移动到前一个字符处                                              |
| QTextCursor.PreviousWord      | 8   | 移动到前一个单词处                                              |
| QTextCursor.Up                | 2   | 移动到上一行                                                   |
| QTextCursor.Left              | 9   | 移动到下一个字符处                                              |
| QTextCursor.WordLeft          | 10  | 移动到下一个单词处                                              |
| QTextCursor.End               | 11  | 移动到文档最后                                                 |
| QTextCursor.EndOfLine         | 13  | 移动到行尾                                                     |
| QTextCursor.EndOfWord         | 14  | 移动到当前单词尾                                               |
| QTextCursor.EndOfBlock        | 15  | 移动到当前文本块尾                                              |
| QTextCursor.NextBlock         | 16  | 移动到下一个文本块开始处                                        |
| QTextCursor.NextCharacter     | 17  | 移动到下一个字符处                                              |
| QTextCursor.NextWord          | 18  | 移动到下一个单词处                                              |
| QTextCursor.Down              | 12  | 下移一行                                                       |
| QTextCursor.Right             | 19  | 移动到下一个字符处                                              |
| QTextCursor.WordRight         | 20  | 移动到下一个单词处                                              |
| QTextCursor.NextCell          | 21  | 移动到当前表格的下一个单元格的开始位置。                         |
|                               |     | 如果当前单元格是本行最后一个，则移动到下一行的第一个单元格开始位置 |
| QTextCursor.PreviousCell      | 22  | 移动到当前表格的前一个单元格的开始位置。                         |
|                               |     | 如果当前单元格是本行第一个，则移动到下一行最后一个单元格的开始位置 |
| QTextCursor.NextRow           | 23  | 移动到当前表格的下一行                                          |
| QTextCursor.PreviousRow       | 24  | 移动到当前表格的前一行                                          |

- **QTextCursor.MoveMode 枚举类型**
使用前先导入 Qt namespace 模块 ： ```from PythonQt.Qt import QTextCursor```。

|        枚举变量         | 值  |                 说明                  |
| ---------------------- | --- | ------------------------------------- |
| QTextCursor.MoveAnchor | 0   | 移动锚点                               |
| QTextCursor.KeepAnchor | 1   | 保持锚点，这种状态下，会选择范围内的文本 |

 - **QTextCursor、QPagedPaintDevice 、QTextCharFormat 、QTextEdit.ExtraSelection、QRegExp、QTextDocument、QPoint 和 QUrl**
这些Qt中的类， 使用前需要先从相应的模块中导入，比如：

``` Python

from PythonQt.Qt import QTextCursor
from PythonQt.QtGui import QPagedPaintDevice
from PythonQt.Qt import QTextCharFormat
from PythonQt.Qt import QTextEdit
x=QTextEdit.ExtraSelection()
from PythonQt.Qt import QRegExp
from PythonQt.Qt import QTextDocument
from PythonQt.Qt import QPoint
from PythonQt.Qt import QUrl

```

---

## 多行文本输入控件的信号

[返回目录](#category)

|信号|接口|说明|
| - | - | - | 
|copyAvailable| void copyAvailable(bool yes)|是否可以进行复制的状态时发出此信号|
|currentCharFormatChanged|void currentCharFormatChanged ( const QTextCharFormat & f ) |当前字符格式发生变化时<br>f是新的格式<br>通常是在html格式输入时当光标位置发生变化时|
|cursorPositionChanged| void cursorPositionChanged()|光标位置改变时发出此信号|
|redoAvailable| void redoAvailable(bool available)|可以重做上一步操作的状态时发出此信号|
|selectionChanged| void selectionChanged()|所选文本范围发生变化时发出此信号|
|textChanged| void textChanged()|文本发生改变时发出此信号，通过程序修改文本也会发出此信号|
|undoAvailable| void undoAvailable(bool available)|可以撤消上一步操作时发出此信号|

---

## 可编程函数

[返回目录](#category)

- [可编程函数的详细说明](1-4-openscript?id=控件的可编程函数)

多行文本输入控件所有可编程函数的清单：

|函数|函数名|传入参数|返回值|说明|
| - | - | - | - | - |
|[缺省值](1-4-openscript?id=default) | 控件名_default | 无 | 输入框中文本内容的初始值<br>**数据类型：字符串**| 返回控件的初始值。<br>控件创建后、新建空白表单后输入框中的文本会还原成初始值。|
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

