## Overview

These are APIs that Node.js Express App will export:
```
Methods	Urls	                       Actions
GET     api/tutorials             get all Tutorials
GET     api/tutorials/:id         get Tutorial by id
POST    api/tutorials             add new Tutorial
PUT     api/tutorials/:id         update Tutorial by id
DELETE  api/tutorials/:id         remove Tutorial by id
DELETE  api/tutorials             remove all Tutorials
GET     api/tutorials?title=[kw]  find all Tutorials which title contains 'kw'
```
## Project Structure
```
app
  config
    db.config.js
    auth.config.js
  controllers
    tutorial.controller.js
    auth.controller.js
    user.controller.js
  middleware
    authjwt.js
    index.js
    verifySignUp.js
  models
    index.js
    tutorial.model.js
    role.models.js
    user.models.js
  routes
    tutorial.routes.js
    auth.routes.js
    user.routes.js
node_modules
package-lock.json
package.json
server.js
```
 
- db.config.js exports configuring parameters for MySQL connection & Sequelize.
- Express web server in server.js where we configure CORS, initialize & run Express REST APIs.
- Next, we add configuration for MySQL database in models/index.js, create Sequelize data model in models/tutorial.model.js.
- Tutorial controller in controllers.
- Routes for handling all CRUD operations (including custom finder) in tutorial.routes.js

## Authentication

- User can signup new account, or login with username & password.
- By User’s role (admin, moderator, user), we authorize the User to access resources

These are APIs that we need to provide:
```
Methods   Urls	              Actions
POST     /api/auth/signup    signup new account
POST     /api/auth/signin    login an account
GET      /api/test/all       retrieve public content
GET      /api/test/user      access User’s content
GET      /api/test/mod       access Moderator’s content
GET      /api/test/admin     access Admin’s content
```

## Architecture with Authentication & Authorization

Via Express routes, **HTTP request** that matches a route will be checked by **CORS Middleware** before coming to **Security** layer.

Security layer includes:

- JWT Authentication Middleware: verify SignUp, verify token
- Authorization Middleware: check User’s roles with record in database

**– config**
- configure MySQL database & Sequelize
- configure Auth Key
  
**– routes**
- auth.routes.js: POST signup & signin
- user.routes.js: GET public & protected resources
  
**– middlewares**
- verifySignUp.js: check duplicate Username or Email
- authJwt.js: verify Token, check User roles in database
  
**– controllers**
- auth.controller.js: handle signup & signin actions
- user.controller.js: return public & protected content
  
**– models for Sequelize Models**
- user.model.js
- role.model.js

– server.js: import and initialize necessary modules and routes, listen for connections.



## Run Server
Run with command:
```
node server.js.
```
