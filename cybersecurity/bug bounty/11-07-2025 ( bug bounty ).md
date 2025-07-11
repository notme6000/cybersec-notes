- ### nuclei
	1. first install golang-go using `sudo apt install golang-go`
	2. install nuclei using `go install -v github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest`
	3. the nuclie will be in `/go/bin` move it to `/usr/bin`
	4. we will get a nuclei template after we run `nuclei` command
	5. nuclei enumeration command `nuclei -u <url>`
		1. `nuclei -u <url>`
		2. `nuclei -l <urltextfil.txt> `
		3. `nucle -u <url> -t <template path>`
- ### ds store github
	1. github link `https://github.com/lijiejie/ds_store_exp.git`-
	2. this tools is used to parse _.DS_store_ file and download files recursively.
- ### key hacks
	1. github link `https://github.com/streaak/keyhacks.git`
	2. KeyHacks shows methods to validate different API keys found on a Bug Bounty Program or a pentest.
- ### android pentesting
	- #### bypass ssl pining in android
		- frida and objection server