- what is CSRF( cross site request frogery)? 
    -  CSRF is a way to trick browser into making unwanted request to site where the user already authenticated depending on the that the browser automatically append session cookie to that request
    - applicable where state and session are managed
- how to protect from CSRF?
     - by using CSRF token, this ensures that request ligitimate from the original source only , as website oonly append CSRF token in the request , which server can used to validate with the token created at the time of HTTP session creation
 