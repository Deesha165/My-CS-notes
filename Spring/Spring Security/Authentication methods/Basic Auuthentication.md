- it is stateless auth method where server doesn't maintain user authentication state
- each time client must pass username and pass with every request 
- these credentials are encoded using base 64 (not encrypted) making it insecure over HTTP
- why we pass credentials as autherization header?
  1- follows HTTP standards
   2- secure as headers has little ability of exposure at debugging 
    3-  consistency as this way is valid regardless the HTTP method
- what is disadvantages of Basic authentication?
  1. Credentials sent in every request, if HTTPS is not enforced, then it can be intercepted and then decoded. 

2. If Credentials are compromised, then only way is to change the credentials. 
    
3. Not suitable for large scale application, as sending credentials with every request is an extra overhead. 
    
    1. As request size increases because of authorization header. 
        
    2. Extra work like decoding, hashing of incoming password, fetching username and password from DB, comparing etc.. 
        
    3. DB lookup to fetch user details which increase latency too. 
![[Pasted image 20250503160715.png]]