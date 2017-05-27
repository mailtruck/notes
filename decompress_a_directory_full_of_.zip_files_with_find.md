# decompress a directory full of .zip files with find

```
find . -type f -name "*.zip" -exec unzip {} \;
```