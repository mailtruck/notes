# rename all files and folders in dir with underscores
```
find -name "* *" -print0 | sort -rz | \
  while read -d $'\0' f; do mv -v "$f" "$(dirname "$f")/$(basename "${f// /_}")"; done
```