## 如何进行一次规范的开发?

> 更新远程代码到本地   

每次开发之前我们需要将 origin develop 更新到本地开发分支  
在本地开发分支上执行以下代码  
 ```git pull origin develop --rebase```   

> 开始开发  

现在你可以进行你的开发了, 要记住的是每天你都需要至少提交一次, 
来记录你的工作进度, 也方便进行代码审核  
[Commit规则](./commitRules.md)  

> 合并commit记录  

在完成了第一个功能点的开发后, 我们要将自己的Commit记录进行一次整理  
```
git rebase -i origin/develop  
# 第一次修改: 选择合并的commit记录
# 第二次修改: 添加合并的commit message
```
如果连续开发了两个功能点, 那么整理第二个功能点时, 则是rebase到第一个功能点之后

> 更新远程代码到本地 

在本地开发分支上执行以下代码, 解决过程中产生的[合并冲突](./handleConflict.md)
```
git pull origin develop --rebase
```

> 提交merge request  

[redmine提交merge request]()  
新建以合并的问题类型  
只能手动调整状态
