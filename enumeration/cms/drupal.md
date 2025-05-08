# Drupal

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
