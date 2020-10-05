# 共同的接口

biForm 中的标准控件都继承自 widgetDelegateBase，有共同的一些属性和方法。

## 外观相关的属性

- ### 属性：geometry （类型：QRect 可读 可写）

控件相对于它的上级控件（父对象）的几何尺寸

| |调用方法|
| - | - |
|读取|const QRect & geometry()|
|修改|void setGeometry(const QRect& rect)|

- ### 属性：x （类型：int 可读 可写）

控件相对于上级控件的位置坐标的 x 值。

| |调用方法|
| - | - |
|读取|int x()|
|修改|void setX(const int x)|

- ### 属性：y （类型：int 可读 可写）

控件相对于上级控件的位置坐标的 y 值。

| |调用方法|
| - | - |
|读取|int y()|
|修改|void setY(const int y)|

- ### 属性：width （类型：int 可读 可写）

控件的宽度。

| |调用方法|
| - | - |
|读取|int width()|
|修改|void setWidth(const int w)|

- ### 属性：height （类型：int 可读 可写）

控件的高度。

| |调用方法|
| - | - |
|读取|int height()|
|修改|void setHeight(const int h)|

- ### 属性：pos （类型：QPoint 可读 可写）

控件左上角相对于上级控件的位置。

| |调用方法|
| - | - |
|读取|QPoint pos()|
|修改|void setPos(const QPoint h)|

- ### 属性：size （类型：QSize 可读 可写）

控件的尺寸。

| |调用方法|
| - | - |
|读取|QSize size()|
|修改|void setSize(const QSize size)|

- ### 属性：rect （类型：QRect 只读）

控件相对于上级控件的矩形区域，等于 QRect(0,0,width(),height())。

| |调用方法|
| - | - |
|读取|const QRect rect()|
|修改|void setRect(const QSize& rect)|

- ### 属性：vAlign （类型：int 可读 可写）

垂直方向的对齐方式。

| |调用方法|
| - | - |
|读取|int vAlign()|
|修改|void setVAlign(int align)|
| |align取值：pub.ALIGNTOP 向上对齐|
| |                 pub.ALIGNBOTTOM 向下对齐|
| |                 pub.ALIGNVCENTER 垂直居中对齐|

- ### 属性：hAlign （类型：int 可读 可写）

水平方向的对齐方式。

| |调用方法|
| - | - |
|读取|int hAlign()|
|修改|void setHAlign(int align)|
| |align取值：pub.ALIGNLEFT 向左对齐|
| |                 pub.ALIGNRIGHT 向右对齐|
| |                 pub.ALIGNHCENTER 水平居中对齐|
| |                 pub.ALIGNJUSTIFY 水平分散对齐|

- ### 属性：maxwidth （类型：int 可读 可写）

最大宽度。

| |调用方法|
| - | - |
|读取|int maxwidth()|
|修改|void setMaxWidth(const int w)|

- ### 属性：maxheight （类型：int 可读 可写）

最大高度。

| |调用方法|
| - | - |
|读取|int maxheight()|
|修改|void setMaxHeight(const int w)|

- ### 属性：minwidth （类型：int 可读 可写）

最小宽度。

| |调用方法|
| - | - |
|读取|int minwidth()|
|修改|void setMinWidth(const int w)|

- ### 属性：minheight （类型：int 可读 可写）

最小高度。

| |调用方法|
| - | - |
|读取|int minheight()|
|修改|void setMinHeight(const int w)|

- ### 属性：visible （类型：bool 可读 可写）

是否可见。

- ### 属性：showInForm （类型：bool 可读 可写）

表单上是否显示。

- ### 属性：showInPDF （类型：bool 可读 可写）

PDF打印时是否显示。

- ### 属性：showInPrinter （类型：bool 可读 可写）

打印机打印时是否显示。


	Q_PROPERTY(bool visible READ visible WRITE setVisible)
	Q_PROPERTY(bool showInForm READ showInForm WRITE setShowInForm)
	Q_PROPERTY(bool showInPDF READ showInPDF WRITE setShowInPDF)
	Q_PROPERTY(bool showInPrinter READ showInPrinter WRITE setShowInPrinter)
	Q_PROPERTY(int maxwidth READ maxwidth WRITE setMaxWidth)
	Q_PROPERTY(int maxheight READ maxheight WRITE setMaxHeight)
	Q_PROPERTY(int minwidth READ minwidth WRITE setMinWidth)
	Q_PROPERTY(int minheight READ minheight WRITE setMinHeight)

### 其它属性

	Q_PROPERTY(int tabOrder READ tabOrder)
	Q_PROPERTY(bool focus READ hasFocus WRITE setFocus)
	Q_PROPERTY(QString toolTip READ toolTip WRITE setToolTip)
	Q_PROPERTY(QString statusTip READ statusTip WRITE setStatusTip)
	Q_PROPERTY(QString whatsThis READ whatsThis WRITE setWhatsThis)	
	Q_PROPERTY(bool acceptDrops READ acceptDrops WRITE setAcceptDrops)
	Q_PROPERTY(bool dragEnabled READ dragEnabled WRITE setDragEnabled)
	Q_PROPERTY(bool reloadWhenCreateNew READ reloadWhenCreateNew WRITE setReloadWhenCreateNew)
	Q_PROPERTY(QString tag READ tag WRITE setTag)	
	Q_PROPERTY(bool updatesEnabled READ updatesEnabled WRITE setUpdatesEnabled)

public:
	
	virtual QString valuePropertyName () const ;

	QFont font() const;
	QColor foreground() const;
	QColor background() const;
	QColor borderColor() const;
	bool showBorder() const;
	int borderWidth() const	;
	int fillStyle() const;
	int showType() const;
	int borderStyle() const;

	int maxwidth() const;
	int maxheight() const ;
	int minwidth() const;
	int minheight() const ;

	bool acceptDrops() const;
	bool dragEnabled() const;
	
	int vAlign() const;
	int hAlign() const;
	int tabOrder() const;
	bool visible() const;
	bool enabled() const;
	QRect geometry() const	;
	int x() const;
	int y() const;
	QPoint pos() const;
	QSize size() const	;
	int width() const;
	int height() const	;
	QRect rect() const;
	bool hasFocus() const	;
	QString toolTip() const;
	QString statusTip() const;
	QString whatsThis() const;

	QString tag() const;
	void setTag(const QString v);
	bool reloadWhenCreateNew() const	;
	bool showInForm() const;
	bool showInPDF() const	;
	bool showInPrinter() const;
	bool updatesEnabled() const;

private:
	QString _tag;
public slots:	
	QPixmap grab();

	virtual void setStyleSheet(const QString& style);

	void setFullScreen();
	void quitFullScreen();

	void setSizePolicy(QSizePolicy policy);
	void showBalloon(const QString& msg);
	void showValidBalloon();
	void hideBalloon();
	void setShowInForm(bool v);
	void setShowInPDF(bool v);
	void setShowInPrinter(bool v);
	void setReloadWhenCreateNew(bool v);
	bool isNull();
	void toTop();
    void toBottom();
	void raise();
	void lower();
	void repaint()	;
	void show();
    void hide()	;

	void setMaxWidth ( int v );
	void setMaxHeight ( int v );
	void setMinWidth ( int v );
	void setMinHeight ( int v );

	void setAcceptDrops(bool v);
	void setDragEnabled(bool v);

	void setUpdatesEnabled(bool v);

	int startTimer ( int interval )		;
	bool killTimer ( int id )		;

	void killAllTimer();

	QStringList timers();

	void startSingleShot ( int interval )		;

	void setFocus(const bool v) const;

	void setEnabled(bool v)	;
	void setDisabled(bool v)	;
	void setVisible(bool v)	;
	void setFont(const QFont &v)		;

	void setGeometry(const QRect v) const;
	void setX(const int v) const;
	void setY(const int v) const		;
	void setPos(const QPoint v) const;
	void setSize(const QSize v) const	;
	void setWidth(const int v) const		;
	void setHeight(const int v) const		;
		
	void setToolTip(const QString v) const;
	void setStatusTip(const QString v) const;
	void setWhatsThis(const QString v) const;
	void setHAlign(int v)	;
	void setVAlign(int v)	;

	void setBorderStyle(int v)	;

	void setFillStyle(int v)	;

	void setShowType(int v)	;

	void setBorderWidth(int v)	;

	void setShowBorder(bool v)	;

	void setBorderColor(const QColor v)	;
	void setBackground(const QColor v)	;
	void setForeground(const QColor v)	;


