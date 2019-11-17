# Snippets, links and notes

## Git

git init
git add / git remove --cached
git commit -m "comment"
git remote add <name> <url>
git push <name>

git status

## Node.js / Express

https://expressjs.com/
https://www.npmjs.com/package/body-parser
https://www.npmjs.com/package/request

```
const express = require('express');
const bodyParser = require('body-parser');
const request = require('request');

const app = express();

app.use(bodyParser.urlencoded({extended: true}));

app.get("/", function(req, res) {
  res.sendFile(__dirname + "/index.html");
})

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

app.listen(3000, function () {
  console.log("Server is running on port 3000");
})
```
