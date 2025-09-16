__CPT ASSIGNMENT : find minimum 3 vulnerabilities between p1 and p3 severity and make a VAPT report__

#### 1. https://www.hcghospitals.in/

__first bug found in www.hcghospitals.in__

1. xss vulnerability was found in the search function of the site
	- `<image/src/onerror=alert(8)> ` this way the payload that executed
	- testing other payloads to exploit the vulnerability

#### 2. https://www.arturia.com/

1. __information exposure__
	- this site exposes __compose.json__, __package-lock.json__, __composer.lock__ files in the url
	- `https://www.arturia.com/composer.json`
		- medium to high 
		- PII
		- Exposure of exact dependency versions + commit references
		- Exposure of dev branch dependencies
	- `https://www.arturia.com/package-lock.json`
	- `https://www.arturia.com/composer.lock` 
		- medium to high
		- Exposure of exact dependencies and versions, including unstable branches (`dev-master`, `dev-main`).
		- Potential exposure to known CVEs in outdated or unstable dependencies.
#### 3. https://www.arturia.com/

1. **missing critical security flags**
	- this site has missing security flags for **Httponly**
	- ![[2025-08-14-132017_1920x1080_scrot.png]]