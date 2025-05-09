# LDAP - 389

### Scans <a href="#scans" id="scans"></a>

```bash
nmap -n -sV --script "ldap* and not brute"

ldapsearch -h <IP> -x -s base
ldapsearch -h <IP> -x -D '<DOMAIN>\<USER>' -w '<PASSWORD>' -b "DC=<1_SUBDOMAIN>,DC=<TDL>"
```

### Graphical Interface <a href="#graphical-interface" id="graphical-interface"></a>

```bash
jxplorer
```
