### 命名规则  

> 文件名命名规则见[文件名命名规则]()

> 类名命名规则  

使用大写字母开头的命名的方式（CapitalizedWords） 

> 内部名使用全小写加点的方式，并只能通过该名称调用  
> 数据库中则使用全小写加下划线的方式，并只能通过该名称调用

```python
class AccountIncoterms(models.Model):
    _name = 'account.incoterms'
    _description = 'Incoterms'
    
    pass
```


> 变量名命名规则  

变量名需要精简易懂，使用保持在三个单词以内小于27个字符的短语
对于Odoo中的变量使用全小写加下划线的方式（lower_case_with_underscores）

```py
# Many2one关系字段时使用_id
company_id = fields.Many2one('res.company', related='journal_id.company_id', ...)

# Many2many关系字段时使用 _ids
invoice_ids = fields.Many2many('account.invoice', 'account_invoice_payment_rel' ...)
```
  

> 常量命名规则  

使用全大写加下划线的方式（UPPER_CASE_WITH_UNDERSCORES）

```
MAP_INVOICE_TYPE_PARTNER_TYPE = {
    'out_invoice': 'customer',
    'out_refund': 'customer',
    'in_invoice': 'supplier',
    'in_refund': 'supplier',
}
```

> 方法名命名规则  

对于Odoo中方法名使用全小写加下划线的方式（lower_case_with_underscores）
Odoo中的私有方法以下划线开头。 
```
def _get_move_reconciled(self):
    pass

def default_get(self, fields):
    pass
```


> 视图命名规则  

使用全小写加下划线的方式。
    - 新视图  
    
    ```
    # Odoo中没有固定的格式，下为自定义格式
    $moduleName_$viewType_view
    
    # 例如
    res_partner_form_view
    account_analytic_line_tree_view
    
    # 若有多个类型相同的视图，则应该在原有ID基础上，在其后面简要描述功能
    # 例如
    crm_case_form_view_oppor
    crm_case_form_view_leads
    
    # Odoo没有统一格式，功能描述可能在前面，也可能在后面
    quick_create_opportunity_form
    create_opportunity_simplified
    ```
    
    
    - 继承视图
    
    ```inherit_原始视图ID```
    

> JS模块命名  

```js
$moduleName.功能+继承的模块类型

# 例如
odoo.define('documents.DocumentsKanbanModel', function (require) {
"use strict";

var KanbanModel = require('web.KanbanModel');
var core = require('web.core');

var _t = core._t;

var DocumentsKanbanModel = KanbanModel.extend({
    pass
})

# 类似的有
documents.DocumentsKanbanController
documents.DocumentsKanbanRenderer
```

[返回首页](./README.md)