- **SSO (Single Sign-On)** is an **authentication process** that allows a user to **log in once** and gain access to **multiple applications or systems** without being asked to log in again for each of them.
- what is JWT?
   - It’s a Stateless Authentication method. 
    
    - Stateless authentication means, server do not maintain the user authentication state (aka Session).  
        
-  JWT has 3 parts 
    
    - HEADER.PAYLOAD.SIGNATURE
- - Header: Metadata about the token, including the algorithm used (HMAC, RSA etc.)  
    
- Payload: Contains claims (user details like userId, role, expiry time)  
    
- Signature: Ensures token integrity (prevents tampering).                     Any change in payload like role from "user" to "admin" recalculated signature will not match the original.
- ![[Pasted image 20250503161200.png]]