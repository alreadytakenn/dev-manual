#### 模板  
<details><summary>视图模板</summary>

```xml
<!-- action 模板，pycharm中的预创建模板 -->
<record id="$action_id$" model="ir.actions.act_window">
    <field name="name">$action_id$</field>
    <field name="type">ir.actions.act_window</field>
    <field name="res_model"></field>
    <field name="view_type"></field>
    <field name="view_mode"></field>
    <field name="context"></field>
    <field name="domain"></field>
    <field name="view_id" ref=""/>
    <field name="search_view_id" ref=""/>
    <field name="help" type="html">
        <p class="o_view_nocontent_smiling_face">
            Create a new record here!
        </p><p>
            Odoo helps you easily track all records related it.
        </p>
    </field>
</record>
```

```xml
<!-- form视图模板 -->
<record id="$view_id$" model="ir.ui.view">
    <field name="name">$view_id$</field>
    <field name="model"></field>
    <field name="arch" type="xml">
        <form string="">
            <header></header>

            <sheet></sheet>

            <!-- 需要继承['mail.thread', 'mail.activity.mixin'] 模型
            <div class="oe_chatter">
                <field name="message_follower_ids" widget="mail_followers"/>
                <field name="activity_ids" widget="mail_activity"/>
                <field name="message_ids" widget="mail_thread" options="{'post_refresh': 'recipients'}"/>
            </div>
            -->
        </form>
    </field>
</record>
```

```xml
<!-- tree视图模板 -->
<record id="$view_id$" model="ir.ui.view">
    <field name="name">$view_id$</field>
    <field name="model"></field>
    <field name="arch" type="xml">
        <tree string="">
            
        </tree>
    </field>
</record>
```

```xml
<!-- kanban视图模板 -->
<record id="$view_id$" model="ir.ui.view">
    <field name="name">$view_id$</field>
    <field name="model"></field>
    <field name="arch" type="xml">
        <kanban class="o_kanban_mobile">
            
            <templates>
                <t t-name="kanban-box">
                    <div t-attf-class="oe_kanban_card oe_kanban_global_click">
                        
                    </div>
                </t>
            </templates>
        </kanban>
    </field>
</record>
```

```xml
<!-- 搜索视图模板 -->
<record id="$view_id$" model="ir.ui.view">
    <field name="name">$view_id$</field>
    <field name="model"></field>
    <field name="arch" type="xml">
        <search string="Search Partner">
           <field name="name" filter_domain="[('display_name','ilike',self)]"/>
           <separator/>
       </search>
    </field>
</record>
```

```xml
<!-- 继承视图模板 -->
<record id="$view_id$_inherit" model="ir.ui.view">
    <field name="name">$view_id$_inherit</field>
    <field name="model"></field>
    <field name="inherit_id" ref="$view_id$"/>
    <field name="arch" type="xml">

    </field>
</record>
```
</details>


#### 例外  

ir.actions.server类型的视图中如果包含代码，则代码必须顶格书写和缩进
```xml
<record model="ir.actions.server" id="action_account_print_checks">
    <field name="name">Print Checks</field>
    <field name="model_id" ref="account.model_account_payment"/>
    <field name="binding_model_id" ref="account.model_account_payment" />
    <field name="state">code</field>
    <field name="code">
if records:
    action = records.print_checks()
    </field>
</record>
```

[返回首页](./README.md)

