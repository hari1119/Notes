![image](https://github.com/user-attachments/assets/725ff996-bde5-4e89-b82d-f77ac78cab0a)


After the OS change we can able to open the terminal directly and using right click option to solve that follow the below step.
- Go to ```cd /usr/bin ```

- ``` sudo cp gnome-terminal gnome-terminal-backup ``` use this command and take backup.
- ``` suod cp gnome-terminal.real gnome-terminal ``` copy the source to gome-terminal.

Now able to open the terminal directly. 

- ```mkdir``` with braces to create multiple folders in one go.
  - ```sh
    mkdir -p {dev,test,prod}/{backend,frontend}
    ```
    
- ```cd``` - to quickly jump back to your previous directory.
   - ```sh
     cd -
     ```
- ```touch``` with a range to create multiple files at once.
  - ```sh
    touch test{1..100}.txt
    ```
- ```tail -f``` to follow log files in real-time.
  - ```sh
    tail -f error_file.log
    ```
- ```history 5``` to recall and re-execute recent commands.
  - ```sh
    !<id>
    ```
