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
 
