- User creation at every time server starts spring security creates user with name "user" and random password stored in inMemoryUserDetailsManager.java
- 
- How can we control the user creation logic?
  1-  Using application.properties       
     (not recommended, only for development and testing)  Internally, it uses reflection and calls  setUserName() and setPassword() method of SecurityProperties.java and overrides the default values.
  2 -  By creating custom InMemoryUserDetailsManager Bean(not recommended, only for development and testing) 
- If, we don't want to store {bcrypt} or any other hashing algo {id} in front of password, then we can define which PasswordEncoder to use. 
Now, since we are always using 1 encoding/hashing algorithm, and control will not goes to "DelegationPasswordEncoder", and it will directly goes to specific Password Encoder, so now no need to put {id} in front of password.
   ![[Pasted image 20250502171905.png]]3 -   Storing UserName and Password (after hashed) in DB (recommended for production)
   
- why we need to implement UserDetails?
   - This is because Spring's internal authentication mechanism (form login, basic auth, JWT, etc.) **only understands `UserDetails` objects** — not your custom `UserEntity` or `UserAuthEntity`. if we don't implement it, then we have to do the mapping (from UserAuthEntity to UserDetails).
- why we need to implement UserDetailsService?
  - Implements UserDetailsService because, for the same reason, during authentication, based on authentication method we are using Basic, jwt, form etc. it will try to load user first, but since we are using DB for storing the username and password, spring security don’t know how to fetch it, so we have to implement UserDetailsService and override the method