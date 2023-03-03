# 0x08. Networking basics #1
  > ### Mandatory
  - `0-change_your_home_IP` Write a Bash script that configures an Ubuntu server with the below requirements.
    - localhost resolves to 127.0.0.2
    - facebook.com resolves to 8.8.8.8.
    - The checker is running on Docker, so make sure to read this
  - `1-show_attached_IPs`
   Write a Bash script that displays all active IPv4 IPs on the machine it’s executed on.
   ```
   sylvain@ubuntu$ ./1-show_attached_IPs | cat -e
10.0.2.15$
127.0.0.1$
sylvain@ubuntu$
   ```
   
> ### Advanced
  - `100-port_listening_on_localhost` 
   Write a Bash script that listens on port 98 on localhost.
    - Terminal 0
      ```
    sylvain@ubuntu$ sudo ./100-port_listening_on_localhost
      ```
    - Terminal 1
    ```
    sylvain@ubuntu$ telnet localhost 98
    Trying 127.0.0.2...
    Connected to localhost.
    Escape character is '^]'.
    Hello world
    test
    ```
    - Terminal 0
```
sylvain@ubuntu$ sudo ./100-port_listening_on_localhost
Hello world
test
```




