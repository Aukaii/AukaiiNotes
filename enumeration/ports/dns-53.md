# DNS - 53

```
dnsenum <DOMAIN>
```

```
dnsrecon -d <DOMAIN>
```

#### Zone transfert <a href="#zone-transfert" id="zone-transfert"></a>

```
dnsrecon -d <DOMAIN> -a
dig axfr <DOMAIN> @ns1.test.com
```

#### DNS brute force <a href="#dns-brute-force" id="dns-brute-force"></a>

```
https://github.com/blark/aiodnsbrute
```
