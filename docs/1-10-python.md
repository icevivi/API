# 第一章 biForm开发基础 - 使用Python第三方库

biForm 使用 Python 做为编程语言，目前发布的 V3.1 基于 Python v3.6.5。

---

<h2 id="category">目录</h2>

- [安装包中的第三方库](#安装包中的第三方库)
- [其它第三方库](#其它第三方库)
- [其它Python的图形库](#其它Python的图形库)

---

## 安装包中的第三方库

[返回目录](#category)

随 biForm 和 PFF 的运行时环境（如 biReader ）已经打包了很多 Python 的第三方库：

|      库       |    版本     |       协议       |                  说明                   |                              项目地址                               |
| ------------- | ----------- | ---------------- | -------------------------------------- | ------------------------------------------------------------------ |
| barcode       | 0.9.0       | MIT              | 一维码生成器                            | [python-barcode](https://pypi.org/project/python-barcode/)         |
| cairocffi     | 1.1.0       | BSD              | Cairo库的Python绑定和面向对象的调用接口  | [cairocffi](https://pypi.org/project/cairocffi/)                   |
| cairosvg      | 2.4.2       | LGPLv3+          | 基于Cairor的SVG转换器                   | [CairoSVG](https://pypi.org/project/CairoSVG/)                     |
| certifi       | 2019.06.16  | MPL-2.0          | 根证书工具                              | [certifi](https://pypi.org/project/certifi/)                       |
| cffi          | 1.14.0      | MIT              | 调用C代码的外部函数接口                  | [cffi](https://pypi.org/project/cffi/)                             |
| chardet       | 3.0.4       | LGPL             | 通用字符编码检测器                       | [chardet](https://pypi.org/project/chardet/)                       |
| code128       | 0.3         | LGPLv2+          | Code-128条码生成器                      | [code128](https://pypi.org/project/code128/)                       |
| colorama      | 0.4.1       | BSD              | 在控制台、命令行输出彩色文字             | [colorama](https://pypi.org/project/colorama/)                     |
| Crypto        | 1.4.1       | MIT              | 加密解密工具                            | [Crypto](https://pypi.org/project/crypto/)                         |
| cssselect2    | 0.3.0       | BSD              | 标记文档的CSS3选择器                    | [cssselect2](https://pypi.org/project/cssselect2/)                 |
| cycler        | 0.10.0      | BSD              | 可组合的样式循环                        | [Cycler](https://pypi.org/project/Cycler/)                         |
| dateutil      | 2.6.0       | Apache/BSD       | 日期和时间工具                          | [python-dateutil](https://pypi.org/project/python-dateutil/)       |
| defusedxml    | 0.6.0       | PSFL             | 防止xml攻击                             | [defusedxml](https://pypi.org/project/defusedxml/)                 |
| easy_install  | 3.6.5       | Python           | 安装工具                                | [EasyInstall](http://peak.telecommunity.com/DevCenter/EasyInstall) |
| elaphe3       | 0.2.0       | BSD              | 条码生成                                | [elaphe3](https://pypi.org/project/elaphe3/)                       |
| et_xmlfile    | 1.0.1       | MIT              | 生成XML文件的库                         | [et_xmlfile](https://pypi.org/project/et_xmlfile/)                 |
| idna          | 2.5         | BSD              | 应用程序中的国际化域名                   | [idna](https://pypi.org/project/idna/)                             |
| jdcal         | 1.4         | BSD              | 日期转换                                | [jdcal](https://pypi.org/project/jdcal/)                           |
| jinja2        | 2.10        | BSD              | 模板引擎                                | [Jinja2](https://pypi.org/project/Jinja2/)                         |
| kiwisolver    | 1.0.1       | BSD              | Cassowray约束求解器的快速实现            | [kiwisolver](https://pypi.org/project/kiwisolver/)                 |
| markupsafe    | 1.1.1       | BSD              | 安全地为HTML/XML标记添加不受信任的字符串  | [MarkupSafe](https://pypi.org/project/MarkupSafe/)                 |
| matplotlib    | 3.0.3       | PSFL             | 绘图库                                  | [matplotlib](https://pypi.org/project/matplotlib/)                 |
| mpl_toolkits  | 1.2.1       | PSFL             | matplotlib工具包                        | [mpl_toolkits](https://matplotlib.org/mpl_toolkits/index.html)     |
| Naked         | 0.1.31      | MIT              | 一个命令行应用程序框架                   | [Naked](https://pypi.org/project/naked/)                           |
| numpy         | 1.16.2      | BSD              | 科学计算                                | [numpy](https://pypi.org/project/numpy/)                           |
| openpyxl      | 2.5.3       | MIT              | 读写xlsx/xlsm文件                       | [openpyxl](https://pypi.org/project/openpyxl/)                     |
| pandas        | 0.24.2      | BSD              | 数据分析                                | [pandas](https://pypi.org/project/pandas/)                         |
| pdf417        | 0.8.0       | MIT              | PDF417二维码生成器                      | [pdf417](https://pypi.org/project/pdf417/)                         |
| PIL           | 1.1.7       | Python           | 图像处理                                | [PIL](https://pypi.org/project/PIL/)                               |
| pip           | 19.0.3      | MIT              | 安装工具                                | [pip](https://pypi.org/project/pip/)                               |
| pkg_resources | 47.3.1      | MIT              | 包资源管理工具                           | [pkg_resources](https://pypi.org/project/setuptools/)              |
| pycparser     | 2.20        | BSD              | C 语言的完整解析器                       | [pycparser](https://pypi.org/project/pycparser/)                   |
| pyexcelerate  | 0.7.3       | BSD              | 用于写Excel兼容的xlsx扩展电子表格文件的库 | [PyExcelerate](https://pypi.org/project/PyExcelerate/)             |
| pygraphviz    | 1.6         | BSD              | Graphviz的Python接口                    | [pygraphviz](https://pypi.org/project/pygraphviz/)                 |
| pylab         | 1.3.2       | MIT              | 开发工具包                              | [pylab-sdk](https://pypi.org/project/pylab-sdk/)                   |
| pyparsing     | 2.2.0       | MIT              | 语法解析                                | [pyparsing](https://pypi.org/project/pyparsing/)                   |
| pytz          | 2017.2      | MIT              | 时区工具                                | [pytz](https://pypi.org/project/pytz/)                             |
| qrcode        | 6.1         | BSD              | QRCode二维码生成器                       | [qrcode](https://pypi.org/project/qrcode/)                         |
| reportlab     | 3.5.13      | BSD              | 生成PDF和图像的库                        | [reportlab](https://pypi.org/project/reportlab/)                   |
| requests      | 2.18.2      | Apache 2.0       | HTTP库                                  | [requests](https://pypi.org/project/requests/)                     |
| scipy         | 1.2.1       | BSD              | 数据、科学、工程领域的软件包              | [scipy](https://pypi.org/project/scipy/)                           |
| setuptools    | 47.3.1      | MIT              | 安装工具                                | [setuptools](https://pypi.org/project/setuptools/)                 |
| shellescape   | 3.8.1       | MIT              | Shell转义字符串                         | [shellescape](https://pypi.org/project/shellescape/)               |
| six           | 1.10.0      | MIT              | Python2和Python3兼容工具包               | [six](https://pypi.org/project/six/)                               |
| sklearn       | 0.20.3      | OSI Approved     | 机器学习、数据挖掘和数据分析工具          | [scikit-learn](https://pypi.org/project/scikit-learn/)             |
| tinycss2      | 1.0.2       | BSD              | CSS解析器和生成器                        | [tinycss2](https://pypi.org/project/tinycss2/)                     |
| tkinter       | 8.6         | Python           | Tk图形库接口                            | [tkinter](https://docs.python.org/3/library/tkinter.html)          |
| upcean        | 2.7.14 RC 1 | OSI Approved,BSD | 条码生成器                              | [PyUPC-EAN](https://pypi.org/project/PyUPC-EAN/)                   |
| urllib3       | 1.22        | MIT              | HTTP库                                  | [urllib3](https://pypi.org/project/urllib3/)                       |
| webencodings  | 0.5.1       | BSD              | WEB内容字符编码                          | [webencodings](https://pypi.org/project/webencodings/)             |
| whoosh        | 2.7.4       | BSD              | 全文搜索引擎、拼写检查工具库              | [Whoosh](https://pypi.org/project/Whoosh/)                         |
| xlrd          | 1.1.0       | BSD              | 读Excel文件的工具                        | [xlrd](https://pypi.org/project/xlrd/)                             |
| xlutils       | 2.0.0       | MIT              | Excel文件处理工具集                      | [xlutils](https://pypi.org/project/xlutils/)                       |
| xlwt          | 1.3.0       | BSD              | 写Excel文件的工具                        | [xlwt](https://pypi.org/project/xlwt/)                             |
| yaml          | 5.3.1       | MIT              | YAML解析器和发射器                       | [PyYAML](https://pypi.org/project/PyYAML/)                         |

以上的版本号针对 Windows 下 V3.1.001 发布的版本，其它平台下的版本或升级版本，可能使用的第三方库的版本号不同，以上只做参考。

## 其它第三方库

[返回目录](#category)

Python 的第三方库非常丰富，开发者在使用过程中有时会需要用到其它第三方库或者自己写的 Python 文件。只需要将相应的文件复制到 biForm 或 PFF运行时环境（如biReader）下就可以使用。只是需要注意的是，如果开发过程中使用到其它库，给最终用户使用时，也需要在最终用户的机器上配置相应的文件，否则会因为缺少依赖的文件影响程序运行。

具体要将文件复制到哪里，不同的操作系统和环境下，也不尽相同，开发者可以在 biForm 中使用 sys.path 查看系统导入外部模块的目录，如下示例：

``` Python
>>> import sys
>>> sys.path
['G:\\biform_dev\\bin', 'G:\\biform_dev\\bin\\py\\Python_Lib', 'G:\\biform_dev\\bin\\py', 'G:\\biform_dev\\bin\\DLLs', 'G:\\biform_dev\\bin\\py\\site-packages']

```

在Linux下返回的目录与上面会不一样。

开发者将第三方库需要的文件复制到这些目录下，就可以使用了。如果知道要复制哪些文件，我们建议开发者安装一个 Python 3.6.5，然后安装自己需要的包，在 Python 中试验是否可以正常使用，如果可以使用的话，一般来讲，将 python 的 site-packages 下这个包对应的目录复制到上面的某个目录，比如“G:\\biform_dev\\bin\\py\\site-packages” 就可以了。

当然，也有一些 Python 第三方库还依赖于其它应用程序，比如 tkinter 依赖 tk 和 tcl 。这类情况下，就需要将相应的 DLL文件（linux下的so文件) 复制到 biForm/biReader 的安装目录下，还有一些 tk 相关的文件也需要配置好，才能正常运行。解决这类环境依赖的问题，需按照第三方库的具体情况来设计解决方案。

虽然 sys.path 可以通过 Python 脚本进行修改，但如果开发者将修改的脚本写在某个PFF文件里，除非将这个PFF文件设置为自启动，否则也不能在PFF运行时环境启动时就执行这段修改代码。但PFF的自启动，有可能是允许最终用户是自己修改的（取决于PFF运行时引擎的设计）。PFF的打开顺序一般也不是固定的。所以，也不能完全保证这个PFF先于其它PFF运行。所以，我们并不建议开发者通过代码修改 sys.path 来加载第三方库或自己的 .py 文件，将文件复制到 biForm 相应目录下是更稳妥、更通用、且行之有效的解决方案。如果一定要修改，需事先了解它何时才会被执行，以及是否会影响其它PFF的运行。

## 其它Python的图形库

[返回目录](#category)

用 Python 开发GUI程序，我们常听到开发者会提到 PyQt、wxWidgets、Tkinter 等图形库。

目前 biForm 的发布版本里已包含了 Tkinter ，因为一些第三方库依赖于 Tkinter 显示图形界面。

开发者刚接触 biForm ，可能觉得它和 PyQt 很象，但 biForm 并没有使用  PyQt 。PyQt 是以 Python 代码运行，调用 Qt 的图形库。biForm以及PFF的运行时引擎，都是 C++ 程序在运行，只是与 Python 集成，可以在 C++ 代码中执行 Python 脚本，并且开放了 Qt 以及应用程序的接口供 Python 脚本调用。所以技术实现上与 PyQt 完全不同。将 PyQt 安装到 biForm 的 site-packages 目录下，其实是可以在 biForm 中调用 PyQt 的，但并不建议开发者这样做。Qt 库虽然很强大，但一般来讲，用它开发代码量较大，程序结构也会比较复杂，学习和掌握 Qt 各个库的用法，也需要更多的时间，即使是使用与C++相比更简洁更易上手的 Python 来调用，这一点也没有很大改变。biForm 做了很多封装，提供了更简单直接的应用框架，大部分应用的开发都比使用 PyQt 更简便。biForm 中也开放了 Qt 库供调用，没必要用 PyQt 再绕一圈来调用。所以，我们发布的版本中并没有包含 PyQt。

wxWidgets 其实也是可以在 biForm 中使用的，但没有打包到发布的版本中。

虽然我们并不推荐开发者在 biForm 中使用这几种库，但如果您以前有源代码使用这些代码，不想过多地修改代码，也可以尝试与 biForm 集成。

biForm 提供了一套自己的图形界面解决方案和应用框架，并且提供了可视化的界面设计器。和以上几种只能使用代码来进行开发的相比，更容易进行快速开发，代码量也更少，并且能够与其它开发者的程序更好地集成，更容易发布，开发者不需要考虑跨平台等方面的细节问题，因此建议开发者尽量使用 biForm 提供的图形界面框架来进行开发，能更好地利用 biForm 这个平台带来的附加价值。
