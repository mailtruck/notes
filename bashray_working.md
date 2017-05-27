```
wholist=(
     'Bob Smith <bob@example.com>'
     'Jane L. Williams <jane@example.com>'
     'Eric S. Raymond <esr@example.com>'
     'Larry Wall <wall@example.com>'
     'Linus Torvalds <linus@example.com>'
   )
wholist=(*)
#
# Count the number of possible testers.
# (Loop until we find an empty string.)
#
count=0
while [ "x${wholist[count]}" != "x" ]
do
   echo 
   echo ${wholist[count]}
   if [ ${#wholist[@]} ]; then
   count=$(( $count + 1 ))
done
```
