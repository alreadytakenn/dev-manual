```
# 推荐用法
if foo is not None:
    pass
# 错误用法
if not foo is None:
    pass
```

---

```
# 提倡使用try execpt捕获异常而不是暴露给用户
# try中包含最少量的代码，避免掩盖了错误
# except捕获具体异常，而不是裸露的except
```

---

```
# 在判断返回值的函数中，如果有一个返回值是None
# 则这个返回值应该显示的写为 return None

# 推荐做法
def foo(x):
    if x >= 0:
        return math.sqrt(x)
    else:
        return None

def bar(x):
    if x < 0:
        return None
    return math.sqrt(x)
    
# 错误做法
def foo(x):
    if x >= 0:
        return math.sqrt(x)

def bar(x):
    if x < 0:
        return
    return math.sqrt(x)
```

---

```
# 使用.startswith()和.endswith()而不是字符串切片来检查前缀或后缀
# .startswith()和.endswith()更干净并且更不容易出错：

```

---


```
# 对象类型比较应始终使用isinstance()而不是直接比较类型

```
[返回首页](./README.md)