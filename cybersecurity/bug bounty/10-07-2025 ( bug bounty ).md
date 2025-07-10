- bug bounty cateogories

| level | severity     |
| ----- | ------------ |
| P1    | critical     |
| P2    | hight        |
| P3    | medium       |
| P4    | low          |
| P5    | informaional |
- ### what to study ?
	- internet, http, TCP/IP.
	- networking.
	- command-line.
	- linux.
	- web technologies, java-script, php, java.
		- at leat one programming language like python or java.
	- KNOWLEDGE OF CMS ( content management systems ).
- ### recon
	- shodan.
	- google archive.
	- google hacking databases.
		- google hacking databases has wayback urls that are used for getting old data of sites. 
- ### REQUIREMENT FOR CRACKING JOB IN PENTESTING 
	- WEB,API,ANDORIOD.
	- thick client, ADP, IOS, SAST, DAST, DOCKER, SECURITY, CLOUD,
- ### what is bug bounty ?
	- bug bounty is a freelancing for pentesters.
- ### what to do ?
	- read hackerone report
	- read medium articles
	- revise the course
	- practice more
	- do in real world
- ### the plan (part 1)
	- #### recon 
		- gather information
	- #### filtration
		- filter out the sensitive informaion
		- like api key or other info of the company
	- ### vuln scan
		- perform a vulnerability scanning 
		- manual or automatic
		- use a checklist for scanning ( create your own checklist )
	- ### collect pii informaion
		- collect personal identification information
- ### (part 2)
	- #### perform vulnerability scanning
		- find the vulnerability through scanning
	- #### exploitation
		- exploite the vulnerability
- ### (part 3)
	- #### create poc
		- create a poc 
			- screen shots or screen records for proof
	- #### proffesional report writting
		- write a report

---
- ### recon ( info gathering )
	- ##### find subdomain
		- use `subfinder` or `sublist3r` 
		- now separate the subdomains with http and https protocol
			- use tools like `httprobe` or `httx` 
			- command `cat subdomain.txt | httprobe > live.txt` 
			- `httprobe` is used to find live subdomains
	- ##### dir enumeration
		- directory bruteforcing
			- use `dirsearch`
			- needs to learn status code for request and reponse
				- 2XX 201 202 203 204 ........... ok
				- 3XX 301 302 303 304 ........... redirects
				- 4XX                 ........... error/not found
				- 5XX                 ........... internal error or logs
			- command for dirsearch `dirsearch -u <url>` - the output will be the dir name with status code.
				- list of sensitive files
					1. /.git  ->  P1 bug
					2. /.git/config/
					3. .htaccess 
					4. etc/passwd
					5. composer.json
					6. package.json
					7. composer.lock
					
