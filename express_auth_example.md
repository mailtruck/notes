# express auth example

> http://stackoverflow.com/questions/16360293/how-to-log-out-from-basicauth-express

```
var express = require('express'),
    http = require('http'),
    app = express();

app.use(express.favicon()); // prevent interference during test
app.use(express.bodyParser());
app.use(express.cookieParser());
app.use(express.session({ secret: 'winter is coming' }));

app.use(function (req, res, next) {
  if (!req.session.authStatus || 'loggedOut' === req.session.authStatus) {
    req.session.authStatus = 'loggingIn';

    // cause Express to issue 401 status so browser asks for authentication
    req.user = false;
    req.remoteUser = false;
    if (req.headers && req.headers.authorization) { delete req.headers.authorization; }
  }
  next();
});
app.use(express.basicAuth(function(user, pass, callback) {
  callback(null, user === 'basic' && pass === 'basic');
}, '***** Enter user= basic & password= basic'));
app.use(function (req, res, next) {
  req.session.authStatus = 'loggedIn';
  next();
});

app.use(app.router);
app.get('/secure', function (req, res) {
  res.send([
    'You are on a secured page.',
    '&lt;br>',
    '<a href="./secure">Refresh this page without having to log in again.</a>',
    '&lt;br/>',
    '<a href="./logout">Log out.</a>'
  ].join(''));
});
app.get('/logout', function (req, res) {
  delete req.session.authStatus;
  res.send([
    'You are now logged out.',
    '&lt;br/>',
    '<a href="./secure">Return to the secure page. You will have to log in again.</a>',
  ].join(''));
});

http.createServer(app).listen(3000, function(){
  console.log('Express server listening on port 3000. Point browser to route /secure');
});
```