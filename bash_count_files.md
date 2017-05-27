```
#!/bin/bash

shopt -s nullglob

myfiles=(/home/ubuntu/tttest/*.xml)

#printf "%s\n" "${myfiles[@]}"

count=${#myfiles[@]}
zero=0
echo $count
if [ "$count" = "$zero" ]; then
  echo no xml files found - shoot off an email to alert the authorities
else
  echo there are some files here 
fi

```