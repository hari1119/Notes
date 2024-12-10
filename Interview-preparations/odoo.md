## Odoo

1. Different between Many2many and One2many fields
    - **M2M** : This creates a link table (or intermediate table) that contains foreign keys referencing the primary keys of both related tables, This allows for the association of multiple records from both sides.
    - Imagine a scenario where you have a Product model and a Category model. A product can belong to multiple categories, and a category can include multiple products. This relationship is defined using Many2many
    - **O2M** : This creates a field in the source model that holds an array of IDs from the target model,It's essentially a list of references to the target model.
      
   **Example**
    - **M2M** : Imagine a scenario where you have a ```Product``` model and a ```Category``` model. A product can belong to multiple categories, and a category can include multiple products. This relationship is defined using Many2many.
    - **O2M** : Consider a ```Sales Order``` model and an ```Order Line``` model. Each sales order can have multiple order lines, but each order line is associated with only one sales order. This relationship is defined using One2many.
      
2. why we want to use the many2many insterd of one2many in the above case.
   -  **Product**: Can belong to multiple categories (e.g., a shirt could be in both "Summer Collection" and "Discount Items").
   -  **Category**: Can contain multiple products (e.g., "Summer Collection" could include shirts, shorts, hats, etc.).
     
   why Not One2many?
   - **One2many on Product**: A product would reference a list of categories, but each category could not easily reference back to multiple products.
   - **One2many on Category**: A category would reference a list of products, but each product could not belong to multiple categories naturally.
   - This could lead to a more complex data structure and make queries less efficient and more complicated. In contrast, Many2many relationships provide a more streamlined and intuitive approach for scenarios where multiple-to-multiple relationships are natural and necessary.
  
3. We have openerp7 and odoo16, we want to migrate the db data from openerp 7 db to odoo16 db, with out the server in active status.
  - It's very complicated thing but,We can able to export the data from the source database (OpenERP7) as a excel format or csv format, to export use the ETL tools or we have the option to exprot the data in csv format from the PG Admin tool, once export the data use the odoo import option to load the data in the target Database.
  - Better chose use the xmlrpc or api options is avaiable, else export the data from the source and use python script to load the data in the target DB.
    
4. what are the cons for the xmlrpc in odoo?
   - **Performance**: XML-RPC can be slower compared to JSON-RPC because XML is more verbose than JSON. This can lead to increased data transfer and processing times.
   - **Complexity**: XML-RPC can be more complex to implement and debug due to its verbose nature and the need to parse XML data structures.
   - **Data Size**: XML-RPC messages tend to be larger in size compared to JSON-RPC, which can impact network bandwidth and performance, especially when dealing with large datasets.
   - **Compatibility:** While XML-RPC is widely supported, some modern APIs and services prefer JSON-RPC or other lightweight protocols like GraphQL for better performance and simplicity.
   - **Security**: XML-RPC can be vulnerable to certain types of attacks, such as XML injection attacks, if not properly secured.

5. super() function use and syntax in odoo.
   - The ```super()``` function in Odoo is used to call methods from a parent class within an inherited class. This is particularly useful when you want to extend or modify the behavior of existing methods without completely rewriting them.
     
   ```python3
   super(ParentClass, self).method_name(args)
   ```
   **Example**
   - Let's say you have a model ```sale.order``` and you want to extend the ```action_confirm``` method. Here's how you can use super()
     
   ```python3
   from odoo import models, fields

   class SaleOrder(models.Model):
       _inherit = 'sale.order'

       @api.multi
       def action_confirm(self):
           result = super(SaleOrder, self).action_confirm()
           # Your custom logic here
           return result
   ```


```python3

import UserError




def action_confirm:
     self.check_user_payment()
     super()

def check_user_payment(self):
     invoice = self.env['account.move'].search([('partner_id', '=', self.partner_id.id),('state', 'not in', ['posted'])])
     reminding_amt = sum([inv.amount_residual for inv in invoice])
     if reminding_amt >= 1000:
         raise UserError("Customer have the pending payment")
```
