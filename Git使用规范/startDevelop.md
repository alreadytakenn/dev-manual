## 如何迅速开始一次新的开发?

> 更新远程代码到本地   

每次开发之前我们需要将 origin develop 更新到本地开发分支  
在本地开发分支上执行以下代码  
 ```git pull origin develop --rebase```   

> 开始开发  

[Commit规则]()  
[Bug反馈]()  

> 合并commit记录  

```
git rebase -i origin/develop  
# 第一次修改: 选择合并的commit记录
# 第二次修改: 添加合并的commit message
```

> 更新远程代码到本地 

在本地开发分支上执行以下代码, 解决过程中产生的[合并冲突]()
```
git pull origin develop --rebase
```

> 提交merge request  

[redmine提交merge request]()