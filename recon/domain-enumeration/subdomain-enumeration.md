# Subdomain Enumeration

### Tools <a href="#passive-sources" id="passive-sources"></a>

{% code overflow="wrap" %}
```bash
#ffuf
ffuf -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt -u http://greenhost.local -H "Host: FUZZ.greenhost.local" -mc all -v -c

obs:apply filters if necessary


#gobuster
gobuster dns -d lookup.thm -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt
```
{% endcode %}

### Passive Sources <a href="#passive-sources" id="passive-sources"></a>

```bash
# https://github.com/OWASP/Amass
# https://github.com/OWASP/Amass/blob/master/examples/config.ini
amass enum -passive -d domain.com

# https://github.com/projectdiscovery/subfinder
# https://github.com/projectdiscovery/subfinder#post-installation-instructions
subfinder -d domain.com -all -silent

# https://github.com/tomnomnom/assetfinder
assetfinder example.com

# https://github.com/tomnomnom/waybackurls
# https://github.com/tomnomnom/unfurl
echo domain.com | waybackurls | unfurl -u domains

# https://github.com/lc/gau
# https://github.com/tomnomnom/unfurl
gau --subs example.com | unfurl -u domains

## Cert Transparency
# https://certificate.transparency.dev/
# https://crt.sh/
# https://github.com/glebarez/cero
cero example.com
# https://github.com/UnaPibaGeek/ctfr
python3 ctfr.py -d domain.com

# Active crtsh monitoring
#https://github.com/g0ldencybersec/gungnir
gungnir -r domains.txt

# https://github.com/gwen001/github-subdomains
github-subdomains -d example.com -t tokens.txt -o output.txt

# https://github.com/christophetd/censys-subdomain-finder
python3 censys-subdomain-finder.py example.com

# https://github.com/SmoZy92/Shodomain
python shodomain.py <SHODAN-API-KEY> example.com

# https://github.com/Cgboal/SonarSearch
crobat -s example.com
```

### Active DNS resolution <a href="#active-dns-resolution" id="active-dns-resolution"></a>

```bash
# Generate custom resolvers list, always
# https://github.com/vortexau/dnsvalidator
dnsvalidator -tL https://public-dns.info/nameservers.txt -threads 200

# https://github.com/d3mondev/puredns
puredns resolve subdomains.txt -r ~/Tools/resolvers.txt

## BF
# https://github.com/d3mondev/puredns
puredns bruteforce ~/Tools/subdomains.txt united.com -r ~/Tools/resolvers.txt

# https://github.com/projectdiscovery/shuffledns
shuffledns -d example.com -list example-subdomains.txt -r resolvers.txt
```

### Alterations and permutations <a href="#alterations-and-permutations" id="alterations-and-permutations"></a>

```bash
#https://github.com/Josue87/gotator
gotator -sub subdomains/subdomains.txt -perm permutations_list.txt -depth 1 -numbers 10 -mindup -adv -md
```

### Crawling <a href="#crawling" id="crawling"></a>

```bash
# 1st resolve subdomains on valid websites
# https://github.com/projectdiscovery/httpx
cat subdomains.txt | httpx -follow-host-redirects -random-agent -status-code -silent -retries 2 -title -web-server -tech-detect -location -o webs_info.txt
# Clean output
cat webs_info.txt | cut -d ' ' -f1 | grep ".domain.com" | sort -u > websites.txt
# Crawl them
# https://github.com/jaeles-project/gospider
gospider -S websites.txt --js -t 20 -d 2 --sitemap --robots -w -r > urls.txt
# Clean output
# https://github.com/tomnomnom/unfurl
cat urls.txt | sed '/^.\{2048\}./d' | grep -Eo 'https?://[^ ]+' | sed 's/]$//' | unfurl -u domains | grep ".domain.com"
```

### DNS records <a href="#dns-records" id="dns-records"></a>

```bash
# https://github.com/projectdiscovery/dnsx
dnsx -retry 3 -a -aaaa -cname -ns -ptr -mx -soa -resp -silent -l subdomains.txt
```

### DNS wordlists <a href="#dns-wordlists" id="dns-wordlists"></a>

```bash
# https://gist.githubusercontent.com/six2dez/a307a04a222fab5a57466c51e1569acf/raw
# https://wordlists-cdn.assetnote.io/data/manual/best-dns-wordlist.txt
# https://gist.github.com/jhaddix/f64c97d0863a78454e44c2f7119c2a6a
```

### Other techniques <a href="#other-techniques" id="other-techniques"></a>

#### Google Analytics ID <a href="#google-analytics-id" id="google-analytics-id"></a>

```bash
# https://github.com/Josue87/AnalyticsRelationships
cat subdomains.txt | analyticsrelationships
```

#### Subdomain discovery with Burp <a href="#subdomain-discovery-with-burp" id="subdomain-discovery-with-burp"></a>

Navigate through target main website with Burp:

* Without passive scanner
* Set forms auto submit
* Scope in advanced, any protocol and one keyword ("tesla")
* Last step, select all sitemap, Engagement Tools -> Analyze target
