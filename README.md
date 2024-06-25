## Overview

These are APIs that Node.js Express App will export:
```
Methods	Urls	Actions
GET	api/tutorials	get all Tutorials
GET	api/tutorials/:id	get Tutorial by id
POST	api/tutorials	add new Tutorial
PUT	api/tutorials/:id	update Tutorial by id
DELETE	api/tutorials/:id	remove Tutorial by id
DELETE	api/tutorials	remove all Tutorials
GET	api/tutorials?title=[kw]	find all Tutorials which title contains 'kw'
```
## Project Structure
```
app
  config
    db.config.js
  controllers
    tutorial.controller.js
  models
    index.js
    tutorial model.js
  routes
    tutorial.routes.js
node_modules
package-lock.json
package.json
server.js
```
 
– db.config.js exports configuring parameters for MySQL connection & Sequelize.
– Express web server in server.js where we configure CORS, initialize & run Express REST APIs.
– Next, we add configuration for MySQL database in models/index.js, create Sequelize data model in models/tutorial.model.js.
– Tutorial controller in controllers.
– Routes for handling all CRUD operations (including custom finder) in tutorial.routes.js
## Run Server
Run with command:
```
node server.js.
```
