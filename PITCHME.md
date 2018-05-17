# Simple Social Network

Note:
First we'll go through what it is.
Then we'll go through what it's made with and how it works.

---

## What is it?
Note:
A social network for small groups of friends to plan events, or form groups.
Ideally used as a way for friends to meet up with eachother in real life.

+++
### Users + Groups + Events + Messages
That's it.
Note:
- These four entities interact in multiple ways to allow users to communicate.
- Events are just groups with a start and end time.

+++
### Security and Privacy?
Note:
- Passwords are salted and hashed
- HTTPS enabled
- CSRF secure
- In the future: All communications encrypted between participants. Nothing to read in the database.

---
## Created using:
##### NodeJS  |  Heroku 
##### PostgreSQL  |  ExpressJS 

---
## NodeJS
A server-side JavaScript runtime environment.
Note:
- Has access to the file system and other system functions much like any other programming language.

+++
### Server
``` javascript
var http = require('http');

http.createServer(function (request, response) {
    response.writeHead(200, {'Content-Type': 'text/plain'});
    response.end('Hello World\n');
}).listen(8080);
```
Note:
- HTTP server is built right into node. Can start it in a few lines..

+++
### Node Package Manager
### (NPM)
Note:
- NPM allows you to isolate all requirements to the project folder. Allows easy passing of dependencies to other systems with package.json

+++

``` json
{
  "name": "my_package",
  "description": "A fake project",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "https://github.com/Bob/my_package.git"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "homepage": "https://github.com/ashleygwilliams/my_package"
}
```

---
## Heroku
Platform as a service (PaaS)
Note: 
- Heroku provides the hardware that the http server will run on.
- HTTPS is provided by default with Lets Encrypt. You don't need to do anything.
- Cheap.

+++
As simple as
``` console
git push heroku master
```
Note:

- It forces you to use version control. You push your git repo to Heroku to 'start the server'

---
## PostgreSQL
Relational Database

+++
### Interfaced with Sequelize
No SQL. Just JavaScript.
Note:
- We interface with the database using the Sequelize node package.
- Sequelize is an ORM.

---
## Express
Unopinionated Node Framework
Note: 
- Express is an unopinionated framework for Node
- Lets you set up a web server and middleware (modifications to requests) easily.

+++
### Middleware
``` javascript
app.use(myMiddleware)
```
Note:
- Middleware is just a function that takes the request  and response, and runs it through code to modify, validate, etc. It then goes on to the next middleware

+++
### Routes
``` javascript
app.get('/', someFunction(req,res))
	.post('/', someOtherFunction(req,res))
```
Note:
- Your endpoints are the functions. 
- Sometimes you'll serve an API
- Othertimes you'll serve a front end view

+++
### Views
``` javascript
var context = { title: 'Hey', message: 'Hello there!' }
app.get('/', function (req, res) {
  res.render('index', context)
})
```
Note:
- Views are rendered in the endpoint functions
- They are passed an object with variables to build the page, like a list of users
- Default is the PUG templating language, but you can use whatever you want. React, vue, etc all work.

+++
### Pug Templates
``` pug
html  
    head
        title This is a pug file!
    body
        header
            p A potential menu
        section
            p Check out all this content!
        footer
            p totally awesome footer
```
Note:
- Can easily use the passed in variables
- Seperate different objects like header, footer, nav
