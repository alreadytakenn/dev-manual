# 分支模型介绍  
大体上基于 Gitflow 的分支模型, 但要求拥有每位开发人员拥有独立的开发分支, 做到每日推送, 以便代码审核和反馈工作进度  

> *master* 分支  

生产分支  
仅允许项目拥有者push  

> *develop* 分支  

主要开发分支  
仅允许项目拥有者push   

> *release* 分支  

释放分支  
要求从develop分支签发, 添加版本标签, 快进合并到master和develop分支

> *hotfix* 分支  

热修分支  
要求从master分支签出, 添加版本标签, 合并到master和develop分支  

> *feature-user* 分支  

个人开发分支  
每日更新, 记录工作进度, 完成工作后发起和并请求  
发起请求前, 要求合并commit记录, rebase到origin/develop的最新记录, 解决过程中产生的冲突