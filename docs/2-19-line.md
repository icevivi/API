# 第二章 标准控件 - 直线控件

直线控件用于显示水平或垂直方向的直线。如下图示：

![example](2-19-01.png)

---

<h2 id="category">目录</h2>

- [继承的属性和函数](#继承的属性和函数)

- [自有属性](#直线控件的自有属性)

- [自有成员函数](#直线控件自有成员函数)

- [信号](#直线控件的信号)

- [可编程函数](#可编程函数)

---

## 继承的属性和函数

- [继承自QObject 的属性](2-1-qobject?id=属性)

- [继承自QObject 的 成员函数](2-1-qobject?id=成员函数)

- [继承自widgetDelegateBase的属性](2-2-base?id=属性)

- [继承自widgetDelegateBase的成员函数](2-2-base?id=成员函数)

---

## 直线控件的自有属性

[返回目录](#category)

|属性|值类型|读写类型|说明|
| - | - | - | - |
|lineColor|QColor|可读 可写|线条颜色|
|lineWidth|int|可读 可写|线宽|
|orientation|int|可读 可写|方向|
|lineStyle|int|可读 可写|线型|

- ### 属性：lineColor （类型：QColor 可读 可写）

线条颜色。

|      |                      调用方法                       |
| ---- | -------------------------------------------------- |
| 读取 | QColor lineColor() const                           |
| 修改 | void setLineColor( const QColor &lineColor ) const |

- ### 属性：lineWidth （类型：int 可读 可写）

线宽（像素为单位）。

|      |                 调用方法                  |
| ---- | ---------------------------------------- |
| 读取 | int lineWidth() const                    |
| 修改 | void setLineWidth( int lineWidth ) const |

- ### 属性：orientation （类型：int 可读 可写）

方向。

|      |                   调用方法                    |
| ---- | -------------------------------------------- |
| 读取 | int orientation() const                      |
| 修改 | void setOrientation( int orientation ) const |
|      | **orientation取值：**                        |
|      | pub.VERTICAL 垂直方向                         |
|      | pub.HORIZONTAL 水平方向                       |

- ### 属性：lineStyle （类型：int 可读 可写）

线型。

|      |                 调用方法                  |
| ---- | ---------------------------------------- |
| 读取 | int lineStyle() const                    |
| 修改 | void setLineStyle( int lineStyle ) const |
|      | **lineStyle取值：**                      |
|      | pub.SOLIDLINE 实线                       |
|      | pub.DASHLINE 破折线                      |
|      | pub.DOTLINE 点划线                       |
|      | pub.DASHDOTLINE 破折-点线                 |
|      | pub.DASHDOTDOTLINE 破折-点-点线           |

---

## 直线控件自有成员函数

[返回目录](#category)

所有属性的设置函数（参考上一节中修改属性的接口），都属于此类，都可以当做槽使用。除此之处， 直线控件没有其它的成员函数。 

---

## 直线控件的信号

[返回目录](#category)

直线控件没有信号。

---

## 可编程函数

[返回目录](#category)

- [可编程函数的详细说明](1-4-openscript?id=控件的可编程函数)

直线控件除了继承的 widgetDelegateBase 中的可编程函数外，没有其它可编程函数。

直线控件所有可编程函数的清单：

|函数|函数名|传入参数|返回值|说明|
| - | - | - | - | - |
|[鼠标进入时](1-4-openscript?id=enter)|控件名_enter|无|无|鼠标光标进入到这个控件时调用|
|[鼠标离开时](1-4-openscript?id=leave)|控件名_leave|无|无|鼠标光标离开这个控件时调用|
|[大小改变时](1-4-openscript?id=resize)|控件名_resize|无|无|控件大小改变时调用|
|[当拖拽进入时](1-4-openscript?id=dragEnter)|控件名_dragEnter|拖拽进入的元数据|是否接受拖拽进入<br>**数据类型：布尔**|当从外部拖拽一些内容进入到这个控件时，会调用此函数。<br>不接受拖拽的控件不会调用此函数。<br>通过脚本判断是否接受拖拽，<br>如果接受，返回 True，如果在控件上放开鼠标，程序会转而调用“当拖拽放下时”函数。<br>如果不接受，返回False，程序将不会调用“当拖拽放下时”函数。<br><br>**传入参数：**<br>format:元数据的格式列表，以列表类型传入<br>data:元数据的内容，以列表类型传入<br>dx:拖入的位置X坐标<br>dy:拖入的位置Y坐标|
|[当拖拽放下时](1-4-openscript?id=drop)|控件名_drop|拖拽放下的元数据|是否接受拖拽放下<br>**数据类型：布尔**|拖拽放下时调用。允许则返回 True，否则返回 False。<br><br>**传入参数：**<br>format:元数据的格式列表，以列表类型传入<br>data:元数据的内容，以列表类型传入<br>dx:放下的位置X坐标<br>dy:放下的位置Y坐标|
|[单次定时器超时时](1-4-openscript?id=singleshot)|控件名_singleshot|无|无|内置单次定时器超时时调用|
|[定时器超时时](1-4-openscript?id=timeout)|控件名_timeout|定时器的ID值|无|内置定时器超时时调用|
