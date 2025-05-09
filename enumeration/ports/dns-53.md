# DNS - 53

```bash
dnsenum <DOMAIN>
```

```bash
dnsrecon -d <DOMAIN>
```

### Zone transfert <a href="#zone-transfert" id="zone-transfert"></a>

```bash
dnsrecon -d <DOMAIN> -a
dig axfr <DOMAIN> @ns1.test.com
```

### DNS brute force <a href="#dns-brute-force" id="dns-brute-force"></a>

```bash
https://github.com/blark/aiodnsbrute
```
