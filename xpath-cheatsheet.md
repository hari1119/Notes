# XPath (XML Path Language)
  Used to extend the odoo template.
  
```
<template id="..." inherit_id="..." name="...">
   <!-- Content -->
</template>
```
| Attribute | Description|
|:----------|:-----------|
|id | ID of the modified view|
|inherited_id | ID of the standard view|
| name | Human-readable name of the modified view |

 - For each XPath, you modify two attributes: **expression** and **position**

```
<template id="layout" inherit_id="website.layout" name="Welcome Message">
   <xpath expr="//header" position="before">
      <!-- Content -->
   </xpath>
</template>
```

# Expressions

This expressions used to select the perticular element in the xml,
Selectors are used inside the expression to target the right element.

| Descendent selectors | Description |
|:---------------------|:------------|
| **/**                | Selects from the root node.|
| **//**               | Selects nodes in the document from the current node that matches the selection no matter where they are. |


|Attribute selectors | Description |
|:-------------------|:------------|
|*                   |Selects any XML tag. ```*``` can be replaced by a specific tag if the selection needs to be more precise.|
|*[@id=”id”]         |Selects a specific ID.|
|*[hasclass(“class”)]| Selects a specific class. |
|*[@name=”name”]     | Selects a tag with a specific name. |
|*[@t-call=”t-call”] | Selects a specific t-call. |z

# Position
   Where we want to apply our changes, in wich possition.

|Position|Description|
|:-------|:----------|
|**replace** | Replaces the targeted node with the XPath content. |
|**inside** | Adds the XPath content inside the targeted node. |
|**before** | Adds the XPath content before the targeted node. |
|**after** | Adds the XPath content after the targeted node. |
|**attributes** | Adds the XPath content inside an attribute. |
