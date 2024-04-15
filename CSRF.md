<h1>CSRF Attacks</h1>
<br>

**Session Management:-**
<br><br>
Every time you login into a page, it sets a cookie based on your information. That cookie will be what the website will use to indentify you in the future. 

**CSRF:-**
<br>
<br>
This is an attack where the attacker uses an already logged in victim to carry out some attack for them.<br><br>
For example, the attacker might send some malicious link to the victim which when clicked, will lead to, say, the victim's details being changed. Browsers by default send cookies with the request to the backend. In this case, the backend will recieve the request and the victim's cookie. This will make the backend think that, in this example, the victim is asking to change some of their details and do it while all that the victim did was click on a link. This could also be done by going to a malicious website that runs something in the background to similar effect.<br><br>

>Question: How is the website running something in background and sending request to another website?

**Requirements for a CSRF attack:-**
- There should be some functionality that can be exploited
- The session handling must be cookie based
- No unpredictable request parameter (example CSRF token)

**Identifying CSRF:-**
- Blackbox:-
    - Map the application
        - review all the key functionality in the website
    - Find all functions that satisfy the requirements mentioned above
    - Use a proof of concept script to confirm whether it is actually vulnerable because there might be unconventional protection against CSRF (usually inadequate). 
        - GET request: using \<img> tag and putting malicious link in the src
        - POST request: form with hidden fields for all the required parameters and the target set to vulnerable URL

>Question: What are these paramets and hidden fields mentioned above? How are they used? Need better understanding.

- Whitebox:- 
    - Find out the framework the application is running on.
    - Find how this framework defends against CSRF.
    - Review code to ensure built in defenses have not been disabled.
    - Look at custom functionality to see if the defense against CSRF has been properly applied.