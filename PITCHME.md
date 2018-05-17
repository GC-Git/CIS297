# Simple Social Network

Note:
First we'll go through what it is.
Then we'll go through what it's made with and how it works.

--
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
Has access to the file system and other system functions much like any other programming language.

+++
### Server
```
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

---
## Heroku
Platform as a service (PaaS)
Note: 
- Heroku provides the hardware that the http server will run on.
- It forces you to use version control. You push your git repo to Heroku to 'start the server'
- HTTPS is provided by default with Lets Encrypt. You don't need to do anything.
- Cheap.

---
## PostgreSQL
Relational Database
Note:
- We interface with the database using the Sequelize node package.
- Sequelize is an ORM.

---
## Express
Unopinionated Node Framework
Note: 
- Express is an unopinionated framework for Node
- Lets you set up a web server and middleware (modifications to requests) easily.