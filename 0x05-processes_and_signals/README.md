# 0x05. Processes and signals
  > ### Mandatory
  - ```0-what-is-my-pid``` Bash script that displays its own PID.
  - ```1-list_your_processes```Bash script that displays a list of currently running processes.
  - ```2-show_your_bash_pid``` Bash script that displays lines containing the bash word, thus allowing you to easily get the PID of your Bash process
  - ```3-show_your_bash_pid_made_easy```Bash script that displays the PID, along with the process name, of processes whose name contain the word bash.
  - ```4-to_infinity_and_beyond``Bash script that displays To infinity and beyond indefinitely.
  - ```5-dont_stop_me_now```Bash script that stops 4-to_infinity_and_beyond process.
  - ```6-stop_me_if_you_can```  Bash script that stops 4-to_infinity_and_beyond process.
  - `7-base_geometry.py, tests/7-base_geometry.txt`Write a Bash script that displays:
    - To infinity and beyond indefinitely
    - With a sleep 2 in between each iteration
    - I am invincible!!! when receiving a SIGTERM signal

  - ```8-beheaded_process``` Bash script that kills the process 7-highlander.
 

> ### Advanced 
  - ```100-process_and_pid_file```  Write a Bash script that:
    - Creates the file /var/run/myscript.pid containing its PID
    - Displays To infinity and beyond indefinitely
    - Displays I hate the kill command when receiving a SIGTERM signal
    - Displays Y U no love me?! when receiving a SIGINT signal
    - Deletes the file /var/run/myscript.pid and terminates itself when receiving a SIGQUIT or SIGTERM signal

 - ```101-add_attribute.py```  Write Bash (init) script 101-manage_my_process that manages manage_my_process. (both files need to be pushed to git)
  ```
  sylvain@ubuntu$ sudo ./101-manage_my_process
Usage: manage_my_process {start|stop|restart}
sylvain@ubuntu$ sudo ./101-manage_my_process start
manage_my_process started
sylvain@ubuntu$ tail -f -n0 /tmp/my_process 
I am alive!
I am alive!
I am alive!
I am alive!
^C
sylvain@ubuntu$ sudo ./101-manage_my_process stop
manage_my_process stopped
sylvain@ubuntu$ cat /var/run/my_process.pid 
cat: /var/run/my_process.pid: No such file or directory
sylvain@ubuntu$ tail -f -n0 /tmp/my_process 
^C
sylvain@ubuntu$ sudo ./101-manage_my_process start
manage_my_process started
sylvain@ubuntu$ cat /var/run/my_process.pid 
11864
sylvain@ubuntu$ sudo ./101-manage_my_process restart
manage_my_process restarted
sylvain@ubuntu$ cat /var/run/my_process.pid 
11918
sylvain@ubuntu$ tail -f -n0 /tmp/my_process 
I am alive!
I am alive!
I am alive!
^C
sylvain@ubuntu$ 
  ```
- ```102-zombie.c```  Write a C program that creates 5 zombie processes.



