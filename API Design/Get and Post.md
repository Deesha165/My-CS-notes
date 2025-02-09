1- Get
  - Data sent is limited
  - Less secure as data can be exposed at URL bar
  - It is idempotent
  - Faster than post
2- Post
 - Large amount of data can be sent because data is sent in body
 - More secure as data is sent in body
 - It is not idempotent
 - slower and less effiecient
 -Follow RESTful conventions:
- Use **GET** for safe, idempotent, read-only operations.
- Use **POST** for operations that change the server state or require data in the request body.
- when to use Get?
  1- Read only operations
  2- Caching
  3- URLs that need to be bookmarked
- when to use Post?
  1- Data submission
  2- Sensitive data
  3- Non idempotent actions
### **Can We Use Them Interchangeably?**

While it’s technically possible to send similar requests using either method, doing so can violate semantic conventions and lead to unintended consequences:

- **Using GET for Non-Read Operations**:
    
    - Insecure for sensitive data.
    - Can result in unintentional actions if users bookmark or share URLs.
- **Using POST for Read Operations**:
    
    - Prevents caching, bookmarking, and efficient use of GET semantics.