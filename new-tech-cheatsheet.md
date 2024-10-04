### List of new technoloies.


#### 1. mesop
- mesop is the UI level framework developed by the google, specially for the AI interface.

  ###### Local setup
  - Install mesop
      - ```pip
          pip install mesop
        ```
  - File Extension
      - File name followed by .py
      - ``` <file_name>.py ```
  - Code Excution
      - ``` mesop <file_name>.py ```

- The mesop using the flask as a server to run.
**Example**
  ```python3
  import random
  import time

  import mesop as me
  import mesop.labs as mel


  def on_load(e: me.LoadEvent):
      me.set_theme_mode("system")


  @me.page(
      security_policy=me.SecurityPolicy(
        allowed_iframe_parents=["https://google.github.io", "https://huggingface.co"]
     ),
     path="/chat",
     title="Mesop Demo Chat",
     on_load=on_load,
     )
  def page():
      mel.chat(transform, title="Mesop Demo Chat", bot_user="Mesop Bot")


  def transform(input: str, history: list[mel.ChatMessage]):
      for line in random.sample(LINES, random.randint(3, len(LINES) - 1)):
        time.sleep(0.3)
        yield line + " "


  LINES = [
       "Mesop is a Python-based UI framework designed to simplify web UI development for engineers without frontend experience.",
       "It leverages the power of the Angular web framework and Angular Material components, allowing rapid construction of web demos
       "With Mesop, developers can enjoy a fast build-edit-refresh loop thanks to its hot reload feature, making UI tweaks and compon
       "Deployment is straightforward, utilizing standard HTTP technologies.",
       "Mesop's component library aims for comprehensive Angular Material component coverage, enhancing UI flexibility and composabil
       "It supports custom components for specific use cases, ensuring developers can extend its capabilities to fit their unique req
       "Mesop's roadmap includes expanding its component library and simplifying the onboarding processs."]
  ```

  #### 2. tomllib
  - ```tomllib``` in the pip based python lib, is like one of the config file.
    ###### Local Setup
    - Install
        - ```pip
            pip install tomllib
           ```
    - File Extension
        - ``` <config_file>.toml ```
  **Example**

  config.toml
  ```
  [server]
  host = "localhost"
  port = 8080
  ssl = false

  [database]
  url = "mongodb://localhost:27017"
  name = "mydb"
  username = "myuser"
  password = "mypassword"
  level = "info"
  ```
  file.py
  ```python3
  import toml

  with open('config.toml', 'r') as f:
	   config = toml.load(f)

  # Access values from the config
  print(config['server']['host'])
  print(config['server']['port'])
  print(config['database']['username'])
  ```

#### 3. mesop
- mesop is the UI level framework developed by the google, specially for the AI interface.

  ###### Local setup
  - Install mesop
      - ```pip
          pip install mesop
        ```
  - File Extension
      - File name followed by .py
      - ``` <file_name>.py ```
  - Code Excution
      - ``` mesop <file_name>.py ```
  
