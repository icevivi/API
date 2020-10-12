# 日期时间编辑器控件

日期时间编辑器控件用于选择设定日期和时间。如下图示：

![example](2-16-01.png)

---

<h2 id="category">目录</h2>

- [继承的属性和函数](#继承的属性和函数)

- [自有属性](#日期时间编辑器的自有属性)

- [自有成员函数](#日期时间编辑器自有成员函数)

- [信号](#日期时间编辑器的信号)

- [可编程函数](#可编程函数)

---

## 继承的属性和函数

- [继承自QObject 的属性](2-1-qobject?id=属性)

- [继承自QObject 的 成员函数](2-1-qobject?id=成员函数)

- [继承自widgetDelegateBase的属性](2-2-base?id=属性)

- [继承自widgetDelegateBase的成员函数](2-2-base?id=成员函数)

---

## 日期时间编辑器的属性

[返回目录](#category)

|属性|值类型|读写类型|说明|
| - | - | - | - |
|wrapping|bool|可读 可写|是否使用值循环|
|format|QString|可读 可写|显示格式|
|calendarpopup|bool|可读 可写|是否弹出日期选择框|
|text|QString|可读 可写|当前显示的文本|
|defaultVal|QString|可读 可写|缺省值|
|checkable|bool|可读 可写|是否可勾选|
|checked|bool|可读 可写|是否被勾选|
|datetime|QString|可读 可写|当前日期时间|
|readonly|bool|可读 可写|是否只读|

- ### 属性：margin （类型：int 可读 可写）

边界宽度。

| |调用方法|
| - | - |
|读取|int margin const|
|修改|void setMargin( int margin ) const|

- ### 属性：wrapping （类型：bool 可读 可写）

是否使用值循环。值循环是指，当前值已到最大值时，若再向上调会转到最小值。只有设置了最大最小值时有效。

| |调用方法|
| - | - |
|读取|bool wrapping const|
|修改|void setWrapping( bool wrapping ) const|

- ### 属性：format （类型：QString 可读 可写）

显示格式。

比如格式设置为 “yyyy-MM-dd hh:mm:ss”，显示的格式就是“2020-06-08 09:08:05“，如果设置为“yy年M月d日 h点m分s秒”，显示的格式就是“20年5月8日 9点8分5秒”。

比如格式设置为 “yyyy-MM-dd”，显示的格式就是“2020-06-08“，如果设置为“yyyy年M月d日”，显示的格式就是“20年5月8日”。

关于格式的设置参考下表，更详细的资料请参考 Qt 文档。

|格式|说明|
| - | - |
|d|日期数值，不补零 (1 到 31)|
|dd|日期，两位，不足两位时在前面补零 (01 到 31)|
|ddd|简化的本地化的周几(如英文 'Mon' 到 'Sun'，中文'周一'到'周日').|
|dddd|本地化的周几(如英文 'Monday' to 'Sunday'，中文'星期一'到'星期日').|
|M|月份数值，前面不补零 (1 到 12)|
|MM|两位的月份数值，不足两位时前面补零 (01 到 12)|
|MMM|简化的本地化的月份名称(如英文 'Jan' 到 'Dec'，中文'一月'到'十二月'). |
|MMMM|本地化的月份名称(如英文 'January' 到 'December'，中文'一月'到'十二月').|
|yy|两位的年份数值 (00 to 99)|
|yyyy|四位的年份数值|
|h|小时的值，不补零 (0 到 23 ，设置了显示上午/下午时为 1 至 12)|
|hh|小时的值，两位数字，不足两位时补零 (00 到 23 ，设置了显示上午/下午时为 01 至 12)|
|H|小时的值，不补零 (0 到 23 ，设置了显示上午/下午时也是为 00 至 23)|
|HH|小时的值，两位数字，不足两位时补零 (00 到 23 ，设置了显示上午/下午时也是为 00 至 23)|
|m|分钟的值，不补零 (0 到 59)|
|mm|分钟的值，两位数字，不足两位时补零 (00 到 59)|
|s|秒的值，不补零 (0 到 59)|
|ss|秒的值 ，两位数字，不足两位时补零 (00 到 59)|
|z|毫秒的值，不补零 (0 到 999)|
|zzz|毫秒的值，三位数字，不足三位时补零 (000 到 999)|
|AP|显示本地化的上午和下午，大写（中文不分大小写）|
|ap|显示本地化的上午和下午，小写（中文不分大小写）|

| |调用方法|
| - | - |
|读取|QString format const|
|修改|void setFormat( const QString &format ) const|

- ### 属性：calendarpopup （类型：bool 可读 可写）

是否提供弹出日历做为日期期的辅助输入方式。在设为 True 时，设置边框的属性无效。

| |调用方法|
| - | - |
|读取|bool calendarpopup const|
|修改|void setCalendarpopup( bool calendarpopup ) const|

- ### 属性：defaultVal （类型：QString 可读 ）

缺省值。控件创建之后默认设置为这个缺省值。

| |调用方法|
| - | - |
|读取|QString defaultVal const|

- ### 属性：text （类型：QString 可读 ）

显示的文本。

| |调用方法|
| - | - |
|读取|QString text const|

- ### 属性：checkable （类型：bool 可读 ）

是否可勾选。如果是可勾选的状态，在未选中时，不允许输入日期。

| |调用方法|
| - | - |
|读取|bool checkable const|

- ### 属性：checked （类型：bool 可读 可写）

checkable为 True 时，是否是选中的状态。

| |调用方法|
| - | - |
|读取|bool checked const|
|修改|void setChecked( bool checked ) const|

- ### 属性：datetime （类型：QString 可读 可写）

当前日期值。返回值会被转换为字符串形式。如果以 obj.date 的方式调用，格式是"yyyy-MM-dd hh:mm:ss"。如果需要其它格式，使用 obj.dateToString(format) 形式调用。同理，修改属性值时，默认格式也是"yyyy-MM-dd"。

| |调用方法|
| - | - |
|读取|QString datetime const|
|修改|void setDatetime( const QString &datetime ) const|

- ### 属性：readOnly （类型：bool 可读 可写）

是否只读

| |调用方法|
| - | - |
|读取|bool readOnly const|
|修改|void setReadOnly( bool readOnly ) const|


