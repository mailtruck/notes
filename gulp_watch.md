I notify wait shell script:

```
#!/bin/bash
cd /var/www
dir='/dir/to/watch'
inotifywait -m $dir -e modify |
  while read file; do
    gulp css-fef // change css-fef to whatever your gulp task is
    echo 'rebuilding' >> buildlog
  done
```