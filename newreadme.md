## Node Modules
In the terminal access the  project directory, type npm init. enter through the object. pull up the project in vs Code and add an index.js file. creat another .js file to the project. the name should be related to your goal.

## Create the array
Create your array in your second .js file. Creat a variable with words that relate to your array so you can lead yourself through your assignment. then under the array state module.exports = foodList, preparing the array to be exported.
```js
const foodList =["Pasta", "Burgers", "Chicken", "Mangos"]
module.exports = foodList;
```
## Export your array to index.js
create a variable and use the following syntax to access your exported .js array.

```js
const foodList = require("./favfoodlist.js");
```
## Using the for loop to print the array.
following for loop starting at the 0 index accesses the array length  and increases to access all items in the array. the console log(foodlLst) prints the array to your terminal..
```js
for(let i = 0; i < foodList.length; i++ ){
    console.log(foodList[i]);
}
```
## Experimenting with npms
explore npmjs for great npms to expirament trhough your js files and log though teminal. make sure you use the correct syntax to fetch the informations from these npms. first line expoerts the npm and the second passes a random one liner. 

```JS
var oneLinerJoke = require('one-liner-joke');
var getRandomJoke = oneLinerJoke.getRandomJoke();
```
## Puttin both the foodlist and custom Npm together

# NODE AND EXPRESS README 

## CREATING A NEW NODE PROJECT
Create a new folder in your project directory through terminal
```
mkdir node-proj
```
## NPM Initialize
Make sure that you are in the project folder and type the following in the prompt
```
npm init -y
```
the `-y` added to `npm init`, allows you to select the defalt values for the `packsgae.json` files

## Create an index.js file
Make sure you are in the project folder and use the touch command.
```
touch index.js
```
## Open the project up in VS Code
In the terminal,use the code . command, to open the project.
``
code .
``
## test the js file 
```js
console.log('Hello')
```
test your file out in terminal with
```
node idex.js
```
## Creating Modules

Inside the initial project folder creat anothe .js file name it relavent like `module.js` then in you module.js file add the following co
de to export 
## Exporting Modules, Importing Modules

```js
module.exports.beBasic = () => "That's so fetch!"
```
this line of code adds a key value pair to our module.exports object.

then in your index.js file add  import your module
```js
const myModule = require('./Module.js');

console.log(myModule.beBasic());
```
the `require`function takes one path to the file that contains the the modules you are exporting.

now, in the console, run 
```
node index.js
```
The exported module will only contain the code that is encapsulated in the module.exports object.


## NODE PACKAGE MANAGER (NPM)
THrees types of Node modules are
- Core Modules(fs) 
- Local Modules (that you create)
- Third Party Modules
NPM is the largest open-source software registry in the world. It includes a website, a registry of Node Packages, and a command line interface that allows us to easily incorporate packages into our programs.


## NPMs I have used
### Nodemon
nodemonis a package manager thaat restarts the application everytime you sav changes to your node. to istall type the following in the comand line:
```
npm i -g nodemon
```
-g allows to install nodemon globally so it doesnt matter what directory we are in.

### Moment
moment is a date formatting module.
to istall type in command:
```
npm i moment
```
### one-liner-joke
a funny 3rd party Node Module which can provide one line joke randomly or from specific tag

This module contains more than 2200 one line jokes.


## Express
Express is a light-weight, web application framework for writing Restful APIs in Node.js.


New Directory for your express project
```
mkdir express
```
Initialize Node
```
cd express
npm init
```

Installing Express
```
npm i express
```

### Create index.js
```
touch index.js
```
### import the express module
in the the index.js
```js
const express = require('express');
```
### Create express app instance
index.js
```js
const express = require('express');
const app = express();
```


### routes
A route is a combination of a URL pattern and HTTP Verb.

In our express project 

## The Request and Response Objects

### Request
The Request object, frequently abbreviated to req, contains all the data we would ever need about the actual request that came in. What are they requesting? What browser are they using? Bunches of other stuff. But mostly we will using three keys inside of it:

### Respone

The Response object, or res for short, is what we use to send something back to the user's browser, or more formally, send a response to the request. There are a number of functions we can use:

### Example of Route

in index.js
```js
const express = require('express');
const app = express();

app.get('/', function(req, res) {
    res.send('Hello, World!');
});

app.listen(8000);
```
then run nodemon
### Examples of request
```js
app.get('/greet/:name', (req, res)=>{
    res.send(`hello ${req.params.first} ${req.params.last}`)
})
app.get('/mulitply:x:y', (req, res)=>{
    res.send(`the answe ${req.params.x*req.params.y}`)
})
app.get('/add/:x:y', (req, res)=>{
    res.send(`the answer ${req.params.x + +req.params.last}`)
})
```

## Views
Writing text to a web page using res.send(), each page will display different HTML, we'll have several HTML files, or `views`.

### example of a views setup
```js
app.get('/', function(req, res) {
  res.sendFile(__dirname+'/views/index.html');
});
```
Must always create a `views `directory.

##Templates

### EJS: Embedded Javascript
One of the most popular JS template engines for express.

install
```
npm install ejs
```

set view to ejs
```js
app.set('view engine', 'ejs');
```
Rename your html files to ejs and relpace your res.send to res.render your route should look like this.
```js
app.get('/', function(req, res) {
  res.render('index.ejs');
});
```
## Templating with variable
Create an object in index.js
```js
app.get('/animals', function(req, res) {
    res.render('animals', {title: 'Hate Animals', animals: ['scorpions', 'spiders']})
  });
```
Now you can embedd the tital variable into index.ejs

```html
<html>
  <head>
    <title>Home Page</title>
  </head>
  <body>
    <h1><%= title %></h1>
  </body>
</html>
```
<% %> tags embedd the JS

## partials
Partials
Partials can be used to modularize views and reduce repetition.
examples of partials
```html

partial/header.js
  <header>
    <img src="http://placekitten.com/500/500">
  </header>
```
```html
index.js
<!DOCTYPE html>
<html>
  <head>
    <title>Home Page</title>
  </head>
  <body>

    <%- include('../partials/header.ejs') %>

    <h1>Hello, <%= name %>!</h1>
```
## INstall EJS layouts
```
npm install express-ejs-layouts
```
require the module to add layouts
```js
var express = require('express');
var app = express();
var ejsLayouts = require('express-ejs-layouts');

app.set('view engine', 'ejs');
app.use(ejsLayouts);

app.listen(3000)
``` 
In an ejs folder within views( which must be called layout.js)

Template like follwows
```html
<!DOCTYPE html>
<html>
<head>
  <title>Title name</title>
</head>
<body>
  <%- body %>
</body>
</html>
```

Now we can set up a few more routes and views
```html
<h1><%= title %></h1>
<ul>
  <% animals.forEach(function(animal) { %>
    <li><%= animal %></li>
  <% }) %>
</ul>
```

```js
app.get('/animals', function(req, res) {
  res.render('animals', {title: 'Favorite Animals', animals: ['sand crab', 'corny joke dog']})
});
```

## EJS CONTROLLERS
We have been placing all routes into index.js when creating a Node/Express app, but this can get cleaned up by grouping related routes and separate these groups into separate files.then the files will go into a controllers folder.
```js
controller middleware

app.use('/faves', require('./controllers/faves'));
```
we also replace app with router like this
```js
var express = require('express');
var router = express.Router();

router.get('/foods', function(req, res) {
  res.render('faves/foods', {title: 'Favorite Foods', foods: ['coconut', 'avocado']});
});

router.get('/animals', function(req, res) {
  res.render('faves/animals', {title: 'Favorite Animals', animals: ['sand crab', 'corny joke dog']})
});

module.exports = router;
```