- Form login authentication
   - it is statefull auth method where server maintains user auth state 
   - so that user doesn't have to provide username/password every time
- user enters credentials using HTML login form
- on successful auth a session is created to maintain user state across different requests
- now with subsequent requests it provides session id and not username/password and server validates it with stored one
- It is default auth method in spring boot security
- what is disadvantages of Form based authentication?
   1. Vulnerable to Security issues like CSRF and Session hijacking : 
Be default, CSRF is enabled for form based login and we should not disable it.
2. Session Management is big overhead and in case of distributed system it can lead to scalability issue. 
    
  3. Database load: if their are multiple servers then we might need to store the session in DB or Cache, which again required memory and lookup time. Which can cause latency issue.
![[Pasted image 20250503160946.png]]![[Pasted image 20250503161029.png]]