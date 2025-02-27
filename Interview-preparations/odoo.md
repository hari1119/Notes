## Odoo

1. Different between Many2many and One2many fields
    - **M2M** : This creates a link table (or intermediate table) that contains foreign keys referencing the primary keys of both related tables, This allows for the association of multiple records from both sides.
    - if we can able to define the table and coulum name within the fields declaretion itself, else system will automatically create, related module along with currecnt module name and with suffix as rel, Example in sale order line. we can able to see the tax_id fields in that m2m table name will be account_tax_sale_order_line_rel, and the table have column as sale_order_line_id and acccount_tax_id, this table is the relation between tha sale order line and account tax.
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

---

Ksolve L2 interview questions: 

1. Abstract Model: What is an abstract model in Odoo, and how is it used to create a base model for other models to inherit from?

2. Odoo Inheritance: Explain the different types of inheritance in Odoo (e.g., _inherits, _name, _description) and provide an example of how to use each type.

3. Compute Field Reuse: If a compute field is already used in another compute field, what will happen if you try to use it again in another compute field, and how can you avoid any potential issues?

4. Search_read: What is the purpose of the search_read method in Odoo, and how is it used to retrieve data from a model?

5. Search_read vs Mapped: Which is faster, search_read or mapped, and why? Provide an example to illustrate the difference.

6. Lambda Filter vs Search: Which is faster, using a lambda filter or the search method, and why? Provide an example to illustrate the difference.

7. Search([]): Is using search([]) correct and recommended? If not, what is an alternative way to achieve the same result?

8. Compute Function Search: Will the search method work inside a compute function, and if so, how?

9. Routes and Pull/Push Rules: Explain how routes and pull/push rules are used in Odoo to manage data exchange between different models.

10. Join and Union in PostgreSQL: How are join and union operations used in PostgreSQL, and provide an example of how to use each operation?

11. Group Access and Delete: If one group has delete access to a particular model, and another group does not, what will happen if a user has access to both groups? Is there a formula to determine the resulting access level?

12. Controller Route and Module Installation: If a controller route is enabled, but the module is not installed, will the route still work? If not, how can you create a route that works even if the module is not installed?

13. Automatic Function Creation: How does Odoo automatically create functions, and what are the benefits and limitations of this feature?

14. Web Hooks, Hosting, and Odoo Configuration: Explain how web hooks, hosting, and Odoo configuration are related, and provide an example of how to set up a web hook in Odoo.

15. Owl.js: What is Owl.js, and how is it used in Odoo to create interactive web pages?

16. Class or Prototype Inheritance: What are the constraints of using class or prototype inheritance in Odoo, and how do they affect the behavior of the inherited models?

17. User Access Group: How do user access groups work in Odoo, and what are the benefits of using them to manage access to different models?

18. Context in Odoo: What is the context in Odoo, and how is it used to pass parameters and variables between different functions and models?

---


1. What are the ORM methords in odoo? | - create , write, unlink, copy, search, search_read, search_count, browse
2. If we have A and B tow deffrenct servers, use to write the A server date in a B server datebase without end endpoint.
3. What is read_group?
4. what is get_view in odoo?
5. Explain view side inheritance ? | - with the view id we can able to inherit and over ride the view in odoo.
6. Difference between server action and window action ? | - Server action  : will done by the python side, for example send mail with out any manual action it will execute automatically - Window action : will be handle in the xml view side, execute from the view side.
7. If new enabled a new field in the class means, how the odoo will identify the new field was added ? | when the particular module get upgrade, in that odoo well identify that new fields has been added.
8. We wanna customise the sale order partner id label as  as customer A in a separate custom module, then we create a another custom module as change same field label name as customer Name ? | Based on the module installation sequence.
9. We wanna customise the sale order partner id label as  as customer A in using xpath in file 1 and same field label name change as customer Name in file 2 ? | It will reflect based on the manifest file sequence in the module.
10. We wanna customise the sale order partner id label as  as customer A in using python in file 1 and same field label name change as customer Name in file 2 ? | : It will reflect based on the __init__.py file sequence in the module.
11. Shallow Copy ? | : Copies the structure, not the elements within nested structures.
12. Deep Copy ? |  Copies the structure and all elements, recursively.
13.  different between @api.onchange and @.api.depends ? |  -  onchage with trigger while user manually change the fields value -  depends with trigger when the field get updating or creation or unlink
14. In-build widgets ? | - float, text, Integer, many2many,  progress_bar, status_bar
15. Different between sql constrains and python constrains. ? | -   sql constrains will be create in the DB -   python @api.constrain
16. Tell me the scenario to use  sql constrain ? | -   To check the unique value with in the columns
17. Give be the brief about MVC pattern ? | - Model View Controller
18. what is record rules, explain with a real time example ? | - we can set a rule based on the record, example company based record view and financial year based records view
19. what are the product types in odoo ? | - consumable, store able , service  





















---

### Odoo Technical Term


![image](https://github.com/user-attachments/assets/bc5b4a2d-914b-496e-9b4e-d3090346f301)



---

### Task 
  - restrict the same customor having payment pending above 1000$ while converting the quotation to sale order in odoo.

### solution:
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
