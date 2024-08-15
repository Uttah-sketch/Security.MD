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

```
## 6 Phases 
* Mission definition 
* Recon 
* Footprinting 
* Explotation & Initial Access
* Post-Explotation 
* Document Mission

### Phase 1 Mission definition 
* Define Goals, scope and RoE
* 

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















```
