---
title: 基于python-docx生成半自动化的word报告
date: 2018-07-06 15:49:47
tags:
---

缘起：
一直以来都有个需求是将固定格式的文档自动化生成，我以前曾经拿`latex`尝试过，效果其实很好，在`linux`下直接就可以生成pdf文档，非常适宜于放在服务器上。
然而，可悲的现实在于，`latex`过于阳春白雪。要说服更多的人走出自己的舒服区掌握一项新技能，实在是一件比触动灵魂更难的事情。
好在`word`还算是很多人都会的一个软件，而`python`也受到越来越多的人的青睐，我也希望走出自己的舒服区来尽量多的尝试它、学会它。

---

快速入门：
---
讲真，最快的入门方式就是看它的官方文档，即：`https://python-docx.readthedocs.io/en/latest/`
不过我想，还是有一些值得记录下来的点作为笔记留作后用：

 - 安装
 python-docx的安装很简单，pip install即可。如果有anaconda的话，可以conda安装。

 - 避免版本问题
 由于python有2和3的问题，所以调用module时需要针对性的进行一些修改。

```python
   # for python 2.7
   reload(sys)
   sys.setdefaultencoding('utf-8')

   # for python <=3.3
   import imp
   imp.reload(sys)
		         
   # for python >=3.4
   import importlib
   importlib.reload(sys)
```

 - 设置字体
 python-docx使用styles.font来指定字体的设置。方式如下：

```python
   document.styles['Normal'].font.name = u'仿宋'
   document.styles['Normal']._element.rPr.rFonts.set(qn('w:eastAsia'), u'仿宋')
```
 - 添加分页符
```python
   document.add_page_break()
```

 - 表格

 - 与其他数据的衔接

 - 后期调整

待续。。。
