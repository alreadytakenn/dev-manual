> python中单引号与双引号相同，因此python不对此做建议

对于Odoo  
在ORM中，优先使用单引号，除非嵌套
```
class ImportInvoiceImportWizard(models.TransientModel):
    _name = 'account.invoice.import.wizard'
    _description = 'Import Your Vendor Bills from Files.'
    
    attachment_ids = fields.Many2many('ir.attachment', string='Files', domain="[('type', '=', 'image')]")
```

在Odoo的视图文件中，优先使用双引号，除非嵌套  
```
<field name="category_id" widget="many2many_tags" options="{'color_field': 'color', 'no_create_edit': True}" placeholder="Tags..."/>
```
[返回首页](./README.md)