# Joomla

```bash
joomscan -u <URL>
./joomlavs.rb --url <URL> -a -v
```

```bash
# Joomscan
joomscan -u  http://10.11.1.111 
joomscan -u  http://10.11.1.111 --enumerate-components

# Juumla
#https://github.com/knightm4re/juumla
python3 main.py -u https://example.com

droopescan scan joomla -u http://10.11.1.111
python3 cmseek.py -u domain.com
vulnx -u https://example.com/ --cms --dns -d -w -e
python3 cmsmap.py https://www.example.com -F

# nmap http-Joomla-brute

# Check common files
README.txt
htaccess.txt
web.config.txt
configuration.php
LICENSE.txt
administrator
administrator/index.php # Default admin login
index.php?option=<nameofplugin>
administrator/manifests/files/joomla.xml
plugins/system/cache/cache.xml
```
