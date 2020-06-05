#### 注释  

1. *请使用英语编写注释*  
2. 注释应该是一个完整的句子，以大写字母开头，除非是使用某个小写的标识符作为开头  
3. 每一句都以句点加两个空格结尾，除非是最后一个句子  
4. 注释行应缩进到与所注释代码相同的位置  

5. 避免使用以下形式的内联注释：
```x = x + 1                 # Increment x```  

6. 应该为你的方法添加一个注释来描述其作用，此类注释添加在```def```之后。  
按照Odoo的风格，有参数和返回值时，需要对其加以解释。
```
@api.multi
def _compute_payment_amount(self, invoices=None, currency=None):
    """Compute the total amount for the payment wizard.

    :param invoices: If not specified, pick all the invoices.
    :param currency: If not specified, search a default currency on wizard/journal.
    :return: The total amount to pay the invoices.
    """
    pass
    return total
```

7. 注释掉一段代码时，请留下注释原因，不保留没必要的注释

8. python中使用#符号注释时， #后空一格，缩进到所注释代码的位置
```python
# 注释内容
```
   使用多行注释时, 多见于使用
```python
class Comments(modeuls.Model):
    """ 注释内容
    返回值介绍
    参数介绍
    """

    _name = 'comments'
    
    pass
```

  
9. xml文件中注释时，前后空一格，缩进到所注释代码的位置 
```xml
<!-- 注释内容 -->
```
[返回首页](./README.md)