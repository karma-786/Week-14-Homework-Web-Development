## Week 14 Homework: Web Development

### Overview

In this homework, we will review the many of the concepts and tools covered in the Web Development unit. If needed, refer to the  reference sheets provided to you.

* [HTTP Reference Sheet](./HTTP_Reference.md)
* [curl Reference Sheet](./cURL_Reference.md)

---

### Questions 

Before you work through the questions below, please create a new file and record your answers there. This will be your homework deliverable.

#### HTTP Requests and Responses

Answer the following questions about the HTTP request and response process.

1. What type of architecture does the HTTP request and response process occur in?  

    * **_Client-Server Architecture, which takes part in OSI layer 7 (the application layer)._**  
    
2. What are the different parts of an HTTP request? 
    
    * **_`The Request Line:` is the very first line in an HTTP request. The combination of three parts forms it-_**
        * The HTTP method used
        * The request URI
        * The HTTP protocol version
            * Example:   
               ````
               GET /hello.html HTTP/1.1
               User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
               Host: www.example.com
               Accept-Language: en-us
               Accept-Encoding: gzip, deflate
               Connection: Keep-Alive
               ````
    
    * **_`The Request Header:` is an `HTTP header` that can be used in an HTTP request to provide information about the request context, so that the server can tailor the response._**
        * Example: from above
           ````
           Accept-Language: en-us
           Accept-Encoding: gzip, deflate
           Connection: Keep-Alive
           ````
    
    * **_`The Request Body:` is data sent by the client to your API. A response body is the data your API sends to the client._**
        * Example: Request Body (HTML)
           ````
           Hello World!
           ````  
           
3. Which part of an HTTP request is optional?
    
    * **_`The Request Body` is optional_**  

4. What are the three parts of an HTTP response?
    
    * **_Status Line - describing the message_**  
    * **_Header - containing attributes_**  
    * **_Body, optional - containing data_**    
        * An Example of HTTP Response:  
           ````
           HTTP/1.1 200 OK
           Date: Mon, 27 Jul 2009 12:28:53 GMT
           Server: Apache/2.2.14 (Win32)
           Last-Modified: Wed, 22 Jul 2009 19:15:56 GMT
           Content-Length: 88
           Content-Type: text/html
           Connection: Closed
           ````  
    
          ![Three parts of an HTTP message](/Images/httpatomoreillycomsourceoreillyimages96872.png)  
          
5. Which number class of status codes represents errors?  
    
    * **_400 codes indicate client errors_**  -- [400 Client Error Codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#4xx_client_errors)
    
    * **_500 codes indicate server errors_**  -- [500 Server Error Codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#5xx_server_errors)  

6. What are the two most common request `methods` that a security professional will encounter?  
    
    * **_`GET` and `POST`._**  
        * **_`GET` method requests ask for data from a server to retrieve data._**
        * **_`POST` method requests send data to a specified resource._**  
    
    * There are several other that are used:
        * `HEAD`
        * `PUT`
        * `DELETE`
        * `CONNECT`
        * `OPTIONS`
        * `TRACE`
        * `PATCH`  

7. Which type of HTTP request method is used for sending data?  
    
    * **_`POST` is used to send data to a server to create/update a resource._**  

8. Which part of an HTTP request contains the data being sent to the server?  
    
    * **_The Request Body_** `POST` request sends data to the server.  

9. In which part of an HTTP response does the browser receive the web code to generate and style a web page?  
    
    * **_The Response Body_** Data received along with the response.

#### Using curl

Answer the following questions about `curl`:

10. What are the advantages of using `curl` over the browser?
    
    * **_`curl` is a free command line tool with many advantages_**
        * authentication
        * HTTP post
        * SSL connections
        * proxy support
        * FTP uploads
        * Saving URL to file
        * Downloading  

11. Which `curl` option is used to change the request method?  
    
    * The options can be **_using the `-X` or `--request` command-line options_**

12. Which `curl` option is used to set request headers?  
    
    * **_`-H`, `--header`_**  

13. Which `curl` option is used to view the response header?  
    
    * **_`-i`, `--include`_**

14. Which request method might an attacker use to figure out which HTTP requests an HTTP server will accept?  
    
    * **_`GET` request because attacker could requests data from a server to figure out which HTTP requests that an HTTP server server will accept._**
    * **_`Options` is another request method that the attacker might figure out since it lists out the communication options for target resource._**  

#### Sessions and Cookies

Recall that HTTP servers need to be able to recognize clients from one another. They do this through sessions and cookies.

Answer the following questions about sessions and cookies:

15. Which response header sends a cookie to the client?  

    ```HTTP
    HTTP/1.1 200 OK
    Content-type: text/html
    Set-Cookie: cart=Bob
    ```  
    
    * **_The `set-cookie` sends the `cookie` to the client, which the cookie sent in `cart=Bob`._**

16. Which request header will continue the client's session?

    ```HTTP
    GET /cart HTTP/1.1
    Host: www.example.org
    Cookie: cart=Bob
    ```  
    
    * **_The `cookie` will continue the client's session._**  

#### Example HTTP Requests and Responses

Look through the following example HTTP request and response and answer the following questions:

**HTTP Request**

```HTTP
POST /login.php HTTP/1.1
Host: example.com
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Content-Type: application/x-www-form-urlencoded
Content-Length: 34
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.132 Mobile Safari/537.36

username=Barbara&password=password
```

17. What is the request method?
    
    * **_`POST`_**  

18. Which header expresses the client's preference for an encrypted response?  
    
    * **_`Upgrade-Insecure-Requests: 1`_**  

19. Does the request have a user session associated with it?  
    
    * **_No the Session is not restablished yet_**

20. What kind of data is being sent from this request body?  
    
    * Login credential was sent.
    ```
    username=Barbara
    password=password
    ```  

**HTTP Response**

```HTTP
HTTP/1.1 200 OK
Date: Mon, 16 Mar 2020 17:05:43 GMT
Last-Modified: Sat, 01 Feb 2020 00:00:00 GMT
Content-Encoding: gzip
Expires: Fri, 01 May 2020 00:00:00 GMT
Server: Apache
Set-Cookie: SessionID=5
Content-Type: text/html; charset=UTF-8
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type: NoSniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

[page content]
```

21. What is the response status code?  
    
    * **_`200`_**

22. What web server is handling this HTTP response?  
    
    * **_`Apache webserver`_**

23. Does this response have a user session associated to it?  
    
    * **_Yes, `Set-Cookie: SessionID=5`_**

24. What kind of content is likely to be in the [page content] response body?  
    
    * **_The code to the website, as seen in `Content-Type: text/html_` (Text / HTML - Detail of the page configuration)**

25. If your class covered security headers, what security request headers have been included?  
    
    * **_HTTP Strict Transport Security (HSTS) - `Strict-Transport-Security:` max-age=31536000; includeSubDomains_**
    * **_X-Content-Type-Options HTTP - `X-Content-Type:` NoSniff_**  
    * **_X-Frame-Options HTTP - `X-Frame-Options:` DENY_**  
    * **_Cross Site Scripting Protection (X-XSS) - `X-XSS-Protection:` 1; mode=block_**


#### Monoliths and Microservices

Answer the following questions about monoliths and microservices:

26. What are the individual components of microservices called?  
    
    * There are 8 core components of microservices, they are called **_`Services`_**:   
        1 **_Clients_** 
        2. **_Identity Providers_** 
        3. **_API Gateway_** 
        4. **_Messaging Formats_** 
        5. **_Databases_** 
        6. **_Static Content_** 
        7. **_Management_** 
        8. **_Service Discovery_**
        ![OptiSol Business Solutions](/Images/Microservice-architecture-766x370.png "8 Core Components of Microservice Architecture")  

27. What is a service that writes to a database and communicates to other services?  
    
    * **_`API`: Application Programming Interface_** 

28. What type of underlying technology allows for microservices to become scalable and have redundancy?  
    
    * **_Cointainers allow microservices to be scalable and redundant, along with Load Balancer_** 

#### Deploying and Testing a Container Set

Answer the following questions about multi-container deployment:

29. What tool can be used to deploy multiple containers at once?  
    
    * **_`Docker Compose` is a tool to deploy multiple containers_**  
        `docker-compose up` to bring up the multiple containers.
        `docker-compose down` to bring down the multiple containers.

30. What kind of file format is required for us to deploy a container set?  
    
    * **_`YAML` file_**  

#### Databases

31. Which type of SQL query would we use to see all of the information within a table called `customers`?  
    
    * **_SELECT statements_** 
        * Example:
          `SELECT * FROM Customers WHERE Last_Name='Smith';`  

32. Which type of SQL query would we use to enter new data into a table? (You don't need a full query, just the first part of the statement.)  
    
    * **_INSERT INTO_**
        * Example:
          `INSERT INTO Customers (field1, field 2, ...) VALUES ('a', 'b', ...);`  

33. Why would we never run `DELETE FROM <table-name>;` by itself?  
    
    * **_It deletes the entire table since it does not have the `where` clause._**  

---

### Bonus Challenge Overview: The Cookie Jar

For this challenge, you'll once again be using `curl`, but this time to manage and swap sessions.

:warning: **Heads Up**: You'll need to have WordPress set up from the Swapping Sessions activity from Day 1 of this unit. If you have not done it or it is improperly set up, please refer to the Day 1 student guide and the Swapping Sessions activity file.

If you recall, on Day 1 of this unit you used Google Chrome's Cookie-Editor extension to swap sessions and cookies. For this homework challenge, we'll be using the command-line tool `curl` to practice swapping cookie and sessions within the WordPress app.

It is important for cybersecurity professionals to know how to manage cookies with `curl`:

- Web application security engineers need to regularly ensure cookies are both functional and safe from tampering.

  - For example, you might need to request a cookie from a webpage and then test various HTTP responses using that cookie. Doing this over and over through the browser is tedious, but can be automated with scripts.

- The same concept applies for penetration testers and hackers: `curl` is used to quickly save a cookie in order to test various exploits.

  - For example, an HTTP server may be configured so that, in order to POST data to specific pages, clients need to have cookies or authentication information set in their request headers, which the server will verify.

#### Revisiting curl

Recall that you used `curl` to craft different kinds of requests for your `curl` activity, and that you saw how to use the Chrome extension Cookie-Editor to export and import cookies and swap sessions.

There will be many systems in which you will need to test requests and cookies that will not connect to a browser or browser extension. 

`curl` not only allows users to look through headers, send data, and authenticate to servers, but also to save and send cookies through two `curl` options: `--cookie-jar` and `--cookie`.

These two options work exactly like Cookie-Editor, but on the command line. 

- `--cookie-jar` allows a curl user to save the cookies set within a response header into a text file.

- `--cookie` allows a user to specify a text file where a cookie is saved, in order to send a request with the cookies embedded in the request header.

Let's look at how we can create a `curl` command that will log into a web page with a supplied username and password, and also save the server's response that should contain a cookie.

#### Logging In and Saving Cookies with Curl

If we want to use the `curl` command to log into an account, `Amanda`, with the password `password`, we use the following `curl` options:

- `curl --cookie-jar ./amandacookies.txt --form "log=Amanda" --form "pwd=password" http://localhost:8080/wp-login.php --verbose`
- `curl`: The tool that we are using.
  
- `--cookie-jar`: Specifies where we will save the cookies.
  
- `./amandacookies.txt`: Location and file where the cookies will be saved.
  
- `--form`: Lets us pick the login username and password forms that we set in our user info earlier. In this case it's our username.
  
- `log=Amanda`: How WordPress understands and accepts usernames.
  
- `--form`: Lets us pick the login username and password forms that we set in our user info earlier. In this case it's our password.
  
- `pwd=password`: How WordPress understands and accepts passwords.
  
- `http://localhost:8080/wp-login.php`: Our WordPress login page.
  
- `--verbose`: Outputs more specific description about the actions the command is taking.  

Run the command:  `curl --cookie-jar ./amandacookies.txt --form "log=Amanda" --form "pwd=password" http://localhost:8080/wp-login.php --verbose`

If the site confirms our credentials, it will give us a cookie in return, which `curl` will save in the cookie jar file `./amandacookies.txt`.

Now let's look at how to use that saved cookie on a page that requires us to be logged in.

#### Using a Saved Cookie

To use a saved cookie, we use the following `curl` syntax:

- `curl --cookie ./amandacookies.txt http://localhost:8080/wp-admin/users.php`
  - `curl`: The tool that we are using.
    
  - `--cookie`: Precedes the location of our saved cookie that we want to use.
    
  - `./amandacookies.txt`: Location and file where the cookies are saved.
    
  - `http://localhost:8080/wp-admin/users.php`: A page that requires authentication to see properly. Note that we are not going to the login page, because supplying a cookie in this instance assumes that we are already logged in.

Now that we know how to use the `curl` cookie jar, let's look at what we need to do for this challenge.

---

### Bonus Challenge Instructions: The Cookie Jar

First, using Docker Compose, navigate to the Day 1 WordPress activity directory and bring up the container set:

- `/home/sysadmin/Documents/docker_files`

Using `curl`, you will do the following for the Ryan user:

  - Log into WordPress and save the user's cookies to a cookie jar.

  - Test a WordPress page by using a cookie from the cookie jar.

  - Pipe the output from the cookie with `grep` to check for authenticated page access.

  - Attempt to access a privileged WordPress admin page.

#### Step 1: Set Up

Create two new users: Amanda and Ryan.   

1. Navigate to `localhost:8080/wp-admin/`

2. On the left-hand toolbar, hover over **Users** and click **Add New**.

3. Enter the following information to create the new user named Amanda.

    - Username: `Amanda`
    - Email: `amanda@email.com`

4. Skip down to password:

    - Password: `password`
    - Confirm Password: Check the box to confirm use of weak password.
    - Role: `Administrator`

5. Create another user named Ryan.

    - Username: `Ryan`
    - Email: `ryan@email.com`

6. Skip down to password:

    - Password: `123456`
    - Confirm Password: Check the box to confirm use of weak password.
    - Role: `Editor`

7. Log out and log in with the following credentials:

    - Username: `Amanda`
    - Password: `password`

#### Step 2: Baselining

For these "baselining" steps, you'll want to log into two different types of accounts to see how the WordPress site looks at the `localhost:8080/wp-admin/users.php` page.  We want to see how the Users page looks from the perspective of an administrator, vs. a regular user.

1. Using your browser, log into your WordPress site as your sysadmin account and navigate to `localhost:8080/wp-admin/users.php`, where we previously created the user Ryan. Examine this page briefly. Log out.

2. Using your browser, log into your Ryan account and attempt to navigate to `localhost:8080/wp-admin/index.php`. Note the wording on your Dashboard.

3. Attempt to navigate to `localhost:8080/wp-admin/users.php`. Note what you see now.

Log out in the browser.

#### Step 3: Using Forms and a Cookie Jar

Navigate to `~/Documents` in a terminal to save your cookies.

1. Construct a `curl` request that enters two forms: `"log={username}"` and `"pwd={password}"` and goes to `http://localhost:8080/wp-login.php`. Enter Ryan's credentials where there are placeholders.

    - **Question:** Did you see any obvious confirmation of a login? (Y/N)

2. Construct the same `curl` request, but this time add the option and path to save your cookie: `--cookie-jar ./ryancookies.txt`. This option tells `curl` to save the cookies to the `ryancookies.txt` text file.

3. Read the contents of the `ryancookies.txt` file.

   - **Question:** How many items exist in this file?

Note that each one of these is a cookie that was granted to Ryan after logging in.

#### Step 4: Log in Using Cookies

1. Craft a new `curl` command that now uses the `--cookie` option, followed by the path to your cookies file. For the URL, use `http://localhost:8080/wp-admin/index.php`.

   - **Question:** Is it obvious that we can access the Dashboard? (Y/N)

2. Press the up arrow on your keyboard to run the same command, but this time, pipe `| grep Dashboard` to the end of your command to return all instances of the word `Dashboard` on the page.

    - **Question:**  Look through the output where `Dashboard` is highlighted. Does any of the wording on this page seem familiar? (Y/N) If so, you should be successfully logged in to your Editor's dashboard.

#### Step 5: Test the Users.php Page

1. Finally, write a `curl` command using the same `--cookie ryancookies.txt` option, but attempt to access `http://localhost:8080/wp-admin/users.php`.

    - **Question:** What happens this time?

---

### References

- Gunjan Kaushik: [What is HTTP Request?](https://www.toolsqa.com/client-server/http-request/), April 10, 2021 on ToolQA  
- 2005-2021 Mozilla and individual contributors: [Search results for: HTTP](https://developer.mozilla.org/en-US/search?q=HTTP) MDN Web Docs.
- Error Codes: [List of HTTP status codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes# "List of HTTP status codes") Wikipedia, the free encyclopedia, Last edited on June 15, 2021, at 23:48 (UTC).  
-  OWASP, Open Web Application Security Project: [Test HTTP Methods](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/02-Configuration_and_Deployment_Management_Testing/06-Test_HTTP_Methods)  
- [HTTP Request Methods](https://www.w3schools.com/tags/ref_httpmethods.asp), On W3Schools  
- Burak Guzel: [HTTP Headers for Dummies](https://code.tutsplus.com/tutorials/http-headers-for-dummies--net-8039), On ENVATO TUTS+ May 12, 2021  
- Goran Aviani: [An introduction to HTTP: everything you need to know](https://www.freecodecamp.org/news/http-and-everything-you-need-to-know-about-it/), On freeCodeCamp SEPTEMBER 11, 2019 / #PROGRAMMING
- WEB HOSTING: [What is curl?](https://blog.pair.com/2018/01/26/curl-description-basic-use-cases/ "What is curl?"), On Pair, January 26, 2018
- Bagder: [Modify the HTTP request](https://everything.curl.dev/http/requests), On Everything curl, Last updated 3 months ago
- Michael Kerrisk, author of The Linux Programming Interface, maintainer of the Linux man-pages project.: [Curl Manual](https://man7.org/linux/man-pages/man1/curl.1.html), curl(1) - Linux manual page - HTML rendering created June 20, 2021 - Hosting by [jambit GmbH.](https://www.jambit.com/index_en.html)
- [HTTP request smuggling](https://portswigger.net/web-security/request-smuggling), On PortSwigger  
- Authored by Ziyahan Albeniz, Reviewed by Sven Morgenroth, Translated by Umran Yildirimkaya: [HTTP Security Headers and How They Work](https://www.netsparker.com/whitepaper-http-security-headers/), On Netsparker by Invicti (White Paper)  
- Jay Thakkar: [HTTP Security Headers: 5 Headers You Must Implement on Your Site](https://www.thesslstore.com/blog/http-security-headers/), On The SSL Store, April 2, 2018  
- [8 Core Components of Microservice Architecture](https://www.optisolbusiness.com/insight/8-core-components-of-microservice-architecture), On OptiSol Business Solutions, August 3, 2020  
- [Use Docker Compose to deploy multiple containers](https://docs.microsoft.com/en-us/azure/cognitive-services/containers/docker-compose-recipe), From Microsoft October 29, 2020  
- Tony Bradley: [The challenges of scaling microservices](https://techbeacon.com/app-dev-testing/challenges-scaling-microservices), On TechBeacon  
- Document ahux in the Knowledge Base.: [SQL example statements for retrieving data from a table](https://kb.iu.edu/d/ahux), On UITS Last modified on March 13, 2020 @ 15:36:50.  
- ADRIENNE WATT & NELSON ENG: [Chapter 16 SQL Data Manipulation Language](https://opentextbc.ca/dbdesign01/chapter/chapter-sql-dml/), On Pressbooks - Database Design - 2nd Edition  
- [SQL DELETE Statement](https://365datascience.com/tutorials/sql-tutorials/sql-delete-statement), From 365 Data Science  

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.  

---
:sunglasses: `Ketan Vithal Patel` :sunglasses:
==============================================
### `June 28, 2021 -- UofT Cybersecurity - Boot Camp`
#### :rose::rose:`Jai Shri Swaminarayan`:rose::rose:
