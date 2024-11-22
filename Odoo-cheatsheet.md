### Odoo ORM between range.
```python3
   ('minimum', '<=', value),('maximum','>=', value)
```


### Uninstall module in CLI
- get into the odoo shell using below cmd.
  
  ```bash
    python3 odoo-bin shell -c odoo.config
  ```
- run the code mentioned below.
  ```bash
   self.env['ir.module.module'].search([('name', '=', '<module_name>')]).button_immediate_uninstall()
  ```
  
### Odoo Scaffold cmd

```bash
   python3 odoo-bin scaffold <module_name> <addons_path>

   Python3 odoo-bin scaffold -t <module_template> <module_name> <addons_path>

```



### Useful Environment Methods
- **env.ref(xml_id, raise_if_not_found=True)**
  - The ref() method is useful for developers aiming to fetch records using XML IDs. By providing an external identifier (module_name.id), this function returns the corresponding recordset. It also offers an optional parameter, raise_if_not_found, which defaults to True and triggers a ValueError if the external ID (xml_id) is not found in the system.
    
  ![image](https://github.com/user-attachments/assets/da7a7bac-ce1c-47d6-b72d-099959372935)
- **env.is_superuser()**
  - Use this method to verify whether the current environment operates in superuser mode. Such capability proves particularly valuable when implementing functionalities restricted to users with superuser privileges.
    
  ![image](https://github.com/user-attachments/assets/0346c1ce-5e83-485e-8d9e-3dba708d04bd)

- **env.is_admin()**
  - The is_admin method verifies if the current user possesses the “Access Rights” group or is in superuser mode. This proves valuable for tailoring specific features or views based on the user’s administrative role.

  ![image](https://github.com/user-attachments/assets/9494638b-217f-4cfd-a7fb-145ecb12d25a)

- **env.is_system()**
  - This method verifies if the current user possesses the “Settings” group or is in superuser mode. This proves valuable for controlling access to system settings or configurations.

  ![image](https://github.com/user-attachments/assets/5b82ed12-79fd-4532-91b5-faba8995d772)

### Alter The Environment
- **Model.with_context(key=value)**
   - This method can be used to modify the context and include additional information within the environment. It merges the provided context seamlessly, so it will override existing keys and add new ones.
   ![image](https://github.com/user-attachments/assets/862c2608-d4d1-4de5-b363-f49841eef5c9)

- **Model.with_user(res_user or ID)**
  - This method proves useful when there’s a need to execute a method or access data with a different user context than the current one. It accepts the User database ID or recordset as a parameter.
  ![image](https://github.com/user-attachments/assets/e56ddd9e-59f0-4dcd-83f0-2ce262bcc679)

- **Model.with_company(res_company or ID)**
   - Certain fields in Odoo are company-dependent, meaning their values vary based on the company. One example is the Purchase Payment Term on Contact. By utilizing with_company and providing the company ID or recordset, you can fetch values specific to that particular company.

   ![image](https://github.com/user-attachments/assets/9e0ae494-962a-4af2-aeea-dbc843ce12fd)

- **Model.sudo()**
  - To execute tasks with superuser privileges, you can utilize sudo() within the environment.

  ![image](https://github.com/user-attachments/assets/a4e53e00-eede-4db1-9e1e-e5eb01dcfbe3)

  







