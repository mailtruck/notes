```
useradd --create-home -d /home/ftp/USERNAME -s /usr/sbin/nologin -p PASSWORD USERNAME
// Make sure username is all lowercase. I don't know why you need to put the password in above command and then reset it in below command but it works 
// Then: 
passwd USERNAME
// You will be prompted for the password enter it again
//Then:
chown 2700 /home/ftp/USERNAME
```


http://www.xorbin.com/tools/sha256-hash-calculator