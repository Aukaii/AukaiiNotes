# TTY Rev Shell

```
# if no python
script /dev/null -c bash

#tty python
python3 -c 'import pty;pty.spawn("/bin/bash")'

#Exporting path
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/tmp  
export TERM=xterm-256color

#adding alias  
alias ll='ls -lsaht --color=auto'

**Keyboard Shortcut:** Ctrl + Z (Background Process.)  
stty raw -echo ; fg ; reset  # Enter 2x
stty columns 200 rows 200
```
