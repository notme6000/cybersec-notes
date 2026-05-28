# cybersploit-2

## scoping phase
- To find the ip of the cybersploit-2 that i hosted on the virtualbox localhost i did a arp-scan
    - _ip : 192.168.1.2_

## recon
- After finding the ip of cybersploit-2 next i did an nmap scan to find the ports and services in the machine with a full port scan for making sure that there are no hidden ports.
    - `nmap -A -T5 -p- 192.168.1.2`
    - There was no hidden port in cybersploit-2.
    - There was 2 port open they were
        - 22 ssh OpenSSH 8.0 (open)
        - 80 http Apache httpd 2.4.37 (open)
- So we got the port 80 http that means we can try to go for the web.
- In the web interface we get a table with name, username and password of some hackers.
- In the frontend source code we get a keyword "ROT47", that is a cipher name.

## enumeration
- After getting the webinterface i did a dir-enumeration to find the hidden files and directories.
- no hidden directories of files where found in the enumeration.
- But the table that contained the user, username and password had a "odd" username and user it was written in a cipher so with the earlier hint of "ROT47" i decypherd it and got the user and username. 
    - user : shailendra 
    - username : cybersploit1
- with the info i have
    - ip : 192.168.1.2    
    - username : cybersploit1
    - password : @twitter
    - `ssh cybersploit1@192.168.1.2`
    - `password : @twitter`
- i tried to ssh login with this details but the password was wrong.
- so i tried to try the username as the password and the user as username and it worked
    - `ssh shailendra@192.168.1.2`
    - `password : cybersploit1`
    - this is the correct credentials. 

## initial access
- using the ssh i got the initial access.
- there was a file named _hint.txt_ 
- the file contained the word _docker_
- the user is not in the sudoers file so we can't use sudo.
- next we have to find a way to escalate our privilege with docker.
- _docker privilege escalation_
    - I did some research and found that if the local unprivileged user that we using is in the docker group we can gain the root shell.
    - The logic is that when docker is running the docker used the host os kernel and we use this function to mount our root directory "/" to the "/mnt" directory of the docker container and gain access to the root shell.
    - I used the id command to find if we are in the docker group and found that we are in the docker group and docker daemon is running in the root privilege.
        - `id`
    - next I started looking for a running dokcer container but there was none. ( that is not a problem )
        - `docker ps` (no need for sudo here because docker daemon is running on root)
    - after that i used this command to pull a docker image and run it and after running it would mount the root "/" to the "/mnt" of the docker conatiner.
        - `docker run -it --rm -v /:/mnt apline` 
        - after that you will get access to the alpine conatiner shell 
        - from there go to the "/mnt"
            - `cd /mnt`
        - after going to the "/mnt" you will find all the directories in the "/".
        - use chroot command to get the shell.
            - `chroot /mnt sh`
            - use `whoami`
        - I got the root shell.
        - The I moved to the "/root" and found the final flag there.



