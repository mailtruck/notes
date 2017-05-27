# node notes

### Jade Syntax: 
* http://naltatis.github.io/jade-syntax-docs/

### list the contents of a directory
```
var fs = require('fs')
var folder = './folder_to_list_files/'

fs.readdir(folder, function (err, files) {
  console.log(files)
})
```

### express basic auth
```
var basicAuth = require('basic-auth');

var auth = function(req, res, next) {
  var user = basicAuth(req);
  function unauthorized(res) {
    res.set('WWW-Authenticate', 'Basic realm=Authorization Required');
    return res.send(401);
  };

  if (!user || !user.name || !user.pass) {
    return unauthorized(res);
  }

  if (user.name === 'USERNAME' && user.pass === 'PASSWORD') {
    return next();
  } else {
    return unauthorized(res);
  }
};
```
