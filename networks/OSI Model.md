- Why we need communication model?
  1- Agnostic applications: without a standard model, your application must have knowledge of the underlying network medium.
  2- Network equipment management: without a standard model, upgrading network equipment becomes difficult.
  3- Decoupled innovation: innovations can be done in each layer separately without affecting the rest of the models.
- 7 layers of OSI model each describe a networking component.    
    layer 7- Application- HTTP/FTP/GRPC - 
    layer 6- Presentation- Encoding, Serialization
    layer 5- Session- Connection establishment, TLS
    layer 4- Transport- UDP/TCP  
    layer 3- Network- IP
    layer 2- Data link- Frames, Mac address Ethernet
    layer 1- Physical- Electric signals, WIFI or radio waves
- TCP/IP model
   - much simpler than OSI just 4 layers
   - 4 layers:
      - Application (layer 5,6 and 7)
      - Transport (layer 4)
      - Internet (layer 3)
      - Data Link (layer 2)
      - 