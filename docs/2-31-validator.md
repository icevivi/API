# 校验器

校验器并不是一种控件，但是在单行文本输入控件中会用到。可以用它输助进行数值的输入。设置了校验器的单行文本输入框会只允许输入符合校验器的数字、负号、小数点符号。

校验器有两类，一个是整数校验器 intValidatorDelegate，一个是双精度浮点数校验器 doubleValidatorDelegate 。

---

<h2 id="category">目录</h2>

- [创建](#创建)

- [属性](#属性)

- [成员函数](#成员函数)

---

## 创建

[返回目录](#category)

创建校验器要通过 pub 对象提供的接口。

调用接口：

|                                         调用接口                                         |             示例             |                             说明                             |
| --------------------------------------------------------------------------------------- | ---------------------------- | ------------------------------------------------------------ |
| intValidatorDelegate* intValidator() const                                              | pub.intValidator()           | 不指定范围，可以允许最大范围的整数值 （-2147483647到2147483647) |
| intValidatorDelegate* intValidator(int min,int max) const                               | pub.intValidator(10,100)     | 指定最大最小值                                                |
| doubleValidatorDelegate* doubleValidator() const                                        | pub.doubleValidator()        | 不指定范围，可以允许最大范围的整数值（无限）                    |
| doubleValidatorDelegate* doubleValidator(double min,double max, int decimals = 0) const | pub.doubleValidator(0,100,2) | 指定最大最小值范围和小数位数                                   |

在控件中使用方式如以下代码所示：

``` python 

#创建一个整数校验器
v_int=pub.intValidator(10,100)

#设置单行文本输入框使用这个校验器验证输入的数值
this.lineedit1.setIntValidator(v_int)

#创建一个浮点数校验器
v_double=pub.doubleValidator(0,100,2)

#设置单行文本输入框使用这个校验器验证输入的数值
this.lineedit2.setDoubleValidator(v_double)

#取消校验器的设置，用传入参数0调用就可以了
this.lineedit2.setDoubleValidator(0)

```

## 属性

[返回目录](#category)

整数校验器的属性：

| 属性 | 值类型 | 读写类型  | 读取 |  赋值函数  |  说明  |
| ---- | ------ | -------- | ---- | --------- | ------ |
| top | int    | 可读 可写 | top | setTop    | 最大值 |
| bottom | int    | 可读 可写 | bottom | setBottom | 最小值 |

双精度浮点数校验器的属性：

|   属性   | 值类型 | 读写类型  |   读取   |   赋值函数   |   说明   |
| -------- | ------ | -------- | -------- | ----------- | ------- |
| top      | double | 可读 可写 | top      | setTop      | 最大值   |
| bottom   | double | 可读 可写 | bottom   | setBottom   | 最小值   |
| decimals | int    | 可读 可写 | decimals | setDecimals | 小数位数 |

## 成员函数

[返回目录](#category)

整数校验器的成员函数：

|   函数   |                    接口                     |       说明        |
| -------- | ------------------------------------------- | ----------------- |
| setRange | void setRange(int bottom,int top) const	 | 设置最大最小值范围 |

双精度浮点数校验器的成员函数：

|   函数   |                              接口                               |            说明            |
| -------- | --------------------------------------------------------------- | -------------------------- |
| setRange | void setRange(double bottom,double top,int decimals=0) const	 | 设置最大最小值范围和小数位数 |
