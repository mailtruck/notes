

find . -type f -exec grep -q "<description></description>" {} \; -exec mv {} ../headlines/ \;