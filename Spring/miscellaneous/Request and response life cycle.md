- Request-> Servlet Container(tom cat)-> dispatcher servlet
- Servlet container to intercept HTTP client request and map to spring framework app
- despatcher servlet does following:
   1- Uses Handling Mapping to determine the controller 
   2- Create an instance of controller class and resolve dependences
   3- Invokes controller method 
   4- some work ....
   5- Get response back to servlet dispatcher