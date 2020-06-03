Guide （redmine）

这是一篇讲解如何正确使用 Redmine 特殊链接语法，学会这个很有必要，能让你的文章有更佳清晰的排版。  
并且redmine支持基础的Markdown语法

```
@username               提及用户
document:filename       连接到文档
#124                    链接至一个问题,若该问题已结束则会用删除线来表示
#124-6                  链接至一个问题的回复
[[wiki]]                链接至当前项目的名为wiki页面
[[redmine_advice:FAQ]]  显示redmine_advice项目wiki页面的一个名为'FAQ'的链接
[[redmine_advice:]]     显示redmine_advice项目wiki首页的链接
document#17             链接到id为17的文档
document:Greetings      链接到标题为“Greeting”的文档
document:"Some document"            文档标题包含空格时使用双引号来表示
sandbox:document:"Some document"    链接至sandbox项目中标题为“Some document”的文档
version#3               链接至id为3的版本
version:1.0.0           链接到名称为“1.0.0”的版本

```

