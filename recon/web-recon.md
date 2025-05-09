# Web Recon

### WAF Checks

```bash
# https://github.com/EnableSecurity/wafw00f 
wafw00f -i websites.txt

# IP Wafs/CDN lists
https://github.com/MISP/misp-warninglists
```

### CMS

```bash
# https://github.com/Tuhinshubhra/CMSeeK 
tr '\n' ',' < websites.txt > cms_test.txt 
python3 cmseek.py -l cms_test.txt --batch -r
```

### Web screenshot

```bash
# https://github.com/sensepost/gowitness
gowitness file -f websites.txt 
gowitness report serve -D gowitness.sqlite3
```

### Fuzzing

```bash
# https://github.com/ffuf/ffuf
ffuf -mc all -fc 404 -ac -sf -s -w wordlist.txt -u https://www.domain.com/FUZZ
```

### URLs

#### URL extraction

```bash
 # https://github.com/jaeles-project/gospider
 gospider -S websites.txt --js -t 20 -d 2 --sitemap --robots -w -r > urls.txt

 # https://github.com/lc/gau
 cat websites.txt | gau --subs 
 
 # https://github.com/tomnomnom/waybackurls 
 cat websites.txt | waybackurls 
 
 # https://github.com/gwen001/github-endpoints 
 github-endpoints -q -k -d united.com -t tokens_github.txt 
 
 # https://github.com/Josue87/roboxtractor 
 cat webs.txt | roboxtractor -m 1 -wb

 # https://github.com/projectdiscovery/katana
 katana -u target.com -ps -silent -pss waybackarchive,commoncrawl,alienvault -o urls.txt ##Passive mode
 katana -u target.com -duc -silent -nc -jc -kf all -fx -xhr -ef woff,css,png,svg,jpg,woff2,jpeg,gif,svg -aff -o urls.txt ##Crawling and Spidering

 # https://github.com/xnl-h4ck3r/waymore
 waymore -i target.com -mode U -oU urls.txt
```

### Filtering

```bash
# https://github.com/tomnomnom/qsreplace
cat urls.txt | qsreplace -a

# https://github.com/s0md3v/uro 
cat urls.txt | uro
```

Patterns

```bash
# https://github.com/tomnomnom/gf
# https://github.com/1ndianl33t/Gf-Patterns 
gf sqli urls.txt
```

#### JS

```bash
# https://github.com/w9w/JSA 
cat urls.txt | python3 jsa.py 

# https://github.com/lc/subjs 
cat js.txt | subjs | httpx 

# https://github.com/GerbenJavado/LinkFinder 
python3 linkfinder.py -d -i https://domain.com/whatever.js -o cli
```

#### Wordlists generation



```bash
# https://github.com/tomnomnom/unfurl 
cat urls.txt | unfurl -u keys 
cat urls.txt | unfurl -u values
```
