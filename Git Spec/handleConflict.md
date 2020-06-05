# 解决冲突  

> Git在代码合并产生冲突时, 添加了一套注释来阐明具体的冲突位置  

解决冲突前, 要明确冲突中代码的所属分支, 应与分支作者协商解决冲突, 切忌修改他人代码  
```
# 假定当前分支为feature-ben
git rebase develop
<<<<<<< HEAD
develop 分支上的代码
=======
feature-ben上的代码
>>>>>>> feature-ben名 


git merge develop || git merge --no-ff develop
<<<<<<< HEAD
feature-ben上的代码
=======
develop上的代码
>>>>>>> feature-ben
```

从上面看到, merge和rebase两种情况下, 冲突的格式有了差别.  
但实际上, rebase是develop分支上重放feature上的修改,   
也可以认为是将feature以快速合并的形式合并到develop上.
所以HEAD指向的基本对象, 后面是合并对象, 将合并对象合并到基本对象上.  

> 产生多个冲突时  

当产生多个冲突时, rebase和merge也分为两种情况  
rebase会每次重放一个commit, 因此rebase后产生多个冲突时, 每次只能解决一个commit中所产生冲突   
解决完一个Commit中的冲突后需要```git rebase --continue```  来进入到下一个commit, 解决下一个冲突.  

而merge时, 则会将分支直接合并, 因此会一次抛出所有的冲突.  

> 由于主分治的改动或者BUG导致合并后你的代码无法运转  

这种情况下禁止修改他人的代码, 来保证自己代码的运作  
应该在redmine中记录相关的问题, 与他人协商之后, 在决定如何更改. 
 




