# 表单的可编程函数

biForm 中每个表单都有开放几个可编程函数。用于处理表单加载、运行、关闭等各种事务的处理。

除了“公共模块”没有函数名之外，其它都有对应的函数名。在表单后台的脚本中可以直接通过这些函数名调用这些函数，但一般不建议这样做，这种调用也只会执行函数体中的脚本，并不会影响表单对事件的响应。

## 目录

|    可编程函数    |                              函数名                               |
| --------------- | ---------------------------------------------------------------- |
| 公共模块        | 提供表单级的函数、变量、类定义等<br>参考[表单的公共模块](1-1-public) |
| 加载前          | [form_beforeload](#beforeload)                                    |
| 加载后          | [form_afterload](afterload)                                      |
| 新建空白表单前   | [form_beforecreatenew](beforecreatenew)                          |
| 新建空白表单后   | [form_aftercreatenew](aftercreatenew)                            |
| 保存前          | [form_beforesave](beforesave)                                    |
| 保存后          | [form_aftersave](aftersave)                                      |
| 删除前          | [form_beforedelete](beforedelete)                                |
| 删除后          | [form_afterdelete](afterdelete)                                  |
| 加载数据时       | [form_loaddata](loaddata)                                        |
| 打印前          | [form_before_print](before_print)                                |
| 打印后          | [form_after_print](after_print)                                  |
| 打印参数        | [form_print_args](print_args)                                    |
| 记录别名        | [form_alias](alias)                                              |
| 编号规则        | [form_number](number)                                            |
| 关闭前          | [form_before_print](before_print)                                |
| 关闭后          | [form_after_print](after_print)                                  |
| 单次定时器超时时 | [form_singleshot](singleshot)                                    |
| 定时器超时时     | [form_timeout](timeout)                                                 |
| 全程过滤条件     | [form_filter](filter)                                                  |
| 关联记录        | [form_relativerecord](relativerecord)                                          |

- ### beforeload

**可编程函数：加载前** 

[返回目录](#目录)

|      内容       |                                   说明                                    |
| --------------- | ------------------------------------------------------------------------- |
| 函数名          | form_beforeload                                                           |
| 传入参数        | 无                                                                        |
| 返回值          | 无                                                                        |
| 建议的返回值类型 | 无                                                                        |
| 使用规则        | 加载这个表单之前被调用。如果返回值为 True 表示允许加载，否则表单将不会被加载。 |
|                 | 在调用这个函数前，表单上控件、数据库等都可以访问。|

- ### afterload

**可编程函数：加载后** 

[返回目录](#目录)

|      内容       |                                   说明                                    |
| --------------- | ------------------------------------------------------------------------- |
| 函数名          | form_beforeload                                                           |
| 传入参数        | 无                                                                        |
| 返回值          | 无                                                                        |
| 建议的返回值类型 | 无                                                                        |
| 使用规则        | 加载这个表单之前被调用。如果返回值为 True 表示允许加载，否则表单将不会被加载。 |
|                 | 在调用这个函数前，表单上控件、数据库等都可以访问。                           |



