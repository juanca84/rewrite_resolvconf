## REWRITE /etc/resolv.conf WHIT crontab

These instructions are util in orden to rewrite /etc/resolv.conf, I had a problem with my network admistrator that rewrite a my dns setting for security.

So I have written a little crontab in orden to rewrite my /etc/resolv.conf each 10 seconds

1. Copy the file /etc/resolv.conf
    ```
    sudo cp /etc/resolv.conf  /etc/resolv.conf.new
    ```
    
1. Write into the new file /etc/resolv.conf.new for example with nano or other texteditor:
    ```
    nameserver 8.8.8.8
    nameserver 9.9.9.9
    ```
    
1. Create a bash file in your home for example:
    ```
    touch /home/user/rewrite_resolvconf.sh
    ```
    And put in the next
    ```
    #!/bin/bash
    set -e
    echo "Actualización resolv.conf"
    sudo cp /etc/resolv.conf.new /etc/resolv.conf
    ```
    And make a file executable
    ```
    chmod +x /home/user/rewrite_resolvconf.sh
    ```

4. Create the crontab with crontab -e and add the next:

    ```
    * * * * * /home/user/rewrite_resolvconf.sh
    * * * * * (sleep 10 ; ls)
    ```

And save and close your file, and ready!!

That's all!!


### Note
Maybe there is someone what these instructions are util
