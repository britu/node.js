# Abbreviation
`
  ### DevDependencies : module only required during development
  Syntax: npm install --save-dev 
  ### Dependencies : modules wihic are required at runtime. 
  Syntax: npm install --save
  ### nodemon : tools that automatically restarting the node aplication when file changes in the directory are dected.
  Syntax: npm install --save--dev nodemon
  or : npm install --save -D nodemon
`

## Node introduction
``Node. js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient, perfect for data-intensive real-time applications that run across distributed devices.
- JavaScript Runtime(NOT a language or a framework)
- Built on the V8 JavaScript engine(Same a Google Chrome)
- written in C++
- Esentially allows us to run JavaScript code on the server
``
## Why use node
`
- Fast, efficient and highly sclabale
- Event driven, non-blocking I/O model
- works on a single thread using nonblocking I/O calls
- Supports tens of thousands concurrent connections
- Optimizes throughput & scalability in apps with many I/O operations
- all of this makes Node.js apps very fast & efficients
- Popular in the Industry and use for backend and front
`
## Best Types of Projects for NODE
`
- REST API & Microservices
- Real Time Services (Chat, Live Updates)
- CRUD Apps - Blogs, Shopping Carts, Social Networks
- Tools & Utilities
Short Answer: Anything that is not CPU intensive
`
##  NPM - NODE PACKAGE MANAGER
`
- Install 3rd packages(frameworks, libraries, tools, etc)
- Packages get stored in the "node_modules" folder
- All dependencies are listed in a "package.json" file
- NPM scripts can be created to run certain tasks such as run a server
EXAMPLE: 
  npm init: Generates a package.json file,
  npm install express: Installs a package locally,
  npm install -g nodemon: Installs a package globally
`
## NODE MODULES
`
- Node Core Modules(Path, fs, http, etc)
- 3rd party modules/packages installed via NPM
- Custom modules(files)
EXAMPLE:
  const path = require('path')
  const myFile = require('./myFile')
`
# LET'S BEGIN
- open the terminal and begin with node environment setup

## npm install for node_modules
 `
 which is in the package.json will be install
 `
## npm init: Generates a package.json file,
`
npm init and follow the instruction
`
## Run any js file from terminal
`
  node index : type this in index.js (console.log("hello from index.js"))
`
## Run object from page and import:
`
#### person.js : page (Object)::

  const person = {
    name: 'John Doe',
    age: 30
  }

module.exports = person;

#### in (Class base) need to make constructoture
  class Person{
    constructor(name, age){
      this.name = name;
      this.age = age;
    }

    greeting(){
      console.log(`My name is ${this.name} and I am ${this.age}`)
    }
  }

  module.exports = Person;

------ index page::
  ##### 1. This is called Module Wraper Function
  ( :: Example::
   : (function(exports, require, module, __filename, __dirname))
  )
  const Person = require('./person');

  //Now we can initiate Person Object

  const person1 = new Person('John Doe', 30);

  person1.greeting();
`
### 2. Followed up example
`
console.log(__dirname, __filename);
common js and es6
`
# NODE CORE MODULE
`
  Ref: https://nodejs.org/docs/latest-v13.x/api/os.html
`
## NODE path Module
`
  //Base file name
  console.log(path.extname(__filename));
  //Create path object
  console.log(path.parse(__filename));
  //Concatenate paths
console.log(path.join(__dirname, 'test', 'hello.html'));
`
## NODE FS (File System) Module
 // Create folder
fs.mkdir(path.join(__dirname, '/test'), {},(err) => {
  if(err) throw err;
  console.log('folder created....')
})
------
## Create file and read
fs.writeFile(path.join(__dirname, '/test', 'hello.txt'),
  'Hello World!',
 (err) =>{
  if(err) throw err;
  console.log('File written to .....');
})

## Rename File
//Rename File
fs.rename(path.join(__dirname, '/test', 'hello.txt'), path.join(__dirname, '/test', 'helloworld.txt'), (err) => { 
  if(err) throw err; 
  console.log('File renamed...console.');
});
`
## Platform Check
`
  const os = require('os');

  //Platform
  console.log(os.platform());

  // CPU Arch
  console.log(os.arch());

  // CPU CRE INFO
  console.log(os.cpus());

  //free memory
  console.log(os.freemem());
  //Total memory
  console.log(os.totalmem());

  //Home dir
  console.log(os.homedir());

  //Uptime
  console.log(os.uptime());
`
## URL MODULES
`
  const url = require('url');

  const myUrl = new URL('http://mywebsite.com/hello.html?id=100&status=active');

  //Serialized URL
  console.log(myUrl.href);
  console.log(myUrl.toString());

  //Host (Root domain)
  console.log(myUrl.host);
  //Hostname
  console.log(myUrl.hostname);
  //Path name
  console.log(myUrl.pathname);
  //Serialized query after the ? 
  console.log(myUrl.search);
  //Params object
  console.log(myUrl.searchParams);
  //add param
  myUrl.searchParams.append('abc', '123');
  console.log(myUrl.searchParams);
  //Loop through params
  myUrl.searchParams.forEach((value, name)=>console.log(`${name}: ${value}`));
`
## HTTP Module
const http = require('http');
//create server object
http.createServer((req, res) => {
  //Write Response
  res.write('Hello world');
  res.end()
}).listen(5000, () => console.log('server running...'))