-  Request-> Tomcat Server -> Filter chains (including security filter chain) ->Servlets(including dispatcher servlet)-> Interceptors -> Controller
- ![[Pasted image 20250502172251.png]]
-  Security filter chain include many filters and depending on the authentication method specific filters goes through either form based , JWT or OAuth

![[Pasted image 20250502172138.png]]