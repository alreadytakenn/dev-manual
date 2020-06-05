#### 缩进  

python本身对缩进就十分严格，并在python3中已经禁止使用tab来缩进。  
推荐使用四个空格为一个缩进单位  
pycharm已自动将tab转换为四个空格 
```
# Odoo中的缩进规则与Python无异大致分为两种

# 一为缩进到界定符（各种括号）打开的位置
help = fields.Html(string='Action Description',
                   help='Optional help text ...',
                   translate=True)

# 一为悬挂式缩进，常见于Selection
state = fields.Selection([
    ('outgoing', 'Outgoing'),
    ('sent', 'Sent'),
    ('received', 'Received'),
    ('exception', 'Delivery Failed'),
    ('cancel', 'Cancelled'),
], 'Status', readonly=True, copy=False, default='outgoing')
```

> 若一个if语句的判断条件过长，以下是推荐的缩进模式  

添加注释来帮助理解  
添加一次缩进来区别后续代码  
在逻辑运算符之前换行  
```
if (this_is_one_thing
        and that_is_another_thing):
    # Since both conditions are true, we can frobnicate.
    do_something()
```

> 对于list等多行构造的元素，界定符与内容的缩进  

将界定符开始后换行  
元素在定义元素的位置进行额外一次缩进  
最后一个元素后追加尾随逗号  
界定符结束前换行并将其缩进到定义元素的位置
```
domain = [
    ('res_model', '=', 'helpdesk.ticket'), ('res_id', 'in', tickets.ids),
    ('consumed', '=', True), ('rating', '>=', 1),
]

values = {
    'team': team,
    'ratings': ratings,
    'stats': stats,
}
```

> 对于单行构造的list等元素  

```
# 除结尾元素外，每个元素后添加空格作为间隔
fields = ['module', 'model', 'name', 'res_id']

```

#### 行长度  

pycharm的默认限制长度为120个字符，不做更改  

#### 运算符的换行  

Odoo中较为少见，为了可读性选择以下风格
```
# 在运算符前换行
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```

#### 空白行  

Pycharm对此已经做了限制，要求模型前有且仅有两行空白行，方法前有且仅有一行 

#### 导入文件  

必须在文件顶部进行导入  
python3已禁止隐式导入  
导入Python文件与导入Odoo文件之间换行，优先导入Python文件  
导入顺序  
1. python标准库
2. 第三方python库
3. 本地应用程序或特定库

```
# 针对Python每行只导入一个python文件
import os
import sys

# 对Odoo无此限制  
from odoo import api, fields, models, tools, _
from odoo.exceptions import except_orm, UserError

```
如果从另一个模块中导入类时，此类名称与本地名称冲突，则应使用以下方式导入  
```
# MyClasshe YourClass 被占用
import myclass
import foo.bar.yourclass

# 调用
myclass.MyClass
foo.bra.yourclass.YourClass
```

#### 定义字段  

字段属性除了关系字段的关系和selection选项外，都需要显示定义  
Odoo对String等属性提供了隐式定义，不推荐  
为字段名无法清除表达字段含义的字段添加help属性  
属性定义顺序
```
# 关系字段
# Many2many, One2many, Many2one
# 关系属性为第一优先级

# 特殊字段
# related, compute，selection
# 特殊属性为第二优先级

# 普通字段属性顺序
# Odoo没有具体做法，但一般String为第一个， Help为最后一个
# string > required,index, default, help, groups, 
```
定义多选项的selection字段时，推荐以下方式缩进  
也应该归属到 *对于list等多行构造的元素*  
```
state = fields.Selection([
    ('outgoing', 'Outgoing'),
    ('sent', 'Sent'),
    ('received', 'Received'),
    ('exception', 'Delivery Failed'),
    ('cancel', 'Cancelled'),
], string='Status', readonly=True, copy=False, default='outgoing')
```


#### 定义字段约束  

尽量使用数据库约束，而非代码或前端约束  
提供清楚简短的约束提示消息  
使用多行形式定义  
定义在模型中所有字段定义之后，方法定义之前，与两者之间保留空白行  
```
_sql_constraints = [
    ('positive_height', 'CHECK(height>=0)', 'Height must be positive'),
    ('default_code_uniq', 'unique(default_code)', "Internal References has been used by other product!"),
]
```

#### 定义方法  

> Odoo中没有具体要求，但CRM中出现一个雏形  
> [CRM中定义方法的规范](https://github.com/odoo/odoo/blob/13.0/addons/crm/models/crm_lead.py)

1. default类的方法  
   在定义模型之后，字段之前
   ```
   class Company(models.Model):
    _name = "res.company"
    _description = 'Companies'
    _order = 'sequence, name'

    @api.multi
    def copy(self, default=None):
        pass

    name = fields.Char(related='partner_id.name', ...)
    sequence = fields.Integer(help='Used to order ...', default=10)
   ```
2. 计算，oncahnge等私有方法
   此类方法置于所有字段之后，ORM方法之前

3. 重写/继承ORM方法  
   CRUD, name_get, name_search等  

4. action相关的方法  
   close_dialog, edit_dialog, toggle_active， 按钮方法等

5. 业务方法  
   定义业务相关的方法  

*以上类型方法都遵循私有方法在前，公有灾后*  
*应该为方法提供简短的注释，包括参数信息，和返回值信息*

```
class Company(models.Model):
    _name = "res.company"
    _description = 'Companies'
    
    # ----------------------------------------
    # Default Methods
    # ----------------------------------------

    # 字段定义
    
    # ----------------------------------------
    # Compute/oncahnge Methods
    # ----------------------------------------

    # ----------------------------------------
    # ORM override
    # ----------------------------------------
    
    # ----------------------------------------
    # Actions Methods
    # ----------------------------------------
    
    # ----------------------------------------
    # Business Methods
    # ----------------------------------------
```