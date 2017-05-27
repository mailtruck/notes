```
find . -type f -name "*filenametosearchfor*"
```

```
find . -type f -exec grep -q "text to find in a file" {} \; -exec echo {} \;

```