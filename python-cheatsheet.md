# Create Python Virtual Enviroment.

#### Use the below command to change the python version.
 ```
 sudo update-alternatives --config python3
 ```

#### If you want to install the current python version.
 ```
 sudo apt-get install <currect-python3.12-version>
 ```

#### Create the python virtual enviroment with the specific version.
- Make sure your terget version installed in your local.
  
```
python3.12 -m venv <env_name>
```
## pyenv
- Once of the opensource for the python version.
  
##### Installation 
```sh
curl https://pyenv.run | bash
```
- Use the above command to download the source
- Once all done we want to export the path, for that use the below command
```sh
export PATH="$HOME/.pyenv/bin:$PATH"
```
- Then, activate the source.
```sh
source ~/.bashrc
```
- Check the version.
```sh
pyenv --version
```

## Basic Async Python with Asyncio

![image](https://github.com/user-attachments/assets/205be8c7-4036-4d99-995a-73c7380d3b85)

##### Understanding async and await
- To grasp the fundamentals of Async Python, you need to understand two essential keywords: async and await.

- async: The async keyword is used to define asynchronous functions. Functions defined with async def can be paused and resumed, allowing other tasks to run in the meantime.
- await: The await keyword is used within async functions to pause execution until a specific asynchronous task is complete. It's essential to remember that you can only use await within an async function.
- Additionally, it’s important to be aware that the GIL (Global Interpreter Lock) in Python is shared when using await. This means that while await can help you perform I/O-bound tasks concurrently, CPU-bound tasks might not see significant benefits due to the GIL.

**Example:**

```python3
import asyncio
import time

async def my_func():
    start = time.time()
    sleep_func = asyncio.sleep(2)  # function called, but not awaited
    print(time.time() - start)
    await sleep_func  # actual await
    print(time.time() - start)

asyncio.run(my_func())
```
###### Common Cases of Concurrency
![image](https://github.com/user-attachments/assets/a84514bb-63b1-466e-91c3-e35e8f1602ae)

### 1. Calling functions in Parallel

 Often, you’ll need to call functions in parallel. When you submit these calls, the order of execution is generally not guaranteed. Two common techniques for handling such scenarios are:

- Using asyncio.as_completed
   - If your main concern is speed, and you don’t need to maintain the order of the outputs, you can use ```as_completed```. This function returns an iterator that yields results as they are completed, allowing you to work with them immediately.

**Example:**

```python3
import asyncio
import random
import time

async def task(name):
    await asyncio.sleep(random.randint(1,3))
    return f"{name} finished"

async def main():
    tasks = [task(f"Task {i}") for i in range(1, 4)]

    start_time = time.time()
    for coro in asyncio.as_completed(tasks):
        result = await coro
        end_time = time.time()
        print(end_time - start_time, result)

    print(f"Total time {time.time() - start_time}")
if __name__ == "__main__":
    asyncio.run(main())
```
- Using asyncio.gather
   - When preserving the order of outputs is crucial, you can use the gather function. However, be aware that this method will wait for all tasks to complete 
  before providing results.

```python3
import asyncio
import random
import time

async def task(name):
    await asyncio.sleep(random.randint(1,3))
    return f"{name} finished"

async def main():
    tasks = [task(f"Task {i}") for i in range(1, 4)]

    start_time = time.time()
    results = await asyncio.gather(*tasks)
    end_time = time.time()

    print(f"gather took {end_time - start_time}")

    start_printing = time.time()
    for result in results:
        print(time.time() - start_printing, result)

    print(f"Total time {time.time() - start_time}")

if __name__ == "__main__":
    asyncio.run(main())
```
### 2. Creating Daemons with create_task

In some cases, you may want to create “daemons” — functions that run in parallel within the same Python run, similar to threads. This can be accomplished using the create_task function.

**Example:**

```python3
import asyncio


async def prints_quickly():
    while True:  # runs forever
        await asyncio.sleep(1)
        print("quick!")


async def prints_slowly():
    while True:  # runs forever
        await asyncio.sleep(3)
        print("slow...")


async def main():
    tasks = [asyncio.create_task(prints_quickly(), name="quick"), 
             asyncio.create_task(prints_slowly(), name="slow")]

    # both functions will run concurrently for 7s before cancelling them...
    await asyncio.sleep(7)

    for task in tasks:
        task.cancel()

    await asyncio.wait(tasks)

    print("Out!")


if __name__ == "__main__":
    asyncio.run(main())
```

### 3. PymuPDF4llm
 you’ve got a PDF filled with images, text, and tables. It’s a chaotic mess, and you’re staring at it with a sense of dread. But then you unleash Pymupdf4llm, and it effortlessly extracts the information, organizing it into a beautiful, markdown format. Talk about a productivity boost!

##### Install

```
pip install pymupdf4llm
```

##### Example
```python

import pymupdf4llm

md_text = pymupdf4llm.to_markdown("input.pdf")
print(md_text)
```

#### Source

- [git](https://github.com/pymupdf/RAG/tree/main/pymupdf4llm)
- [pip](https://pypi.org/project/pymupdf4llm/)

### 4. To check the battery life of the machine using python

```python3

from plyer import notification
import psutil
from icecream import ic
from time import sleep

while True:
    battery = psutil.sensors_battery()
    life = battery.percent
    ic(f"Battery Life Now Is {life}")
    if life < 80:
        notification.notify(
            title="Battery Low",
            message="Please connect to a power source",
            timeout=10
        )
    sleep(50)
```

### 5. Log the clip borad history in python

```python3
import pyperclip
import time

def log_clipboard():
    previous = ""
    while True:
        try:
            current = pyperclip.paste()
            if current != previous:
                with open("clipboard_log.txt", "a") as log:
                    log.write(f"{current}\n")
                previous = current
        except pyperclip.PyperclipException as e:
            print(f"Error reading clipboard: {e}")

        time.sleep(1)

log_clipboard()
```

