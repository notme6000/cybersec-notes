### host header injection attack
- #### host header attack on
	- 2XX 3XX
		- 2XX - 200 201 203 204 205 ( successfull response )
		- 3XX - 300 301 302 303 304 ( redirected to somewhere )
	- use burp (intercept) to change the host of the request if it changes sucessfully the site will be vulnerable to __HOST HEADER INJECTION ATTACK__
	- 