# 单行文本输入控件

单行文本控件用于输入文字。可以有多种格式，比如下图显示了几种不同样式：

![example](2-3-01.png)

## 继承

- [继承自QObject 的属性](2-1-qobject?id=属性)

|属性|值类型|读写类型|说明|
| - | - | - | - |
|objectName|QString|可读 可写|对象名称|

- [继承自QObject 的 属性成员函数](2-1-qobject?id=成员函数)

- [继承自widgetDelegateBase的属性](2-2-base?id=属性)

|属性|值类型|读写类型|说明|
| - | - | - | - |
|background|QColor|可读 可写|背景色|
|borderColor|QColor|可读 可写|边框颜色|
|borderStyle|int|可读 可写|边框样式|
|borderWidth|int|可读 可写|边框宽度|
|dragEnabled|bool|可读 可写|是否允许拖动内容|
|enabled|bool|可读 可写|是否可用|
|fillStyle|int|可读 可写|填充类型|
|focus|bool|可读 可写|是否获得输入焦点|
|font|QFont|可读 可写|字体|
|foreground|QColor|可读 可写|前景色|
|geometry|QRect|可读 可写|位置尺寸|
|hAlign|int|可读 可写|水平方向对齐方式|
|height|int|可读 可写|高度|
|maxheight|int|可读 可写|最大高度|
|maxwidth|int|可读 可写|最大宽度|
|minheight|int|可读 可写|最小高度|
|minwidth|int|可读 可写|最小宽度|
|pos|QPoint|可读 可写|位置|
|rect|QRect|只读 |边框矩形尺寸|
|reloadWhenCreateNew|bool|可读 可写|表单新建时是否重新加载|
|showBorder|bool|可读 可写|是否显示边框|
|showOnForm|bool|可读 可写|表单上是否可见|
|showOnPDF|bool|可读 可写|PDF输出时是否可见|
|showWhenPrint|bool|可读 可写|打印时是否可见|
|size|QSize|可读 可写|尺寸|
|statusTip|QString|可读 可写|状态栏提示文本|
|tabOrder|int|只读 |tab键顺序|
|tag|QVariant|可读 可写|备用属性|
|toolTip|QString|可读 可写|工具提示|
|updatesEnabled|bool|可读 可写|是否允许刷新|
|vAlign|int|可读 可写|垂直方向对齐方式|
|visible|bool|可读 可写|是否可见|
|whatsThis|QString|可读 可写|“这是什么”提示文本|
|width|int|可读 可写|宽度|
|x|int|可读 可写|x方向位置|
|y|int|可读 可写|y方向位置|

- [继承自widgetDelegateBase的成员函数](2-2-base?id=成员函数)

## 单行文本输入控件的属性

- ### 属性：caption （类型：QString 可读 可写）

标题显示的文字。

| |调用方法|
| - | - |
|读取|QString caption const|
|修改|void setCaption( const QString &caption ) const|

- ### 属性：editorFont （类型：QFont 可读 可写）

文本编辑控件的字体。注意 font 属性指标题的字体，editorFont才是输入文字的控件的字体。

| |调用方法|
| - | - |
|读取|QFont editorFont const|
|修改|void setEditorFont( const QFont &editorFont ) const|

- ### 属性：editorBackColor （类型：QColor 可读 可写）

文本输入控件的背景色，只在填充属性为“填充”时有效。

| |调用方法|
| - | - |
|读取|QColor editorBackColor const|
|修改|void setEditorBackColor( const QColor &editorBackColor ) const|

- ### 属性：editorForeColor （类型：QColor 可读 可写）

文本输入控件的前景色。

| |调用方法|
| - | - |
|读取|QColor editorForeColor const|
|修改|void setEditorForeColor( const QColor &editorForeColor ) const|

- ### 属性：editorBorderColor （类型：QColor 可读 可写）

文本输入控件边框颜色。

| |调用方法|
| - | - |
|读取|QColor editorBorderColor const|
|修改|void setEditorBorderColor( const QColor &editorBorderColor ) const|

- ### 属性：margin （类型：int 可读 可写）

边界宽度。

| |调用方法|
| - | - |
|读取|int margin const|
|修改|void setMargin( int margin ) const|

- ### 属性：maxLength （类型：int 可读 可写）

输入文本最大长度。

| |调用方法|
| - | - |
|读取|int maxLength const|
|修改|void setMaxLength( int maxLength ) const|

- ### 属性：editorBorderStyle （类型：int 可读 可写）

文本编辑器边框类型。

| |调用方法|
| - | - |
|读取|int editorBorderStyle const|
|修改|void setEditorBorderStyle( int editorBorderStyle ) const|
| |**editorBorderStyle取值：**|
| |pub.NOFRAME 没有边框|
| |pub.UNDERLINE 下划线|
| |pub.RECTANGLE 矩形边框|

- ### 属性：captionPosition （类型：int 可读 ）

标题所在位置。

| |调用方法|
| - | - |
|读取|int captionPosition const|

- ### 属性：shadow （类型：int 可读 可写）

输入框边框特效样式。

| |调用方法|
| - | - |
|读取|int shadow const|
|修改|void setShadow( int shadow ) const|
| |**shadow取值：**|
| |pub.PLAIN 平的|
| |pub.RAISED 上凸|
| |pub.SUNKEN 下陷|

- ### 属性：editorFillStyle （类型：int 可读 可写）

输入框背景填充样式。设置为“透明”时，背景色无效。

| |调用方法|
| - | - |
|读取|int editorFillStyle const|
|修改|void setEditorFillStyle( int editorFillStyle ) const|
| |**editorFillStyle的值：**|
| |- pub.FILLED_BACKGROUND 填充|
| |- pub.TRANSPARENT_BACKGROUND 透明|

- ### 属性：isPWD （类型：bool 可读 可写）

是否是密码输入控件。密码输入控件会显示特殊字符替代输入的文字。

| |调用方法|
| - | - |
|读取|bool isPWD const|
|修改|void setIsPWD( bool isPWD ) const|

- ### 属性：inputMask （类型：QString 可读 可写）

输入掩码。详细用法参考Qt文档。

| |调用方法|
| - | - |
|读取|QString inputMask const|
|修改|void setInputMask( const QString &inputMask ) const|

- ### 属性：text （类型：QString 可读 可写）

输入的文字。

| |调用方法|
| - | - |
|读取|QString text const|
|修改|void setText( const QString &text ) const|

- ### 属性：displaytext （类型：QString 可读 ）

输入框显示的文字。

| |调用方法|
| - | - |
|读取|QString displaytext const|

- ### 属性：defaultVal （类型：QString 可读 可写）

缺省文本。

| |调用方法|
| - | - |
|读取|QString defaultVal const|
|修改|void setDefaultVal( const QString &defaultVal ) const|

- ### 属性：editorVAlign （类型：int 可读 可写）

输入框文本垂直方向对齐方式。

| |调用方法|
| - | - |
|读取|int editorVAlign const|
|修改|void setEditorVAlign( int editorVAlign ) const|
| |**editorVAlign取值：**|
| |pub.ALIGNTOP 向上对齐|
| |pub.ALIGNBOTTOM 向下对齐|
| |pub.ALIGNVCENTER 垂直居中对齐|

- ### 属性：editorHAlign （类型：int 可读 可写）

输入框文本水平方向对齐方式。

| |调用方法|
| - | - |
|读取|int editorHAlign const|
|修改|void setEditorHAlign( int editorHAlign ) const|
| |**editorHAlign取值：**|
| |pub.ALIGNLEFT 向左对齐|
| |pub.ALIGNRIGHT 向右对齐|
| |pub.ALIGNHCENTER 水平居中对齐|
| |pub.ALIGNJUSTIFY 水平分散对齐|

- ### 属性：readOnly （类型：bool 可读 可写）

是否只读。只读的文本输入控件可以通过脚本修改其中的文字，但不允许用户修改。

| |调用方法|
| - | - |
|读取|bool readOnly const|
|修改|void setReadOnly( bool readOnly ) const|

