0x01. Basic authentication
Back-endAuthentification

By Guillaume, CTO at Holberton School
Weight: 1
Background Context
In this project, you will learn what the authentication process means and implement a Basic Authentication on a simple API.

In the industry, you should not implement your own Basic authentication system and use a module or framework that doing it for you (like in Python-Flask: Flask-HTTPAuth). Here, for the learning purpose, we will walk through each step of this mechanism to understand it by doing.



Resources
Read or watch:

REST API Authentication Mechanisms
Base64 in Python
HTTP header Authorization
Flask
Base64 - concept
Learning Objectives
At the end of this project, you are expected to be able to explain to anyone, without the help of Google:

General
What authentication means
What Base64 is
How to encode a string in Base64
What Basic authentication means
How to send the Authorization header
Requirements
Python Scripts
All your files will be interpreted/compiled on Ubuntu 18.04 LTS using python3 (version 3.7)
All your files should end with a new line
The first line of all your files should be exactly #!/usr/bin/env python3
A README.md file, at the root of the folder of the project, is mandatory
Your code should use the pycodestyle style (version 2.5)
All your files must be executable
The length of your files will be tested using wc
All your modules should have a documentation (python3 -c 'print(__import__("my_module").__doc__)')
All your classes should have a documentation (python3 -c 'print(__import__("my_module").MyClass.__doc__)')
All your functions (inside and outside a class) should have a documentation (python3 -c 'print(__import__("my_module").my_function.__doc__)' and python3 -c 'print(__import__("my_module").MyClass.my_function.__doc__)')
A documentation is not a simple word, it's a real sentence explaining what's the purpose of the module, class or method (the length of it will be verified)
Tasks
0. Simple-basic-API
mandatory

Download and start your project from this archive.zip

In this archive, you will find a simple API with one model: User. Storage of these users is done via a serialization/deserialization in files.

Setup and start server
bob@dylan:~$ pip3 install -r requirements.txt
...
bob@dylan:~$
bob@dylan:~$ API_HOST=0.0.0.0 API_PORT=5000 python3 -m api.v1.app
 * Serving Flask app "app" (lazy loading)
...
bob@dylan:~$

Use the API (in another tab or in your browser)
bob@dylan:~$ curl "http://0.0.0.0:5000/api/v1/status" -vvv
*   Trying 0.0.0.0...
* TCP_NODELAY set
* Connected to 0.0.0.0 (127.0.0.1) port 5000 (#0)
> GET /api/v1/status HTTP/1.1
> Host: 0.0.0.0:5000
> User-Agent: curl/7.54.0
> Accept: */*
>
* HTTP 1.0, assume close after body
< HTTP/1.0 200 OK
< Content-Type: application/json
< Content-Length: 16
< Access-Control-Allow-Origin: *
< Server: Werkzeug/1.0.1 Python/3.7.5
< Date: Mon, 18 May 2020 20:29:21 GMT
<
{"status":"OK"}
* Closing connection 0
bob@dylan:~$

Repo:

GitHub repository: alx-backend-user-data
Directory: 0x01-Basic_authentication
 Done? Help Check your code Get a sandbox

1. Error handler: Unauthorized
mandatory

What the HTTP status code for a request unauthorized? 401 of course!

Edit api/v1/app.py:

Add a new error handler for this status code, the response must be:
a JSON: {"error": "Unauthorized"}
status code 401
you must use jsonify from Flask
For testing this new error handler, add a new endpoint in api/v1/views/index.py:

Route: GET /api/v1/unauthorized
This endpoint must raise a 401 error by using abort - Custom Error Pages
By calling abort(401), the error handler for 401 will be executed.
