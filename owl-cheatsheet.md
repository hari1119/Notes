![image](https://github.com/user-attachments/assets/4e3e2e93-67ff-49c3-8ed1-c2ac50908b26)

# OWL 

- [OWL official](https://odoo.github.io/owl/)


### OWL Devtools

To explore the OWL framework in the odoo, there is a specific chrome extension for developers,this is use full to understand the OWL structure.

[OWL Devtools Guide](https://github.com/odoo/owl/blob/master/doc/tools/devtools_guide.md)

### OWL Field Widgets

Basic field widgets creation follow the step by step to create your first field widgets using OWL in odoo17.

Path in manifest --> ```module_name/static/src/js/js_file.js```

```
    'assets': {
        'web.assets_backend': [
        "fields_databank/static/src/js/code_field.js"
        ]
     },
```   
Create js file in the above mentioned path.

### code_field.js

```
/** @odoo-module **/
const {xml, Component} = owl;
import { standardFieldProps } from "@web/views/fields/standard_field_props";

export class CodeField extends Component {
    setup() {
        // This setup is useless here because we don't do anything
        // But this is where you will use Hooks
        super.setup();
    }
}

CodeField.template = xml`<pre t-esc="props.value" class="bg-primary text-white p-3 rounded"/>`;
CodeField.props = standardFieldProps;

```

In this above code, we can able to see the ``` const {xml, Component} = owl; ```

```const``` in the js syntax to store the data in a variable 
for example

``` 
const PI = 3.14159;
console.log(PI); // Output: 3.14159
```

``` const {xml, Component} = owl; ``` , this line of code is using object destructuring to extract the properties **xml** and **Component** from the object **owl** and assign them to constants with the same names.

- ```owl``` is assumed to be an object that contains properties named xml and Component.
- ```const {xml, Component} = owl;``` destructures the **owl** object, extracting the properties **xml** and **Component**.
- It then assigns these extracted properties to constants named ```xml``` and ```Component```, respectively.


```import { standardFieldProps } from "@web/views/fields/standard_field_props";```
This line of code is an import statement in JavaScript, specifically using **ECMAScript** modules syntax.

- ```import```: This keyword is used in JavaScript to import functionalities from other modules.
- ```{ standardFieldProps }```: This part of the import statement is called object destructuring. It means that only the named export **standardFieldProps** from the module **"@web/views/fields/standard_field_props"** will be imported.
- ```from "@web/views/fields/standard_field_props"```: This specifies the module from which to import. **"@web/views/fields/standard_field_props"** is the module path.

So, the line is importing the named export **standardFieldProps** from the module located at **"@web/views/fields/standard_field_props"**. After this import, you can use the **standardFieldProps** variable to access whatever was exported from that module.

```
export class CodeField extends Component {
    setup() {
        // This setup is useless here because we don't do anything
        // But this is where you will use Hooks
        super.setup();
    }
}
```

This code defines a JavaScript class named **CodeField** that extends the **Component** class. It appears to be using the Owl framework or a similar library due to the use of the **Component** class.

- ```export```: This keyword is used to export declarations (functions, objects, or classes) from a module, making them available for import by other modules.
- ```class CodeField extends Component ```: This line defines a class named CodeField that extends the Component class. This means that CodeField inherits all properties and methods from Component and can also have its own properties and methods.
- ```setup() { ... }```: This is a method definition within the **CodeField** class. It overrides the **setup()** method inherited from the **Component** class. In the comment, it mentions that it's where you would typically use Hooks (if you're following React's terminology). However, in this example, it doesn't perform any additional functionality and simply calls super.setup() to invoke the setup() method of the superclass (Component)

In a real-world scenario, you would typically use the **setup()** method to initialize component state, set up event listeners, perform data fetching, or any other necessary setup tasks for your component.

```CodeField.template = xml`<pre t-esc="props.value" class="bg-primary text-white p-3 rounded"/>`; ```
 
```CodeField.props = standardFieldProps;``` 

We can able to see that in the template **t-esc="props.value"**, while using this we can able to access the filed value before and after data store in the db.

Not only the field value we can able to get some standard data about the filed with using the filed widgets.

We can see that in this file : 
 odoo/addons/web/static/src/views/fields/standard_field_props.js  

This are the standard props values and keys.
![image](uploads/dde85157b89645b885805c265c185e7b/image.png)


To register the filed component.

```registry.category("fields").add("code", CodeField);```



### code_field.js

```
/** @odoo-module **/
const {xml, Component} = owl;
import { standardFieldProps } from "@web/views/fields/standard_field_props";

// Import the registry
import {registry} from "@web/core/registry";

export class CodeField extends Component {
    setup() {
        // This setup is useless here because we don't do anything
        // But this is where you will use Hooks
        super.setup();
    }
}

CodeField.template = xml`<pre t-esc="props.value" class="bg-primary text-white p-3 rounded"/>`;
CodeField.props = standardFieldProps;

// Add the field to the correct category
registry.category("fields").add("code", CodeField);
```

### Use the custom widgets in the xml attributes.

``` <field name="purpose" widget="code"/> ``` 

### Result :
![image](uploads/bb5c9060ea1da351ac336c103da5a1c6/image.png)


### Experienced issue :

![image](uploads/909ed4c97d05c971fd2145ac7e2b00c0/image.png)


### Solution:
To solve this for temporally, command the registry part alone.  


### To remove the key form the registry.
```registry.category("fields").remove("code");``` 


### OWL Play Ground
 - we can use this OWL play ground as a online compiler.
 - [Play Ground](https://odoo.github.io/owl/playground/)


### OWL Session Slide.
 - Find the OWL slide and video link below.
 - [Slide](https://docs.google.com/presentation/d/1a_UMftIetHKEzbHomlTpaykVJx_R6ebTUxkNgH_xze8/edit?usp=sharing)

### OWL Services
- We will also create the services in OWL

     - ``` registry.category("services").add("dashboard.statistics", statisticsService); ```
- Once we registered the services in the registry, then we will able to use any where using the below syntax.
     - ``` this.statistics = useState(useService("dashboard.statistics"));  ```

### OWL ORM
- Using the OWL orm we can able to contact the database.
    - ``` const options_key = await this.orm.searchRead("cm.master", domain, ["name","id"], { }); ```
    - For more check this link [Click Here](https://ajscript.com/odoo/dashboard/odoo-dashboard-using-owl-action-service/)

### Website
- Using the OWL framework we can able to build the website with the multiple page redaction
- As like the Model-View-Controller  

