# LDAP - 389

### LDAP - 389 <a href="#ldap---389" id="ldap---389"></a>

#### Scans <a href="#scans" id="scans"></a>

```
nmap -n -sV --script "ldap* and not brute"

ldapsearch -h <IP> -x -s base
ldapsearch -h <IP> -x -D '<DOMAIN>\<USER>' -w '<PASSWORD>' -b "DC=<1_SUBDOMAIN>,DC=<TDL>"
```

#### Graphical Interface <a href="#graphical-interface" id="graphical-interface"></a>

```
jxplorer
```
