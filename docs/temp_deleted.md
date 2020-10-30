- ### sendData

调用接口：QString sendData(const QString& filter="""",const QString& toJID="""",const QString& title="""",const QString& msg="""") const

[返回目录](#category)

发送表单数据给其他人。向下兼容保留。

|   内容   |  名称  | 数据类型 |                    说明                     |
| ------- | ------ | ------- | ------------------------------------------- |
| 传入参数 | filter | QString | 需要发送的数据的过滤条件                     |
| 传入参数 | toJID  | QString | 接收人的JID                                 |
| 传入参数 | title  | QString | 发送的数据的标题                             |
| 传入参数 | msg    | QString | 同时给接收人发送的消息                       |
| 返回值   |        | QString | 如果发送成功，返回空字符串，否则返回错误信息。 |

- ### isDraft

调用接口：bool isDraft() const

[返回目录](#category)

当前记录是否“草稿”状态。向下兼容保留。

|   内容   | 名称 | 数据类型 |    说明    |
| ------- | ---- | ------- | --------- |
| 传入参数 | 无   |         |           |
| 返回值   |      | bool    | 是否是草稿 |

- ### isInbox

调用接口：bool isInbox() const

[返回目录](#category)

当前记录是否“收件”状态。向下兼容保留。

|   内容   | 名称 | 数据类型 |    说明    |
| ------- | ---- | ------- | --------- |
| 传入参数 | 无   |         |           |
| 返回值   |      | bool    | 是否是收件 |

| [isDraft](#isDraft)                             | bool isDraft() const                                                                 | 是否是草稿                                      |
| [isInbox](#isInbox)                             | bool isInbox() const                                                                 | 是否是收件                                      |
