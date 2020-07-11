# 信息检索期末项目——使用说明

本项目由python编写，用户交互界面使用pyQT5编写，查询过程不使用外置库手动实现了课堂所学的几种查询方式，因此运行本项目只需要**PyQt5**和**nltk**两个外置库，同时，请确保运行机器至少有2GB的存储空间用于存放**大量**的评论文本数据。

该文本的目的是详细说明从数据集下载到运行文件的全过程，为方便老师对我的项目进行测试

### 运行前准备

1. 运行本项目前需配置好Python3环境及上述两个外置库，只要是新近的版本即可，无特殊版本号要求。
2. 准备数据，数据来自——聚数力：[**Airbnb 开放数据**](http://dataju.cn/Dataju/web/datasetInstanceDetail/309)，可以使用该链接下载文本数据，我们的项目使用的是其中纽约市的数据，下载后使用解压缩工具，把数据集中纽约市里的*.gz文件解压出来，会得到含有评论文本的csv文件，新建一个命名为data的文件夹，将这些解压后的csv文件放入data文件夹下，并将data文件夹放入项目中的所有py文件的同一目录下。
3. 运行项目目录中的 **data_handling.py** 文件，该文件会将data文件夹中的文本转换成便于处理的形式，存储在同一目录下的out文件夹中，转换过程中不要强行终止程序，否则会导致文本数据的不完整，有了这个文件夹我们就可以运行项目了，但是如果想项目初始化得更快可以先把其他文件也放在目录下，后面会做说明。
4. 若没有准备out文件夹程序也不会出现异常退出，但是相当于对一个空的数据集进行搜索，是不会搜索到结果的

### 项目结构

* 程序执行的入口：main.py
* 需要的文件夹/文件：【都是放在main.py同一目录下】
  * out文件夹【通过原始数据处理而来，处理的脚本文件已给出】【必需】
  * index文件夹【存储标准大小倒排索引的文件夹】【程序检测到不存在会重新构建】【不必需】
  * doc_len.json【存储文档长度的文件】【程序检测到不存在会重新构建】【不必需】
  * 提交的项目中所有的python文件

### 减少等待时间的处理方式

如上面介绍的项目结构所示，虽然index文件夹和doclen.json文件都不是必需的，但是项目中有检测这两个文件/文件夹是否存在的代码，如果提供了现成的文件/文件夹，程序会跳过这个构建过程，可以大大加快程序的初始化进度。如果blackboard的网站情况允许，我将会上传这些预备文件，如果无法上传这么大的数据文件，还需要麻烦老师耐心等待程序自己进行倒排索引的构建和文本长度的计算。此外，即使原本这些文件不存在，在运行了一遍程序后这些文件会存储在本地文件夹下，第二次运行该程序同样会跳过对应的等待时间。【注意：如果程序执行到一半强行终止会生成不完整的数据文件，需要把不完整的文件删除，否则会出现查询结果有偏差或者程序运行异常的情况】

### 项目运行

确认以上**文件**和**环境**部署好后可以直接使用python运行main.py文件启动该项目。