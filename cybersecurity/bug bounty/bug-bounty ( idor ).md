### IDOR ( insecure direct object reference )
- IDOR is a type of access control vuln in digital security.
- This can occur when a web application or application programming interface uses a identifier for direct access to an object in an internal database but does not check for access control authentication.
- IDOR is a vulnerability in which we can manipulate the unique id of a request for getting unautherized access to info.

`application -> user account -> assing (userid) -> forgot password -> request to server -> intercept -> change userid -> attacker can receive the link of victim forgot password`

`facebook -> user account -> assign (userid) -> delete id -> request to server -> intercept -> change userid -> attacker can delete the id of victim`


# bug-bounty ( xss - cross site scripting )

### xxs ( cross site scripting )
- It is a type of security vulnerability that can be found in some web apps.XSS attacks enable attackers to inject client-side scripts into web pages viewed by other users.
- cross site scription vulnerability may be used by attackers to bypass access controls such as the same-origin policy.
- similar like html injection, but in this case we are executing js payloads.
- motives : steal cookies, sessions and perform account takeover.
- sample payload `<script>alert(1)</script>`
- most commonly used tags for payloads : `script, img, svg, href`
- example :
	- `<img scr=x onerror=prompt(1)>`
	- `<svg/onload=alert(1)>`
- test (sandbox env) js xss payload : [prompt.ml](https://prompt.ml/0)
- cmp to : 14:12