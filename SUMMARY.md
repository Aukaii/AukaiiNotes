# Table of contents

* [Welcome](README.md)

## Recon

* [Web Recon](recon/web-recon.md)
* [Nmap Scanning](recon/nmap-scanning.md)
* [Domain Enumeration](recon/domain-enumeration/README.md)
  * [Subdomain Enumeration](recon/domain-enumeration/subdomain-enumeration.md)
  * [Subdomain Takeover](recon/domain-enumeration/subdomain-takeover.md)

## Enumeration

* [Ports](enumeration/ports/README.md)
  * [FTP - 21](enumeration/ports/ftp-21.md)
  * [SSH - 22](enumeration/ports/ssh-22.md)
  * [TELNET - 23](enumeration/ports/telnet-23.md)
  * [SMTP - 25](enumeration/ports/smtp-25.md)
  * [DNS - 53](enumeration/ports/dns-53.md)
  * [FINGER - 79](enumeration/ports/finger-79.md)
  * [KERBEROS - 88](enumeration/ports/kerberos-88.md)
  * [HTTP - HTTPS - 80 - 443](enumeration/ports/http-https-80-443.md)
  * [POP3 - 110](enumeration/ports/pop3-110.md)
  * [RPCBIND - 111](enumeration/ports/rpcbind-111.md)
  * [SNMP - 161](enumeration/ports/snmp-161.md)
  * [LDAP - 389](enumeration/ports/ldap-389.md)
  * [SMB - 445](enumeration/ports/smb-445.md)
  * [MSSQL - 1443](enumeration/ports/mssql-1443.md)
  * [NFS - 2049](enumeration/ports/nfs-2049.md)
  * [MYSQL - 3306](enumeration/ports/mysql-3306.md)
  * [RDP - 3389](enumeration/ports/rdp-3389.md)
  * [VNC - 5800-58001-5901](enumeration/ports/vnc-5800-58001-5901.md)
  * [WINRM - 5985 - 5986](enumeration/ports/winrm-5985-5986.md)
* [Files](enumeration/files.md)
* [CMS](enumeration/cms/README.md)
  * [Wordpress](enumeration/cms/wordpress.md)
  * [Drupal](enumeration/cms/drupal.md)
  * [Joomla](enumeration/cms/joomla.md)

***

* [Web](web.md)

## Exploitation

* [Payloads](exploitation/payloads.md)

***

* [Reverse Shells](reverse-shells.md)
* [File transfer](file-transfer/README.md)
  * [Linux](file-transfer/linux.md)
  * [Windows](file-transfer/windows.md)
* [Full tty shell](full-tty-shell.md)

## Post Exploitation

* [Host Enumeration](post-exploitation/host-enumeration/README.md)
  * [Linux](post-exploitation/host-enumeration/linux.md)
  * [Windows](post-exploitation/host-enumeration/windows/README.md)
    * [AD](post-exploitation/host-enumeration/windows/ad/README.md)
      * [Kerberos](post-exploitation/host-enumeration/windows/ad/kerberos.md)
    * [Ps tips & tricks](post-exploitation/host-enumeration/windows/ps-tips-and-tricks.md)
* [Privilege Escalation](post-exploitation/privilege-escalation/README.md)
  * [Linux](post-exploitation/privilege-escalation/linux/README.md)
    * [Suid](post-exploitation/privilege-escalation/linux/suid.md)
    * [Sudo](post-exploitation/privilege-escalation/linux/sudo.md)
    * [Leverage LD\_PRELOAD](post-exploitation/privilege-escalation/linux/leverage-ld_preload.md)
    * [Kernel](post-exploitation/privilege-escalation/linux/kernel.md)
    * [Capabilities](post-exploitation/privilege-escalation/linux/capabilities.md)
    * [Path hijacking](post-exploitation/privilege-escalation/linux/path-hijacking.md)
    * [Cron](post-exploitation/privilege-escalation/linux/cron.md)
    * [Library Hijacking](post-exploitation/privilege-escalation/linux/library-hijacking.md)
    * [Simple Docker Scape](post-exploitation/privilege-escalation/linux/simple-docker-scape.md)
    * [Linpeas](post-exploitation/privilege-escalation/linux/linpeas.md)
  * [Windows](post-exploitation/privilege-escalation/windows.md)
    * [1. Services](post-exploitation/privilege-escalation/windows/1.-services.md)
    * [2. Services](post-exploitation/privilege-escalation/windows/2.-services.md)
    * [Certificate Dialog - CVE-2019-1388](post-exploitation/privilege-escalation/windows/certificate-dialog-cve-2019-1388.md)
* [Pivoting](post-exploitation/pivoting/README.md)
  * [Pivoting with SSH](post-exploitation/pivoting/pivoting-with-ssh.md)
  * [Pivoting with Ligolo-ng](post-exploitation/pivoting/pivoting-with-ligolo-ng.md)
  * [Pivoting with chisel](post-exploitation/pivoting/pivoting-with-chisel.md)
  * [Others](post-exploitation/pivoting/others.md)
* [Tunneling - Port Forwarding](post-exploitation/tunneling-port-forwarding/README.md)
  * [Port Forwarding using SSH](post-exploitation/tunneling-port-forwarding/port-forwarding-using-ssh.md)
  * [Port Forwarding using Ligolo-ng](post-exploitation/tunneling-port-forwarding/port-forwarding-using-ligolo-ng.md)
* [Hashes](post-exploitation/hashes/README.md)
  * [Linux](post-exploitation/hashes/linux/README.md)
    * [Unshadow](post-exploitation/hashes/linux/unshadow.md)
    * [Responder](post-exploitation/hashes/linux/responder.md)
  * [Windows](post-exploitation/hashes/windows/README.md)
    * [Mimikatz](post-exploitation/hashes/windows/mimikatz.md)
    * [Getting Hashes on Servers](post-exploitation/hashes/windows/getting-hashes-on-servers.md)
    * [Getting hashes on old systems](post-exploitation/hashes/windows/getting-hashes-on-old-systems.md)
    * [Getting hashes in memory cache](post-exploitation/hashes/windows/getting-hashes-in-memory-cache.md)
    * [Getting hashes remotely](post-exploitation/hashes/windows/getting-hashes-remotely.md)
    * [Pass the hash](post-exploitation/hashes/windows/pass-the-hash.md)
    * [Hash examples](post-exploitation/hashes/windows/hash-examples.md)
    * [Bruteforce hashes](post-exploitation/hashes/windows/bruteforce-hashes.md)
