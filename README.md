# Snippets, links and notes

## Git

git init  
git add / git remove --cached  
git commit -m "comment"  
git remote add <name> <url>  
git push <name>  

git status  -s  

git diff  (shows changes)  

##### Squash  

git commit --amend --no-edit  (merge to last commit)  
git commit --amend -m "new message"

git rebase -i HEAD~3   (HEAD = @)

##### Reseting  A - B - C (master)

|...| HEAD | index | Working Dir |
| ---| ---| ---| ---|
|git reset --soft B  | B | C | C |
|git reset (--mixed) B  | B | B | C |
|git reset --hard B  | B | B | B |

###### More:  
git reflog (log all ref updates)

git show  =  git show HEAD
git show <commit-id>: filename > oldfile.html (creating a file to open in editor)





## Node.js / Express

https://expressjs.com/  
https://www.npmjs.com/package/body-parser  
https://www.npmjs.com/package/request
https://www.npmjs.com/package/nodemon  


npm init  
npm install express

=======
---CORS middleware
https://expressjs.com/en/resources/middleware/cors.html  

var express = require('express')  
var cors = require('cors')  
var app = express()  

app.use(cors())  

--------------  
```
const express = require('express');
```
*Node.js body parsing middleware.
Parse incoming request bodies in a middleware before your handlers, available under the req.body property.*
```
const bodyParser = require('body-parser');
```
*Request is designed to be the simplest way possible to make http calls.*
```
const request = require('request');

const app = express();

app.use(bodyParser.urlencoded({extended: true}));
```

*To serve static files such as images, CSS files, and JavaScript files, use the express.static built-in middleware function in Express. For example, use the following code to serve images, CSS files, and JavaScript files in a directory named public:*
```
app.use(express.static("public"));
```

*The HTTP GET method is used to request a resource from the server. Requests using GET and HEAD methods should only retrieve data (server must not change its state). If you want to change data on the server, use POST, PUT or DELETE methods.*
```
app.get("/", function(req, res) {
  res.sendFile(__dirname + "/index.html");
})
```

*The HTTP POST method is used to send data to the server, or to create/update a resource. Unlike GET and HEAD requests, the POST requests may change the server state.*
```
app.post("/", function(req, res) {
  var crypto = req.body.crypto;
  var fiat = req.body.fiat;
  request('https://apiv2.bitcoinaverage.com/indices/global/ticker/' + crypto + fiat, function(error, response, body) {
    var data = JSON.parse(body);
    var price = data.last;
    var currentDate = data.display_symbol;

    res.write("<p>The current date is " + currentDate + "</p>");
    res.write (`<h1>The ${crypto}${fiat} price is ${price} </h1>`);


    res.send();
  })

})
```
*Binds and listens for connections on the specified host and port.*
```
app.listen(3000, function () {
  console.log("Server is running on port 3000");
})
```
### In Form tag we need to add action= "/" and method = "post"

### process.env.PORT when deploying to Heroku || 3000

# MONGO DB

*show databases inside mongo shell*  

```
show dbs
```

*Create or insert collection of documents (single data record), where collection is the name*  
```
db.collection.insertOne( {
  name: "sue",
  age: 26,
  status: "pending"
  })

  show collections
```

# MONGOOSE



# HTML/CSS

https://codeguide.co/  
https://randoma11y.com/  
https://code.tutsplus.com/tutorials/the-30-css-selectors-you-must-memorize--net-16048  
https://ia.net/topics/responsive-typography-the-basics  
https://www.smashingmagazine.com/2014/04/understanding-css-timing-functions/  

IMPORTANT
- https://www.bootstrapcdn.com/fontawesome/
- https://cdnjs.com/libraries/animate.css/

https://unicode-table.com/en/  
https://www.w3schools.com/cssref/css_default_values.asp  
https://tympanus.net/codrops/css_reference/  


# JS
- https://underscorejs.org/#  
- https://github.com/michalsnik/aos
