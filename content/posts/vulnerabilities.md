---
createdAt: "2026-07-08T16:30:00.000Z"
updatedAt: "2026-07-08T18:30:00.000Z"
Status: "In progress"
Credits and Reference: ""
Dave Prowse: ""
title: "Vulnerabilities"
---

## **Injection Vulnerabilities:**

1.  SQL Injection (SQLi): **SQL injection (SQLi)** is a **web security vulnerability** that allows attackers to manipulate database queries, potentially accessing unauthorized data or modifying content.
2.  Blind SQL Injection: [**Blind SQL injection**](https://owasp.org/www-community/attacks/Blind_SQL_Injection)[ is a ](https://owasp.org/www-community/attacks/Blind_SQL_Injection)[**web security vulnerability**](https://owasp.org/www-community/attacks/Blind_SQL_Injection)[ where an attacker exploits an application vulnerable to SQL injection, but the application’s HTTP responses do not reveal the results of the SQL query or any database errors](https://owasp.org/www-community/attacks/Blind_SQL_Injection).
    1. **Scenario**:
       - The web application accepts user input (e.g., search queries, form fields).
       - The input is used in SQL queries without proper validation or sanitization.
       - If the application is vulnerable, the attacker can manipulate the input to inject malicious SQL code.
    2. **Distinguishing Feature**:
       - Unlike regular SQL injection, where data is directly retrieved from the database, **blind SQL injection** relies on asking the database a series of **true or false questions**.
       - The attacker doesn’t see the actual data; they infer it indirectly.
    3. **Techniques**:
       - **Content-Based Blind SQLi**:
         - The attacker sends queries that return either ‘true’ or ‘false’.
         - Example: Injecting **`1=1`** and **`1=2`** to compare responses.
       - **Time-Based Blind SQLi**:
         - The attacker delays the server’s response by injecting time-consuming operations.
         - Example: Waiting for a delay if a condition is met (e.g., **`WAITFOR DELAY '00:00:10'`**).
    4. **Impact**:
       - Successful blind SQL injection allows attackers to extract sensitive data, bypass authentication, or manipulate application behavior.
       - [Defense involves secure coding practices, automated testing, and vigilant security measures](https://owasp.org/www-community/attacks/Blind_SQL_Injection)
3.  Cross-Site Scripting (XSS): **Cross-site scripting (XSS)** is a **web security vulnerability** that allows attackers to inject **malicious scripts** into web pages viewed by other users. These scripts can compromise the interactions users have with a vulnerable application.
    - **Reflected XSS**: The malicious script comes from the current HTTP request.
    - **Stored XSS**: The malicious script originates from the website’s database.
    - **DOM-based XSS**: The vulnerability exists in client-side code rather than server-side code.
4.  Cross-Site Request Forgery (CSRF): [**Cross-site request forgery (CSRF)**](https://en.wikipedia.org/wiki/Cross-site_request_forgery)[, also known as ](https://en.wikipedia.org/wiki/Cross-site_request_forgery)[**one-click attack**](https://en.wikipedia.org/wiki/Cross-site_request_forgery)[ or ](https://en.wikipedia.org/wiki/Cross-site_request_forgery)[**session riding**](https://en.wikipedia.org/wiki/Cross-site_request_forgery)[, is a ](https://en.wikipedia.org/wiki/Cross-site_request_forgery)[**malicious exploit**](https://en.wikipedia.org/wiki/Cross-site_request_forgery)[ of a website or web application where unauthorized commands are submitted from a user that the web application trusts](https://en.wikipedia.org/wiki/Cross-site_request_forgery).

    1. The attacker tricks a user into performing an action unintentionally.
    2. The action could be changing the user’s email address, password, or making a funds transfer.
    3. Depending on the action, the attacker might gain **full control** over the user’s account.
    4. [If the compromised user has a ](https://portswigger.net/web-security/csrf)[**privileged role**](https://portswigger.net/web-security/csrf)[, the attacker could control all the application’s data and functionality](https://portswigger.net/web-security/csrf).

    To prevent CSRF attacks, developers should:

    - Implement **anti-CSRF tokens** to validate requests.
    - Use **same-site cookies** to restrict cross-origin requests.
    - Ensure that actions requiring user consent (e.g., changing settings) are **protected against CSRF**.

5.  HTML Injection: HTML Injection involves injecting HTML code through vulnerable parts of a website. The attacker’s goal is to change the website’s appearance or manipulate displayed information. The injected data can include simple HTML tags or even entire fake forms or pages.

    - **Appearance Change**: Attackers alter how the website looks.
    - **Identity Theft**: Similar to XSS, attackers can steal user identities.
    - **Stored HTML Injection**: Malicious HTML code saved on the server executes whenever the user interacts with the affected functionality.
    - **Reflected HTML Injection**: Malicious HTML code is reflected back to the user in response to their input.

    **Prevention Strategies**:

        - **Sanitize Input**: Validate and sanitize user input to prevent malicious code injection.
        - **Escape Output**: Properly escape HTML content before rendering it in web pages.
        - **Use Security Libraries**: Leverage security libraries to handle input/output securely.

6.  OS Command Injection: **OS command injection** is a **web security vulnerability** that allows attackers to execute arbitrary commands on the underlying operating system. This occurs when web applications call operating system commands with user-supplied input provided as arguments. [The consequences of OS command injection can be severe, potentially leading to full compromise of the application and its data1](https://portswigger.net/web-security/os-command-injection)[2](https://www.fastly.com/learning/what-is-os-command-injection)[3](https://www.fastly.com/blog/back-to-basics-os-command-injection)[4](https://portswigger.net/burp/documentation/desktop/testing-workflow/input-validation/command-injection)[5](https://owasp.org/www-community/attacks/Command_Injection). Developers should validate and sanitize user input to prevent such vulnerabilities

## Broken Authentication and Session Management:

1.  Session Fixation :
    • A Session fixation attack is an attack that occurs when a malicious user sets up a fake session before the legitimate users are able to log in. This leads to the entire system getting compromised and used to steal sensitive data.
    • A session fixation attack is a type of remote code execution attack which is used to exploit software designed with web-server session management features.

           **Common Causes of Session Fixation Vulnerabilities:**

        1. **Session Management Issues:**
        	- Poor session management practices, such as not generating a new session ID upon authentication or not properly invalidating session IDs after logout, can lead to session fixation vulnerabilities.
        2. **Insecure Session ID Handling:**
        - Lack of randomness or predictability in session ID generation can make it easier for an                         attacker to guess or brute force valid session IDs.

        Remediation for Session Fixation :


           **a. Invalidate Old Session IDs: Invalidate any existing session IDs associated with the user upon successful authentication. This prevents attackers from reusing previously generated session IDs.**


            b. **Implement Cross-Site Request Forgery (CSRF) Protection: Implement CSRF protection mechanisms to prevent attackers from forcing users to authenticate with a fixed session ID using malicious requests.**


             c. **Use Strong Session ID Generation: Generate session IDs using a cryptographically secure random number generator to ensure unpredictability and randomness. Avoid using predictable patterns or algorithms that could be easily guessed by attackers.**


        [Session fixation | OWASP Foundation](https://owasp.org/www-community/attacks/Session_fixation)

1.  Brute Force Attack : A brute force attack is a hacking method that uses trial and error to crack passwords, [login credentials](https://www.fortinet.com/resources/cyberglossary/login-credentials), and encryption keys. It is a simple yet reliable tactic for gaining unauthorized access to individual accounts and organizations’ systems and networks. The hacker tries multiple usernames and passwords, often using a computer to test a wide range of combinations, until they find the correct login information.

1.  Session Hijacking
1.  Password Cracking
1.  Weak Password Storage
1.  Insecure Authentication
1.  Cookie Theft
1.  Credential Reuse

## Sensitive Data Exposure:

1. Inadequate Encryption
2. Insecure Direct Object References (IDOR)
3. Missing Security Headers

## Security Misconfiguration:

1. Default Passwords
2. Directory Listing/ LFI /RFI
3. Open Ports and Services
4. CORS
5. HTTP Security Headers Misconfiguration

They might ask this like owasp 2017 vs 2021 what has changed?

## XML-Related Vulnerabilities:

1. XML External Entity (XXE) Injection

## Broken Access Control:

1. Privilege Escalation
2. Insecure Direct Object References
3. Deserialization

## Insecure Communication:

1. Man-in-the-Middle (MITM) Attack
2. Insufficient Transport Layer Security
3. Insecure SSL/TLS Configuration
4. Insecure Communication Protocols

## Client-Side Vulnerabilities:

1. DOM-based XSS
2. Insecure Cross-Origin Communication
3. Browser Cache Poisoning
4. Clickjacking
5. Server-Side Request Forgery (SSRF)
6. Blind SSRF 37.X-Content-Type-Options Bypass
7. Content Security Policy (CSP) Bypass
8. Race Conditions
9. Price Manipulation

How would you test an ecommerce website? Approach
