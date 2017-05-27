# Synchronous Read Files in Node


```
var fs = require('fs')

var readDir = function (dir) {
  return fs.readdirSync(dir)
}
```