# sc-node-express

## What is Node?
Node or node.js is the run time environment which works on standalone machines and http component is added in node.js to even work on server side. Also known as server side javascript. Basically node.js is designed by using the V8 javascript engine. 

## What is Express?
To develop web applictions node.js require a framework. So express is the framework.

## Steps how to do sc-node-express application.

### Create Cloud Repo

1. Create cloud repo 
2. Add README.md (always!)
3. Add .gitignore - when ever we select .gitignore file it ask for to choose templet,without choosing the repo wont create. So being node-express application we have to choose node.

### Clone Repo 

1. Clone the repo down to your machine. In your git projects root folder, git clone <yoururl> 
2. cd into that folder
  
### Build the App

```
npm init
```
to start a package.json file.package.josn is the file which holds metadata of the project like dependecies,version,scripts,keywords,author etc. Make note of your entry point - name this app.js instead of index.js.
```
npm install express 
```
to add express dependency
Open folder in VS Code (code .)
Create app.js and customize it to say Hello world.
```
npm install 
```
to install dependencies. Before next command all the dependencies have to be installed which are present in package.json
```
node app.js
```
to start
### View
![](https://raw.githubusercontent.com/sudheera96/sc-node-express/main/Screenshot%20(243).png)

> The above process created node_modules folder. So we can ignore that vast folder by .gitignore file. 
> As we choosed .gitignore with node template so node_modules ignore automatically.

### 4 files - app.js, package.json, package-lock.json, .gitignore

#### app.js 
It is the file used to create web application by using express framework. 
```
const express = require('express')
```
We are importing express package to the express value.
```
const app = express()
```
Initiating application by calling express method.
```
const port = process.env.PORT || 3000
```
In order to deploy application in server application rather than specify the exact port it's better to specify a particualr port number and no port number. Because to work server application on any port.
```
app.get('/', (req, res) => {
  res.send('Hello world from Sri Sudheera`s app!')
})
app.get('/about', (req, res) => {
    res.send(' You have requested the about page! ')
  })
app.get('/contact', (req, res) => {
    res.send(' You have requested the contact page! ')
  })
app.get('/help', (req, res) => {
    res.send(' You have requested the help page! ')
  })
app.get('/help/:topic', (req, res) => {
    res.send(` You have requested the help ${req.params.topic} page! `)
  })
  
app.listen(port, () => {
  console.log(`Example app listening at http://localhost:${port}`)
})

```

get() is HTTP verb. res and req are the two objects of express also know as response and request. Request object request the server for the information asked by the client and Response object sends that information to the client. /: is used to include a parameter. What ever might client enters the response will available.

#### Difference between package.json and package-lock.json
| package.json                                                            | package-lock.json                                                                |   
|-------------------------------------------------------------------------|----------------------------------------------------------------------------------|
|The package. json is used for more than dependencies - like defining project properties, description, author & license information, scripts, etc.| The package-lock. json is solely used to lock dependencies to a specific version number |                    number 
                                                                                                                                                
### Prepare for Heroku

For node.js heroku is one of the best server application.

* In package.json, add (type, don't copy)  "engines": { "node": "15.x" }  - it require for heroku to have latest version of node.
* In package.json, add a new scripts entry: "start" : "node app.js" - in order to use default port 3000 by heroku use the start script.
* Have the app listen on process.env.PORT || 3000 - add this line app.js file.

### Heroku App Config (deploy on push to repo)

* Login to Heroku (use same email as you use for GitHub)
* Create a new app (I use the same name as my repo if the name not taken already, orelse use other name)
* Deploy / Deployment method = GitHub (and connect to your repo)
* Deploy / Enable Automatic Deploys. 
* Settings / Get the app URL

## Heroku Link
* https://cs-node-express.herokuapp.com/
* https://cs-node-express.herokuapp.com/about
* https://cs-node-express.herokuapp.com/contact
* https://cs-node-express.herokuapp.com/help
* https://cs-node-express.herokuapp.com/help/login
* https://cs-node-express.herokuapp.com/help/:topic

## Reference
[what is process-env-port](https://stackoverflow.com/questions/18864677/what-is-process-env-port-in-node-js)

[Difference between package.json and package-lock.json](https://stackoverflow.com/questions/45052520/do-i-need-both-package-lock-json-and-package-json#:~:text=No.-,The%20package.,to%20a%20specific%20version%20number).

[Express](https://flaviocopes.com/express/)






