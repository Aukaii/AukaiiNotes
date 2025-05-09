# SNMP - 161

### Brute force community string <a href="#brute-force-community-string" id="brute-force-community-string"></a>

```bash
onesixtyone -c /home/liodeus/wordlist/SecLists/Discovery/SNMP/common-snmp-community-strings-onesixtyone.txt <IP>
```

```bash
snmpbulkwalk -c <COMMUNITY_STRING> -v<VERSION> <IP>
```

```bash
snmp-check <IP>
```
