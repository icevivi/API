# 第二章 标准控件 - 矩形控件

矩形控件用于显示一个矩形图形。如下图示：

![example](2-17-01.png)


---

<h2 id="category">目录</h2>

- [继承的属性和函数](#继承的属性和函数)

- [自有属性](#矩形控件的自有属性)

- [自有成员函数](#矩形控件自有成员函数)

- [信号](#矩形控件的信号)

- [可编程函数](#可编程函数)

---

## 继承的属性和函数

- [继承自QObject 的属性](2-1-qobject?id=属性)

- [继承自QObject 的 成员函数](2-1-qobject?id=成员函数)

- [继承自widgetDelegateBase的属性](2-2-base?id=属性)

- [继承自widgetDelegateBase的成员函数](2-2-base?id=成员函数)

---

## 矩形控件的自有属性

[返回目录](#category)

|     属性      | 值类型 | 读写类型  |     说明     |
| ------------- | ------ | -------- | ------------ |
| fillColor     | QColor | 可读 可写 | 填充颜色      |
| isRoundCorner | bool   | 可读 可写 | 是否使用圆角  |
| xCorner       | int    | 可读 可写 | 圆角x方向曲率 |
| yCorner       | int    | 可读 可写 | 圆角y方向曲率 |

- ### 属性：fillColor （类型：QColor 可读 可写）

填充颜色。

|      |                      调用方法                       |
| ---- | -------------------------------------------------- |
| 读取 | QColor fillColor() const                           |
| 修改 | void setFillColor( const QColor &fillColor ) const |

- ### 属性：isRoundCorner （类型：bool 可读 可写）

是否使用圆角。

|      |                     调用方法                     |
| ---- | ----------------------------------------------- |
| 读取 | bool isRoundCorner() const                      |
| 修改 | void setRoundCorner( bool isRoundCorner ) const |

- ### 属性：xCorner （类型：int 可读 可写）

圆角x方向曲率。

|      |               调用方法                |
| ---- | ------------------------------------ |
| 读取 | int xCorner() const                  |
| 修改 | void setXCorner( int xCorner ) const |

- ### 属性：yCorner （类型：int 可读 可写）

圆角y方向曲率。

|      |               调用方法                |
| ---- | ------------------------------------ |
| 读取 | int yCorner() const                  |
| 修改 | void setYCorner( int yCorner ) const |

---

## 矩形控件自有成员函数

[返回目录](#category)

所有属性的设置函数（参考上一节中修改属性的接口），都属于此类，都可以当做槽使用。除此之处， 矩形控件没有其它的成员函数。 

---

## 矩形控件的信号

[返回目录](#category)

矩形控件没有信号。

---

## 可编程函数

[返回目录](#category)

- [可编程函数的详细说明](1-4-openscript?id=控件的可编程函数)

矩形控件除了继承的 widgetDelegateBase 中的可编程函数外，没有其它可编程函数。

矩形控件所有可编程函数的清单：

|函数|函数名|传入参数|返回值|说明|
| - | - | - | - | - |
|[鼠标进入时](1-4-openscript?id=enter)|控件名_enter|无|无|鼠标光标进入到这个控件时调用|
|[鼠标离开时](1-4-openscript?id=leave)|控件名_leave|无|无|鼠标光标离开这个控件时调用|
|[大小改变时](1-4-openscript?id=resize)|控件名_resize|无|无|控件大小改变时调用|
|[当拖拽进入时](1-4-openscript?id=dragEnter)|控件名_dragEnter|拖拽进入的元数据|是否接受拖拽进入<br>**数据类型：布尔**|当从外部拖拽一些内容进入到这个控件时，会调用此函数。<br>不接受拖拽的控件不会调用此函数。<br>通过脚本判断是否接受拖拽，<br>如果接受，返回 True，如果在控件上放开鼠标，程序会转而调用“当拖拽放下时”函数。<br>如果不接受，返回False，程序将不会调用“当拖拽放下时”函数。<br><br>**传入参数：**<br>format:元数据的格式列表，以列表类型传入<br>data:元数据的内容，以列表类型传入<br>dx:拖入的位置X坐标<br>dy:拖入的位置Y坐标|
|[当拖拽放下时](1-4-openscript?id=drop)|控件名_drop|拖拽放下的元数据|是否接受拖拽放下<br>**数据类型：布尔**|拖拽放下时调用。允许则返回 True，否则返回 False。<br><br>**传入参数：**<br>format:元数据的格式列表，以列表类型传入<br>data:元数据的内容，以列表类型传入<br>dx:放下的位置X坐标<br>dy:放下的位置Y坐标|
|[单次定时器超时时](1-4-openscript?id=singleshot)|控件名_singleshot|无|无|内置单次定时器超时时调用|
|[定时器超时时](1-4-openscript?id=timeout)|控件名_timeout|定时器的ID值|无|内置定时器超时时调用|
