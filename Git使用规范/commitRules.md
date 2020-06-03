# Commit规则  

redmine 中为一个问题或者一次功能的开发提供了四个状态, 分别是:  
1. Start
2. Working
3. Finished
4. Closed
5. Blocked  

redmine 会为每一个问题或者功能的开发提供一个编号, 
所以推送时, 为了推送到相关问题或者功能下, 我们必须在Commit msg 中添加问题编号  

而问题编号, 对一次推送的内容表述不够明确, 所以应该在Commit msg 中添加问题名  

为了时每一次Commit记录, 都能清晰的描述出这次推送的意义, 还要为Commit msg进行分类  
并在Commit msg中加入分类标签  
Commit类别暂定为:  
1. FEAT     开发新功能
2. TEST     测试
3. DEBUG    修复BUG

 ==综上所述==, 暂定Commit规则为:    
\[Commit 类型\]问题名 开发状态 问题编号.

例如: 
```git commit -m "[FEAT] #18 打印BOM表 Working." ```
