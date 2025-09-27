#### detecting sql injection vulnerabilties
- using quote char `'` and observe the error.
- boolean conditions `OR 1=1` and `OR 1=2`, observe the reponse.
- __SQL__ specific syntax that evaluates to the base value of the entry point, and to a different value, and look for systematic differences in the application responses.
- using time delay payloads and observe the differences in the time taken to respond.
- OAST payloads designed to trigger and out-of-bound network interaction when executed within a __SQL__ query, and monitor any resulting interactions.
#### blind sql injection
- blind __SQL__ injection is a blind vulnerability. 
- this means that the application does not return the results of the __SQL__ query or the details of the database errors within its response.
- more complicated and difficult to preform.
- ##### techniques to exploit blind sql injection vuln
	1. change the logic of the query to trigger a detectable difference in the application's response depending on the truth of the single condition.
		- this involves injecting a new condition and observing the working of the application to detect the difference in the appliction response.
	2. conditionaly trigger a time delay in the processing fo the query
		- this enables you to infer the truth of the condition based on the time that the app takes to respond. 
	3. trigger an out-of-band network interaction, using OAST techniques.
		- when using OAST techniques the query process in the application but will not show a visible difference but will interact with the external server ( out-of-band ) that the attacker controlles and thus the attacker knows that the blind __SQL__ injection is successful.
#### second order sql injection
- first order __SQL__ injection occurs when the application processes user input from an HTTP request and incorporates the input into a __SQL__ query in an unsafe way.
- second order __SQL__ injection occurs when the application takes the user input from an HTTP request and stores for future use ( usually done by placing the user input to a database ), but no vulnerability occurs at the point where the data is stored. Later, when data handling a different HTTP request, the application retrieves the stored data and incorporates it into a __SQL__ query in an unsafe way.
	- __second order SQL injection is also known as STORED SQL injection
	