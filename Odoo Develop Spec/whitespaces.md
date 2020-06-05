### 空格或空行在表达式和语句中的用法  

---
> 空行  

1. 新建模型前空两行  
2. 新建方法前空一行
3. 删除不必要的空行  
4. python文件末尾空一行  
5. 视图/数据文件中每条记录之间空一行



---
> 冒号(:)在除以下情况都只在右侧添加一个空格  

1. 在字符串切片时  ```string[0:5]```
2. 换行

---
> 多项式中出最后个元素外，每个元素后都添加一个空格  

```python
domain = ['|', '|', (expression_1), (exoresssion_2), (expression_3)]  

create({'name': 'Space', 'age': 17, 'height': '2m'})
```

---
> 在计算中  

```python
# 正确用法
i = i + 1
submitted += 1
x = x*2 - 1
hypot2 = x*x + y*y
c = (a+b) * (a-b)

###############################

# 错误用法
i=i+1
submitted +=1
x = x * 2 - 1
hypot2 = x * x + y * y
c = (a + b) * (a - b)
```
