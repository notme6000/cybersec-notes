## DC-4 from the DC series. 

### step-by-step walkthrough

#### 1. recon
    1. scanned the ip of the DC-4 machine using nmap aggresive and script scan for finding the running services and any knowing vulnerabilities.
        `nmap -A --scirpt vuln 192.168.1.2`
    
    - got 2 open ports 
        - port 22 ssh 
        - port 80 http with nginx 1.15.10

<------nmap scan image here------>

    2. used fuff to dir enumerate the web-page for finding any hidden dir and only got "css".
        `fuff -u http://192.168.1.2/FUZZ -w <wordlist>`
    3. used fuff one more time to scan for php files
        `fuff -u http://192.168.1.2/FUZZ.php -w <wordlist>`

