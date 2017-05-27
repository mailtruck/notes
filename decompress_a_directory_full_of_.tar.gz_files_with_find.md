# decompress a directory full of .tar.gz files with find

```
find . -type f -name "*.tar.gz" -exec tar -zxvf {} \;
```